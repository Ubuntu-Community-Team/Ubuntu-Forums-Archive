---
title: "Black Screen After Boot Up"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by ishift on 2006-11-02
hey guys..

i have this recurring problem.

whenever i boot up my laptop the first time, after the splash screen (with the ubuntu logo and the progress bar underneath), the screen goes black.

the system is on, the lights are on, but the hard drive stops "working" and it just spits out a black screen. the only thing i can do is press the power button to reboot.

i was told that it could possibly be that x is not starting. however, i tried going through the recovery mode through the grub menu. even though i used the **startx** command, same thing happened.

what seems to be the problem? and how can it be fixed?

oh and my laptop specs are in my sig.

thanks in advance!

---

### Post by ishift on 2006-11-03
i forgot to add...

i have the savage s3 video card.

---

### Post by Paul41 on 2006-11-03
> i have the savage s3 video card.
I have seen someone else here having problems with the savage video card, but I don't remember if there was a resolutions. Try to search the forums for the savage video card.

---

### Post by docshawnc on 2006-11-03
Hi -
    The T22 does this as well.  Have a look here (it worked for me)
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21)

One other point, choose the 24 bit color option in config

---

### Post by ishift on 2006-11-03
thanks!

that worked. w00t. :)

---

### Post by sarangbapat on 2007-06-25
[FONT="Century Gothic"]
I am also experiencing the same problem,but the problem is slightly different. I installed ubuntu 7.04 on my 2nd partition and having a dual boot with windows. After I boot into ubuntu by selecting the grub entry,the screen goes blank. Then I need to press Ctrl+Alt+F1 in order to bring up the alternate console. After that ubuntu starts the booting process. If I dont press Ctrl+Alt+F1, then the blank screen remains as it is and nothing happens. (I actually kept the blank screen for 15 mins, but really nothing happens till I press Ctrl+Alt+F1.)  I dont type any command, nothing, just press Ctrl+Alt+F1 and continue booting. This is something really wierd!
[/FONT]

---

### Post by sarangbapat on 2007-06-25
[FONT="Century Gothic"]Forgot to add one customization i did while installation, I selected /dev/sda2 as grub install location. Not sure why ubuntu sets the name of my HDD as sda1, sda2, etc. Its a normal HDD(Samsung) and not USB.[/FONT]

---

### Post by Gipper P on 2007-06-25
I have a very similar problem to the first one - I will elaborate on my specific position to see if anything different should be done.

I installed Ubuntu 6.06 on my system, and that worked fine. I then decided to upgrade to 7.04 and therefore had to upgrade to 6.10 first. This happened without any problems: it only said that some packages weren't going to be supported. This happened again for the 6.10 -> 7.04 upgrade.

Now, once I start the 7.04 version, I get the ubuntu loading screen, with the logo and the progress bar. After this the screen is just black. The monitor light is still green, indicating that it is still receiving some kind of signal. 

Starting in recovery mode and using 'startx' creates the same situation. 

The computer that I am installing it on is a Pentium 4 2.8GHz, 512MB RAM, 60GB HDD, 128MB Ati Graphics.

Is there anything I can do to stop these blank screens?

Many thanks in advance for your help.

James

---

### Post by matthew871 on 2007-06-25
I have a similar problem and was about to start a new thread. 

Tried installing Ubuntu 7.04 on a blank 250 gig Western Digital HD using the "whole disk" option (second from the default in the installer). Installation seems to go well (despite having to use "safe graphics mode" to get to it) -- it tells me it is complete and needs to reboot, take the CD out, etc. So I do that, and then after the BIOS info scrolls past it stops at a black screen with a flashing cursor about six lines down. I tried pressing a bunch of random key combinations. Nothing happens, so I reboot and change drive order to get back to XP.

However, same install CD works fine on an older HD (also by Western Digital). So this is not a BIG problem, but wish I could use the newer, larger HD above for installation. 

Thanks if anyone can help. I have a GeForce 6600, and I formatted both drives in the same "quick format" manner inside XP.

---

### Post by Knoopd on 2007-06-25
I also have this problem.  I installed doing a dual boot with WinXP.  I have a ATI X800 in this thing.  When GRUB starts I get a blank screen.  Attempting to do the ALT-CTL-F1 thing does not work, nor any key combo that I attempt.  Going into recovery mode I can get things going by following the instructions I found in a post here.  At the prompt type:

wget [http://mylittleubuntuguide.com/files/ati](http://mylittleubuntuguide.com/files/ati)
sudo chmod +x ati
./ati
startx

I still get a blank screen if I do not boot into recovery mode and startx.  Normal boot still does not work.

---

### Post by blitzer on 2007-07-16
I used to have the same problem with an Ati Card I switched to Nvidia and the problem is gone.   I would have to boot 3 times before the log-in screen appeared and out of the blue the log-in would appear on the first boot.

I used the open source drivers (ati) using the code sudo dpkg-reconfiguer xserver-xorg and this did not help.

Sure would like to know what is happening ?

---

