---
title: "Problems rebboting after upgrading to 11.10"
date: 2011-10-20
forum: Apple Hardware Users
---

### Post by canhoto on 2011-10-20
Hi.

I upgraded my G4's Xubuntu to 11.10 (from within the 11.04's update manager), and, when rebooting just after installing, I get the following message:
> WARNING bootdevice may be renamed. Try root=/dev/sda3
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/vmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
- Missng modules (cat /proc/mudules; ls/dev)
ALERT! /dev/hda3 does not exist. Dropping to a shell!

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initranfs)

Any help, please?

Thanks

---

### Post by Boris1975 on 2011-10-20
Same problem here with Ubuntu PPC.
I found out that when pressing TAB while chosing if booting from cd or hdd you can boot if chosing 'old', but this is no final solution.
 
Boris

---

### Post by conal on 2011-10-20
Same here, on two different powerpc boxes - I went back to other distros on both but I'm keen to know when someone finds a fix! A few other people have commented on this in other threads.

---

### Post by canhoto on 2011-10-20
> **Boris1975 said:**
> Same problem here with Ubuntu PPC.
I found out that when pressing TAB while chosing if booting from cd or hdd you can boot if chosing 'old', but this is no final solution.
 
Boris

You mean pressing TAB 
-when the screen with the several drives/system appearsafter holding the alt key
or
-while rebooting, instead of the alt key?

Because pressing TAB usually is used when the yaboot prompt appears, which is not the case.

And what happens when you choose "old"?


Thanks

---

### Post by canhoto on 2011-10-20
> **conal said:**
> Same here, on two different powerpc boxes - I went back to other distros on both but I'm keen to know when someone finds a fix! A few other people have commented on this in other threads.
Xubuntu 11.04 was ok, although quite slow (that's why I did the upgrade, to try to fix that). Xubuntu 10.04 and 10.10 run well, too.

But I would like to fix the problem and run 11.10 instead of reinstalling a new system again (which it will happen if I try to downgrade, I think). I did that once (I completely installed Xubuntu after problems with Ubuntu), and I had to set my preferences, copy my documents from a Mac, etc. (I didn't do a backup because most of the documents were on the mac).

Is there a way to downgrade without a clean reinstall?

---

### Post by Boris1975 on 2011-10-20
> **canhoto said:**
> You mean pressing TAB 
-when the screen with the several drives/system appearsafter holding the alt key
or
-while rebooting, instead of the alt key?
 
Because pressing TAB usually is used when the yaboot prompt appears, which is not the case.

I will check this when being at home. As far as I remember I could chose between booting Gnu/linux pressing l or booting from CD pressing c. Pressing TAB shows different possibilities. One was 'old'. 
> **canhoto said:**
> 
 
And what happens when you choose "old"?
 
 
Thanks
With 'old' Unity started.

---

### Post by conal on 2011-10-20
> Xubuntu 11.04 was ok, although quite slow (that's why I did the upgrade, to try to fix that). Xubuntu 10.04 and 10.10 run well, too.

Yes, Xubuntu 11.04 totally hogged the CPU on both these boxes that's why I upgrded too.  Now I have gone back to Xubuntu 10.10 on one and MintPPC on the other, as they were orginally. Super-annoying to waste so much time re-installing, but then I usually find I spend much more time trying to fix a problem!

---

### Post by canhoto on 2011-10-20
> **conal said:**
> Yes, Xubuntu 11.04 totally hogged the CPU on both these boxes that's why I upgrded too.  Now I have gone back to Xubuntu 10.10 on one and MintPPC on the other, as they were orginally. Super-annoying to waste so much time re-installing, but then I usually find I spend much more time trying to fix a problem!

Sure. It's probably what I'm going to do if there's no fiz to the problem. Actuall, the only strong reason why I wanted to upgrade to 11.04 was the possibility to use LibreOffice instead of OpenOffice, which I'm not sure we can do with 10.10 or 10.04. OpenOffice gave me some problems with Ubuntu (maybe it was because I messed up things). Of course, 11.04 is graphical very nice, also, but that's not the most important.

---

### Post by Boris1975 on 2011-10-20
> **conal said:**
> Yes, Xubuntu 11.04 totally hogged the CPU on both these boxes that's why I upgrded too. [...]
I had the same problem. 11.10 solved it... If no someone could offer a sollution to the booting problem, I would be happy again. :-) I think I am going to try a clean install...

---

### Post by rsavage on 2011-10-20
Reboot:
[http://ubuntuforums.org/showthread.php?t=1861871](http://ubuntuforums.org/showthread.php?t=1861871)

CPU hog:
[http://ubuntuforums.org/showthread.php?t=1859152](http://ubuntuforums.org/showthread.php?t=1859152)

---

### Post by Boris1975 on 2011-10-20
Thanks a lot! I will give it a try.

---

### Post by drs305 on 2011-10-20
canhoto,

If you boot the LiveCD and then download/run the Boot Info Script it will generate a file called RESULTS.txt

This file will show us the status of your boot files. Please post it's contents and we may be able to see what is causing your problems (if it's boot-related).

You can get to the script download page by clicking the "BIS" link in my signature line.

---

### Post by canhoto on 2011-10-20
> **rsavage said:**
> Reboot:
[http://ubuntuforums.org/showthread.php?t=1861871](http://ubuntuforums.org/showthread.php?t=1861871)

CPU hog:
[http://ubuntuforums.org/showthread.php?t=1859152](http://ubuntuforums.org/showthread.php?t=1859152)


Thanks, rsavage. You've been a good help: thanks to you I changed from raw Ubuntu to Xubuntu which is great. But now I have this problems. Two questions:

- The solution for de CPU hog, if I understood, is to upgrade to 11.10, right?:D
- As for the solution for the reboot problem, I'm not sure if yaboot runs. But doesn't the difference between sda and hda drives related to the fact they are SATA vs. IDE? Sorry for my ignorance.

Another question: is the CPU problem happening only with Xubuntu 11.04, I mean, if I reinstall (with Xubuntu 10.04 cd), I then install the Lubuntu packages, I run Lubuntu and then I upgrade it to Lubuntu 11.04, will it be ok?

---

### Post by rsavage on 2011-10-20
> **canhoto said:**
> 
- The solution for de CPU hog, if I understood, is to upgrade to 11.10, right?:D

canhoto and everyone else who is affected by the bug should comment on the thread I linked.  I've been trying to get to the bottom of it with the help of Ms Daisy who's been a real star.  She's brand new to linux too.  If 11.10 is the fix then that needs to be confirmed by one of you!

> **canhoto said:**
> 
- As for the solution for the reboot problem, I'm not sure if yaboot runs. But doesn't the difference between sda and hda drives related to the fact they are SATA vs. IDE? Sorry for my ignorance.
There have been changes in the kernel.  hda is now sda.

> **canhoto said:**
> 
Another question: is the CPU problem happening only with Xubuntu 11.04, I mean, if I reinstall (with Xubuntu 10.04 cd), I then install the Lubuntu packages, I run Lubuntu and then I upgrade it to Lubuntu 11.04, will it be ok?
It's a hardware/firmware problem with your particular cd rom drive.  Changes to the kernel/udev/udisks have brought it to light. Fix xubuntu 11.10 before trying lubuntu.  It should be easy as per link.  If you want to try Lubuntu 11.04 then install it from the 11.04 mini CD, but it is likely to suffer from the same problem as xubuntu 11.04.  I am only speculating btw as I don't really know.

---

### Post by canhoto on 2011-10-20
I typed "old" in the second yaboot prompt and, apparently, I'm on Xubuntu 11.10, with a aparently healthier CPU usage. What does this "old" thing mean? Can I configure the yabbot from here?

---

### Post by canhoto on 2011-10-20
In the second yaboot prompt, I just typed "old" and, apparently, I'm in  the 11.10 Xubuntu (with a healthy CPU usage!). What does this "old"  mean? Can the yaboot fix be done from this "old" (new) system?

The reason why I tried that is because I couldn't type the '=' sign to run the comman suggested on [this]("http://ubuntuforums.org/showthread.php?t=1861871") thread, which was
```
Linux root=/dev/sda3
```
Meanwhile I tried to change yabootconfig from the "old" thing using this command:

```
sudo yabootconfig -r /dev/sda3
```

I had an error message. Then I tried to open yabootcnfig from terminal and it proposed me to install yaboot in hda2 so that it could be able to boot from hda3 (soemthing like that). I accepted it, hoping to solve the problem

Now, when rebooting, I don't even have the second yaboot prompt to be able to choose "old"!

What to do?

---

### Post by rsavage on 2011-10-21
canhoto, you are your own worst enemy!

Do you get any options like press L for linux etc?

I think you are going to have to use a live cd (any one should do) like this person did [http://ubuntuforums.org/showthread.php?t=1865723](http://ubuntuforums.org/showthread.php?t=1865723) to redo your yaboot partition.  I don't really know enough about chroot to give you detailed instructions.  Type "man yabootconfig" to find out what that command does.

Specifying root using the UUID number is probably best. "sudo blkid" is the command to use to find this.  

Surely one of your keys on the keyboard must be the = sign?  Did you not set it to a mac keyboard at install?

---

### Post by Boris1975 on 2011-10-21
> **rsavage said:**
>  If 11.10 is the fix then that needs to be confirmed by one of you!
I can confirm this.

---

### Post by canhoto on 2011-10-21
> **rsavage said:**
> canhoto, you are your own worst enemy!

Do you get any options like press L for linux etc?

I think you are going to have to use a live cd (any one should do) like this person did [http://ubuntuforums.org/showthread.php?t=1865723](http://ubuntuforums.org/showthread.php?t=1865723) to redo your yaboot partition.  I don't really know enough about chroot to give you detailed instructions.  Type "man yabootconfig" to find out what that command does.

Specifying root using the UUID number is probably best. "sudo blkid" is the command to use to find this.  


Thanks for your support! Meanwhile, without answer, I reinstalled Xubuntu10.04 and upgraded to 10.10, and it seems to be working properly although I have some questions, which I intend to ask on a new thread.

I ask myself if I ever will be able to upgrade... to 11.04 doesn't work it's slowliness, and to 11.10 it's risky (if something goes wrong, as it was the case, it's not a problem when you have your documents in another place, as I have, but it can be in one year or so if it becomes my main computer, as I intend to; before you ask, yes, I heard about backing up). And the next LTS 12.04 is very tempting.

Anyway, to be useful, I can confirm that in 11.10 (booted with "old" command) the CPU problem is solved.
> Surely one of your keys on the keyboard must be the = sign?  Did you not set it to a mac keyboard at install?

I'm using a (quite new) Logitech keyboard. The original Apple was having some keys stuck and the current Apple's are too expensive. I tried all the keys (I think), I don't know why it wasn't there. If you know how to configure that, it will probably be useful in the future...

---

