---
title: "Duel Boot Help??"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by frostbytes on 2007-09-10
I just installed Kubuntu to duel boot on my desktop.  Everything went swimmingly, it installed great, the windows partition wasn't hurt or anything, no complaints.  So, I restart the computer and the screen comes up to choose my OS to boot into.  I choose Windows so that it can do its little disk check thingy.  After it gets done, I restart (4 times now) and the screen to allow me to choose my OS will not pop up, and I am stuck in windows.  If anyone could help me fix this, I'd be in their debt.  Thanks!!

---

### Post by overdrank on 2007-09-10
> **frostbytes said:**
> I just installed Kubuntu to duel boot on my desktop.  Everything went swimmingly, it installed great, the windows partition wasn't hurt or anything, no complaints.  So, I restart the computer and the screen comes up to choose my OS to boot into.  I choose Windows so that it can do its little disk check thingy.  After it gets done, I restart (4 times now) and the screen to allow me to choose my OS will not pop up, and I am stuck in windows.  If anyone could help me fix this, I'd be in their debt.  Thanks!!

Hi you can try and re install the grub with this thread
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

---

### Post by frostbytes on 2007-09-10
thank you alot, im starting that right now

---

### Post by Tyke91 on 2007-09-10
reinstalling grub - standard procedure for anyone who switches operating systems and ubuntu alot

```
sudo grub
```
```
find /boot/grub/stage1
```
this will give you a list of hard drives that you can boot grub from, choose the one you have ubuntu on (they start at 0 and count up, so (hd0,0) is your first one, and so on)
```
root (hd?,?)
```whichever you chose to do in the step before
```
setup (hd0)
``` sets up the MBR with the new settings


so for example, my ubuntu is located on (hd0,2)

so my commands would look like this

```
sudo grub

find /boot/grub/stage1
     (hd0,2)

root (hd0,2)

setup (hd0)

```


EDIT: aww... beat me to it

---

### Post by frostbytes on 2007-09-10
> **overdrank said:**
> Hi you can try and re install the grub with this thread
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

OK i did the grub reinstall, now the Kubuntu AND my XP partition says```
Error 22: No Such Partition
```...any thoughts on how to fix this??

---

### Post by overdrank on 2007-09-10
> **frostbytes said:**
> OK i did the grub reinstall, now the Kubuntu AND my XP partition says```
Error 22: No Such Partition
```...any thoughts on how to fix this??

Just a quick question did you substitute the out put for the numbers given in the "how to"

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

---

### Post by frostbytes on 2007-09-10
> **overdrank said:**
> Just a quick question did you substitute the out put for the numbers given in the "how to"

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Yea I made sure I entered the right numbers.....I'm going to do it again, I just dont understand why it wouldnt find the xp partition either.....ill let you know

---

### Post by frostbytes on 2007-09-10
Still aint working....I'm going to reinstall....see if that gets me anywhere

---

### Post by enzeru on 2007-09-10
> **frostbytes said:**
> Still aint working....I'm going to reinstall....see if that gets me anywhere

You might try repairing the boot record with a windows installation disc, i was dealing with a similar problem earlier tonight [here]("http://ubuntuforums.org/showthread.php?t=547862"), one thing that helped me was resetting the boot record

[QUOTE=CaptainInsaneO]If you have a Windows install disc, run fixmbr from the repair utility on that disc. (i.e. boot into windows setup, choose "Repair" and run fixmbr). That should reset the mbr on your Windows disc, no switching of discs needed and you should be good to go from there.[/QUOTE]

---

### Post by frostbytes on 2007-09-10
alight, thats actually what I was thinking....ill try that now, and let you know

---

### Post by frostbytes on 2007-09-10
is there anyway to turn grub off....so that I can boot back into windows and start this whole process over??

---

### Post by enzeru on 2007-09-10
thats what i was looking for, I am not very knowledgeable in this department but when i snooped around grub a bit i couldn't find any sort of removal feature.  If you rewrote the boot with the windows repair it should have "forgotten" about grub though allowing you to set it up again

---

### Post by Maestro23 on 2007-09-10
To the OP, if you're trying to setup a dual-boot system, the following is a good guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by frostbytes on 2007-09-11
I got it all working....I reinstalled unbuntu over the kubuntu partition and everything works now....i figure my kubuntu install disk was faulty?? regardless, thanks for all the help guys!

---

### Post by overdrank on 2007-09-11
> **frostbytes said:**
> I got it all working....I reinstalled unbuntu over the kubuntu partition and everything works now....i figure my kubuntu install disk was faulty?? regardless, thanks for all the help guys!

Great glad to hear and good luck and enjoy! :KS

---

