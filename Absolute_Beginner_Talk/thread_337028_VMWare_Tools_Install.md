---
title: "VMWare Tools Install"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Contrid on 2007-01-12
Hi there,

How difficult is it to install vmware tools?
In the vmware server console with Windows XP currently running, I click "Install VMWare Tools..."

It's taking ages...
I can't see any progress at all...and don't know if it's installing.
The "Install VMware Tools..." changed to "Cancel Vmware tools install..."
I've been sitting here for hours.

Please help.
I really need to get this installed, since XP is quite slow.

Thanks in advance

---

### Post by Iarwain ben-adar on 2007-01-12
Hiya,
please click "install Vmware Tools",
and then you go inside Xp.

Open your cd-drive (the one in Xp), and install the tools :wink:


Iarwain

---

### Post by Contrid on 2007-01-12
> **Iarwain ben-adar said:**
> Hiya,
please click "install Vmware Tools",
and then you go inside Xp.

Open your cd-drive (the one in Xp), and install the tools :wink:


Iarwain

I love the way you put the "the one in XP" between brackets.
I'm dead serious when I say that I didn't know that.
Let me give it a shot and get back here right now.
Thanks so much. ;)

---

### Post by Contrid on 2007-01-12
It's extremely slow...
I have a pretty nice computer.

AMD 64 x2 Dual Core 2,2Ghz
1Gig Dual Band DDR2 800
nVidia Geforce 6600 256Mb DDR3

For some reason it's sooooo slow...
(the xp)
What can I do to speed it up?

---

### Post by Iarwain ben-adar on 2007-01-12
It is installed?
Did you reboot?

btw, i didn't know that either when i first started using Vmware :oops:


Iarwain

---

### Post by Contrid on 2007-01-12
> **Iarwain ben-adar said:**
> It is installed?
Did you reboot?

btw, i didn't know that either when i first started using Vmware :oops:


Iarwain

I haven't installed it yet.
Windows XP is running very very very slowly.
You have no idea.
It takes about 20 minutes to open "My Computer"

---

### Post by Contrid on 2007-01-12
I know that XP has alot of things running.
Maybe I should boot into it and remove all autostart items.
Disable virtual drives, etc...

---

### Post by Iarwain ben-adar on 2007-01-12
That's strange indeed :?

Just a quick question:
Did you assign enough ram to Xp? (normally you should, but one can never know :D )

And 20 minutes is quite slow, yes...

Isn't there a heavy program in Ubuntu running? Or something that could take out all your pc's power?


Iarwain

---

### Post by toolazy2work on 2007-01-12
Is XP installed in the Virtual machine or is linux install in the virtual machine?  You have to mount the cd image within the virtual machine and run it from with in the virtual machine.  Also, how much memory do you have allocated to your virtual machine?  This will affect the performance drastically.  How many process do you have running as well as your virtual machine?  This will also affect performance.  Try adjusting memory to see if this has any increase in speed and report back.

---

### Post by Contrid on 2007-01-12
> **toolazy2work said:**
> Is XP installed in the Virtual machine or is linux install in the virtual machine?  You have to mount the cd image within the virtual machine and run it from with in the virtual machine.  Also, how much memory do you have allocated to your virtual machine?  This will affect the performance drastically.  How many process do you have running as well as your virtual machine?  This will also affect performance.  Try adjusting memory to see if this has any increase in speed and report back.

Nothing is installed on vmware.
XP is being used as a physical drive.
I'm currently running Ubuntu as I type this.

I was thinking...
Maybe I can boot into XP and install VMware tools that way !?!?
Is it possible?

---

### Post by Iarwain ben-adar on 2007-01-12
Meuh?

How do you mean? Are you running Xp _inside_ Vmware?
Do you want to install Vmware tools in a real Xp (e.g. not emulated?)

If that's what you mean, i'm afraid that doesn't work...
(but i am not always correct, so do note take my word for truth :wink:)


Iarwain

---

### Post by Contrid on 2007-01-12
Yeah...I'm running XP inside vmware using physical disc partition.
Is that wrong ?

---

### Post by Iarwain ben-adar on 2007-01-12
I didn't know that was even possible :D

Don't know what could go wrong though (maybe the slowness is because of that, i do not know)

Just a quick question, are the Ubuntu and Xp drives 1 ?

Are they on the same hard drive, but different partition? (if so, that _could_ explain the slowness)
If not, i do not know actually :?


Iarwain

---

### Post by Contrid on 2007-01-12
Hi there,

WinXP is on another hard-drive.
Ubuntu is on it's own.

---

### Post by Iarwain ben-adar on 2007-01-12
Hmm,
so the hard drive shouldn't be having any problems then...

Don't know anything more, sorry.


Iarwain

---

### Post by toolazy2work on 2007-01-12
what do do the cpu usages look like on each os? is there something taking up a lot of cpu usage.  I thinkt hat this slow running is inevitable because two oses are trying to run independantly so i think they are arguing over the cpu and memory?  you need to create a vmx file and install xp on that.  this should fix the slowness issue

---

### Post by Contrid on 2007-01-12
Ok, guys...
Thank you very much for your responses.
I really appreciate the time you took to help me out.

I booted into windows, and cleaned it up.
Uninstalled unecessary applications, including antivirus, firewall, etc...
I also removed all startup entries (autorun)

It works fine now in vmware.
I used that OS for years, so it's bloated full of software installations, shortcuts, etc...

I'll come back once vmware tools has been installed.

---

### Post by Iarwain ben-adar on 2007-01-12
Just glad you got it worked out :D


Iarwain

---

### Post by Contrid on 2007-01-12
It works GREAT!!!
I'm really impressed with this.
There are ONLY two reasons why I need XP.
[LIST=1]
[*]Flash
[*]Photoshop[/LIST]No one will see me dual booting again. ;)

THANK YOU very much for all of your help.
Everyone who posted here.

---

