---
title: "Long Boot Times, Start-up Program Problems &amp; Susupend Issues in Feisty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by HokkaidoHillbilly on 2007-04-24
Hey everybody,

Since upgrading to Feisty from Edgy, I've noticed 3 main problems which, while they aren't major or anything, are somewhat annoying to say the least:

1) Boot times from when I first turn on the computer to when I can finally log-in seem to have increased substantially, sometimes taking as long as 2 minutes.  I know that this isn't related to my CPU (a dual core T2500/2GHz) as Edgy seemed to boot up in a flash.  I went ahead and installed bootchart and am including the log ping if it can help anybody to figure out what might be wrong.

2) For some reason, I can't seem to add anything to to the start-up menu via System->Preferences->Sessions.  I mean, I can add programs (gmailchecker & Skype, for instance), but after I reboot or log out/in, it's like I never added those programs and the start-up menu doesn't show them.  Could this be related to whatever's causing the long boot times, i.e. problem 1?

3) I've set up the computer to suspend when I close the laptop lid, but whenever I open it back up, it never comes back to life and I'm forced to reboot.  Are there any fixes for this that I'm not aware of, or is this just a problem w/ Dell M1210's?

Thanks!



HH ;)

---

### Post by HokkaidoHillbilly on 2007-04-24
bump ;)

---

### Post by HokkaidoHillbilly on 2007-04-25
One last bump, and if I don't get a hit, I'll separate my questions into different threads.

Anyone?  Anybody?  Buller? ;)

---

### Post by tedrogers on 2007-05-02
I am having these same issues nearly!

My boot time is over 2 minutes.

I've tried disabling services that aren't required (like Bluetooth and Printing), commented out unused interfaces in my /etc/network/interfaces file and made sure that feisty isn't trying to sync the time with server on boot (which caused some problems in edgy i believe).

Anyone know what's going on? This is really annoying the hell out of me. Win-blows boots faster than this!!

---

### Post by tedrogers on 2007-05-02
Bumpity bump bump

---

### Post by HokkaidoHillbilly on 2007-05-07
Well, at least it's nice to see somebody else w/ this same problem.  The weird thing is that it seems like the more I use Feisty the longer the boot times take, yet when I boot into XP, it flies.

Now that Dell's gonna be supporting Ubuntu maybe they'll do something to fix issues like this, but I'm certainly not gonna hold my breath.  :roll:

---

### Post by Lucifiel on 2007-05-07
Yeah, Feisty has like 2 mins worth of boot-time for me. I even tried enabling parallel booting and other configurations but they did nothing for me.

---

### Post by silent1643 on 2007-05-07
heh why not just leave your computer on 24/7 :)

---

### Post by Lucifiel on 2007-05-07
> **silent1643 said:**
> heh why not just leave your computer on 24/7 :)

High electricity bills, anyone?

Please do remember that electricity can be pretty expensive for those living in certain cities and countries.

---

### Post by silent1643 on 2007-05-07
[link]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed") might be of some use
or even this [link]("http://ubuntuforums.org/showthread.php?t=89491")

---

### Post by tedrogers on 2007-06-08
Nah....were not talking about optimising for speed here.

Here is the solution I think.

[http://ubuntuforums.org/showthread.php?t=450121&page=2]("http://ubuntuforums.org/showthread.php?t=450121&page=2")

It's all to do with the new kernel having problems with some CD / DVD drives (especially Lite-On and NEC - and I have both!)

You need to add "irqpoll" at the end of your /kernel argument in the menu.lst.

See the post above for instructions.

Hope this helps you all.

---

