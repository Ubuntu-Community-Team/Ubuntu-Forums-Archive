---
title: "Macbook Pro 2,2 Keyboard and Mouse Issue"
date: 2013-08-10
forum: Apple Hardware Users
---

### Post by QREJnYw on 2013-08-10
Hello.

    I'd been wanting to dual boot my MBP with linux for some time now, and I finally decided to take the dive last night.
I used [UNetbootin]("http://unetbootin.sourceforge.net/") to create a Ubuntu 12.04 USB stick on an 8GB SanDisc Cruzer flash drive. This proceeded without error. 
I also have the latest version of [rEFInd]("http://www.rodsbooks.com/refind/") installed.

     Upon rebooting, rEFInd offers me the option to boot into OSX from HD, EFI with the rEFInd icon, as well as Linux from the drive. I selected linux from the drive. 
After about 15 seconds, UNetbootin presents me with the first attached image.
At this point, I am unable to use the mouse or the keyboard to select other options, but it eventually automaticly boots after 10 seconds.
Ubuntu boots without issue as shown in the second attached image. 
And eventually lands on the desktop shown in the third image. 

At this point, the built-in keyboard and trackpad are completely unresponsive. The only thing I am able to do that provides any sort of response is press the power button. 

Here's my system details:

[IMG]http://i.imgur.com/uSnErJ9.png[/IMG][IMG]http://i.imgur.com/lqbeVnA.png[/IMG]

I should note, I have not used linux before, so my skill level is relatively low. I'd like to think I'm reasonably proficcient with computers in general, in that I've gotten this far, but I thought it would be worth mentioning I have no prior experience with linux or ubuntu.

Please let me know if any other information would be useful. 
Any help is greatly appreciated, thank you.

---

### Post by r3dbeard on 2013-08-10
I've been digging and there doesn't seem to be a lot of info/docs related to installing ubuntu on 2,2's; however, I have spent a lot of time doing it in just about every way immaginable on my 5,1 and found that earlier versions are typically more compatible with older systems. That being said my suggestion is to start with a version 10.10 install and upgrade your way to 12.04. I also suggest being hardwired to your internet connection so that it can gather updates while it installs. 

Once installed, using the "Update Manager" found under System / Administration in the menu at the top of the screen should allow you to upgrade to v11.04 then once installed repeat to upgrade to v11.10 then once more to v12.04. I know this seems tedious and to be completely up front could take a few hours. However, updating/upgrading like this is something completely unique to free/opensource software. No "Upgrade" button will ever exist for OS X or Windows as they're often not built on the backs of previous stable versions like many *nux flavors are.

This link suggests that ubuntu v10.10 works quite well with 2,1 models which is why I suggest starting there: [https://help.ubuntu.com/community/MacBook2-1/Maverick](https://help.ubuntu.com/community/MacBook2-1/Maverick)
This is the download link for ubuntu 10.10. I would suggest grabbing a desktop version and then installing laptop-mode-tools once the system is up and running.: [http://old-releases.ubuntu.com/releases/maverick/](http://old-releases.ubuntu.com/releases/maverick/)

Hope this helps.

---

### Post by QREJnYw on 2013-08-11
Thanks so much for your input. I'll try 10.10 and post back here with my results.

---

