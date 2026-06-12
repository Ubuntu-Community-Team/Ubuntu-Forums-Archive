---
title: "Installation XP or Ubuntu first - 4 drives involved?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by gmilne on 2007-12-27
I have 2x400G drives with XP installed on existing C:\.

I'm adding  2x80G drives and want to install Ubuntu on what will become the new C:\  (with the option to boot XP) and a new installation of XP on the other, (New D:\ drive).

Is there an order in which I should do this? (eg install the new XP on D:\ first so that the boot manager is loaded?)

Anything else I should watch out for?

Many thanks
/gm

---

### Post by jas0 on 2007-12-27
I'm sure that someone will jump in with an article or a forum post which will help you with the process.

As a general rule, always setup Windows first and Ubuntu second. But keep in mind that before you do anything, ALWAYS back up your data.

---

### Post by gmilne on 2007-12-27
My data is on current drives C: and D:. After the installation of my 2 new drives, (which will become C: and D:) my data will remain on what will become E: and F: after installation of the 2 new drives no? Since these drives won't be accessed during the OS installation process shouldn't they be OK without backup? 
Thanks
/gm
PS  I I do have to backup, what free program  should I use?

---

### Post by phr0ze on 2007-12-27
> **gmilne said:**
> My data is on current drives C: and D:. After the installation of my 2 new drives, (which will become C: and D:) my data will remain on what will become E: and F: after installation of the 2 new drives no? Since these drives won't be accessed during the OS installation process shouldn't they be OK without backup? 
Thanks
/gm
PS  I I do have to backup, what free program  should I use?

Famous last words...
Yes they should be OK if you pick everything correctly. But ubuntu does not use letters like windows does. And even windows will give you a hard time picking drive C if one is already there. I often have to physically remove drives from my system before windows install will assign the new one as C. You will also want to check boot priorities in the BIOS too, of the old drive may still be the one to boot.

Personally I used to stick lots of drives in my system, but now I avoid it and use external cases unless I'm using RAID. SO... I recommend that you only keep 2 hard drives in the system and put the other two in cases which only cost about $30.

---

### Post by jas0 on 2007-12-27
To backup, copy your data to a separate drive. After you're done, disconnect the drive and keep it in a safe place. Copy your data to the drive from time to time to make sure that you have a fresh backup.

Now, as far as the drives go, let me try to explain how things will work...

You have 4 drives

Drive 1 = C:
Drive 2 = D:
Drive 3 = Empty
Drive 4 = Empty

Right now you probably have the BIOS boot from Drive 1.

When you put in the Ubuntu boot CD and you start the installation wizard, select drive 3 for the install and tell is to automatically partition it. Make sure that you do not accidentally select drives 1 or 2. Alternatively, you can select drive 3 for the / (/ is sort of equivalent to C: in windows) parition and drive 4 for the /home partition (sort of like your documents partition).

The installer will detect that you have Windows installed on drive 1 and automatically add it to the startup menu. It will also overwrite the boot sectors on drive 1 with GRUB.

If I were you, I would not do anything until someone posts a good guide with screenshots. It's very easy to botch this setup.

---

### Post by irv on 2007-12-27
Maybe you might want to try this this: There is a program called gparted live. You can download it from [ftp://download.tuxfamily.org/gpartedlive/]("ftp://download.tuxfamily.org/gpartedlive/")
You can download the iso file and burn a CD. Boot your PC with it and you will see your hard drives that are installed and the space that is used and the free space.
What I did on my laptop was to install XP and then Ubuntu. When I got done I didn't have enough space on my Ubuntu install so I used gparted and took some space from Windows and gave it to Ubuntu.
After installing Ubuntu it just sets up grub a boot menu so you can chose between Ubuntu and XP.
If you use gparted be careful not to take too much space from Windows or you may have trouble.
Also I would recommend backing up your data. If anything goes wrong you may lose it. It is always a good practice to backup data on a regular bases.
Irv

---

### Post by gmilne on 2007-12-27
Thanks to everyone. 

OK I can copy everything to external drives.

I had planned on physically disconnecting my current 400G drives C: (with XP on it) and D:\ (data)

I intend to then install Ubuntu on one of the new blank 80G and then another XP on the 2nd new 80G drive.

Next I would reconnect my 400G drives. Am I correct in assuming that both Ubuntu and XP will recognise these drives?

If all went well I then plan to delete my original XP from my old drive.

Anything wrong with these procedures?

---

### Post by jas0 on 2007-12-27
> **gmilne said:**
> Thanks to everyone. 

OK I can copy everything to external drives.

I had planned on physically disconnecting my current 400G drives C: (with XP on it) and D:\ (data)

I intend to then install Ubuntu on one of the new blank 80G and then another XP on the 2nd new 80G drive.

Next I would reconnect my 400G drives. Am I correct in assuming that both Ubuntu and XP will recognise these drives?

If all went well I then plan to delete my original XP from my old drive.

Anything wrong with these procedures?

The only problem you will encounter if you disconnect your current drives will be the inability to easily boot into Windows. But, if you just like to test things, you'll be fine. Once you're done, just connect your old drives back up and go from there. When you're comfortable with Ubuntu, you can start dual booting, where you will be able to have everything connected at once.

---

### Post by jken146 on 2007-12-27
Check out [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)

---

