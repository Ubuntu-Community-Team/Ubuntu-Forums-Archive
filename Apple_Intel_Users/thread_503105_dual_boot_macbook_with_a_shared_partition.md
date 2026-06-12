---
title: "dual boot macbook with a shared partition"
date: 2007-07-17
forum: Apple Intel Users
---

### Post by mshale on 2007-07-17
ok, so I have a question about getting ubuntu up and running on my new macbook.  I want to to dual boot OS X and ubuntu and have a shared partition for all of my multi media files.  I will also want to run windows xp (because i have a blackberry pearl that needs it to install apps on the phone) as an emmulation in OS X.  I need some suggestions on how I should partition the 200GB HD.  I figure a/b 10-15Gig for ubuntu, But i'm not at all sure a/b how much space i should give OSX for i have no idea how much space the emulated windows.  All of the howtos to get the dual boot going have no mention of any other partitions.  

To boot, I would like to use grub, and Gparted as the partition editor simply because I am comfortable with these programs.  I read something about getting this to work if REFIT was used... 

Any suggestions or comments?

---

### Post by cyberdork33 on 2007-07-17
If you are wanting to run windows in a VM then you don't need a partition for it.

---

### Post by mshale on 2007-07-17
I know that, but i'm saying that i want one partition for OSX, one for ubuntu, and one to put all of my Music and stuff.  But my main question was how much space does mac osx and a VM windows take up?  should i give it like 20Gig, or more like 30?

---

### Post by cyberdork33 on 2007-07-17
> **mshale said:**
> I know that, but i'm saying that i want one partition for OSX, one for ubuntu, and one to put all of my Music and stuff.  But my main question was how much space does mac osx and a VM windows take up?  should i give it like 20Gig, or more like 30?

Sorry, your description sounded like you were trying to make a partition for windows. Your OSX partition needs to be as big as the image file you make for windows, plus OSX and anything else you plan to install (apps).

My OSX partition uses about 40GB right now with a couple of VMs and a bunch of apps.

---

### Post by mshale on 2007-07-17
> **cyberdork33 said:**
> Sorry, your description sounded like you were trying to make a partition for windows. Your OSX partition needs to be as big as the image file you make for windows, plus OSX and anything else you plan to install (apps).

My OSX partition uses about 40GB right now with a couple of VMs and a bunch of apps.


Great, I believe that answered one of my questions.  I appreciate that.  so, as of now, I'm planning on 35 Gig for OSX and vm windows, and 15 for ubuntu, and 150 gig for the media partition.  

I still would like to know if i can use Gparted to partition and install rEFIt and then install ubuntu on the 15 gig partition.

Thanks for our input!

---

### Post by cyberdork33 on 2007-07-17
apparently gparted cannot create HFS+ partitions so you will need to create your OSX partition before doing anything else. You can create the other partitions with the ubuntu installer or gparted, (or whatever really). rEFIt needs files on your OSX partition so you need to install OSX before you can install rEFIt.

---

### Post by Gen2ly on 2007-07-18
I like this [wiki]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Preparing_the_Disk") on partition making:

---

