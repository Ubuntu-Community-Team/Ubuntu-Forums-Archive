---
title: "problem with GNOME Settings Daemon"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by hardikorama on 2007-05-03
I just installed fiesty fawn and on start-up, was greeted by the following error message

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Message did not receive a reply (timeout by message bus)

GNOME will still try to restart the Settings Daemon next time you log in.
```

after a little googling, i installed drivers for my nvidia 6200 and it restarted. it is showing all ok in the 'restricted drivers manager'. but i m still getting the error i mentioned above. please help.

---

### Post by Kobalt on 2007-05-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/61381](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/61381) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Make sure the two lines of your local interface is set properly in your /etc/network/interfaces, looking like this : > auto lo
iface lo inet loopback

---

### Post by hardikorama on 2007-05-03
yes. they are exactly the way you stated.

---

### Post by hardikorama on 2007-05-03
bump

---

