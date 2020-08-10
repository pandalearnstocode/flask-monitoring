# Steps to reproduce

## Delete existing db & Create a DB

```bash
cd app
rm fmd.db
sqlite3 fmd.db
.tables
.exit
```


## Adding config file in `main.py`

```python
app = Flask(__name__)
dashboard.config.init_from(file='/config.cfg')
dashboard.bind(app)
```


## Structure of config file

```
[dashboard]
APP_VERSION=1.0
GIT=https://github.com/pandalearnstocode/flask-monitoring.git
CUSTOM_LINK=dashboard
MONITOR_LEVEL=3
OUTLIER_DETECTION_CONSTANT=2.5
SAMPLING_PERIOD=20
ENABLE_LOGGING=True

[authentication]
USERNAME=admin
PASSWORD=admin
GUEST_USERNAME=guest
GUEST_PASSWORD=['dashboardguest!', 'second_pw!']
SECURITY_TOKEN=cc83733cb0af8b884ff6577086b87909

[database]
TABLE_PREFIX=fmd
DATABASE=sqlite:////app/fmd.db

[visualization]
TIMEZONE=Europe/Amsterdam
COLORS={'main':'[0,97,255]',
        'static':'[255,153,0]'}
```

## Resources:
* [Docker image](https://github.com/tiangolo/meinheld-gunicorn-flask-docker)
* [Flask Monitoring Dashboard](https://medium.com/flask-monitoringdashboard-turtorial/monitor-your-flask-web-application-automatically-with-flask-monitoring-dashboard-d8990676ce83)