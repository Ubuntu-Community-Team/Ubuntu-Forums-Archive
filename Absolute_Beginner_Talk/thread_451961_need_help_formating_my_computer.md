---
title: "need help formating my computer"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by indrion on 2007-05-22
Ok, I installed Ubuntu a few weeks ago, and then i had a lot of crap on it (games, music, pictures) and apparently installing every game in the add\remove programs list wasn't the best idea, because while i took them off my computer locked up, so i needed to reboot. then when i tried to log in it said that there wasn't enough space on the hard drive, please contact the administrator or something like that.

so now for about a week i've been booting my computer from the Ubuntu disk, but i want to get windows back. only problem is, when i try to install my XP home edition on boot (because i can't open my disk drive while it's on because of the ubuntu disk) my computer just randomly shuts down during the installation. then i tried my XP professional, same thing.

The only thing i can think of is to format my whole computer, but i have no clue how. I'd prefer to do it myself because i don't have that much money i can use to have it fixed at a shop.

I have a HP Pavilion dv8000 Notebook.

Can somebody help me or point me in the direction of somebody or something that can help?

And PLEASE remember that i will only send it to a shop as an absolute last resort.

---

### Post by blind0wl on 2007-05-22
Are you watching the install of XP Home?  If so where is the PC shutting down?  Is it in the same place every time, or different places?  Are you sure your Power is plugged in properly?  (Thats usually the most common one with laptops).  Your best bet (easiest) is to run the Windows CD and format the drive when you get prompted.  Its not that far into the install so I'm trying to figure out where your PC is shutting down.

---

### Post by scrooge_74 on 2007-05-22
You should try to find a friend whith enough knowledge to help you on your task..  Very odd   that you cant just put the XP in CD in a erase everything.

There are a couple of things you can do.. you can recover the space been taken by downloaded packages that are not needed anymore.

If you trully want to erase your system and either stay on XP or dual boot, you should at least divide your disk in diferent partitions so you can keep your information from been lost everytime you need to reinstall XP or trash your Linux install.

You could either use the Live CD and start an install, when it comes to the partition part, tell the system to do it manually and make the partitions you need, the first one make it ntfs so you can later install XP. Make another in fat32 for your data, and leave some space for a later install of Ubuntu :)

Then tell the system to format all.  Then get out of the install program shutdown your PC and put the XP CD in the bay, start up again and install XP on the ntfs partition that should be recognize.

Latter if you want you can add Ubuntu to the unused space and point it to read the fat32 partition and the ntfs if you want.  Later you can make your /home have a symlink to the fat partition.

It aint to difficult in the end.

A helpfull site is:    [http://www.psychocats.net/](http://www.psychocats.net/)

If you decide to abandon Linux then have fun in XP and we await your return when you are ready.

---

### Post by oilchangeguy on 2007-05-22
are one of the xp cd's a factory restore cd? don't use that one. is the xp pro legal? (that really doesn't matter for this part) insert the non system restore cd. follow the prompts until you get to the part about partitioning. delete any existing partition, then you should be able to install xp. use the legal copy for the actual install.

---

### Post by indrion on 2007-05-22
i can't do any of that...it just randomly shuts down when i'm installing windows, both of em no particular spot. its plugged in, i have an external fan under it, and i can't resize the partion in ubuntu because it only effects the disk and is just undone as soon as the computer gets turned off

---

### Post by scrooge_74 on 2007-05-22
If you use Gparted it will erase all data on the disk..even if it is a Live CD since anyway that is the correct way to do it.,

---

### Post by indrion on 2007-05-23
> **scrooge_74 said:**
> If you use Gparted it will erase all data on the disk..even if it is a Live CD since anyway that is the correct way to do it.,

well i'm worried that if i take ubuntu off it might not let me install windows without crashing

also, why would i want to take it off the disk...thats my only way to open my computer...

---

### Post by indrion on 2007-05-24
bump, i need to do this before friday, can somebody please help

---

### Post by psusi on 2007-05-24
Huh?  You want to reformat the whole drive right?  Then boot from the live cd and fire up gparted and delete all the partitions on the drive.  Then try installing windows.  

Also is this a desktop or a laptop?  You say windows just completely powers off the computer during the install?  At what point?

---

### Post by indrion on 2007-05-24
> Huh? You want to reformat the whole drive right? Then boot from the live cd and fire up gparted and delete all the partitions on the drive. Then try installing windows.

Also is this a desktop or a laptop? You say windows just completely powers off the computer during the install? At what point?
yes i want to format the whole drive, and its a laptop and it just randomly boots down, no particular time.

edit: ok, i just deleted all of the partitions and it just left one there and it said unallocated, here a ss of what it looks like, did i do it right?
[img]http://i140.photobucket.com/albums/r6/Indrion/Screenshot.png[/img]

---

### Post by psusi on 2007-05-24
Yep... that disk is clean.  

Another possibility is that the system is overheating and shutting itself down.  You might find some options in the bios to limit the cpu speed.

---

### Post by obrient on 2007-05-24
Yeah if it is unallocated it means that there isn't anything on it. Now you should be able to boot up with the Win XP disc and get it going. It is odd that the machine is rebooting mid install. When you do get to the Windows hard drive formating you do still need to tell it to format it NTFS or Fat 32. Give it a shot, you really have nothing to loose. I would watch the prompts and make sure that it is going okay.

---

### Post by indrion on 2007-05-24
how would i limit the cpu speed, because that's defenately the problem.

---

### Post by obrient on 2007-05-24
Try checking your BIOS settings and see if you can change it there. Other than that I am unsure.

---

### Post by indrion on 2007-05-24
where do i get into the BIOS settings?

---

### Post by obrient on 2007-05-24
When you boot up your computer you should see the something in the bottom left hand corner of the screen that say press ESC to enter bios. Other keys are delete and F1 to enter BIOS.

---

### Post by indrion on 2007-05-24
ok, i'll restart now and check

---

### Post by jerrylamos on 2007-05-24
Looks pretty blank from here.
Windoze likes to be the first partition on the first hard drive.  If XP, select format NTFS.
Ubuntu can be next.  You'll need a swap at least 512 MB file type swap.  The Ubuntu partition file type ext3 can be next.  Personally I like to have a couple Linux partitions, one that works for me like Edgy 6.10 and a new one to try like Feisty 7.04.  Either will use the same swap.

That would be 4 partitions which you can do as all primary.

With partitions set up with Gparted, on install, select manual partitioning.

Cheers, Jerry

---

