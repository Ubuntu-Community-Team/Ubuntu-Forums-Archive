---
title: "New To Linux... install?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by djrenown on 2007-02-02
I'm brand new to linux and this is my first post ever, so excuse me if this q has been asked a million times.  I ran ubuntu off the live cd and thought it was great, it autodetected all my hardware except my wireless card.  I want to install ubuntu but had a question on partitioning.  I am planning on partitioning my harddrive into 4 partitions. 

p4 2.52ghz, 55gb hard drive, 768mb ram

1) NTFS: Windows XP (18gb)
2) EXT3: Ubuntu root
3) EXT3: Ubuntu home
4) Swap (1.5gb)

I am planning on using FS-Drive in order to allow windows to write to the EXT3 filesystem.  My Main question is how much room should i give to Ubuntu OS in the root directory?  As you can tell I dont have a large hard drive so i would like to opitimize my space but still run Ubuntu with no issues.  THanks for your advice.

---

### Post by Bachstelze on 2007-02-02
Hi and welcome to Ubuntu :)

5 GB is usually enough for the root filesystem - I currently have 2435 MB used on mine - but having 7-8 is nice if you want to experiment with the OS.

---

### Post by bodhi.zazen on 2007-02-02
You can likely reduce swap to 500 Mb, or perhaps 768 Mb.

---

### Post by djrenown on 2007-02-02
Thanks guys for the info, especially about possibly reducing the swap size portion.  One more quick q... When i boot ubuntu 6.1 off the the live CD it gives me this error message when it enters the desktop: "THERE WAS AN ERROR STARTING THE GNOME DAEMON".  Is this because im booting off of the cd or is it because of something else?  Thanks again.

PS.  i can still use ubuntu after i hit ok to the error message.

---

### Post by bodhi.zazen on 2007-02-02
My initial thought is did you check the MD5 sum of your downloaded iso and burned CD ?

---

### Post by djrenown on 2007-02-02
The only thing i did was when i booted off the cd i click the option to check cd... everything came out good?  i dont know what md5 is.

---

### Post by bodhi.zazen on 2007-02-02
I am not sure about your error message. :(

I suppose if everything looks OK you could try to install ???

FYI MD5SUM is one way to confirm the integrity of your downloaded iso.

Here is a brief overview: [http://www.ubuntuforums.org/showthread.php?&t=290339](http://www.ubuntuforums.org/showthread.php?&t=290339)

---

