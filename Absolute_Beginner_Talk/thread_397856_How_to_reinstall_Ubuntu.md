---
title: "How to reinstall Ubuntu?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Fjatle on 2007-03-31
Hi all!

I have recently got Linux on my laptop.. I am as newbie as it gets..
First of some tech about my installation:
A guy at work set up my computer like this:

One Ntfs Partition with windows on it (dont want to lose that!)
One Fat32 Partition where I store media for use in both Ubuntu and Windows. (Dont want to loose that one either!)

Then I have a reiserfs partiton with ubuntu on it.
One small ext partition with grubloader on
And one (or two?) partition wich is called extended (I dont know what that is for.

-------------------------------------

edit: My version is Ubuntu Edgy (6.10) by the way

Now on to my problem:

After Installing and uninstalling Lots of software, my desktop will not load.. I only get a ubuntu-brown screen. Usally there is a window popping up at startup which indicates what software is being booted. This is no longer appearing.

I dont know what have caused this (problably my installing and uninstalling, but I dont know which software may caused it), and I dont know how to figure out what may caused it, since the only way I can do anything is to go to the command line (and I am not familar with the command line)

So a quick fix must be to reinstall My ubuntu (I guess??)
Now since I am a comlete newbie at this, I need a step-by step guidence of how to do it..

The last time I tried to REinstall, I ended up with TWO Ubuntu partitons, and nothing worked.
 
IF anyone bother to give me this step by step guide (keep in mind all my patitons),
then i have another issue in mind..
You see, there is some conflict with my Intel945 Graphic driver.. :(
I could only get 1024x768 insted of 2080x800 which is recommended for my screen.
It can be fixed with the 915resolution. But the guy who fixed it for me came up with 
this following problem: 
915resolution got loaded AFTER X got loaded. So I had to do the CTRL+ALT+BACKSPACE to load X with 915resolution... understand??

So if i get Ubuntu reinstalled, how can i change the boot order so 915resolution can be started before X??

----------------------------

---

### Post by zvacet on 2007-03-31
Boot up your Ubuntu CD and start installation proces.When you came to partition step choose manualy way.You will see all partitions you have,and stay away of everything you want to keep.That leed as to space that can be format.If you didn´t erase your swap partiton leave it too.Basicly you will install Ubuntu on the space left after all of this.Highlight that partition and choose to delet it.Now you  have free space to install.if that partition is 10GB or less choose automaticly make partition(or something like that) And installer wlll format partition for you.Let that partition be in ext3 format.About resolution issue I can not help.Search the forum and I´m sure you will find answer.

---

### Post by mikewhatever on 2007-03-31
The setup with Grub boot loader on a separate partition is somewhat uncommon, I don't know a guide that deals with that kind of installation. Basically, all you need to do is format Ubuntu ext3 partition, reinstall Ubuntu on it, and install Grub to the partition intended for it. Here is a guide that deals with the clean install and partitions, apart from the one for Grub.

---

### Post by Fjatle on 2007-03-31
Thanks for fast reply!

About that grub partition..
The guy who set up my partitions said i cannot use reiserfs to start the grub.

But still he advised me to use reiserfs becouse it could handle more cut-the-power-off-kind-of-shutdown :)

But ok, I defenitly leave the ntfs and the Fat32 partions. That is a no-brainer.

But do i ONLY format the reiserfs? or should i format both reiserfs AND the grub partiton?

IF i only format reiserfs, will ubuntu installer automagicly make another grub and all hell is loose??

---

### Post by seshomaru samma on 2007-03-31
What I would do is :
Boot from the live CD
open a terminal and put the command :
```
sudo fdisk -l 
```
this will give you the partition table the way linux sees it
make sure you identify your windows and data partitions which you dont want to lose (in case of doubt post the output here and we will help you identify)
{EDIT - I guess you did that already}
install Ubuntu
when you get to the partition part chose 'manually edit the partition table'
format all the partitions (except the two you want to keep) as Ext3 
 { EDIT- format the grub partition as well}
continue with the installation 
towards the end it will ask you if you want Grub (the boot loader) to be installed on the MBR - answer 'yes' - this will make things much more simple
after you install ubuntu -post a new thread in this forum about your graphic card and screen resolution and we will help you solve the problem

---

