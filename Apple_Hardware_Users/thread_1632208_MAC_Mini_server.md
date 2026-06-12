---
title: "MAC Mini server"
date: 2010-11-27
forum: Apple Hardware Users
---

### Post by steam willy on 2010-11-27
Hi all

I am running a small mac mini server with 10.04 LTS server and a wondering if anyone could give me hint on what software I should use for monitoring the health status of the machine itself. The problem is basically that I just set up the new server (the old one died of a logical board error) :( and i am not sure anymore on the environment conditions ( like temp, CPU usage time, hard disk uptime  and so one) and I'd like, from time to time, have a look at the machine.

On the machine there is already logzilla (as a web application) running so mysql , php, apache is available

---

### Post by RandomJoe on 2010-11-28
I don't have the very latest Mini model (mine is about a year old) so not sure everything would still work the same...

I'm using lmsensors and hddtemp for monitoring temperature, and found my Mini ran considerably warmer than I wanted (especially the hard drive).

I found a shell-script somewhere called 'applesmc.sh' that allows for setting temp limits and minimum fan speed.  Only issue (as I read from my notes from a year ago, don't remember the details!) is that the script as I got it was buggy - I made some changes to suit my desires, and it now works fine.  The Mini runs much cooler, and the fan ramps up much sooner when the CPU load increases.

'sensors' gives me fan speed, and three temps.  Don't remember right off what each is, they're always within a couple degrees of each other.

'hddtemp /dev/sda' gives me the drive temp.

'smartctl -a /dev/sda' gives me SMART info from the drive.

I never set up anything to remotely or automatically monitor things, I just ssh in and manually check things from time to time.  I keep meaning to set up some automatic logging or at least alarming, just never have gotten around to it.

Here's where I got the 'applesmc.sh' script:
[http://stargate.solsys.org/mod.php?mod=faq&op=extlist&topicid=27&expand=yes#118](http://stargate.solsys.org/mod.php?mod=faq&op=extlist&topicid=27&expand=yes#118)

---

