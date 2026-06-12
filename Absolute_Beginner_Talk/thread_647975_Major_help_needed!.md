---
title: "Major help needed!"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Goemon4 on 2007-12-23
*short explination at bottom if you dont feel like reading, im just trying to explain things, but if you need to know what help i need scroll to the bottom*

Ok, i recently replaced ubuntu with fedora core 8 recently, and loved it. I was messing around in yums gui, and went to install all the gnome packages (ya know right click, install optional packages or something) welll i accidentally hit deselect all packages, and it removed EVERYTHING!! (gnome, xfce, gdm, hell i cant even run the ifup command!) 

i say the ifup command cause i can boot into a text based fedora. Since x wont load, and i have no login manager. I thought in the text interface i can just use yum and re-install gnome and everything else. Well it didnt configure my internet connection, so i try ifup eth0 as root. Command not recognized. Apparently that isnt working. 

So i have been desperatly trying to find a way to access my hard drive from a live cd. I only have a fedora live cd, a suse live cd, and a x/k/ubuntu live cds. (and, as usual, have no blank discs, so no knoppix, which i heard could automount hard drives) 

Ok, so in suse i tried re-sizing the partition, so mabey i could install suse then access the other partition in there. Well, that didnt work, (mostly since i have no clue how to use yast) so i went back to my fedora live cd and tried using gparted... That couldnt resize it either. I found out in suse that the drive was (instead of ext3) LVM2_member and i have no idea why.

I pretty much just need to back up a few very important files, like irreplaceable files. While in text-based fedora i found out my home folder was perfectly intact so i just need to find a way to access it with a gui, since i need to back up files scattered throughout my drive also.

So if anyone knows anyway in the ubuntu live cd to access this drive in nautilus or something, id love you for life. Or just anyway to access hard drive via the live cd, would help tremendously! 

I just need to access a  LVM2_member partition in the ubuntu live cd. i hope this made some sense, but if not im sorry, im desperate, and need to get these files. I still cant believe i made such a stupid move, or that it would cause this much trouble

---

### Post by spiderbatdad on 2007-12-23
I don't think you can mount a file system from the live cd. Do you have enough space to install 7.10 and use guided partitioning? Then mount the other file system to you desktop.

---

### Post by bwhite82 on 2007-12-23
You don't need X to have a "login manager" simply type in "login" at the CLI and supply your admin password then copy the necessary files to a USB stick or what have you.

---

### Post by Goemon4 on 2007-12-23
@ spiderbatdad - no, the partition there takes up my whole drive, i have about 50 megs free, and i dont think i could install any linux distro on that.

@ Soldierboy - i know, like i said, i can get into fedora without X i just cant do much from there. All i have atm is a psp with a 4gig memory stick for backup. But the problem is, i was an idiot, and forgot to backup some files. i tried to half-**** things by keeping temp backups on my psp, since my card reader sucks.  i didnt know it would have been such a mistake. 

Like i said, i just need a way to access my hard drive somehow. If worse comes to worse, ill loose some schoolwork and what not, i guess my profs will understand :(

---

### Post by bwhite82 on 2007-12-23
Perhaps I am misreading your original post. You can access the Fedora machine via command line right? If so, you can do anything you want to from there, no need for a desktop, just need to know some commands to navigate your way around CLI. I'm not sure how Fedora lays out your hard drive but on Ubuntu you would type:

cd /home/yourusername

That gets you into  your home directory where your personal files *should* be.

Then to view all the files and directories there:

ls

You can then copy any file you want onto your media of choice (may have to mount it first):

cp filename.extention /media/yourmedia

---

### Post by bwhite82 on 2007-12-23
At any rate, if you still want to mount the disk via LiveCD, use the Ubuntu one, once booted, open a terminal and type:

mount /dev/harddrivealias (<---sda,sdb,hda,hda1,sdb1, etc)

Once you've mounted it, it should place a link on your desktop to the drive.

---

### Post by Goemon4 on 2007-12-23
yeah i can access it just fine. Im missing some core services tho. Of course the ls, cp, mount etc commands all work, i just cant use things like ifconfig/ifup/ifdown for some reason. I know i can use the command line to copy them, i just need to remember what i dont have backed up. I guess ill wing it then, say know how to figure out where my psp is mounted? I use mount, and it dosnt really reveal anything for some reason (while in no x-ed fedora) and mount -a isnt turning up anything either for some reason (it keeps outputting the same 8 things, nothing new when i put my psp in disk mode)

ty for your other post (missed that) ill try it now, so ignore the rest of my post

trying /dev/sda2 isnt working, i just get this 

ubuntu@ubuntu:~$ mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab


ya know, i think the format type is my problem, i guess ill have to part with the data... man im still baffled on how it became a LVM2_member format, thanks for all the help though,

---

