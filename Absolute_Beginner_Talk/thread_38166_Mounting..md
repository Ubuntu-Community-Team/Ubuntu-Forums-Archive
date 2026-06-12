---
title: "Mounting."
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by Kairo Annunaki on 2005-05-30
I'm having some trouble mounting my other hard drive. I have two hard drives. One is a Maxtor, which is mounted right now, the one I'm using for Linux. The other is a Western Digital, which is wiped out also. It's showing up in the System>Administration>Devices, in that tree list.

But I don't know exactly how I mount it.

---

### Post by Kairo Annunaki on 2005-05-30
Ok. What type of disk label am I suppose to use for Gparted, when I am formatting another HD for Ubuntu?

---

### Post by Gsibbery on 2005-05-30
[QUOTE=Kairo Annunaki]I'm having some trouble mounting my other hard drive. I have two hard drives. One is a Maxtor, which is mounted right now, the one I'm using for Linux. The other is a Western Digital, which is wiped out also. It's showing up in the System>Administration>Devices, in that tree list.

But I don't know exactly how I mount it.[/QUOTE]

# mount  /dev/hdbx /mnt/hdbx

where x is the partition. 

You may need to create the mount point in the /mnt directory and choose a file system type using the "-t" option. You'll normally have to be logged in as root to do this. 

Once you have it successfully mounted you can add it to your /etc/fstab to mount it at boot time. 

If you get any errors, post them here.

---

### Post by Kairo Annunaki on 2005-05-30
Ok. About partitioning it...

Does it matter what disk label it is? By default it says msdos.

---

### Post by Gsibbery on 2005-05-30
[QUOTE=Kairo Annunaki]Ok. About partitioning it...

Does it matter what disk label it is? By default it says msdos.[/QUOTE]

I dont think the label matters. For example, you could mount a hard drive to /mnt/floppy if you wish as long as that directory doesnt have a filesystem mounted to it already. 

There is some docs on parted [here ](http://www.gnu.org/software/parted/manual/text/parted.txt) that may be of help.

---

### Post by Kairo Annunaki on 2005-05-30
Ok. I'm in my terminal and did a cd to the /mnt

I don't quiet understand this yet though:

mountpoint [-q] [-d] [-x] path

I don't understand what those mean.

---

### Post by Kairo Annunaki on 2005-05-30
Hey. I think I did it...

I edited the file fstab and added this line:

/dev/hdc1       /Programs/      ext2   

Then I made a folder with 

sudo mkdir /Programs/

Then I cd'ed to the /mnt folder and did

sudo mountpoint /dev/hdc1

And saved. Then I navigated to the folder "Programs" which I made. And it's a 10 GIG HD, but it says... "Free Space: 8.9" and there's a folder in it called "lost+found" with a red "x" at the top of the icon.

---

