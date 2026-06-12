---
title: "How to access ntfs files on same hd of dual boot"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by evets on 2006-12-11
Greetings from the great State of Confusion!

Having a successful install and no problems that I haven't been able to resolve on my own, I feel pretty good and I am enjoying this new experience.

Thanks to those who have posted from their own experience, you HAVE helped me...a lot! :)

Now, I need to ask a few questions...

1. How can I access the NTFS files on the same hd as my dual boot Ubuntu/WinXP? I've tried "Browsing" it, but I just get spanked with a "You dont have permission" error msg.

2. I am using a Tablet PC. The "Pen" is working. ( Woo-Hoo ), but I don't know of any "pen" aware applications I can use. Does anyone?

3. I still have not yet figured out how to install my PCMCIA "Aircard", although I have seen that it is recognized by ubuntu.

4. Does anyone have any experience with WINE or VMWare for Linux?

If I can get access to my XP files, get my aircard working and be able to write with my pen, especially on PDF's, I don't see a real need to boot into Windoze any more at all! I use this for business, so these are essential for me.

Thanks so much for any help.


evets

---

### Post by SonicChao on 2006-12-11
I can answer #1.

Run:

```
sudo nautilus /tmp/disks-conf-hda1
```

---

### Post by koolkid64us on 2006-12-11
I'm using Xubuntu 6.06, and accessing NTFS is a matter of a simple 


sudo "file manager" command in the terminal

where "file manager" means the file manager used in your distro, in your case, its the nautilus manager, whereas I'm using the "Thunar" manager.

Sudo gives you "root" access

---

### Post by koolkid64us on 2006-12-11
About the WINE.  


1. Install the package from the repository using Synaptic Package Manager

2. Go to the folder where you downloaded/have your window$ program

3. Open Terminal Here, usually on the right click menu.  Some Cases, it'll be in an "Actions" sub-menu.

4. Type "ls" to be sure you know the EXACT SPELLING of the program (cAsE SeNsItIvE).

5. Type: wine "program name"

6. Should start.  Not 100% compatible with EVERY windows program, but a good chunk of them :).

7. Have fun

---

### Post by Famicommie on 2006-12-11
This is stolen from the system docs that come with Ubuntu:

1. Make a directory where the partition can be made available ("mounted"):

```
sudo mkdir /media/windows
```

2. Next, back up your disk configuration file and open the file in a text editor with administrative privileges:

```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

3. Append the following line to the end of the file:

```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

> Replace /dev/hda1 with the correct device name for your partition.

If your Windows partition uses the FAT32 filesystem, replace ntfs with vfat in the above command.

If you have a FAT32 filesystem, it is also safe to allow read-write access. To do this, change the value of umask to 0000.

4. Save the edited file.

5. The changes will take effect when the computer is restarted.

6. ?????

7. PROFIT!

I did this and it worked like a charm. The mounted drive will be available right on the desktop.

---

### Post by evets on 2006-12-11
Famicommie:

You said to save the new fstab, but where? I have no "Save" option, and I tried to save it to/etc/ but I got the "you don't  have permission" error msg.

---

### Post by evets on 2006-12-11
SonicChao: That worked nicely, thanks.

---

