---
title: "Would Somebody Please Help Me!!!"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-11-15
I have posted this for the 5th time and I want an answer,

Ehem,

I have just installed Ubuntu on a computer that ran XP for a while now, I CAN'T boot Ubuntu, and I CAN'T boot from XP, Ubuntu gets stuck at "Configuring Network Interfaces" and XP doesn't show up in the GRUB boot menu, I am screwed with an underpowered Laptop that is the only one I can use, I WAN'T HELP AND I WILL STAY HERE 'TILL I HAVE SOME. I am about to break down in a heavy cry, OK I have loved Ubuntu since it came out, I don't want this to be the reason why I no longer use it...:mad:

---

### Post by yurtfg89327tfg0o on 2006-11-15
Firstly I'd suggest a radical change of attitude if you want to be helped.

Why not boot the Ubuntu LiveCD, mount your hard drive, examine the grub files (/boot/grub/menu.lst) to see if XP is in the boot list?

Or maybe you could try here
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by TheRingmaster on 2006-11-15
why not just install xubuntu ([http://www.xubuntu.com](http://www.xubuntu.com)). you said that it was "underpowered" right?

---

### Post by aidanr on 2006-11-15
can you boot up into recovery mode (press esc when grub is loading and choose the second option)

then type in the following when its finished booting
```
nano /boot/grub/menu.lst
```
scroll down with the arrow key to the end and add the following below the second grub entry
```
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
where hd0,0 is the first partition on the first harddrive, if windows is on another partition, change accordingly
then hit "ctrl+o" to save and "ctrl+x" to exit
then type "reboot" and when grub loads again you should now have an entry to load windows

if you can't boot up into recovery more, you can try booting up the ubuntu live cd and mounting the root partition and editing /boot/grub/menu.lst that way
to mount the partition, open a terminal and type in
```
mkdir /tmp/ubuntu
mount /dev/hda2 /tmp/ubuntu
gedit /tmp/ubuntu/boot/grub/menu.lst
```
replacing hda2 with the name of the partition ubuntu is installed on


as for the problem with ubuntu getting stuck on configuring network interfaces, first try disabling your network adapter in the computers bios and then see does it boot up fully, just to confirm that the network interface is causing the problem

how long has it been doing this, have you made any major hardware or software changes recently?

---

### Post by Frak on 2006-11-15
> **TheRingmaster said:**
> why not just install xubuntu ([http://www.xubuntu.com](http://www.xubuntu.com)). you said that it was "underpowered" right?
I run Xubuntu thank you very much,
(I'm sorry I'm so gripey, when you have a woman yell at you for being the "smartest man alive and for not leaving things alone", you get pretty tensed up)

---

### Post by Frak on 2006-11-15
> **aidanr said:**
> can you boot up into recovery mode (press esc when grub is loading and choose the second option)

then type in the following when its finished booting
```
nano /boot/grub/menu.lst
```
scroll down with the arrow key to the end and add the following below the second grub entry
```
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
where hd0,0 is the first partition on the first harddrive, if windows is on another partition, change accordingly
then hit "ctrl+o" to save and "ctrl+x" to exit
then typr "reboot" and when grub loads again you should now have an entry to load windows

if you can't boot up into recovery more, you can try booting up the ubuntu live cd and mounting the root partition and editing /boot/grub/menu.lst that way
to mount the partition, open a terminal and type in
```
mkdir /tmp/ubuntu
mount /dev/hda2 /tmp/ubuntu
gedit /tmp/ubuntu/boot/grub/menu.lst
```
replacing hda2 with the name of the partition ubuntu is installed on
Thats just it, when it boots it stops at "configuring network interfaces", I don't know how to fix it, that's why I came to you guys.

---

### Post by aidanr on 2006-11-15
does that happen in recovery mode and with the live cd? does it happen with other live cd's? does it still happen if you disable your network interface in the bios?

---

### Post by bollix47 on 2006-11-15
You could try downloading and burning [Super Grub Disk.]("http://adrian15.raulete.net/grub/tiki-index.php")

---

### Post by djsroknrol on 2006-11-15
What kind of networking do you have on the laptop?...wireless?...we all would love to help if you give us some specs or stats..

---

### Post by Frak on 2006-11-15
> **aidanr said:**
> does that happen in recovery mode and with the live cd? does it happen with other live cd's? does it still happen if you disable your network interface in the bios?
Thanks aidanr, I would like to try your idea but I have to learn to use the bios that I have first, It should work.

---

### Post by Frak on 2006-11-15
> **djsroknrol said:**
> What kind of networking do you have on the laptop?...wireless?...we all would love to help if you give us some specs or stats..
A desktop with wireless but its trying to boot with the default, grounded, version.

---

### Post by Frak on 2006-11-15
Hey this might not work, but I'll wait an approval from you guys, I kept enabling the wireless card during the live session, on my laptop when that happened it started to boot from that with the WEP code so do you think that'll help the network problem.

---

### Post by aidanr on 2006-11-15
when you turn on the laptop, look out for a message about entering setup or something similar, depending on your laptop manufacturer it could be one of a few keys to access it, such as the delete key or F2

edit:// eh, not sure bout the WEP thing, haven't run linux on a lappy before, but possibly i guess

---

### Post by Gaweph on 2006-11-15
> **Frak said:**
> Hey this might not work, but I'll wait an approval from you guys, I kept enabling the wireless card during the live session, on my laptop when that happened it started to boot from that with the WEP code so do you think that'll help the network problem.

Did you say that it was using the wrong NIC, its using your lan card, instead of Wireless? is that correct? Do you mean it works with wireless, but you just cant get into it to enable it?

Just skip the network step when its booting (CTRL + C at that part), then once inside ubuntu change the default device to the wireless one, then try restarting GDM, or restart the box.

---

### Post by Frak on 2006-11-15
> **Gaweph said:**
> Did you say that it was using the wrong NIC, its using your lan card, instead of Wireless? is that correct? Do you mean it works with wireless, but you just cant get into it to enable it?

Just skip the network step when its booting (CTRL + C at that part), then once inside ubuntu change the default device to the wireless one, then try restarting GDM, or restart the box.
OMG, you are a freakin genius, I didn't know you could do that, I'm so happy, thank you all and sorry for being such a gripe.

EDIT
I also didn't activate the wireless in live mode this time either.

---

### Post by aidanr on 2006-11-15
cool, didn't know you could skip steps of the boot process like that, learn something new everyday i suppose;), btw i was reading the thread all wrong, i thought the problem was with the laptop, i see now reading back that the problem is with the desktop and your currently on the laptop:rolleyes:

---

### Post by yurtfg89327tfg0o on 2006-11-15
Thread closed?

---

### Post by TheRingmaster on 2006-11-15
> **yurtfg89327tfg0o said:**
> Thread closed?
I don't think so ;)

---

### Post by Gaweph on 2006-11-15
> **Frak said:**
> OMG, you are a freakin genius, I didn't know you could do that, I'm so happy, thank you all and sorry for being such a gripe.

EDIT
I also didn't activate the wireless in live mode this time either.

Not a problem, i actualy had the same problem back when i was using Hoary.  Hope everything is working now.

---

### Post by Frak on 2006-11-16
I also solved the problem by finding out that Kubuntu runs better than Ubuntu does, still have the GRUB problem but I'll eventually fix that, I just can't get packages to show up, if any of you have any expertise on that subject.

---

