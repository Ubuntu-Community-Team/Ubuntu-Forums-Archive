---
title: "A few small issues I am having... including sleep mode."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by foldor on 2007-02-11
I am currently running Ubuntu 6.10 on an IBM ThinkPad R60 and I have a few various issues that I'm hoping can be solved.

First, my laptop won't properly wake up form sleep mode, when I try to wake it up the screen is completely black and wont turn on properly. I have tried this twice and it has done the same thing both times. As a side note, hibernation seems to work ok.

Second, I'm not sure if it's an issue with Firefox or not, but whenever I click a link that is set to open a new window, it does not use a new tab. I have the setting applied in the preferences that tells it to open in a new tab, but it somehow still does. I have to force the link to be opened in a new tab by middle-clicking the link manually.

Last of all is more of a question of convenience. I have only recently started using Linux and, while I am comfortable with the terminal if necessary, I prefer not to use it sometimes. Is there any way to allow my user account to modify folders and files NOT in my home directory without opening any major security holes?

Thanks in advance, I really appreciate everything the community does for each other here. I have already solved a few issues just browsing around myself.

---

### Post by orlox on 2007-02-11
about the "file modyfing issue"...

I found it usefull at times to open a file explorer as root

```
$gksu nautilus
```

This, in case your using ubuntu...This will open a window asking for your superuser password, and then will open the file explorer as root.

---

### Post by foldor on 2007-02-12
Great! Thats one less issue I have now. :)  Now I have one more question for everyone. I have created a FAT32 partition on my HDD and I have mounted in my /media directory as sda2. I was wondering how come I cannot change owner of this file system and, why I cannot make a link to anything inside the partition.

Again, thanks in advance,
Foldor

---

### Post by foldor on 2007-02-12
Just a quick bump.

---

### Post by Dan Lyke on 2007-10-29
Found your note because I too am having sleep mode troubles in Gutsy, and this is ages late, but I'll try anyway.

The reason you can't change owners in the FAT32 is that FAT32 doesn't have any place to store that information. There used to be a VFAT filesystem which kept a hidden file in each directory to keep ownership information, and in that way the FAT32 filesystem was made to work kind of like a real filesystem, but I don't know what the current state of that is.

As for links, you should be able to do symbolic links from outside that filesystem to inside of it, but again, a limitation of the filesystem is that it doesn't know how to do links, so any notion of such things would have to be on a layer above FAT32, and wouldn't be visible to whatever other than Linux viewed that partition.

---

