#Raspberry Pi Alarm Clock
###Introduction
It’s an alarm clock that syncs with our Google Calendar. It could fetch our events information and set alarm automaticlly. 
###Usage
- *httplib2*:  
First download httplib2 library and unzip it. Then:
```
$ cd httplib2-0.9.2/
$ sudo python setup.py build
$ sudo python setup.py install
```

- *apiclient*:
```
$ sudo pip install --upgrade google-api-python-client 
```

- *APSchedule*:   
For APScheduler, we need to install version 2.1.2, if you have already installed APScheduler, you need to uninstall it.
```
$ sudo pip uninstall apscheduler
$ sudo pip install apscheduler==2.1.2
```

### Design
Since google calendar provide API for us to get upcoming ten events, we could use this API connecting with our google calendar. When first run quickstart.py, it will attempt to open a new window or tab in our default browser for the authorization. Then we could get the upcoming ten events.

![GitHub](http://coderxiaoyu.com/alarmclock/img/calendar1.png)

For setting alarm, we get the json file of each event and obtain the start time information. We convert current time and start time into the same format and compare. If there are same, we use mpg123 to play the alarm music stored in a certain path. To add alarm at specific time/date, just head to Google Calendar and create an Event. 

![GitHub](http://coderxiaoyu.com/alarmclock/img/calendar2.png)

Since we could set our event time correct to minute in google calendar, in our program we use scheduler to trigger our event synchronization program every 60 seconds.