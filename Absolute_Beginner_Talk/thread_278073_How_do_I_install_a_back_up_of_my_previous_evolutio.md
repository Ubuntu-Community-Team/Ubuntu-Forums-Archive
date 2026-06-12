---
title: "How do I install a back up of my previous evolution email on a fresh ubuntu install"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by jogogets on 2006-10-15
G'day all,

I wanted to do a fresh install of ubuntu so I backed up my evolution files by following the advice on this thread:

[http://www.ubuntuforums.org/showthread.php?p=1621267#post1621267](http://www.ubuntuforums.org/showthread.php?p=1621267#post1621267)

The result is that I have a back up file of evolution named:

evolution-backup.tar.gz

Can someone please guide me to save the files onto my fresh install. How do I install the package? I have tried a number of ways but no luck. I'm sure the answer is simple, I am a noob but loving linux.

Thanks in advance!

---

### Post by Old Pink on 2006-10-15
> **jogogets said:**
> Can someone please guide me to save the files onto my fresh install. How do I install the package? I have tried a number of ways but no luck. I'm sure the answer is simple, I am a noob but loving linux.

Which "ways" have you tried? 

I need to know what advice to avoid giving. :)

---

### Post by jogogets on 2006-10-15
Hi,

Thanks for the quick reply. I've tried by typing: sudo apt-get install evolution-backup.tar.gz in the terminal. 

I've also tried navigating to the evolution directory in the terminal then typing install evolution-backup.tar.gz.

I tried double clicking on the package. That unloads the archive files but so far hasn't added the files to my evolution email inbox. 

I also tried opening the package and double clicking the config files, that unloaded some of the archive files but again no luck.

I think the answer must be simple. Thanks for helping me. Any thoughts?

---

### Post by LukeyMI on 2006-10-15
Extract it to your home folder. Move that file to /home/yourusername and then run this from the command line:

tar -xzf evolution-backup.tar.gz

Launch evolution when complete.

---

### Post by jogogets on 2006-10-15
Thanks LukeyMI,

That worked. Just a warning to any others that may thinking of backing up their evolution emails. My backup seems to have only copied 99 emails out of 500 or so. Also my contacts were not transferred. 

To avoid any dramas I have selected to leave a copy of all emails in my gmail server. That way i always have a backup.

Thanks again Lukey MI for your help.

---

