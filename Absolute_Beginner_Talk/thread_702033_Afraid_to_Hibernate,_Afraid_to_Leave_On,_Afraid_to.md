---
title: "Afraid to Hibernate, Afraid to Leave On, Afraid to Shut Down"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Teasdale on 2008-02-19
I've read that hibernate doesn't work too well in Ubuntu. When I did it, it ended at a black screen and I wasn't sure whether it was cuing me to turn off the power button or if it just hadn't worked. So I haven't wanted to try it again.

When I shut down, it ends on an Ubuntu screen and I'm not sure whether it's cuing me to turn off the power button or whether it's locked up right there. If I do press the power button, I have to press it for a few seconds - and sometimes that reboots it! That can't be right, so I'm hesitant to do that.

So generally, I've been leaving the computer on. But then I read a thread that said that Ubuntu can fail to boot after a power outtage - all data is lost, Ubuntu has to be reinstalled - and we get enough thunderstorms here that sometimes our power will go out during the night for a few hours.

Today I decided to turn off the computer since I was going to be out all day. I left it on the Ubuntu screen because, really, I'm not sure whether I'm supposed to turn it off at that point. When I got back later, I turned the computer back on (by holding down the power button so that it rebooted, I guess) but it didn't start up quite right. It went to a black screen and started doing some kind od dev/hda1 scan and then flashed the Ubuntu screen and then went black and then it did start up fine - but that process was scary enough that I don't think I want to try that again.

Every option sounds scary - what is everyone else doing with their Ubuntu at the end of the day?

---

### Post by JoshuaRL on 2008-02-19
Well, it shouldn't do that.  What happens if you put the following into the terminal:
```

shutdown

```
What errors come up?

And the scan was probably an automated thing that it does every 30 reboots.  If it didn't bring up any errors you should be fine.

---

### Post by ryanhaigh on 2008-02-19
It sounds like hibernation isn't working for you as the computer shouldn't be displaying anything so I would recommend not using hibernate but rather just shutting down, boot times are very good on the latest releases anyway.

As far as ubuntu failing to boot after a power outage the only reason that would happen is that the disk was not unmounted cleanly and needs to be checked as it would in Windows. Sometimes you will need to intervene to fix the filesystem as it may not be able to do everything automatically but this has been rare for me, if it does you may end up with some files in a special lost+found directory which are files the check was able to recover but doesn't know where they belong again this has been rare for me.

Your final issue is actually associated with the disk check as well, because your system didn't unmount ubuntu had to check the integrity of the filesystem (checkdisk in windows) that is what scan /dev/hda1 was doing. Once it determined that there were no problems or was able to repair any problems found the boot process continued and everything was back to normal.

My recommendation for you would be to get a UPS which will allow you to shutdown your system cleanly when you lose power. If you don't want to do that (they can be expensive) just shut down the system when you are not using it. It would be useful to know the specs on your system to help diagnose these issues.

---

### Post by Teasdale on 2008-02-20
> **JoshuaRL said:**
> 
And the scan was probably an automated thing that it does every 30 reboots.  If it didn't bring up any errors you should be fine.

It *did* say something like "34 boots since check" or something similar.

I do have a UPS, but if the power stays out more than 30 minutes, it would lose power.

"It would be useful to know the specs on your system to help diagnose these issues."

What kind of specs?

1.66GH processor
240 MB Ram
32 bit processor
AMD Athlon processor ACPI x86
NVidia card

Those specs?

Tonight, when I turn off for the night, I'll try typing shutdown in the terminal.

---

### Post by Wiebelhaus on 2008-02-20
If your in an area such as myself with storms and faulty electrical grids you shouldn't run a mission critical or expensive (1,000 inch HDTV ) electrical system of any kind without [this]("http://www.apc.com/products/family/index.cfm?id=21"):

[IMG]http://www.apc.com/resource/images/family/primary/21_fam.jpg[/IMG]

Once you use one , you will never not ... again.

It's worth the 40 bucks man , seriously.

---

### Post by ryanhaigh on 2008-02-20
There is a package available to allow you to monitor your UPS and shutdown when it loses power I dont have the serial cable required for comms with my UPS so I have never used it myself but I believe its called upsd and is in the repos.

---

