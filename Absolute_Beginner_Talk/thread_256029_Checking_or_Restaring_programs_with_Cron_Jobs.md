---
title: "Checking or Restaring programs with Cron Jobs?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by HedonismBot on 2006-09-12
Hi all,

Great luck so far on this forum, need a little help with Cron jobs though:

I work in development, but, as I'm still a Linux n00b, need a little help with setting up a cron job!

I have two scripts that need to be monitored and restarted if the go down.

First, there is the Sportsticker listener I wrote.  It's in 
/home/sportsticker/sportsticker.php

The second is the Java client that Sportsticker gave us.  The Java file 
is in /home/sportsticker/sportsticker.php

I run it by doing 'java -jar WireParserClient2.02a.jar 
./WireParserClient.properties'

So, the Sportsticker listener needs to be run first.  It can be run as a daemon by appending & to the end of the command line right?.  Then the Java client from Sportsticker needs to be run.

Is there a way to only start them if they're not running? Or should I just have it happen at an interval. I can set-up cron to do one thing, but Don't know about conditions or even the syntax too much.

Anyone can help me, that'd be great!

(I'm so very close to abandoning my Windows ways for good!) =D>

---

### Post by whizbaby on 2006-09-12
What you want to do is possible but non-trivial with cron (I believe you would have to write a script that tests if your other scripts are running and start that with cron, too). Try with inittab, here's a little overview of the whole matter (basically cron is for definite points in time (e.g. 12:00:00 or @reboot)):

[http://aplawrence.com/Unixart/startup.html](http://aplawrence.com/Unixart/startup.html)

---

