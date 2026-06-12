---
title: "[SOLVED] Noobie: Xubuntu is a CPU hog on my laptop"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Sonidos on 2007-10-25
Hey Folks, first time poster on the forum and new to Ubuntu/Xubuntu.

I have been messing around with my old Toshiba laptop.  It's a 2000 Satellite that was running Win ME with  a P3 Coppermine chip and 256M of memory and a 20G drive.

I had initially loaded the LTS version of Xubuntu and the laptop was flying.  I reloaded Win ME on the system to compare.  Now, I installed the Gutsy version of Xubuntu and the laptop is booting forever and applications take forever to load.

I checked the system resources and the CPU is running anywhere from 90 to 100%.  WOW!!!  Memory useage is running around 40 to 50%, so that is much better than ME, which hogs up to 75% most of the time.

Any clues on why Xubuntu seems to be slamming my CPU so hard and what can I do to restore performance?

Oh, and how do I access root to configure my system?

Thanks and I look forward to years of working with Ubuntu and Xubuntu!

---

### Post by -grubby on 2007-10-25
> **Sonidos said:**
> 

Oh, and how do I access root to configure my system?


you don't want to be root. What asks you to be root? Your root temporarily when you type in your password when the prompt for that comes up

---

### Post by scrooge_74 on 2007-10-25
you type sudo in a terminal followed by the command you need to do root things

type top on a terminal and check which app is taking over the resources

---

### Post by Sonidos on 2007-10-25
Ok...guess I got confused about when I need to access root.

It seems the CPU is getting smacked hard by gnome-system-mo 42% and Xorg 40%

---

### Post by lazyart on 2007-10-25
gnome-system-mo is probably gnome-system-monitor -- the exact app you are using to see what eating up resources.

---

### Post by scrooge_74 on 2007-10-25
If you are using Xfce4 you can take out all that gnome stuff that is slowing down your system

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

EDIT: if you use top on a terminal you are not using gnome-sys-monitor

---

### Post by Sonidos on 2007-10-25
This is good stuff.  Ok, its better now.  Down to about 25% to 30%.  Now if I can improve the boot up speed.  I saw something about a black screen and resolution settings.  Thanks!  I think I'm on my way!

---

### Post by scrooge_74 on 2007-10-25
To improve boot speed check this  thread on the Debian forum and in the Ubuntu forum

[http://forums.debian.net/viewtopic.php?t=14129&highlight=xfce4](http://forums.debian.net/viewtopic.php?t=14129&highlight=xfce4)
[http://www.ubuntuforums.org/showthread.php?t=329309](http://www.ubuntuforums.org/showthread.php?t=329309)

---

### Post by Sonidos on 2007-10-26
scrooge, thanks!

Ha!  I tried another suggestion from another thread and something happened and I got a kernel panic message and the laptop won't boot.  So I'll invest some more time in getting it right by sifting through the forum.

Thankfully, the laptop is something for the kids to browse and write reports for school and I'm in no hurry.

;-)

---

### Post by scrooge_74 on 2007-10-26
You can always try to boot in safe mode and fix last thing you did.

If the laptop is for kids to browse and work you can install Debian Etch, it should work pretty well and not use that many resources.  I know it first hand ;)

I am currently using Xfce4, Xfmedia, Firefox (Iceweasel), Skype, Gaim, tor, Boinc (for setiathome) and Open Office at the same time and usually my average work load is less than 25%

---

### Post by philinux on 2007-10-26
What does xfce look like compared to gnome desktop ? And what cant it do?

---

### Post by Sonidos on 2007-10-26
scrooge,

Awesome!!!  I'll give Etch a try tonight.  That pretty much fits the bill of what I wanted for the kids.  My preteen likes to chat with her friends and both kids have assignments to pick up from their school websites and produce on Word.  My son will get a kick out of having a computer that looks different from everything else he sees.

---

### Post by scrooge_74 on 2007-10-26
I also advice you to install Dansguardian, that will give you a little confort on the subject of pictures and websites not for kids. I have it install for my kids, it makes wonders screening websites.

As for Philinux question go to [http://xfce.org/](http://xfce.org/)  and take a look.  Xfce will do almost all the things Gnome can but lighter

---

### Post by Sonidos on 2007-10-26
Scrooge,

I've hit the motherlode!  Great- I've got a project for the weekend.  The kids will be thrilled.

Thanks for helping me get this off the ground.  The Toshiba laptop has been with me for a long time and its like a tank, so I hope to get another year or two of service from it.

---

### Post by scrooge_74 on 2007-10-26
Great to hear you have a good project for the weekend. i will probably be around during the weekend if you need help

---

