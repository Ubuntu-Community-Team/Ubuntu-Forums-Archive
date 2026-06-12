---
title: "dapper will not install correctly."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by mattgaunt on 2006-10-18
Right so i installed dapper from the live CD installed fine, but when i load it from grub after reboot it says

> /bin/sh: can't access tty; job control turned off

So i installed Edgy and that worked fine, the problem is, being a noob i cant  figure out how to use edgy when all the tutorials online for ubuntu are largely for dapper not edgy ](*,) 

So basically i desparetly want edgy to work, plz plz plz can a moderator or someone with vast knowledge of dapper give me a hand

My computer is AMD 64 processor with two hard drives, dual booting windows and dapper(well meant to be dual booting)

Thanks for any who reads this

Thanks even more if you can help

Matt

---

### Post by K.Mandla on 2006-10-18
A couple of things come to mind. 

1. Do you get any kind of login prompt at all, or is the computer locked after that?

2. Try pressing ALT+CTRL+F1 or F2 or F3 ... all the way to F7.

3. If you can get any kind of prompt, could you please post the guts of the /etc/inittab file? Use this prompt, if you have one after you log in:

```
sudo nano /etc/inittab
```
Unless I'm mistaken, that error message means Dapper can't get at one of the tty interfaces, and that's why it's freaking out. If you can get to another terminal window (that's the F1, F2, F3, etc. stuff), then at least there is some sign of life in there. 

A possible reason why your machine was working in Edgy is that Edgy uses a different startup system, and so the files are in different places.

Don't worry! We'll get it sorted out! :D

---

### Post by mattgaunt on 2006-10-18
I tried but nothing of that works, i cant get into the log screen, during the  boot it gets to mounting root folder i think it is and stays there for a bit and thats it, the it goes to busy box and gives the /bin/sh: can't access tty; job control turned off

---

### Post by PriceChild on 2006-10-18
Could i point out that moderators are just like you.... but with extra buttons to press, we're not more knowledgable (sp?) than others.. I'm renaming your thread appropriately.

Have you tried booting a different kernel from grub?

EDIT

whoops didn't realise this was your first boot...

---

### Post by K.Mandla on 2006-10-18
> **mattgaunt said:**
> I tried but nothing of that works, i cant get into the log screen, during the  boot it gets to mounting root folder i think it is and stays there for a bit and thats it, the it goes to busy box and gives the /bin/sh: can't access tty; job control turned off
Okay, let's try this. It's going to be a little tricky, but we'll see what happens.

Boot your computer to a live CD. It doesn't matter what version, or even if you use Ubuntu.

Open a terminal window and type this command.

```
sudo fdisk -l
```
That should give you a list of drives connected to your computer, and the partitions that are on it. The trick is this: You have to try and pick out the partition that is your root partition.

Chances are it's /dev/hda1, so try this next:

```
sudo mount /dev/hda1 /mnt
```
With any luck, that will tell Linux to mount your hard drive partition to the /mnt folder it has in its live environment. The idea is to access that partition, and look inside the /etc/inittab file. So next:

```
cd /mnt
ls
```
You should see what looks like the root directory of your Ubuntu partition. Now ...

```
cd etc
```
and then

```
ls
```
Hopefully you will see the inittab file in there somewhere, and see if you can open it with this command.

```
sudo nano inittab
```
If you get this far, we might have some luck. Post the guts of that file here, if you can. :-k

---

### Post by K.Mandla on 2006-10-19
By the way, it looks like this is a fairly common problem with installations from the live CD.

[http://www.ubuntuforums.org/showthread.php?t=252578](http://www.ubuntuforums.org/showthread.php?t=252578)
[http://www.ubuntuforums.org/search.php?searchid=8953742](http://www.ubuntuforums.org/search.php?searchid=8953742)

It might be less work to start with a fresh installation from the alternate CD. Dapper's live CD is, unfortunately, known to have problems. :rolleyes:

---

### Post by mattgaunt on 2006-10-19
Sorry Price child, my bad, anyway i think ill scrap this and try the alternate CD because while in the LiveCD i did just hav a go at mounting the hard drive by just right clicking on it and i had no luck with that and as you said it seems to be a common problem with no clear way to resolve it, so ill giv the alternate CD ago and see if it will make me happy lol

Thanks so much for the help K.mandla, peeps like you that make so much less daunting lol

Im sure ill tlk 2 ya in a bit byee

---

### Post by mattgaunt on 2006-10-20
Hey jus to let you guys know, the alternate CD worked perfectly and there is no problems what so ever so thnk you so so much for all your help!!!

---

### Post by cmavr8 on 2006-10-28
> **K.Mandla said:**
> Okay, let's try this. It's going to be a little tricky, but we'll see what happens.

Boot your computer to a live CD. It doesn't matter what version, or even if you use Ubuntu.

Open a terminal window and type this command.

```
sudo fdisk -l
```
That should give you a list of drives connected to your computer, and the partitions that are on it. The trick is this: You have to try and pick out the partition that is your root partition.

Chances are it's /dev/hda1, so try this next:

```
sudo mount /dev/hda1 /mnt
```
With any luck, that will tell Linux to mount your hard drive partition to the /mnt folder it has in its live environment. The idea is to access that partition, and look inside the /etc/inittab file. So next:

```
cd /mnt
ls
```
You should see what looks like the root directory of your Ubuntu partition. Now ...

```
cd etc
```
and then

```
ls
```
Hopefully you will see the inittab file in there somewhere, and see if you can open it with this command.

```
sudo nano inittab
```
If you get this far, we might have some luck. Post the guts of that file here, if you can. :-k


Hello everybody. I am having the same problem and have done what K.Mandla says. Should I now post my inittab here? Is this thread still active? 

Thanks for reading!

(I am almost desparate, as my main system is down and unbootable... You know how it feels. I have google a lot on the problem but can't go through... It occured after upgrading from Dapper to Edgy (stable))


[COLOR="Red"][SIZE="5"]EDIT: I found the solution! Grub was aiming to the wrong partition (swap!) and thus it couldn't boot ubuntu properly. I replace the right UUID and it works! 

CU![/SIZE][/COLOR]

---

### Post by noerrorsfound on 2006-10-29
> **cmavr8 said:**
> Hello everybody. I am having the same problem and have done what K.Mandla says. Should I now post my inittab here? Is this thread still active? 

Thanks for reading!

(I am almost desparate, as my main system is down and unbootable... You know how it feels. I have google a lot on the problem but can't go through... It occured after upgrading from Dapper to Edgy (stable))


[COLOR="Red"][SIZE="5"]EDIT: I found the solution! Grub was aiming to the wrong partition (swap!) and thus it couldn't boot ubuntu properly. I replace the right UUID and it works! 

CU![/SIZE][/COLOR]
So how do I do this? I have Ubuntu installed on its own hard drive.

---

### Post by Aurelius on 2006-10-29
Here's excerpts from my menu.lst
```

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=3613a231-decc-44c6-925e-9e942a4bb014 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot


title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=3613a231-decc-44c6-925e-9e942a4bb014 ro quiet splash 
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```

Are you talking about changing some other UUID? Because the -386 entry works fine, it's just the -generic one that gets the tty error.

---

### Post by cmavr8 on 2006-11-05
You don't need to do what I write in red, unless your partition table is screwed up like mine. Have you had any errors during resizing/moving partitions?

(sorry for not answering immidiately but this forum notifies me to my old (and not frequently checked) email.)

---

### Post by cmavr8 on 2006-11-05
> **noerrorsfound said:**
> So how do I do this? I have Ubuntu installed on its own hard drive.

> **Aurelius said:**
> Here's excerpts from my menu.lst
```

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=3613a231-decc-44c6-925e-9e942a4bb014 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot


title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=3613a231-decc-44c6-925e-9e942a4bb014 ro quiet splash 
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```

Are you talking about changing some other UUID? Because the -386 entry works fine, it's just the -generic one that gets the tty error.


I needed to change everything as my part. table was bad (see previous post). Your two uuids look alike, so your problem is elsewhere...

---

### Post by shakyone on 2006-12-19
cmavr8,

     I have the same problem.  I loaded 6.10 to my USB hard drive (/dev/sda), sda1 is the ext3 partition, with the normal hard drive disconnected from the computer (Dell Latitude D620).  When I boot with the laptop hard drive connected, I get the "/bin/sh: can't access tty; job control turned off" problem.  

     However to make things interesting... When I disconnect the laptop hard drive and have the USB drive plugged in, the system loads properly.  I had a Dell Latitude D600 up until two weeks ago.  I ran 6.10 off the same portable USB drive with it, and never saw this error.  When I review my GRUB menu.lst file it shows the root at (hd0,0).  I am not sure what I need to change to to make this work.  

     I'm guessing we have the same problem with the root address, and that throws the error, since the initial post was a dual-boot computer with the second drive having Ubuntu.  I have this configuration in my home desktop computer and left the ubuntu drive as the Master on the IDE but I followed Confused 57's install method, (it leaves NTLDR in tact, and ubuntu directs the bootloader to NTLDR in the slave drive MBR for Windows bootup), so I never encountered this problem there nor should I.  I think there is something wrong with the GRUB install in 6.10, in that it does not cross-check where the root is during install.  I do not know how to fix it.  Anyone knowledgeable know?

Shakyone.

---

### Post by cmavr8 on 2006-12-19
I'm not knwoledgeable but I would guess your grub doesn't know about the HD. I think a reinstallation of grub would fix the problem. I also think it has to be on the HD, that is always there...

But it's easier to update the grub on the flash disk, so you might try that first... There is a way to reconf grub without formating. Please google it...

Good luck
hope I help

---

### Post by shakyone on 2007-03-29
Cmavr8, I cannot tell if you are responding to my USB install question.  I sent you a private message too, to speed up response time.

Below my post (Shakyone) you responded about the UUID edit in Red.  Are you saying it applies in my case or not?  I re-installed to my USB a little while ago, and GRUB now points properly to Sda, yet I still get the Bin/Sh errors when the internal hard drive is connected during a USB boot.  I'm concerned I'm going to have a failure of the Hard drive connector if I keep pulling it out to reboot when I use Ubuntu.  So I keep asking questions. 

Thanks.

Shakyone

---

### Post by dstew on 2007-03-29
shakyone, I think the problem is that grub counts drives (hd0, hd1 etc.) by using the numeration that your BIOS produces when the computer first turns on. If you unplug a drive, the numbers will be wrong, and grub will get lost. There are ways to get around this. see:

[http://www.gnu.org/software/grub/manual/grub.html#Device-map](http://www.gnu.org/software/grub/manual/grub.html#Device-map)

---

### Post by wab1sab1 on 2007-03-29
I encounter this same problem with a Live CD Edgy install.  It didn't happen after install, but rather after i updated my grub.conf, and reran grub-install.  I've got ubuntu on it's own disk, hd0,1 (hdb1 is root, hdb5 is swap) but my grub is on hd0,0 (where i have gentoo linux, as well as the operating system which must not be named). I'm not sure if this is compounding the problem or not.

Booting into gentoo, I find I cannot mount my ubuntu root partition.  e2fsck says it was not unmounted cleanly, and found bad blocks, groups, and directories.   I told it to fix all the problems it found (about 60 in total), and that seems to have fixed it for me.  Ubuntu is back up and running in all it's beryl-infused glory.

---

### Post by shakyone on 2007-03-31
Thanks for your help.  I don't know how, but somewhere along the way my Ubuntu healed itself.  I cannot figure out what I did exactly that got it working.  I will post more if I ever figure it out.  I will probably have the same occur when I switch to feisty, and have more to report.

Shakyone

---

### Post by azinas on 2007-04-14
hello? is this still active? Can someone please let me know how to do the last step?
thanks

---

### Post by cmavr8 on 2007-04-14
Tried reinstalling grub?

---

### Post by jlkz on 2007-05-29
my nano inittab says nothin

---

### Post by britoca on 2007-07-17
> **mattgaunt said:**
> Hey jus to let you guys know, the alternate CD worked perfectly and there is no problems what so ever so thnk you so so much for all your help!!!

where do I download this "alternate CD"?

---

### Post by kadnan on 2007-08-19
I am unable to load Ubuntu from CD under VMWare. Every time I try to load Ubuntu fro CD in Vmware,it loads from hard disk. What should I do so that it loads from LIVE CD?

I am also getting similar problem but can't even get into Grub menu

---

### Post by netgooroo on 2007-09-04
I'm getting the same error now. I just upgraded my install from 6.10 Edgy to 7.04 Feisty and on the very first boot, this comes up

BusyBox V1.1.3 (Debian 1:1.1.3-3Ubuntu3) Built in shell (ash)
/Bin/sh: can't access tty; job control turned off (initramfs)

Now, I get the Ubuntu splash screen but that's as far as I get. Grub doesn't come up at all. I really hate to do a re-install over this install as I have it just how I want it and I would loose everything. :confused: If anyone can help, I would be VERY greatful.  
The pastebin is here---http://paste.ubuntu-nl.org/36378/ 

It's the same as the error I posted above but, I thought I would throw it in there as well. 

Thanks!

---

### Post by cmavr8 on 2007-09-05
netgooroo,
if you can see the Ubuntu splash screen, you're past grub...

---

### Post by netgooroo on 2007-09-05
> **cmavr8 said:**
> netgooroo,
if you can see the Ubuntu splash screen, you're past grub...

But I get no log in screen. I thought the log in screen was Grub..  Anyway, it freezes on the splash screen and that error pops up.

---

### Post by cmavr8 on 2007-09-05
No, grub is before any OS. It's the OS selector!

Can't help on the tty problem...
What does google say?

---

### Post by FuturePilot on 2007-09-05
Some people have had success with this method
[http://ubuntuforums.org/showthread.php?t=421588]("http://ubuntuforums.org/showthread.php?t=421588")

---

### Post by SpiritIsReality on 2007-09-05
howdy

I figured the same as far as using dapper to match the internet guides
the latest releases, feisty, soon to be gutsy, are better at ...
the help found at this link is fairly up to date 
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
and then there's free linux books online
[http://ubuntuforums.org/showthread.php?t=484846&highlight=free+books](http://ubuntuforums.org/showthread.php?t=484846&highlight=free+books)

trails

---

### Post by boob11 on 2008-02-02
Thnax

---

