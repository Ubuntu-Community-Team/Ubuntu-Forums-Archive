---
title: "Boot difficulties in Ubuntu"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Allrab on 2006-09-28
H have a full Ubuntu instalation on one my disk all of it just one partition.
I do want to make another smaller partition for window$ but I can not boot with the disc.
So how do I do this?

Is there a forum post about this or can anyone explain this to me?

---

### Post by gn2 on 2006-09-28
My own preference for installing different OS's is to put them on different hard drives.

This makes administration much less complicated.

---

### Post by Allrab on 2006-09-28
Now that comment did not help at all did it.
Im looking for help regarding this problem.

If you have any input please post it here.
It could be a link to another topic or a helpful guide to solve this.

// Allrab

---

### Post by Bigbluecat on 2006-09-28
Hi Allrab,

It's not clear which disc you are trying to boot - is it a WinXP install disk?

Anyway I found the following guide very useful in setting up my system. 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I have WinXP and Ubuntu on two separate hard drives.

You can also serach the forums for dual boot and partition issues. There is lot's of help in here.

---

### Post by Allrab on 2006-09-28
Thank you, I will investigate this.

// Allrab

---

### Post by Metacarpal on 2006-09-28
I think I'm following you - You mean that you currently have:

1 partition, with Ubuntu installed
1 installation CD for WindowsXP

and you want to add WindowsXP to your computer?

Well, there are a number of ways to do this, but adding Windows to an existing Ubuntu install can cause all kinds of problems, and always removes GRUB from the MBR, and you'd have to fix it later.

My suggestion: back up your personal files, do a clean install of WindowsXP, then re-install Ubuntu.

In any event, you said you can't boot from the disc - so the CD-ROM drive won't boot?  You'll probably have to enter your BIOS settings when the computer first comes on, then set the boot order to load from CD-ROM first.

---

### Post by Allrab on 2006-09-28
How do I do that?
Thats what I need to do!

But I cant boot from the CD. thats my problem.

// Allrab

---

### Post by Metacarpal on 2006-09-28
Okay - what kind of computer do you have?

On many computers, pressing F12 at the right time (just before it tries to load from the hard drive - a prompt usually appears on the screen) will give you a list of boot devices, and you can choose CD-ROM temporarily there.  If not, you'll have to reconfigure your BIOS settings.

Most computers, when you first power them on, display a message saying "Press [key] to enter Setup" - this is often Esc, F1, F2, F10, Del, or somesuch.

If your system doesn't display that, just start hitting those keys (one at a time) as soon as the computer starts showing things on the screen.  With any luck, you'll get into BIOS setup.

Otherwise, you'll need to do a web search for your computer's model number and BIOS to find instructions on how to get in.  For instance, on my Toshiba, I first have to hit Esc and then, when prompted, hit F1.

Once you're in BIOS setup, there should be a section marked "Boot" or something similar.  At the bottom of the screen should be instructions on how to get from one section to another.  Once you're there, you'll need to mark the CD-ROM as the first boot device.

Then hit whatever key your BIOS has set as "Save and Exit" (again, should be shown at the bottom of the screen).  This will save your changes and restart your system, and it should then boot from the CD-ROM drive.

Note: all (or almost all) BIOS systems use keyboard navigation only.  Your mouse won't work.  This is normal.

---

### Post by Allrab on 2006-09-28
I think the problem is the GRUB.
It will not launch the corupted M$ windows..
Boot is set on CD first.

I love my Ubuntu but Compiz will not run smoothly with Wine and World of Warcraft so I need to do a Windows install just to play this game.

It worked before I used Compiz and before the new Wine update that messes with my ATI card and screws textures up. That is a known Wine bug on their site. I cant wait for an update on this as I am adicted to World of Warcraft.

// Allrab

---

### Post by gn2 on 2006-09-28
> **Allrab said:**
> Now that comment did not help at all did it.
Im looking for help regarding this problem.

Actually it is sound advice, and was intended to illustrate that there is an alternative to the dual-boot on one hard drive scenario, which to be frank is a potential minefield.

Thing is, you know about it now, so you have been helped, even if you can't appreciate the fact.

Hope you don't have the same problems that (lots) of other people are having with their dual-boot systems come time when they want to remove Ubuntu...

---

### Post by xpod on 2006-09-28
> Actually it is sound advice, and was intended to illustrate that there is an alternative to the dual-boot on one hard drive scenario,

IF you happen to have a second hd:D

---

### Post by Allrab on 2006-09-28
I do hope I can still use Ubuntu even after or if i get window$ back in to the machine.
I love Compiz to much... It is cool to brag with to your M$ friends, I have to :p 

// Allrab

---

### Post by bulldog on 2006-09-28
If you install windows and you need to reinstall GRUB do the folowing,boot the live cd when you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by Metacarpal on 2006-09-28
If you install XP after installing Ubuntu, you'll need to reinstall GRUB to the master boot record (MBR).  [See this thread]("http://www.ubuntuforums.org/showthread.php?t=224351") for a howto.

---

