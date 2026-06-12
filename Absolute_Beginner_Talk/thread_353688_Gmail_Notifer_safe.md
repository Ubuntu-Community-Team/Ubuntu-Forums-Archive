---
title: "Gmail Notifer safe?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by SnowPunk98 on 2007-02-05
[http://gmail-notify.sourceforge.net/](http://gmail-notify.sourceforge.net/)

Is that program safe to use, since my username and password are being put into it and its not official from Google it is a little concerning. Of course I feel that it is legit but I just want to double check =D

---

### Post by raul_ on 2007-02-05
No problems here, and never heard of any :) It's the same thing of being afraid to input your messenger password in GAIM or your e-mail password in Thunderbird

---

### Post by closetpirate on 2007-02-05
I hope not I have been using it since it came out a year or more ago

---

### Post by Spr0k3t on 2007-02-05
One of the greatest features of Open Source.  You can get the source, check it out on your own, and compile the source to be sure it's safe.  I too run this applet and love it.  I just wish the applet image would change if there is an unread email, rather than just the notification.  However, I've not worked with the configuration outside of id/pass.

---

### Post by wildkarde on 2007-02-05
> **Spr0k3t said:**
> One of the greatest features of Open Source.  You can get the source, check it out on your own, and compile the source to be sure it's safe.  I too run this applet and love it.  I just wish the applet image would change if there is an unread email, rather than just the notification.  However, I've not worked with the configuration outside of id/pass.

May I suggest [checkgmail]("https://sourceforge.net/projects/checkgmail/").
Seems to be what you're looking for.

---

### Post by tagginannie on 2007-02-05
> **wildkarde said:**
> May I suggest [checkgmail]("https://sourceforge.net/projects/checkgmail/").
Seems to be what you're looking for.


If you don't like any of those try _[Google Toolbar Beta]("http://tools.google.com/firefox/toolbar/FT3/intl/en/")_ for Fire Fox

Suzy:KS
[ ]("http://tools.google.com/firefox/toolbar/FT3/intl/en/")

---

### Post by OrangeCrate on 2007-02-05
I use Todd Long's Gmail Manager extension to manage two Gmail accounts. You can check it out here:

[https://addons.mozilla.org/firefox/1320/](https://addons.mozilla.org/firefox/1320/)

---

### Post by SnowPunk98 on 2007-02-05
CheckGmail looks nicer, I guess ill give both a try and see how they work out.

---

### Post by DarkReverend on 2008-03-19
I use gmail-notifer myself - its included in the kubuntu package repository now too.  One thing to note is that it will store your password in plain text, so be aware of that at least.

I've had a problem with mine crashing, and not exiting cleanly (the tray icon will be gone, but the space will still be blocked)  this is because one process still hangs around.  I also have 3 gmail addresses, and you can only store one password.

To manage this, I wrote this script
```
 for pid in `ps -Ao pid,command | grep -e '\(gmail-notify\|notifier.py\)' |  grep -v grep | sed "s/^[ ]*//" | cut -d\  -f1` ; do kill -9 $pid ; done

sleep 3

cp /home/me/scripts/gmail_files/address1.notifier.conf /home/me/.notifier.conf
gmail-notify &
sleep 2
cp /home/me/scripts/gmail_files/address2.notifier.conf /home/me/.notifier.conf
gmail-notify &
sleep 2

```
it kills the two processes for each gmail-notifier, and then replaces the existing notifier config file with a copy of one thathas the login info stored.  You can copy the last three lines and do it for as many addresses as you have.

---

