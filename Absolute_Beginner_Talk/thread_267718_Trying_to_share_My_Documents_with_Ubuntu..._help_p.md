---
title: "Trying to share My Documents with Ubuntu... help please"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by limitedmage on 2006-09-29
Hi,

I started using Ubuntu a couple of days ago, and I think it's great. It's a really good OS.

I wanted to see if anyone could help me on this.

I currently have 5 drive partitions:

One is a FAT16 30 Mb partition that came out-of-the-box with the Dell computer I have and I dare not touch :) (hda1)

Another is the Windows XP NTFS drive (hda2)

The third is a FAT32 partition I have been using to share files between Windows and Linux, where the My Documents folder is located (hda5)

And the last two are the Ubuntu partition and swap partition.

I seem to have the following problem: I cannot write anything into the My Documents folder. *Only* the My Documents folder. I can write anything into the hda5 partition, but not inside the My Documents folder. Every time I try to do this, I get an error saying I don't have permission to write on this folder. In Nautilus, the folder icon has a little padlock, which I suppose means it is protected. It works completely fine on Windows.

How can I 'unprotect' the folder so Ubuntu can write on it? Is this a Windows problem or a Ubuntu problem? I would really appreciate if someone could help me on this!

---

### Post by orb9220 on 2006-09-29
If it is in a ntfs partition ubuntu dosn't write to ntfs. There are ways to write to ntfs but are new and considered experimental.  [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

For sharing music,pics,docs I have a fat32 that both xp and linux can read and write too. The easy way is to copy the docs to a fat32 partition and  have your xp apps load and save them there instead of the default my documents.

---

### Post by limitedmage on 2006-09-29
I just said that it *is* in a fat32 partition. The problem is that the My Documents folder (only the folder, not the whole partition) is write-protected in Ubuntu. How do I disable this?

---

### Post by joshyf on 2006-09-29
i had good fun playing with this, as it just happened to me recently... firstly i followed some other *nix users advice and changed my /etc/fstab to the follwing:

/dev/hda4 /media/documents vfat umask=0,user,codepage=850,iocharset=iso8859-15 0 0

with /dev/hda4 being the partition to be mounted, and /media/documents was where i could access the partition when it was mounted. this didn't exactly fix it, but it did allow me to 'chown' the My Documents folder on the partition so that anyone can access it. chown 777 My Documents should do it, i think...

let me know how you go...

---

### Post by limitedmage on 2006-09-29
hmmm... I edited fstab and used chown and I got the following from the terminal:

```

:~$ chown 777 "/media/hda5/My Documents"
chown: changing ownership of `/media/hda5/My Documents': Operation not permitted

```

Even using 'sudo' it displayed this message.

Any ideas, anyone?

---

### Post by orb9220 on 2006-09-29
Don't think fstab likes spaces in folder names. You might go to folder and rename to My-Documents instead and update the fstab accordingly.
This is my fstab for my fat32
/dev/hdd1  /home/drives/hdd1  vfat  defaults,utf8,umask=007,gid=46  0     0
Which gives me full access.

Sorry couldn't be more help.

---

### Post by limitedmage on 2006-09-29
Well, I logged in as root and could not change permissions.... I guess this means the problem is XP. Also, I changed the My Documents folder. Now it's only called 'Documents'. I changed the Windows reference to it, and the protection did not change.

However, when I logged in as root I did have full write access.

I don't get why Linux needs to have all these users with all these different permissions if only one person is going to use the computer....

---

### Post by joshyf on 2006-09-29
you may need to remount the partition as well, using umount and mount. and sorry, i gave you the wrong command :S chown is for changing ownership, chmod is for changing permissions. so you want to:

sudo chmod 777 Documents

i think :) good luck!

---

### Post by orb9220 on 2006-09-29
For the same reason you can make xp just like linux with restricted access  to files and programs and then they too would not have to worry about viruses,trojans,spyware,rootkits,etc... And Vista is doing exactally that and learning to implement security features as linux does.

It is frustrating at first but if you stick with and learn some of the work-arounds like changing or creating an icon using gksudo nautilus will give you access to all your files. And learning the correct fstab entry  for your partition which you only have to do once.

---

### Post by limitedmage on 2006-09-29
Thanks! Now it worked perfectly! Thanks a lot to both of you.

---

