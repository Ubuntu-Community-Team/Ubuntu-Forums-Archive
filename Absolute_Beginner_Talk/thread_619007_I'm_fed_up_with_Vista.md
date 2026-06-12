---
title: "I'm fed up with Vista"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by ChunkOFunk on 2007-11-21
Some may recognize me from a previous post where I wanted a seperate partition with Vista on it, and one with Ubuntu. I went about this the wrong way and ended up with a not functioning boot menu that didn't recognize The Ubuntu boot sector (Or something to that effect). So I was left with a smaller vista partition and a not functioning Ubuntu Partition. 

So, Now what I want to do is:
1. Delete the not functioning Ubuntu partition
2. Create a new partition that won't break my Vista one to Install Ubuntu on
3. Back up All my media on my  Vista Partition onto my Ubuntu partition
4. Reformat the broken Vista install (Without corupting my Ubuntu partition) to install XP on it
5. Enjoy a not broken Dual Booting experience Ubuntu for casual and business, XP for games

Even something as simple as a link to how to do this would be wonderfully appriciated. 


Wonderfully appreciated
Duncan Smith

*Yeah that's right, I used my REAL name*

---

### Post by mdpalow on 2007-11-21
I think it would be prudent at this point to first back-up your media to CD/DVD or maybe a USB External Hard Drive. Any chance you can do that before doing all that you want to do?

If so, I think there's a pretty simple and straight-forward way of doing this.
..

---

### Post by bluepowder7 on 2007-11-21
question - why not just copy the files you want to keep from Vista onto an external hard drive or burn onto a CD / DVD, and then wipe the entire hard drive clean and do a proper install of WinXP followed by Ubuntu.  would save you the hassle of moving partitions around and hoping that your files don't go POOF in the process.

EDIT - do you have a USB memory stick?  if not, get one.  it'll come in handy.  would all your crap fit onto a 4gig stick?  if so, get one, move files, format entire hard drive, reinstall OSes.  ta-da!!!

---

### Post by mdpalow on 2007-11-21
> **bluepowder7 said:**
> question - why not just copy the files you want to keep from Vista onto an external hard drive or burn onto a CD / DVD, and then wipe the entire hard drive clean and do a proper install of WinXP followed by Ubuntu.  would save you the hassle of moving partitions around and hoping that your files don't go POOF in the process.

Exactly what I was going to suggest if you could save off the media...

..

---

### Post by Jimmyfj on 2007-11-21
Depending on the size of your hard drive the best thing to do is to make a aprtition for your XP, with the XP installer. Install XP and then defrag the drive before you go about installing Ubuntu. Just use the Ubuntu Live Cd for the Ubuntu install and let the installer resize your drive during install. 

Decide how big a partition you'll need for XP and let Ubuntu take over the rest of the disk. Unless you are experienced with disk partitioning let the installer create the partitions for you. Make sure to backup your data before you do anything else.

---

### Post by Dripbagulhos on 2007-11-21
> **ChunkOFunk said:**
> Some may recognize me from a previous post where I wanted a seperate partition with Vista on it, and one with Ubuntu. I went about this the wrong way and ended up with a not functioning boot menu that didn't recognize The Ubuntu boot sector (Or something to that effect). So I was left with a smaller vista partition and a not functioning Ubuntu Partition. 

So, Now what I want to do is:
1. Delete the not functioning Ubuntu partition
2. Create a new partition that won't break my Vista one to Install Ubuntu on
3. Back up All my media on my  Vista Partition onto my Ubuntu partition
4. Reformat the broken Vista install (Without corupting my Ubuntu partition) to install XP on it
5. Enjoy a not broken Dual Booting experience Ubuntu for casual and business, XP for games

Even something as simple as a link to how to do this would be wonderfully appriciated. 


Wonderfully appreciated
Duncan Smith

*Yeah that's right, I used my REAL name*

There is no need of re-installing Ubuntu!! The problem is that you installed Ubuntu before Vista. You should always install any Windows first (leavng space for linux partitions) and after this any Linuxes.

Try to do the following:

1) Boot with live cd
2) Open the terminal
3) type sudo grub
4) It will open a grub shell. On that shell type root (hd0,1) suposing you have only one hd 
5) type setup (hd0)
6) type quit

It should re-install grub and you will be able to start ubuntu. I think after this you will have to edit /boot/grub/menu.lst to have a menu with your vista partition. Mine (windows XP) is like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by stinger30au on 2007-11-21
you always need to install windows first.it likes to think it is important and needs to take everything over.
after it has been setup you can then install what ever else you like, where ever you like

---

### Post by ChunkOFunk on 2007-11-21
Thanks for all the responses guys. Yeah, I do have an external hard drive, it just has a pretty slow write speed, so I tend to get irritated, and system formats kill me inside, but I guess theres no way of getting around it. *I always forget something when I'm formatting*

Thanks for all the help.

---

### Post by mike555 on 2007-11-21
Be sure to backup your bookmarks/favorites ........ many people forget them .

---

### Post by gn2 on 2007-11-21
> **stinger30au said:**
> you always need to install windows first

No you don't, you can install it after installing Ubuntu first, but you'll need to re-install Grub or use an alternative bootloader.
Windows likes to sit at the start of the hard drive, but can be made to boot from anywhere on the drive.

---

### Post by shearn89 on 2007-11-21
Its just easier to install 'doze first, and then when the kids have had their fun, let the real men out to play...

EDIT: sorry, i don't know why i had to make that sound so macho. What i mean is, it saves you reinstalling grub if you install windows first.

---

