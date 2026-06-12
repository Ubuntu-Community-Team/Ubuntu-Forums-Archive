---
title: "Netatalk up and running but cannot use it as TimeMachine"
date: 2017-06-03
forum: Apple Hardware Users
---

### Post by mattiash on 2017-06-03
Hello all!
I hope I have put this the right department. ;)

I have setup an server 17.04 and installed and configured Netatalk to be used as a TimeMachine option for my macOS clients.
The share do show itself under the Time Machine preferences in macOS but... when I choose it it pops up a login dialog, as it should, I log in with an Linux account for the server that works (checked) and hit Login, after a short while it disappears and I get thrown back to the choose dialog for where I have to choose what share I want to us. And around around we go.

I have been fiddling in afp.conf and AppleVolumes.default and /user/local/etc/afpd.conf. Using the following guides:
[http://dae.me/blog/1660/concisest-guide-to-setting-up-time-machine-server-on-ubuntu-server-12-04/](http://dae.me/blog/1660/concisest-guide-to-setting-up-time-machine-server-on-ubuntu-server-12-04/)
[https://www.outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/](https://www.outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/)
[https://kofler.info/netatalk-3-konfiguration-fuer-time-machine-backups/](https://kofler.info/netatalk-3-konfiguration-fuer-time-machine-backups/)

So how do I get macOS not to popup the same login again and again?

In AppleVolues.default I added this:
```
:DEFAULT: options:upriv,usedots
```




In /user/local/etc/afpd.conf I added this:
```
[Global]
; Global server settings
vol preset = default_for_all_vol
hostname = TimeCapsule
log file = /var/log/netatalk.log
log level = default:info
uam list = uams_dhx.so,uams_dhx2.so
save password = yes
disconnect time = 168
dsireadbuf = 96
sleep time = 24
tcprcvbuf = 524288
tcpsndbuf = 524288
dircachesize = 131072
keep sessions = yes
mimic model = Xserve

[default_for_all_vol]
file perm = 0664
directory perm = 0774
;cnid scheme = cbd
valid users = @usergroup

[Homes]
basedir regex = /home
cnid scheme = dbd
home name = Home: $u

[TimeMachine]
path = /TimeMachine
time machine = yes
valid users = user1 user2 user3 user4
vol size limit = 1000000

```

I have an share (link) at root level called TimeMachine. Permissions are correct since the users can login via apple-K to that share and read/write.

So what have I done wrong?

---

### Post by howefield on 2017-06-03
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ian-weisser on 2017-06-03
Do you have an HFS+ partiton for Time Machine to detect and use?

---

