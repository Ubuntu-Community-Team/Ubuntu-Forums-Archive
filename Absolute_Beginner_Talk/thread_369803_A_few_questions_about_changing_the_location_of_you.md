---
title: "A few questions about changing the location of your desktop, etc."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by JimmyHopkins on 2007-02-25
Anyways, I'm a ex-windows user (gasp) and I need some newbie help.

I just made a new partition (/media/DATA) to store all my data (basically my home folder and my desktop).

I want to know

1. How do you change the location of your desktop? I want my desktop to be in /media/DATA/desktop, not /home/username/desktop.

2. How do you change the place of your home? I want Places -> HOME to link to /media/DATA/, but gnome thinks my home is still at /home/username/

Thanks in advance!

(I'm using ubuntu 6.10)

---

### Post by JimmyHopkins on 2007-02-25
bump

---

### Post by taurus on 2007-02-25
What filesystem is /media/DATA?

---

### Post by JimmyHopkins on 2007-02-25
ext3. I used partition magic to basically divide my current ubuntu partition in half.

---

### Post by BobSongs on 2007-02-25
First off: Welcome aboard! Ubuntu's going to be a fun experience. And don't worry about the Windows thing. Many of us are refugees from one camp or another. It's okay. I personally use *gasp* all three: Linux, Windows and Mac OS X. So there. ;-)

I understand the desire to move your home and desktop folders for easier backup. However, I'm not terribly certain one can simply "move" these folders. And if they're on a different physical drive then I understand even more. 

A quick Google search revealed **[this tutorial]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")** by an Ubuntu user. Hope it comes in handy.

Bob

---

### Post by taurus on 2007-02-25
So, basically you want to move your $HOME to that new partition.  Maybe this guide would help, especially the section about [COLOR="Red"]Using the new partition[/COLOR].

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by undertakingyou on 2007-02-25
Also wondering if you could just go SYSTEM => ADMINISTRATION => USERS AND GROUPS and then click on you, click properties, and under the advanced tab in the box that says home folder, just change it to your new drive.  

I haven't tried it.  I just wonder if it could be that easy.  

Doesn't have a spot for desktop though.

---

### Post by JimmyHopkins on 2007-02-25
Tanks.

I actually saw the first guide. I just forgot about it. :p I read it to find out how to see the list of mountable partitions (fdisk -l or whatever).

Does anyone know about the desktop thing? I use firefox which downloads to the desktop. I know I can change that, but it's just too convenient to have everything dl to the desktop.

BTW, I'm doing this because I plan to *AGAIN* nuke ubuntu to install windows (since it like to delete Linux), ubuntu, and kubuntu. having a tri-boot system. 

I wish linux didn't suck at gaming. :( I'm only getting windows back on for Half Life 2.




ALSO: Why does ubuntu nuke windows? Since I installed ubuntu, my windows partition doesn't exist. I just installed with default options, but I assumed it wouldn't delete windows. Knoppix and Fedora Core 6 never did.

Thanks again for all your help.

---

### Post by kevinlyfellow on 2007-02-25
to change your home directory go to the User settings (under the administration panel) and you can change users home directories from there.  Very unfortunately, the gnome devs thought that it would be a good idea to have only two possible places for the Desktop folder -- ~/Desktop or ~

---

### Post by taurus on 2007-02-25
~/Desktop (with a capital D) is part of your $HOME directory so if you move your $HOME to the new partition, so does $HOME/Desktop.

And as far as I know, Ubuntu doesn't nuke your Windows (unless you told the installer to erase your Windows partition).  You just have to mount it first before you use it.

---

### Post by undertakingyou on 2007-02-25
I have heard that some people can run Half Life 2 on ubuntu.  Steam has a linux install.  I don't know if those other people used wine or what.  But some said they could get it going.  I love that glorious game :-D 

On the other note, the default ubuntu option (I think) is to reformat the whole hard drive to ext3.  So, that would wipe out windows.  Be careful of your transfer of the home directory.  If you want windows to see it you can't use ext3.  Windows can't read it.

---

### Post by taurus on 2007-02-25
> **undertakingyou said:**
> If you want windows to see it you can't use ext3.  Windows can't read it.

Yes, it can.

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by JimmyHopkins on 2007-02-25
Sweet! Changing my home via System ->admin ->users and groups changed my desktop location to /media/DATA/desktop. Silly linux users, trying to get me to use the terminal :p. J/K.


BTW, new question. how well does linux read fat32? I'd love to make /media/DATA into fat32 (instead of ext3) so windowz, ubuntu, and kubuntu could all access like one huge data pool.


Also, I'l ask the inverse. How well does windows access ext3? Can it modify files, use files, or just read files? If windows could modify/run/add files to ext3, I'd be throughly pleased.


OFFTOPIC: How old are you undertakingyou? I'm not a predator or anything, but I don't usually expect linux geeks being young enough to play games like hl2. I'm 15. started messing with linux when I was around 13. My first distro was knoppix :p. Then FC6, which is too hard for linux newbs. Then I took a distro quiz and it said ubuntu was a perfect match. It was right. ubuntu is soooo easy!

EDIT: Sorry, just read the link the user above me posted.

---

### Post by Patrick K on 2007-02-25
> but I don't usually expect linux geeks being young enough to play games like hl2.

I'm 58 and I play HL1. I'd do HL2 but my Win OS (W98) isn't up to it.

---

### Post by undertakingyou on 2007-02-25
> **taurus said:**
> Yes, it can.

[http://www.fs-driver.org](http://www.fs-driver.org)

Thanks for putting this out there.  I didn't know. Everyone says windows is ready out of the box and look at the addon's you need to get it to work!:)

[QUOTE=JimmyHopkins]OFFTOPIC: How old are you undertakingyou? I'm not a predator or anything, but I don't usually expect linux geeks being young enough to play games like hl2. I'm 15. started messing with linux when I was around 13. My first distro was knoppix . Then FC6, which is too hard for linux newbs. Then I took a distro quiz and it said ubuntu was a perfect match. It was right. ubuntu is soooo easy![/QUOTE]

I'm 24 almost 25, but the age doesn't matter.  Who wouldn't want to be Gordon Freeman and rescue Alex? ;)

---

