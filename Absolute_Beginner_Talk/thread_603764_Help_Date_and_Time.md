---
title: "Help Date and Time"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-11-05
I have a weird issue with Date and Time on Ubuntu. I'm dual-booting with XP on another drive. When I correct the time on Ubuntu, XP time is messed up. When I correct the time on XP, Ubuntu time is messed up.

Has anyone else encountered this? Synchronizing with internet servers doesn't seem to work...

---

### Post by deadgobby on 2007-11-05
Check you BIOS time clock. So when your computer boot up, go into BIOS and see what date and time is. If you change the clock on BIOS, it may sync up with booth O/S.

---

### Post by kebes on 2007-11-05
> **Nessa said:**
> I have a weird issue with Date and Time on Ubuntu. I'm dual-booting with XP on another drive. When I correct the time on Ubuntu, XP time is messed up. When I correct the time on XP, Ubuntu time is messed up.

Has anyone else encountered this? Synchronizing with internet servers doesn't seem to work...

I'm guessing you're running into the timezone problem (is the difference in the times equal to your timezone?). This is a well-established problem when dual-booting, since Linux assumes the hardware clock represents UTC, whereas Windows assumes the hardware clock represents local time. Luckily Linux provides ways to change this to fix it.

If you go into your clock settings, I think you can select between setting the hardware as either UTC or local time. Try switching that, and then adjust the time and see if it "sticks."

If not, you can do this via the commandline in Linux (this is based on notes when I had to fix this on a Fedora machine... but it should work in Ubuntu also):

1. In Linux, set the date and time to what it currently is. For example if it's 10:20am local time:
```
sudo date -s 10:20
```
2. Then update the hardware clock accordingly, and force this to be considered "localtime":
```
sudo /sbin/hwclock --systohc --localtime
```
3. Check to make sure it looks right:
```
sudo /sbin/hwclock --localtime
```
4. Sync between hardware clock and system clock:
```
sudo /sbin/hwclock --hctosys --localtime
```

Now Linux should consider the clock to be "localtime" ... which should be identical to what Windows is doing. So after rebooting into Windows, the time should look right.


Hope that helps.

---

### Post by yogo on 2007-11-06
@Kebes

Those are some nice tricks.

I removed the system clock...ie remove from panel, now when I want to try and add the clock back in, it comes in the form of an icon. How do I get it back digital?

TIA

---

### Post by Melhisedek on 2007-11-06
I have similar problem in that that clock is always one hour back from the one I set it to. When I right click and choose "adjust time and date" I can change it but it doesn't show in system tray (still one hour back) I tried manually updating and syncing with servers but still it shows "wrong" time... Should I try and change time zone perhaps? We are on daylight savings now here in Sweden. Ubuntu maybe doesn't know it or something?

XP clock is ok no matter what I do in Ubuntu

---

### Post by rbo83 on 2007-11-07
The easiest way to fix the problem is to update the /etc/default/rcS file which looks something like this :

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no


SImply change the line UTC=yes to UTC=no if you keep you system clock in local time, and then reboot. As you reboot, check your BIOS's time to set it to your local time. The reboot will cause the /etc/adjtime file to be automatically updated to set the time to LOCAL instead of UTC

Does someone know how to submit a change request to UBUNTU to add the UTC/LOCAL option (same date/time option display as in Fedora) : i.e. have an option to tell the system whether the system clock is a UTC or LOCAL value. It is just a checkbox. I don't know why this is not available in the UBUNTU Date/Time menu.

---

### Post by Nessa on 2007-12-20
My BIOS clock is right.

@kebes, I kept getting an error saying the time stamp is too far in the future.

@rbo83, looks like that did the trick.

Thanks for all the help guys. :)

---

### Post by boaz60 on 2008-01-02
I've done everything suggested in this thread and I still can't resolve my clock issues with a win2k dual boot and gutsy.

I've narrowed it down that somehow ubuntu and my bios clock can't get along by a 7 hour difference.

I'm not sure but it seems to have something to do with UTC, because I think I might be 7 hours from UTC in my MST time zone.  

Anyways, when I set my bios clock to the correct LOCAL time, which is what win2k wants it to be, Ubuntu boots 7 hours behind my system clock.  If at this point, I check the UTC box ON, the clock displays the correct time.  That's great, until I reboot, the hwclock now is now 7 hours AHEAD of the actual time, which causes win2k to also match the now wrong system clock.

As I mentioned before, I've done everything in this thread.  Even when I did the command to sync the /sbin/hwclock --hctosys --localtime , it looked fine until I rebooted and ubuntu had set my hw clock 7 hours ahead.

I'm using an intel brand motherboard.

edit:  Well after some more tinkering, I've had success with a combination of syncing hctosys localtime commands while setting UTC to ON.  I had been trying painstakingly to get it to work with UTC off, which caused the problem mentioned above by itself, but with the sync command and UTC ON ubuntu seems to get along with my bios now.  So UTC off doesn't always seem to be the correct choice with these type of problems.

Thanks.

---

### Post by bindatype on 2008-01-02
No one has suggested using network time which I find odd. Set it by hand via

```

$ sudo ntpdate time-a.nist.gov

```
You can use your favorite time server...I happen to use nist.

[http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/](http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/)
This link gives a more thorough tutorial about setting it up. 

Once you use network time you won't have to worry about setting it up again--so long as you have a network connection.

---

