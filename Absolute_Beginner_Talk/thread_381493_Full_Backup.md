---
title: "Full Backup"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Linuturk on 2007-03-11
I've got blown speakers on my system. This is covered under my Best Buy (they suck) warranty. 

I've tried to send off my laptop without the hard drive, but they just won't repair it without my hard disk in there.

I need to backup my entire system. All of it. 

I'm guessing a tarball of / will handle this, but I don't know how to do this. I'll also need to restore it when the system eventually comes back wiped with Windows installed.

I'll also be posting a summary of the horror I went through with Best Buy.

---

### Post by scxtt on 2007-03-11
if you have a 2nd hard drive (even external), install partimage (after booting to a LiveCD) - aptitude install partimage ... that'll make a "partition image" that you can restore very easily ...

won't get into details now, since i don't know if you ONLY have 1 HDD ... (a udf DVD might work :-?)

---

### Post by Linuturk on 2007-03-11
Well, I have another computer. I just have to figure out how to mount it's 300 GB hard drive on my system and copy said tarball or image there.

---

### Post by Linuturk on 2007-03-11
[http://www.ubuntuforums.org/showthread.php?t=381533](http://www.ubuntuforums.org/showthread.php?t=381533) << checkout the full story here

---

### Post by scxtt on 2007-03-11
yes, there's a network option for partimage - never done it myself, but i'm sure it's not too hard to configure (man page would shed light i'm sure) ...

but yeah, if you can mount it (via samba or NFS) after booting the LiveCD you should be golden ... :)

---

### Post by Linuturk on 2007-03-14
would a 

tar -czvf archive.tar / --exclude /dev/

work?

---

### Post by scxtt on 2007-03-15
i suppose, but i don't really like an 'all encompassing' tar file for a backup ...

---

