---
title: "Changing permission"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Baasha on 2006-06-01
I have a dual-boot system with Win2k and Dapper.  When installing, I set up a FAT32 partition so I could share files.  After using those files I want to delete them, but discovered that I am not allowed because that partition is owned by root.

I tried to change permission using chown in the terminal but the terminal says no such directory exists.  That partition is called sda6 on my system.  Using the file browser I can see it as a main entry under file system and also as a sub-directory under media.

How do I access it to change the ownership?  Once the ownership is changed will I be able to change its name to something more meaningful than sda6?

---

### Post by ComplexNumber on 2006-06-01
[quote=Baasha]I have a dual-boot system with Win2k and Dapper.  When installing, I set up a FAT32 partition so I could share files.  After using those files I want to delete them, but discovered that I am not allowed because that partition is owned by root.

I tried to change permission using chown in the terminal but the terminal says no such directory exists.  That partition is called sda6 on my system.  Using the file browser I can see it as a main entry under file system and also as a sub-directory under media.

How do I access it to change the ownership?  Once the ownership is changed will I be able to change its name to something more meaningful than sda6?[/quote]
there is no reliable way of writing to the FAT/NTFS partition at this time (AFAIK). you can read it, but not write to it.

---

### Post by Herman on 2006-06-01
> I have a dual-boot system with Win2k and Dapper. When installing, I set up a FAT32 partition so I could share files. After using those files I want to delete them, but discovered that I am not allowed because that partition is owned by root.
I tried to change permission using chown in the terminal but the terminal says no such directory exists. That partition is called sda6 on my system. Using the file browser I can see it as a main entry under file system and also as a sub-directory under media.
How do I access it to change the ownership? 
Try following this link, (Click 'GO').
**Relaxing the 'read/write' permissions for a FAT32 partition** (when it is already automatically mounted on boot-up.) Applies to Breezy i386 installed on hard disk.................[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#1p10")

(It works for Dapper as well as Breezy). You can read/write FAT filesystems, but NTFS is read-only for Linux as far as I know.

---

### Post by ComplexNumber on 2006-06-01
>  (It works for Dapper as well as Breezy). You can read/write FAT filesystems, but NTFS is read-only for Linux as far as I know.so FAT is writable? i was led t believe by all that i've read that neither FAT nor NTFS nor any other windows file system is writable. oh well, one learns something new everyday.

---

### Post by Baasha on 2006-06-01
[QUOTE=Herman]Try following this link, (Click 'GO').
**Relaxing the 'read/write' permissions for a FAT32 partition** (when it is already automatically mounted on boot-up.) Applies to Breezy i386 installed on hard disk.................[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#1p10")

(It works for Dapper as well as Breezy). You can read/write FAT filesystems, but NTFS is read-only for Linux as far as I know.[/QUOTE]

Ok, I did that and everything seemed to work exactly as expected, only when I opened that directory I still couldn't delete the files.  When i checked for the permissions I found that they were still listed as root and I was not allowed to change anything.  What next?

---

### Post by S{yndrom}e on 2006-06-02
where exactly are thes files located

When i used to duel boot my window files were located under /media/windows

so what i would do was cd /media/windows

and then

sudo rm *filename* for files and sudo rm -r *directory*for directories

combining sudo with rm will remove even if it is owned by root.

The other way is to use nautilus via root

To do this type sudo nautilus and navigate to the files and delete them via GUI.

---

### Post by dynnamitt on 2006-06-15
[QUOTE=Herman]Try following this link, (Click 'GO').
**Relaxing the 'read/write' permissions for a FAT32 partition** (when it is already automatically mounted on boot-up.) Applies to Breezy i386 installed on hard disk.................[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#1p10")

(It works for Dapper as well as Breezy). You can read/write FAT filesystems, but NTFS is read-only for Linux as far as I know.[/QUOTE]

Nice howto there...

I find just one thing missing;
And that is "figuring out" a way to change file permissions without sudo.
[B]Sometimes files has been set as "readonly" from windows, and to be able to write to this file from within linux u have to check all write flags on that file as root. 
I cannot do this as my normal user... or can I ??  :confused: 
[/B]

---

### Post by puterboy on 2006-06-15
[QUOTE=Baasha]I have a dual-boot system with Win2k and Dapper.  When installing, I set up a FAT32 partition so I could share files.  After using those files I want to delete them, but discovered that I am not allowed because that partition is owned by root.

I tried to change permission using chown in the terminal but the terminal says no such directory exists.  That partition is called sda6 on my system.  Using the file browser I can see it as a main entry under file system and also as a sub-directory under media.

How do I access it to change the ownership?  Once the ownership is changed will I be able to change its name to something more meaningful than sda6?[/QUOTE]

Same thing here, and all I had to do was rename it. i dunno if this works for you or not....i renamed it, and the lock windows put on it was removed.

---

