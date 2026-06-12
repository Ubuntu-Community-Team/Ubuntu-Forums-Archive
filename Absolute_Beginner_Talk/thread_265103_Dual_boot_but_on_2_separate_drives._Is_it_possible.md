---
title: "Dual boot but on 2 separate drives. Is it possible/sensible?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by alanmzifa on 2006-09-25
I've just stuck a 2nd hand HDD in my desktop as slave.

I was wondering if it's possible to have Ubuntu on this drive and dual boot it with XP which is on my original (and master) drive.

Anyone know if it is and how I might go about it or is this sort of set-up pointless?

Separately, whatever drive I set up Ubuntu on is it possible to make the file system FAT32 for the Ubuntu partitions (I might put my photos on that drive and access them from Photoshop on my XP drive).


thanks

---

### Post by bulldog on 2006-09-25
Yep there is no problem to do so.
You can't install Ubuntu on a FAT32 partition for sure,it use ext2 or 3.

But there are some issues you should concider.
First to make a separate FAT32 partition to exange your data with XP.

You should realize that Ubuntu install GRUB on the first bootdisk.in your case your windows disk.
This is not always preferable and if possible I would change the boot sequence in the BIOS and made the second hdd [Ubuntu] the boot device so GRUB will be installed there with an option to start your windows.

But in case of trouble you can easely change the boot device in your BIOS and boot from your original windows hdd.

If you need more information how to set things up,just let us know.

---

### Post by xpod on 2006-09-25
Probably the safest bet:D

---

### Post by bodhi.zazen on 2006-09-25
Afternoon Bulldog. I see you've been here.

xpod: good news 'bout that arm.

---

### Post by bulldog on 2006-09-25
> **xpod said:**
> Probably the safest bet:D

I'm very sure it's the safest bet,I do it myself this way.
Although I never needed it,in case of what ever I have always a fresh windows waiting for me.:D

---

### Post by bulldog on 2006-09-25
> **bodhi.zazen said:**
> Afternoon Bulldog. I see you've been here.

xpod: good news 'bout that arm.

Well good evening to you too bodhi [it's 22:11 here]

---

### Post by alanmzifa on 2006-09-25
Thanks for the very quick replies.

Just to confirm I have got this clear ...

In chronological order....

I change my boot sequence to 
1/ cdrom
2/ hdd1  (second hdd)
2/ hdd0  (original hdd)

then reboot with the Ubuntu live cd.

Ubuntu will then load onto hdd1 rather than hdd0 and install there with GRUB which will ensure subsequent reboots hit GRUB on hdd1 (slave) and give me the boot sequence (including Windows XP on hdd0).

When partitioning my Ubuntu installation on hdd1 I can use ext2/3 for the root partition and FAT32 for Home? Or do I have to use ext2/3 for Home also and put my pictures folder on a separate partition as FAT32 for Windows to access.

Have I got it right?

---

### Post by alecjw on 2006-09-25
I don't reccomend a seperate FAT32 partition. There are plenty of progs for windoze which will open ext2/3 partitions.

---

### Post by bodhi.zazen on 2006-09-25
> **alanmzifa said:**
> Thanks for the very quick replies.

Just to confirm I have got this clear ...

In chronological order....

I change my boot sequence to 
1/ cdrom
2/ hdd1  (second hdd)
2/ hdd0  (original hdd)

then reboot with the Ubuntu live cd.

Ubuntu will then load onto hdd1 rather than hdd0 and install there with GRUB which will ensure subsequent reboots hit GRUB on hdd1 (slave) and give me the boot sequence (including Windows XP on hdd0).

When partitioning my Ubuntu installation on hdd1 I can use ext2/3 for the root partition and FAT32 for Home? Or do I have to use ext2/3 for Home also and put my pictures folder on a separate partition as FAT32 for Windows to access.

Have I got it right?


boot order in bios:[list=number][*]CD-ROM
[*]Hard Drive[/list]

install ubuntu

allow ubunut to install grub to your MBR.

---

### Post by xpod on 2006-09-25
The three amigo`s

[ATTACH]16345[/ATTACH]:mrgreen: 

And the leg`s fine.......he landed on his heid

EDIT:> [it's 22:11 here]
Strange......it`s only the 23rd o september here..Soon be xmas where you are then:mrgreen:

---

### Post by bodhi.zazen on 2006-09-25
> **xpod said:**
> The three amigo`s

[ATTACH]16345[/ATTACH]:mrgreen: 

And the leg`s fine.......he landed on his heid

Now that's nice. Sorry 'bout da well whatever..... :p

---

### Post by alanmzifa on 2006-09-25
> **bodhi.zazen said:**
> boot order in bios:[list=number][*]CD-ROM
[*]Hard Drive[/list]

install ubuntu

allow ubunut to install grub to your MBR.

and as there are **2** hdd s

1./ cdrom
2./ HDD1
3./ HDD0 

yes?

---

### Post by maaronB on 2006-09-25
> **alanmzifa said:**
> 
...

When partitioning my Ubuntu installation on hdd1 I can use ext2/3 for the root partition and FAT32 for Home? Or do I have to use ext2/3 for Home also and put my pictures folder on a separate partition as FAT32 for Windows to access.
...


Read
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by bodhi.zazen on 2006-09-25
> **alanmzifa said:**
> and as there are **2** hdd s

1./ cdrom
2./ HDD1
3./ HDD0 

yes?

In your BIOS you only need to boot to 1 HD, your master, HDD0.

Grub will do the rest...

---

### Post by xpod on 2006-09-25
Sorry mate.
Once you start up the live cd and run the installer it will end up at the partitiong stage from where you can just point it to the HD that windows is NOT on and it will do it all for you.

Or these 2 good men will show you how to set up all the partitions manually with partitions for all your needs.

It`s all a bit intimidating at first but it`s not as scary as it seems.
Just so long as you keep track of what HD is what:mad:

---

### Post by bulldog on 2006-09-25
> **alanmzifa said:**
> Thanks for the very quick replies.

Just to confirm I have got this clear ...

In chronological order....

I change my boot sequence to 
1/ cdrom
2/ hdd1  (second hdd)
2/ hdd0  (original hdd)

then reboot with the Ubuntu live cd.

Ubuntu will then load onto hdd1 rather than hdd0 and install there with GRUB which will ensure subsequent reboots hit GRUB on hdd1 (slave) and give me the boot sequence (including Windows XP on hdd0).

When partitioning my Ubuntu installation on hdd1 I can use ext2/3 for the root partition and FAT32 for Home? Or do I have to use ext2/3 for Home also and put my pictures folder on a separate partition as FAT32 for Windows to access.

Have I got it right?

Yep you got the big lines.
You should create an FAT32 partition outside your Ubuntu.

You will encounter one thing when you do it this way.

It seems windows want to be installed onto the first hdd and can't imagine it isn't.
When you install the way I suggested,you have to make some changes to your menu.lst.
You have to map your hdd's there but that's a minor thing and cost no more as 5 minutes to accomplish.
Give me a pm or reach me on msn to ask how to that.
Windows will not boot from GRUB as you do so,but don't worry it will.

---

### Post by bodhi.zazen on 2006-09-25
> **maaronB said:**
> Read
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Nice link for sure, but we are dealing with 2 HD and, at the moment, setting bios. :idea:

---

### Post by bulldog on 2006-09-25
> **bodhi.zazen said:**
> In your BIOS you only need to boot to 1 HD, your master, HDD0.

Grub will do the rest...

Nope,bodhi,sorry but that's not what I have in mind.

I wil swap the hdd's so grub will install on it's own hdd and not the windows hdd.

So when grub failes he can swap back the bootdevices in BIOS and start windows with is own loader without dealing with GRUB at that moment.

The only weak thing is,he must have the possebillity to swap his bootdevice in BIOS,but if he can boot the second hdd this is the safest way to do.

---

### Post by bodhi.zazen on 2006-09-25
Thanks for the info Bulldog. My BIOS will not do that; thus I was confused. :rolleyes:

Now I know why I usually leave the partitioning to you (and the humor to xpod).

---

### Post by alanmzifa on 2006-09-25
bodhi, that link explains the different file formats very well. Nice and simple.

bulldog, so what do I need to do?

If I start the install now it should only take about 20 minutes. 

Can you explain about this menu.lst, where it is and what I have to do to edit it to make it "map" the hard drives. (Can you tell I've no idea what I'm talking about?). And is mapping the hard-drives the last thing I do after going through the install cycle?

---

### Post by xpod on 2006-09-25
> My BIOS will not do that; thus I was confused. 

So is that "bad luck" or "luck o the irish"??

You all know what I thought a "partition" was a month or 2 ago so dont worry about the confusion mate:mrgreen:

---

### Post by bulldog on 2006-09-25
Mapping the hdd is the last thing you do after the install.:D

Are you sure you can swap your boot device?
If so do it and fir up the live cd.

On the desktop you'll find the install button.
Some questions are asked and you have to fill in not fifficult to do.

When coming to partitioning your hdd you have three options,I skip the manual because you must be knowing a little more about that,just let Ubuntu use the whole hdd,exeption if you make your FAT32 on this drive to.
Then you should point out ubuntu manually to the space you provided for it.

Look carefull you choose the right hdd and the right partitions and if you're sure it's what you want hit the install or apply button.

After half an our or so it's done and you will reboot and remove the cd.
Now you will see GRUB and you can choose between windows and grub,default is ubuntu.

Choose ubuntu and see if it's booting well without errors.[most of the time]
 If it loads fine you should open a terminal from your menu.

Type in your terminal.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_copy

To make a copy of your menu.lst,make a habbit to make a copy before altering things.

Type in terminal

sudo gedit /boot/brub/menu.lst

Opens your menu.lst in an editor.

Goto the bottem wher you see your windows and alter it as follows.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader    +1

This should work fine but if it isn't switch the (hd0.0) and the (hd1.0) on both lines.

sudo means asking for root rights and you should enter the password you made by installing.

I wish you succes with installing,but all should be smooth if you use common sense and don't over haste,read well,especially the partitioning and it will work like a charm.

---

### Post by jimrz on 2006-09-25
> **alanmzifa said:**
> I've just stuck a 2nd hand HDD in my desktop as slave.

I was wondering if it's possible to have Ubuntu on this drive and dual boot it with XP which is on my original (and master) drive.

Anyone know if it is and how I might go about it or is this sort of set-up pointless?

Separately, whatever drive I set up Ubuntu on is it possible to make the file system FAT32 for the Ubuntu partitions (I might put my photos on that drive and access them from Photoshop on my XP drive).


thanks

absolutely is possible. i have my desktop setup that way. don't know how big your drives are ( i have 2 rather large ones) but would definitely recommend creating a large separate FAT32 partition where you can keep your photos/music/whatever and have access from both ubuntu + xp.

also stongly recommend [[COLOR="Sienna"]**_downloading_**[/COLOR]]("http://www.ubuntu.com/download") the "alternate" install cd and following [[COLOR="Sienna"]**_this_**[/COLOR]]("http://users.bigpond.net.au/hermanzone/") excellent guide for your install.

Welcome !

---

### Post by alanmzifa on 2006-09-26
Install and repartitioning went pretty much OK but....


I seem to have run into trouble with the menu.lst file. Have tried to switch things in it but can't boot Windows, just Ubuntu.

Forgot to take a copy of menu.lst so I'm going to go through the whole thing again to get myself back to the unadulterated menu.lst file.

[B]

jimrz , can you show me what you're menu.lst file text is?[/B]

I have a 2 HDD set-up.
XP is on master  (hda - first partition)
Ubuntu is on slave (and so should GRUB). (hdb - first partition)

Boot order in BIOS should be hdb then hda.

---

### Post by alanmzifa on 2006-09-26
Well, I think I sorted it out.

I re-installed from scratch to get back to my virgin menu.lst and changed the boot order. 

I had my slave HDD set as 1st boot (hd1) thinking that GRUB was installed there.

GRUB must be on my master, original HDD (hd0) as changing the boot sequence to have hd0 first corrected the problems. I didn't need to edit the menu.lst file, Ubuntu/GRUB did it all on it's own. I can now boot into both Windows XP and Ubuntu.


Thanks to everyone who commented and offered help, especially bulldog.


The only small problem I had which I couldn't resolve during installation was my old Ubuntu partitions on the original (master) dual booted drive. 
I wasn't able to reformat this space to NTFS and instead had to leave it as ext3. So hd0 has 2 instead of 1 partitions and I've 4Gb "lost" space.

---

### Post by gn2 on 2006-09-26
You might be able to get the "lost" space back using the gparted live CD?

---

### Post by bulldog on 2006-09-26
Glad to hear you made it work.

Not exactly like I had in mind,but who cares :)
The lost space isn't lost and we can get it back.

When you're ready to do so,give a shout and we'll be here.

Let me welcome you to the Ubuntu world,and enjoy.

To get your multimedia stuff,java and a lot of other programs,I advice to take a look at Easy Ubuntu.

[http://ubuntuforums.org/showthread.php?t=84742](http://ubuntuforums.org/showthread.php?t=84742)

And take a look at the HowTo tips and tric's forum,you can learn a lot from it.

Succes.

---

