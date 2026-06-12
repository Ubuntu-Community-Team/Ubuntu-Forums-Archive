---
title: "Need Help!  Installing apps without internet access..."
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by volk on 2005-09-02
OK, I have Ubuntu successfully installed on my computer.  I feel pretty sure that I understand how to use Synaptic, too.  My problem is that this machine has no internet access, so I am resorting to downloading apps off of the internet at work, burning them to a CD and then taking them home to the Ubuntu machine.    Unfortunately, I have absolutely no clue as to getting an application package and its dependencies installed once I have the CD home :?  I tried to add the CD to synaptic, but it gives me an error and tells me there are no packages on the disc.  Do I need to uncompress the files in Winzip and then burn the uncompressed files to a CD in Windows first?

I am starting small here, and have just one app that I would like to install: Qcommicbook.  It is a simple sequential image reader that was downloadable directly from the developer's website.  I don't know if it will help or not, but the developer's site is [here.](http://linux.bydg.org/~yogin/) I downloaded the appropriate package, but I need to know where to go from here...I will have to be able to do this kind of thing if I am going to make linux useful for my home.

Please Help!

---

### Post by aysiu on 2005-09-02
Ubuntu is Debian-based and so uses .deb files (not .rpm). If you can get a bunch of .debs, you can use the command *sudo dpkg -i packagename.deb* to install the .deb.

I think there was some Ubuntu extras CD around once, too. Does anyone remember where that was?

---

### Post by volk on 2005-09-02
Do I need to unpack the file to a specific location first, or do I just run the dpkg command?

---

### Post by aysiu on 2005-09-02
[QUOTE=volk]Do I need to unpack the file to a specific location first, or do I just run the dpkg command?[/QUOTE] Just run the command.

---

### Post by TristanMike on 2005-09-02
Hello, if you're looking for the extras cd, the how to and download can be found here... [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147)

---

### Post by Evilchicken on 2005-12-08
[QUOTE=TristanMike]Hello, if you're looking for the extras cd, the how to and download can be found here... [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147)[/QUOTE]Thank you! I also do not have an internet connection to my ubuntu box so I've been downloading everything from school. This is the most incredibly useful forum ever.

---

