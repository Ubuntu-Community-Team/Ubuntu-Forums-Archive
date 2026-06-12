---
title: "G3 Blue and white install problem"
date: 2008-10-02
forum: Apple Hardware Users
---

### Post by jpates20 on 2008-10-02
Hi 

I have a g3  tower (blue and white) new world, 300 and 400 mhz 256 ram ,lost all data no possible way to retrieve it, i replaced the HD with a 15 GB WD HD ,that was pulled out of a old compag, replace the cd rom it wes spent! live cd works great of xubuntu, hardware seems to be working, but the network ,when the live cd is loaded the date sed august 1957. I like to put a fresh copy Xubuntu, is there any thing more i need to do? here the error log file......thanks   john

Traceback (most recent call last):
File "/usr/bin/ubiquity", line 130, in ?
install(sys.argv[1])
File "/usr/bin/ubiquity", line 54, in install
wizard = ui.Wizard(distro)
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 171, in __init__
self.customize_installer()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 300, in customize_installer
self.tzmap = TimezoneMap(self)
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1615, in __init__
self.tzdb = ubiquity.tz.Database()
File "/usr/lib/python2.4/site-packages/ubiquity/tz.py", line 182, in __init__
self.locations.append(Location(line, iso3166))
File "/usr/lib/python2.4/site-packages/ubiquity/tz.py", line 168, in __init__
today = datetime.datetime.today()
ValueError: microsecond must be in 0..999999

---

### Post by paul_mcl on 2008-10-02
Your battery is out. You can buy the another (new) one or use ntpdate to get time from network time sever each time, for example:
```
ntpdate pool.ntp.org
```

---

### Post by jpates20 on 2008-10-03
> **paul_mcl said:**
> Your battery is out. You can buy the another (new) one or use ntpdate to get time from network time sever each time, for example:
```
ntpdate pool.ntp.org
```

Thanks you

---

