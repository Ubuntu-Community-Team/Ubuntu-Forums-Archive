---
title: "CPU 100%, temp 72*C"
date: 2010-05-05
forum: Apple Hardware Users
---

### Post by Joey Hogan on 2010-05-05
Hi all!

I just installed Ubuntu 10.04 64-bit on my Macbook 4,1. I let it sit, completely idle, for about half an hour, and when I came back the fan was running very loud. I checked out System Monitor and it reported that one of my CPU cores was running at 100% while the other was at about 4%. Opening terminal and typing "sensors" shows that sensor #2 is at 72*C, and most of the other sensors were at 50*C or so. The bottom of the laptop was warm to the touch, but it definitely wasn't 72* warm.

Does anyone know what might be the issue with this?

---

### Post by buntuLo on 2010-05-05
next time it happens, launch top and see which process is using so much cpu.

---

### Post by clymir on 2010-06-07
I just came back to my idle computer and found the same problem,
and running system monitor on 3 second refreshes it reported
 **sudo was consuming 85%**
and it had been for over ten minits.

Thats a lot of clock cycles to be working on a task. 

I had just closed GFTP prior to this.

I also noticed my system took longer than normal to boot up this morning.

ANY IDEAS?

Thanks.

---

### Post by sha.goyjo on 2010-06-07
What is your cpu governor? Ondemand? Performance? You should be able to tell with the cpu panel applet.

---

### Post by linuxopjemac on 2010-06-07
You might want to install the applesmc-dkms package which takes care of things like the temperatures and keyboard backlight. It can be installed from the Mactel PPA.

[http://mac.linux.be/content/karmic-koala-macbook-41](http://mac.linux.be/content/karmic-koala-macbook-41)
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by alexmurray on 2010-06-07
> **linuxopjemac said:**
> You might want to install the applesmc-dkms package which takes care of things like the temperatures and keyboard backlight. It can be installed from the Mactel PPA.

[http://mac.linux.be/content/karmic-koala-macbook-41](http://mac.linux.be/content/karmic-koala-macbook-41)
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)
How is that relevant to figuring out which process is using 100% CPU? Besides applesmc simply exposes the temperature values so you can read them, it doesn't enable any automatic temperature regulation - that is all handled by the internal SMC hardware chip. 

Anyway, if at 100% CPU the temp is still only at 72C I'd say that is a good indication the automatic thermal regulation of the SMC is working very well - otherwise I'd expect the temp to be around 95C.

---

### Post by clymir on 2010-06-08
> **sha.goyjo said:**
> ...You should be able to tell with the cpu panel applet.

 Thanks for responding. No idea. My installation reported that the cpu panel applet was unsupported. Im running seriously elderly hardware.  Never the less, I did find it really bizzare that ANYTHING would be running at 100% at that time, much less SUDO, and much less for over ten minits, which is as big as my log is.

I observed a second occurrance that was 5 minits of update-apt-xapian-index. Whatever that is.  

Maybe I just hadnt noticed these events in 8.04.  but in veiw of the number of potential back doors in our present Global Embrace of software and network,  I wish these events were declared up front, as you would expect from anyone rattling around in your attic at odd hours;  disappearing before you find your flashlight.

I think I'll write a sniffing extract of TOP and see if I cant make my logs more intelligent. Thanks again.

---

### Post by clymir on 2010-06-16
> **clymir said:**
>  I think I'll write a sniffing extract of TOP and see if I cant make my logs more intelligent. Thanks again. Well, I came up with this but don't laugh, Im a heavy duty mechanic, not a programmer: 

```
sudo nice -n -10 top | grep -P "[2-9]{1}[0-9]{1}\.[0-9]{1}" | sed 's/    / /g' | sed 's/[[]39\;49m//g' | sed 's/[[]m//g' | sed 's/(B//g' >'/tmp/top.txt'
```For all that was sed, I didnt get much accomplished:
was trying to snip the 0018 stuff out of there also. :)

and I cant think of a way to boot it at startup either...
so I just added this to Startup Applications:

```
gnome-terminal --geometry=23x10 -t TOP -e 'sudo nice -n -10 top'
``` ...all afterI toggled all the defaults in TOP off manually first (except %CPU for applications) and
"W"rote the changes to the config file of course.

Now to find an environment variable for Up and Dowload traffic, and CPU temp, and maybe I'll try my hand at piping this to a Perl throttle and screamer. Don't say I didnt warn you.

> My primary fear about cyberspace is that people don't understand the  risks...
 Leverage Unpredictability...Embrace Simplicity...Watch the Watchers...
- [BRUCE SCHNEIER]("http://www.schneier.com/essay-062.html")

---

