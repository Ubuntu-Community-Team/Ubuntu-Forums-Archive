---
title: "Ubuntu keeps hanging suddenly in 7.10"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by nmrao on 2007-12-21
My Ubuntu keeps hanging all of sudden.  Is there any way to diagnose this problem? Like, some log file or something that I can check?


System Specs:
Pentium 4  3.00GHz
RAM 2 GB
Powercolor ATI Radeon XPRESS 200 Series
80GB  Hard Drive

---

### Post by Lord_Dicranius on 2007-12-21
What are you doing on the machine when it hangs?  What apps do you have open?

---

### Post by pjones0404 on 2007-12-21
are u running desktop effects?

i find that my system will hang occasionally even when surfing the web if effects are on. if i disable them it never hangs. just a thought.

---

### Post by fain on 2007-12-21
You could check /var/log/messages or check the gui version in system->administration->system log

If you need real time during hangs

You could set up a ssh server and log in from another machine and then
```
sudo tail -f  /var/log/syslog
```
(you might not need to "sudo")
this will show the last few lines of "syslog" and update as needed.
you could do this for any log file for that matter. kern.log etc

---

### Post by MC_LA on 2007-12-21
I'm having the same problem. Doesn't seem to have any correlation to the app that's running. I have two flavors: one where I still have mouse control, but I nothing responds; and two where I have no response whatsoever.  The only fix for either is a hard reboot.  Around the same time I started having problems with my main menu where my Applications menu went blank.

---

### Post by fain on 2007-12-21
> **MC_LA said:**
> I'm having the same problem. Doesn't seem to have any correlation to the app that's running. I have two flavors: one where I still have mouse control, but I nothing responds; and two where I have no response whatsoever.  The only fix for either is a hard reboot.  Around the same time I started having problems with my main menu where my Applications menu went blank.

Have you tried "ctrl-alt-f1" to drop into a terminal instead of hard rebooting?
If you can, execute
```
sudo /etc/init.d/gdm restart
```
if using Gnome

---

### Post by MC_LA on 2007-12-21
Thanks, that was very useful. It helped me find the problem...which was that I was low on disk space. :oops:

---

### Post by fain on 2007-12-21
Glad to be of help :)

---

### Post by MC_LA on 2007-12-24
Turns out my low disk space wasn't the only cause for the hanging. I fixed the low disk space problem, and the hanging is less frequent, but still occurring on a regular basis.  Is Ubuntu 7.10 just not that stable ?

---

### Post by ~LoKe on 2007-12-24
7.10 is plenty stable.  Try checking your hard drive for corruption.

```
fsck /dev/sda1
```
Change sda1 to the name of your device.  You can find out what it is by typing this into the terminal:
```
sudo fdisk -l|grep /dev
```
You must unmount the disk you're trying to fsck.  If it's your /root partition, you're better off just running a LiveCD and doing it that way.

---

### Post by fain on 2007-12-24
Ive had this problem a couple times. If you can ctrl-alt-f1 into a terminal then its not ubuntu thats crashing, its gnome. In which it could be a problem with your video card driver.

---

### Post by MC_LA on 2007-12-24
Thanks for the reply, I learned some new things.  

From what I can tell, my drive looks good. Here are the results from the fsck command:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda1: clean,  113702/7028736 files, 10206120/14040802

---

### Post by mivo on 2007-12-24
I started having this problem about a week ago, and I had not rebooted in the two weeks prior (so perhaps an update caused it). What fixed it for me was to completely turn off the "desktop effects" (System -> Preferences -> Appearance), and then turn them back on. I know this does sound a little esoteric, but I haven't had a problem since. :) The symptoms were that the system would suddenly freeze, though the mouse could still be moved. Restarting X (ctrl+alt+backspace) did not work, but the REISUB method allowed for safe restarting (holding down ctrl+printscreen and typing REISUB at the same time).

I also experienced these troubles in the Gutsy on a different computer, but that was prior to the release, so it may have been caused by something else.

---

### Post by MC_LA on 2007-12-25
Thanks!!!  It's only been about a day, but every since I  turned off the visual effects,  I haven't had any hanging. I think you nailed the problem. Thanks again!!!

---

### Post by MC_LA on 2007-12-29
Yup, it's confirmed, almost a week and no hanging, a new record for me. The only difference has is turning off the the effects.....Thanks for the advice.

---

### Post by mivo on 2007-12-30
Have you tried to turn the effects back on to see if the hanging remains fixed? I could safely use effects again after turning them off and back on. :)

---

### Post by MC_LA on 2008-02-16
so it's been almost two months and not another hang. I've been very impressed with the stability of Ubuntu 7.10.  Thanks

I haven't tried turning effects back on since I don't really miss it...and why fix it if it ain't broke. :)

---

### Post by jcitguy78 on 2008-02-16
This is off topic but **fain** what did your mobo cost and where did you get it. the stats on it look sweet.

---

### Post by fain on 2008-02-17
> **jcitguy78 said:**
> This is off topic but **fain** what did your mobo cost and where did you get it. the stats on it look sweet.

Hey, I cant remember how much it was, like 159 or something probably gone down by now. I got it at newegg, I do remember that. If i was gonna buy something now theres better ones out.

 But this one has done me good. The only problem I've had out of it is a compatibility issue with AMD cool n' quite and my Asus Nvidia 8800 Ultra. Not sure which to blame though. I had dual 7600gt's by evga and had no problems.

O and i have never officially used the built in wifi It does to appear to see wireless networks in the Network-manager.
I just did a test on my home wireless and had no luck. It might take some tweaking. I have no use for it.

---

