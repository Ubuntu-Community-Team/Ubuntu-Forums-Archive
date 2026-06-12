---
title: "Understanding Partitions"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Sq322 on 2006-05-30
I currently have a winxp laptop setup with the NTFS file system.
When i look at my partitions i have
hda1 which is a fat16 partition
hda2 which is the main xp partition (ntfs)
hda3 which is a fat32 partition

Any idea why i have ALL 3 of these ?
I am gonna install dapper into an extended partition with the unused HD space from hda2
basically setting up the machine with 
swap - 1gb 
/      - 4gb
/home - 8gb

Any insight into my multiple windows filesystems would be good before i forge forward.
Thx

---

### Post by tonyr on 2006-05-30
Is your laptop a major brand, or did it come with some well known 
commercial support package?  I have a Dell laptop which was purchased
directly from Dell.  It came formatted with a dedicated small support partition (hda1)
and a fat32 partition (hda2), but when it was new the OS was NT or Win2k. I think.

I suspect something like that is going on with your laptop.  You should find out what the
partition sizes are with **fdisk** or **gparted** or **qtparted**.

---

### Post by Rinzwind on 2006-05-30
sq322: companies like dell put 2 hidden partition onto your disc.
1 with your Windows emergency disc. The other one 1 forgot what it was for :)

I deleted them after I made a copy of Windows (like I was told to) and then installed Ubuntu :+

---

### Post by Sq322 on 2006-05-30
Thx for the response
It is in fact a Dell Laptop
And now that you mention it, the hda1 partition does have some stuff in it that deals with Dell and the support that they install

I am guessing that this is NOT a stumbling block to installing Ubuntu in the way i laid it out..
correct?

---

### Post by tonyr on 2006-05-30
...and I guess it would be good to know whether there is anything you want to keep
on the third partition...

---

### Post by Sq322 on 2006-05-30
[QUOTE=Rinzwind]sq322: companies like dell put 2 hidden partition onto your disc.
1 with your Windows emergency disc. The other one 1 forgot what it was for :)

I deleted them after I made a copy of Windows (like I was told to) and then installed Ubuntu :+[/QUOTE]

I plan on keeping my windows partition as i need it for some work related things.

what do you mean you deleted them (i assume you are referring to the fat16 and fat32 partitions..) were you still able to boot into your windows partition after that ?

---

### Post by Rinzwind on 2006-05-30
[QUOTE=Sq322]I plan on keeping my windows partition as i need it for some work related things.

what do you mean you deleted them (i assume you are referring to the fat16 and fat32 partitions..) were you still able to boot into your windows partition after that ?[/QUOTE]

No no. Sorry for not being clear :)

Dell (for instance) ships your harddisc with Windows installed. But it also has  small hidden partitions (I think it was 8 mb on my system?). On that they install a recovery: it contains all the drivers your system needs (so you can recover your system to the default Dell shipped it with). 

When you are inside windows you should have a link inside 'start programs' where you can  make your Windows CD. It'll create a CD with your serial in it (so you don't  need to type it when you install it) and some other shortcuts.

After making your CD you can free those MBs and add them to your normal disc with partition magic.

---

### Post by tonyr on 2006-05-30
[QUOTE=Sq322]Thx for the response
It is in fact a Dell Laptop
And now that you mention it, the hda1 partition does have some stuff in it that deals with Dell and the support that they install

I am guessing that this is NOT a stumbling block to installing Ubuntu in the way i laid it out..
correct?[/QUOTE]

No problem. I still have the originally defined partitions, plus several more
defined later with multiple *ixen.    If you are planning to keep a Wx OS
in the NTFS partition (I guess I'm assuming there is one there) that
you want to keep, the Ubuntu installation will recognize it as such and
set up a 'dual-boot' situation for you.   If you are just going to wipe it
all and start over,  it doesn't matter.

---

### Post by aysiu on 2006-05-30
Some reading you may be interested in:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by tonyr on 2006-05-30
...and here's a plug for the wiki...[DrivesAndPartitions]("https://wiki.ubuntu.com/DrivesAndPartitions")

EDIT: repaired link

---

### Post by aysiu on 2006-05-30
[QUOTE=tonyr]...and here's a plug for the wiki...[DrivesAndPartitions]("https://wiki.ubuntu.com/DrivesAndPartitions)[/QUOTE] Your link has too many https in it.

[https://wiki.ubuntu.com/DrivesAndPartitions](https://wiki.ubuntu.com/DrivesAndPartitions)

---

### Post by tonyr on 2006-05-30
oops, sorry..thanks for the fix...

---

### Post by Sq322 on 2006-05-31
[QUOTE=aysiu]Some reading you may be interested in:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)[/QUOTE]

aysiu
I have read and re-read your stuff..it is great..
thx for the quick links :-D
I am gonna lay it out as the linux partition being an extended partition containing
(1) /home
(2) /
(3) swap

---

### Post by Sq322 on 2006-05-31
Ok i am midway thru install and partitioning and this is what i get.
I set my partitions as follows.
hda4 is an extended partition
i created 3 subs under it.
768mb as swap
5 gb as ext3 for /
6 gb as ext3 for /home

when i pass thru the installer and it asks to confirm it is showing TWO swap and one ext3 ?? ( the second swap is the one i set to be /home )
What Gives ?? !

---

### Post by aysiu on 2006-05-31
No idea.

Are you using Breezy or Dapper?

If you're using Dapper, can you post a screenshot?

---

### Post by Sq322 on 2006-05-31
Dappers new installer. Which up until this stage worked beautifully.
I used gparted to set my partitions with ease.

I am working off of the RC that i downloaded ..
Wonder if it is an installer bug...

excuse my noobity..where would i find the app to take the screenie

---

### Post by aysiu on 2006-05-31
[QUOTE=Sq322]Dappers new installer. Which up until this stage worked beautifully.
I used gparted to set my partitions with ease.

I am working off of the RC that i downloaded ..
Wonder if it is an installer bug...

excuse my noobity..where would i find the app to take the screenie[/QUOTE] You can try just pressing the [Print Screen key](http://www.jhu.edu/~gifted/writing/techhelp/images/printscreenbutton.jpg). That should invoke *gnome-screenshot*.

---

### Post by tonyr on 2006-05-31
In Ubuntu (Gnome) it's **Applications->Accessories->Take Screenshot**.
In Kubuntu (KDE) it's **Kmenu->Graphics>Screen Capture Program (Ksnapshot)**.

Attach the resulting .png file with the **paperclip** icon in this editor.

---

### Post by Sq322 on 2006-05-31
[QUOTE=aysiu]You can try just pressing the [Print Screen key](http://www.jhu.edu/~gifted/writing/techhelp/images/printscreenbutton.jpg). That should invoke *gnome-screenshot*.[/QUOTE]
:D 
Im a fluent computer user...i just thought there was something more too it than that...
thx for the graphical assistance locating the key though :p

---

### Post by aysiu on 2006-05-31
[QUOTE=Sq322]:D 
Im a fluent computer user...i just thought there was something more too it than that...
thx for the graphical assistance locating the key though :p[/QUOTE] When I'm in the Absolute Beginner section, I usually tend to err on the side of explaining too much!

---

### Post by Sq322 on 2006-05-31
[QUOTE=aysiu]When I'm in the Absolute Beginner section, I usually tend to err on the side of explaining too much![/QUOTE]
No problem at all
totally understandable.

it gave me a good midday laugh

---

### Post by Sq322 on 2006-05-31
[Partition Bug?]("http://ubuntuforums.org/showthread.php?p=1072904#post1072904")

Here is a link to a post in the Dapper Forum and the responses i got from those folks.
Sounds like i am just gonna wait yet another day or so to get installed.

---

