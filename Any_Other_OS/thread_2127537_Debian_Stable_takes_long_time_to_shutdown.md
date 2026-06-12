---
title: "Debian Stable takes long time to shutdown"
date: 2013-03-20
forum: Any Other OS
---

### Post by linuxyogi on 2013-03-20
Hi,

My debian stable box is recently taking a lot of time to shutdown.

How to troubleshoot this issue ?

---

### Post by mamamia88 on 2013-03-20
Why are you shutting it down?  Doesn't that defeat the purpose of debian stable?    Are you getting a root prompt to enter your password before shutdown?  Try shutting it down form a terminal.  Try running shutdown as root in a terminal and see how long it takes

---

### Post by 2F4U on 2013-03-20
> **linuxyogi said:**
> Hi,

My debian stable box is recently taking a lot of time to shutdown.

How to troubleshoot this issue ?

If I were you I would start by looking into the log file (/var/log/messages, if I am not mistaken) and see if there is something unusual. It could be an application or service that takes a long time to respond to the shutdown request.

---

### Post by tancrackers on 2013-03-21
> **mamamia88 said:**
> Why are you shutting it down?  Doesn't that defeat the purpose of debian stable?    Are you getting a root prompt to enter your password before shutdown?  Try shutting it down form a terminal.  Try running shutdown as root in a terminal and see how long it takes
Shutting down is proper protocol in order to maintain the computer's longevity.

And try updating when you first turn on the computer, because keeping fakeroot temporarily enabled will prompt your password upon shut down.

---

### Post by tgalati4 on 2013-03-21
```
sudo shutdown -h now
```
Keep a camera handy to capture any screen messages that float by.

---

### Post by linuxyogi on 2013-03-21
[IMG]http://i851.photobucket.com/albums/ab73/img2010_album/shutdown.jpg[/IMG]

---

### Post by mips on 2013-03-21
if you dont't use bluetooth & IPv6 disable it and se what gives.

---

### Post by tgalati4 on 2013-03-21
So it's taking a lot of time at the command line login?  Use a stopwatch and time how long it takes from the time "login:" shows up until complete shutdown.

Check your log files after your next boot in /var/log.  Note the clock time that you shut down.  Scroll through the logs at that time and look for error messages.

---

