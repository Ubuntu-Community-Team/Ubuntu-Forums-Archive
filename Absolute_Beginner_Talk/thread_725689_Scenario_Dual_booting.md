---
title: "Scenario: Dual booting"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-03-15
I have Ubuntu on my original hard drive. I added another hard drive and switched the jumper to slave. I would like to run Vector Linux on the slave. 

What do I need to do? The second hard drive shows up in places>computer>18.3 GB volume.  I assume my jumpers are correct right?

I had installed Vector on that second hd but I'm not sure how to boot it.  So thats why I'm here, Do I need to re-install Vector on that second hd or can I somehow boot it?

If I have to re-install is it risky to my master hd with Ubuntu on it?:confused:
The screenshot shows the 18.3 GB volume after I open it. So it does have the vector files on it. 

Thank you.

---

### Post by Diabolis on 2008-03-15
You just need a correctly configured boot loader like grub, super grub or lilo.

Ubuntu uses by default grub, and you already have it installed, so you can just configure it to recognize your second operating system.

[http://ubuntuforums.org/showthread.php?t=577721](http://ubuntuforums.org/showthread.php?t=577721)

---

### Post by Indy452 on 2008-03-15
Thanks diabolis,  You make it sound easy. I hope it is. 

In the post you linked are you saying I also should run this command?....
Code:

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit


I'm not sure what to put in place of the x   Is it like hd0 and hd1??

Neal

---

### Post by Diabolis on 2008-03-16
Yeah the x is the number of the partition where you want grub to reside. It just has to be a bootable partition.

More info about grub: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

What you need right now is this: [http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

which explains what I said in detail.

---

### Post by Indy452 on 2008-03-16
> **Diabolis said:**
> Yeah the x is the number of the partition where you want grub to reside. It just has to be a bootable partition.

More info about grub: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I don't want to seem like a pest or anything but how do find that information?  I just don't want to compromise my beloved Ubuntu.

What I'm saying is; where do find out out which HD is 0 and which is 1?

Neal

---

### Post by sandysandy on 2008-03-16
>  What I'm saying is; where do find out out which HD is 0 and which is 1?

use code
[COLOR="Blue"]
sudo fdisk -lu[/COLOR]

regards

---

### Post by Diabolis on 2008-03-16
Numbering starts from 0. So if you have PHYSICALLY 2 hard drives,  the one that came with your pc is hd0 and the one you added is hd1.

---

### Post by VraiChevalier on 2008-03-16
@Indy452

If Vector Linux installed it's own boot loader it may have partitioned your second hard drive. When you edit your /grub/boot/menu.lst file be extra careful to specify which partition the Vector Linux is on (hdb0 or hdb1 etc).

I mention this because I had a devil of a time getting my setup to dual boot Ubuntu 7.10 and openSUSE 10.3 until I finally got the correct drive and partition entered.

---

### Post by Diabolis on 2008-03-16
Read this, it will explain everything and even if you mess up you can always run the command again and again. It would not break any of your installations.

[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by Indy452 on 2008-03-16
Thank you Diabolis, I feel a bit more comfortable now about trying it.

I'll run that command you linked and see what happens.

I also have a copy of Super grub disk. Can that help me with this whole process?
I messed around with it last night and got confused by what I should be doing with it so I gave up. I guess I could try again sometime if suggested. I just was unsure about which direction to take in super grub disk to fix my dilema.

Neal

---

### Post by sandysandy on 2008-03-16
with super grub disk u can do following

fix MBR of windows

fix MBR of Linux (loads GRUB of selected distro)



regards

---

### Post by Indy452 on 2008-03-16
> **sandysandy said:**
> use code
[COLOR="Blue"]
sudo fdisk -lu[/COLOR]

regards

Disk /dev/sda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders, total 29336832 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008499e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    28017359    14008648+  83  Linux
/dev/sda2        28017360    29334689      658665    5  Extended
/dev/sda5        28017423    29334689      658633+  82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders, total 40088160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000db155

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    38331089    19165513+  83  Linux
/dev/sdb2        38331090    40082174      875542+   5  Extended
/dev/sdb5        38331153    40082174      875511   82  Linux swap / Solaris


Heres what I get from that code....I don't see a hd0 or hd1  I see sda and sdb is this what I should enter in the linked code?      Agghhh!  I wish I knew what I was doing so I could get it over with without the worry of screwing this up because I've screwed others up b4 so bear with me. Thanks

---

### Post by sandysandy on 2008-03-16
> Heres what I get from that code....I don't see a hd0 or hd1 I see sda and sdb is this what I should enter in the linked code? Agghhh! I wish I knew what I was doing so I could get it over with without the worry of screwing this up because I've screwed others up b4 so bear with me. Thanks 

sda is first hard disk   hd0

sdb is second   hd1

regards

---

### Post by Indy452 on 2008-03-16
sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

O.K. if this was your computer what would you type?  I can't copy and paste so when typing I can't get the code to stack on top of each other like shown above its all in a line correct?

When typing, when I get to the third line shown above should I type hd1 or sd1 or sdb?  and what number after the comma,  1 again??:confused:  And should setup be the same as root then?

---

### Post by Diabolis on 2008-03-16
hda0 is the number for your first disk, if you make 2 partitions on that disk their numbers will be:
hda0,0 and hda0,1

read this: [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

```
find /boot/grub/stage1
```

will tell you which partitions are bootable, so the output of this command will be the input of the next command.

```
root (hdx,x)
```
The 'root (hd0,1) will tell GRUB which operating system partition contains the GRUB I want to install from.

```
setup (hdx)
```
The 'setup' command is the command that tells GRUB exactly where to install Grub to.


Do not hesitate on asking more if you don't get it working yet.

---

### Post by Indy452 on 2008-03-16
Ha! O.K., I'm sorry. I was trying to put the whole code into the terminal! I didn't realize that it was in stages. (It helps to read the linked tutorials!)  I feel like an idiot now! I'm not afraid of the terminal, I just want to be sure I get it right the first time is all. 

Thanks, Diabolis!  I'll take it from here.

Neal

---

### Post by Indy452 on 2008-03-16
> **Diabolis said:**
> hda0 is the number for your first disk, if you make 2 partitions on that disk their numbers will be:
hda0,0 and hda0,1

read this: [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

```
find /boot/grub/stage1
```

will tell you which partitions are bootable, so the output of this command will be the input of the next command.

```
root (hdx,x)
```
The 'root (hd0,1) will tell GRUB which operating system partition contains the GRUB I want to install from.

```
setup (hdx)
```
The 'setup' command is the command that tells GRUB exactly where to install Grub to.


Do not hesitate on asking more if you don't get it working yet.



So root will be the Ubuntu ststem my original hd? (hd0,0)  
And setup will be the vector hd? (hd1,0)?

I'm having trouble understanding this. I've read the linked tutorials at least ten times but I just don't seem to get it. 
I just don't understand hermans examples.  What about this paragraph at the end?..............

Installing GRUB to a non-first MBR:
The BIOS normally only boots the MBR of whichever disk is set in the BIOS as the first hard disk.
If you have more than one hard disk in your computer, you can install GRUB to the MBR of your other hard disks as well. You can use a chainloader command from your first hard disk's GRUB to boot GRUB or any other boot loader in any other hard disk. This is useful for people who have a lot of operating systems and they want to spread them over several GRUB menus.
To install GRUB to a second hard disk, you would use 'setup (hd1)', and for a third hard disk 'setup (hd2)', and so on.

Should I do this?

---

### Post by Diabolis on 2008-03-16
This is the output of fdisk:
*I deleted some stuff*
```
Disk /dev/sda: 15.0 GB
/dev/sda1 * 63 28017359 14008648+ 83 Linux
/dev/sda2 28017360 29334689 658665 5 Extended
/dev/sda5 28017423 29334689 658633+ 82 Linux swap / Solaris

Disk /dev/sdb: 20.5 GB
/dev/sdb1 * 63 38331089 19165513+ 83 Linux
/dev/sdb2 38331090 40082174 875542+ 5 Extended
/dev/sdb5 38331153 40082174 875511 82 Linux swap / Solaris
```

So you got ubutnu on sda1 and vector on sdb1, right?  You can see they are the bootable partitions because they are marked with an asterisk..

That means that the output of **find /boot/grub/stage1** was:

(hd0,0) and (hd1,0)

I don't know if vector comes with grub so the safest is to install it from the ubuntu partition which is hd0,0.

root(hd0,0)

and then you tell grub where you want to install it

setup(hd0)

If you want to see if it works with vector, then it would be

root(hd1,0)
setup(hd1)

---

### Post by handydan918 on 2008-03-16
> **VraiChevalier said:**
> @Indy452

If Vector Linux installed it's own boot loader it may have partitioned your second hard drive. When you edit your /grub/boot/menu.lst file be extra careful to specify which partition the Vector Linux is on (hdb0 or hdb1 etc).


This is incorrect. grub nimbers drives differently. The first drive , first partition wil be listed as (hd0,0).
The second hard drive, first partition, will be listed as (hd1,0)

---

### Post by Indy452 on 2008-03-16
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)

grub> root (hd0,0)

grub> setup(hd0)

Error 27: Unrecognized command

grub> 



I get this when I hit enter. Unrecognized command.

What can I do?

---

### Post by Diabolis on 2008-03-16
You need to separate it
```
setup (hdx)
```
Notice the space between the **p** and the **(**

Use tab completion so you don't make this kind of errors.

---

### Post by Indy452 on 2008-03-16
That worked but no change in booting Vector. I went to other operating systems in the boot loader page ( think its called)

When I ran the code in terminal I saw succedded something or another so I assume the codes worked but how do I access Vector or hd1?

Do I need to run the codes for Vector?
 
" If you want to see if it works with vector, then it would be"

root(hd1,0)
setup(hd1)


Thanks, Neal

---

### Post by Diabolis on 2008-03-16
If the commands went well, you just have to reboot your pc. You'll see then the grub menu in which you'll see all your operating systems, from where you can choose which one you want to use.

Every time you turn on your pc this is the order in which software runs:
[B]
bios / bootloader / operating system[/B]

grub is a bootloader.

Thats why you can play around with it safely. If you mess up, you can always try it again. The operating system stands separated form the boot loader.

---

### Post by Indy452 on 2008-03-16
> **Diabolis said:**
> If the commands went well, you just have to reboot your pc. You'll see then the grub menu in which you'll see all your operating systems, from where you can choose which one you want to use.

Every time you turn on your pc this is the order in which software runs:
[B]
bios / bootloader / operating system[/B]

grub is a bootloader.

Thats why you can play around with it safely. If you mess up, you can always try it again. The operating system stands separated form the boot loader.



Thank you for sticking in there with me Diabolis, I wish I could just have you phsically do this for me but I see you live way too far for me to drive it to you:)

Anyway, I tried both codes once with hd0 and once with hd1 and It still does not work. I'm not sure what else to try.
When I re-boot and the grub menu comes up I can choose between Ubuntu, Ubuntu recovery mode, Ubuntu memory test, Other OSes, and Windows 200/xp.
I choose "other operating systems and hit enter and I get an error 11 unrecognized device string. Press any key to continue.

Is this where the Vector should be showing up?  I don't have any trouble booting the Ubuntu choices obviously since thats what I use.

I'll check back in a bit.

Neal

---

### Post by Diabolis on 2008-03-17
> When I re-boot and the grub menu comes up I can choose between Ubuntu, Ubuntu recovery mode, Ubuntu memory test, Other OSes, and Windows 200/xp.

From what I saw in the output of fdisk, you only have two operating systems or at least you only have two bootable partitions. So, if now you are saying that you can boot into ubuntu and windows and you also want to boot into vector, you should have three bootable partitions.

If thats correct this problem doesn't have to deal with grub. Maybe vector is not correctly installed.

---

### Post by Indy452 on 2008-03-17
Hmmm, thats funny because I don't even have a windows OS on this machine or partition that I'm aware of. When I set up Ubuntu on the original hd, I choose to put it on the whole disc, but I did have another hd as slave with windows xp on it but I took it out when I could'nt figure out how to boot it. The same problem I'm having now with Vector.

How about this, I don't mind re-installing Vector to the second hd but I don't know how to access it. I don't want to re-install Ubuntu or loose it because its my primary OS and I have lots of settings and stuff in it.


What about super grub disk? Can it help me out here? I don't really understand partitions and booting and all that well but I'm open to learn more if someone can link more learning material about grub, booting, partitions etc, Hermans is good but I find myself doozing off when reading through it.

Or maybe I should just scrap the whole idea on this particular machine and try it on another I have with its hard drives, that way I won't ruin anything and learn how to do it before doing it to this machine.

Thanks, Neal

P.S, I no longer use any form of MS windows so all the work done will be 100% linux based. No partition or hd will be used with windows .:)

---

### Post by Indy452 on 2008-03-17
> **Diabolis said:**
> From what I saw in the output of fdisk, you only have two operating systems or at least you only have two bootable partitions. So, if now you are saying that you can boot into ubuntu and windows and you also want to boot into vector, you should have three bootable partitions.

If thats correct this problem doesn't have to deal with grub. Maybe vector is not correctly installed.

No I can't boot into windows either. Its on the list but when I select it and hit enter I get an error message, I don't recall which error but  some error number. I don't have windows on this machine at all in any form.

Neal

---

### Post by Diabolis on 2008-03-17
Then the commands are not working properly. After you execute those commands grub is reinstalled and the menu is updated. That would remove operating systems that no longer exist from the **menu.lst** file. You can check it here:
```
sudo gedit /boot/grub/menu.lst
```
You can check if the commands configured everything properly without booting by looking at this file.

Every operating system installs a bootloader. If vector uses grub, then it will have a menu.lst file too. Give a look to it, maybe that will give you a clue on what is going wrong.

---

### Post by Indy452 on 2008-03-17
O.K here it is, I hope that theres no sensitive info on here!

I don't get it. what am I looking for?...........................



## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e60cff42-8f9a-4581-8fd4-aab955832b97 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e60cff42-8f9a-4581-8fd4-aab955832b97 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Diabolis on 2008-03-17
This is the important part:
```
## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e60cff42-8f9a-4581-8fd4-aab955832b97 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e60cff42-8f9a-4581-8fd4-aab955832b97 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows NT/2000/XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

You may remove the last lines, you only need this part:
```
## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e60cff42-8f9a-4581-8fd4-aab955832b97 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e60cff42-8f9a-4581-8fd4-aab955832b97 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

```

After you reinstall grub, the menu.lst file is updated. And an entry like this one should appear:
```
title Ubuntu VECTOR, kernel 2.6.##-##-generic
root (hdx,x)
kernel /boot/vmlinuz-2.6.##-##-generic root=UUID=#### ro quiet splash
initrd /boot/initrd.img-2.6.##-##-generic
quiet
```

The same is true for the windows partition that you mentioned before. Grub recognizes both linux and windows. As you can see **title**  is the name that appears on the grub menu, you may change it to whatever you want.

---

### Post by Indy452 on 2008-03-17
So its not seeing vector then? 

What about the windows thing? I thought I did'nt have windows anymore. I want to get rid of windows then if its still on the hd then. How do I do that?

---

### Post by Diabolis on 2008-03-17
No, windows is not there anymore. The entry you have is just a left over from the time where you did have windows. When grub is updated it only adds new entries, but it does not remove old ones.

And IF you are sure you did everything correct while reinstalling grub, then yes, vector is not being recognized.

Can you elaborate on this:
> I have Ubuntu on my original hard drive. I added another hard drive and switched the jumper to slave. I would like to run Vector Linux on the slave.

Since you have tried so many times and is not working yet, here might be the problem.

---

### Post by Indy452 on 2008-03-17
I have installed Ubuntu on the hard drive that was in this computer originally. 
I took another hard drive from another computer very similar to this one that I previously installed Vector linux gold on. I took the hard drive and put it into the computer that Ubuntu has and set the jumper to slave. Thats pretty much it. I just thought I could boot it somehow and have my two favorites in one machine rather that two seperate machines.

Why don't I go back to the page where we were discussing the codes and I'll give it one more try.

Disk /dev/sda: 15.0 GB
/dev/sda1 * 63 28017359 14008648+ 83 Linux
/dev/sda2 28017360 29334689 658665 5 Extended
/dev/sda5 28017423 29334689 658633+ 82 Linux swap / Solaris

Disk /dev/sdb: 20.5 GB
/dev/sdb1 * 63 38331089 19165513+ 83 Linux
/dev/sdb2 38331090 40082174 875542+ 5 Extended
/dev/sdb5 38331

This says to me that there is something there.
If you tell me exactly what to run in terminal I'll give it a try. Just to be extra sure.
 I obviously don't have faith in my own judgement but I've been wrong  before, I'll be the first to admit that.

What was it again.....I'm never really sure what to put where the ? mark is.
 
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?)
quit

---

### Post by Diabolis on 2008-03-19
sudo grub
**find /boot/grub/stage1** It will find all the places _from_ where you can install grub.
**root (hd?,?)** Select _from_ where you want to install grub
**setup (hd?)** Select the drive _in_ which you want to reinstall grub
quit

So the output of **find** is the input of **root**. Since you have 2 hard drives, the input of **setup** can be hd0 or hd1.

Probably you already typed the correct commands, but it will never work. This is the reason:
> I took another hard drive **from another computer** very similar to this one that I previously installed Vector linux gold on. 

I just tried that. I installed ubuntu through my desktop pc into a removable hard drive, then I plugged it into my laptop and reinstalled grub. Now my laptop showed in the grub menu the windows installation that I have in my desktop pc and I can't boot.

You can't install an operating system in computer A, remove the hard drive and try to boot with it in computer B. Probably its because when you install an operating system lots of configurations are made and some of them must be hardware specific. The bad new is that you have to reinstall vector. 

The only way I've heard that will let you do this, is by making a bootable usb stick. I haven't made one yet, but seems like its not too difficult.

[How to make a bootable usb stick]("http://people.ofset.org/~ckhung/p/mk-boot-usb/index.php")

I just wonder how the bootable usb handles those "hardware specific configurations" or whatever doesn't let you do it by installing in computer A and the trying to boot into other pcs.

---

### Post by Diabolis on 2008-03-19
I made a thread about this topic: [Installed and trying to boot on another pc]("http://ubuntuforums.org/showthread.php?t=728952")

---

### Post by Indy452 on 2008-03-19
Wow , I'll bet you're onto something here Diabolis.

I would not have a problem re-installing Vector because it was a fresh install on the other machine.
The question is, Is it accesable? How do I install a OS to the other drive?  I don't have any usb sticks besides a 1GB usb mp3 player that looks alot like one.

I'll check in again sometime.

Thanks for the research, Diabolis.

Neal

---

### Post by Diabolis on 2008-03-19
No no the usb stick was just extra info, you don't need one. Just plug in the hard the drive into the machine where is going to stay, insert the cd and install as usual. The OS will only work on the machine were you install it.

---

### Post by Diabolis on 2008-03-19
The answer is no, vector is not accessible unless you boot it in the original machine where it was installed.

---

### Post by Indy452 on 2008-03-19
Say I leave everything alone as it is. Ubuntu on drive a and what is an unbootable vector on drive b.

I fire up the computer with the Vector install cd.   What will happen? How do I direct the install to drive b?  I don't want to make a mistake and install vector over Ubuntu in drive a.
If I do this will I  be able to install Vector over the existing vector that won't boot?



Neal

---

### Post by Diabolis on 2008-03-20
Yes. I'm sure that at some point of the installation, vector will ask you which drive you want to use. It will happen when you are are asked to choose/make a partition. Probably the process is similar if not the same to the one you followed while installing ubuntu. Pick the option that says "manual" so you can select the second drive.

---

### Post by Indy452 on 2008-03-23
> **Diabolis said:**
> Yes. I'm sure that at some point of the installation, vector will ask you which drive you want to use. It will happen when you are are asked to choose/make a partition. Probably the process is similar if not the same to the one you followed while installing ubuntu. Pick the option that says "manual" so you can select the second drive.

I decided to try to install Vector tonight and I became freaked out so I canceled the install till I do a bit more research. 

Vector installs much differently to me than Ubuntu. Ubuntu was very easy to understand and made more decisions for you where Vector is a bit more "involved".
I think vector uses Lilo, will it co-exist with my Ubuntu on the other drive?
I don't see any trouble with that do you?  Also I need to use fdisk to show vector where to go I think, is fdisk easy to understand?

Neal

---

### Post by Diabolis on 2008-03-24
Lilo will replace grub and probably it will detect ubuntu, so go ahead. Just careful when selecting in which disk you are installing, good luck. I just gave a quick look to the man page of fdisk, and seems like everything its widely explained. I think that the man page will tell you all what you need to know for now.

---

### Post by Indy452 on 2008-04-04
Thanks  Diabolis, I just thought I'd let you know I pretty much gave up on this because I can't seem to get the other hd to boot. I even installed Vector to the other hd through the computer but I still can't boot it so I'm done I guess.

I figure I'm a one OS kinda guy. (no choice):(

Maybe some day when I get a newer machine I can try it again.

Neal

---

