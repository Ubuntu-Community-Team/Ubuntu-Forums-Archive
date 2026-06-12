---
title: "Ubuntu is the only distribution that doesn't recognize my monitor resolutions!!"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Ifaistos on 2007-06-16
Hello everyone :-)

I have decided only yesterday to switch completely to Ubuntu 7.04.  Before  I decided to go full Ubuntu I had this rig, dual booting Open Suse and Windows XP.  I downloaded also Fedora 7 and I installed it to check it out.. I decided to go Ubuntu because it is "richer" and I find it user friendly.

Before I installed Ubuntu I 've used Gparted latest CD and Knoppix 5.1.
ALL OF THEM recognized my monitor correctly and had no problem accepting the 1280x1024, 60Hz resolution.

Ubuntu Live CD was the only one that didn't do well.  But I decided to go with it, since I knew that Ubuntu does not include the ATI drivers and I was hoping that when I install the drivers the monitor would be recognized correctly and would have no problem.

But guess what?  After I downloaded and installed the drivers all I could get was 1024x768.  I had the same problem about 2 years ago!!  For crying out loud, it can't be that difficult to fix this bug!  It seems that all the other distributions I've used have no problems at all..

Having said that... Is there ANY way of getting my monitor recognized correctly without having to edit a config file?  The previous time I tried to do that, I rendered my system unbootable!! lol
had to reinstall... :(

If you are sure, that there is absolutely NO WAY to do that without editing the config file, could you please redirect me to a page that explains how to do that like I am a five year old?

Thank you all in advance for you help and time :)

---

### Post by meborc on 2007-06-16
```
sudo dpkg-reconfigure xserver-xorg
```is the answer usually...

sorry if your experience is not as good as mine... :) why on earth are you using ubuntu then if you had better time with other distros? ;)

...and for longer read on resolutions and ubuntu - [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by linfidel on 2007-06-16
Hi,
I'm pretty new myself, but I've had the opposite results - Ubuntu has always done the best at recognizing my monitors, and I once booted the live CD just to read the parameters it wrote into the configuration file.

However, even when it didn't do well, I was always able to fix it using a combination of things.

First, was the monitor on when you booted up?  It seems to always detect the monitor, and if there's no monitor, it may come up in low-res mode.  I have a KVM switch, so sometimes it isn't switched to Ubuntu; in those cases, I do control-alt-backspace, which restarts X-windows, and it detects the monitor.

Next, try looking in the menu "System", "Administration", "Restricted Drivers Manager"; your card may have a proprietary driver listed, and you may need to enable this driver.

Lastly, you may need to run this command at a terminal prompt:
"sudo dpkg-reconfigure xserver-xorg"
This is the magic incantation for video cards.  There are a bunch of questions, most of which will be answered by hitting "Enter" or maybe "Tab, Enter" if the Enter key isn't focused.  But when you get to the monitor characteristics, choose Medium unless you really know a lot about monitors; medium lets you choose 1280x1024 60 Hz, for example.

In my limited experience, these steps have always worked.  Usually the dpkg-reconfigure step is the one that I use the most - you can probably Google that term to find out more.

---

### Post by Brightbelt on 2007-06-16
If it makes you feel any better, I tried Mandriva hoping it would fare better with my ATI X1650, but guess what?
It did no better than Ubuntu. 

This program got my resolution correct when nothing else would work. 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) 

I recommend doing it right after your Ubuntu install when things are clean and fresh. 

I hope this helps,...Frank B.

---

### Post by Brightbelt on 2007-06-16
In case you go with the 'sudo dpkg-reconfigure xserver-xorg" route, choose the 'Vesa' driver. That's the very first part of the reconfiguring process. 

It seems anti-intuitive to choose that if you've got an ATI or other brand but it is what works. 

Good Luck, Frank B.

---

### Post by linfidel on 2007-06-16
> **meborc said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```is the answer usually...

sorry if your experience is not as good as mine... :) why on earth are you using ubuntu then if you had better time with other distros? ;)

...and for longer read on resolutions and ubuntu - [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto):o You slipped your post in while I was responding.  I'm glad you responded, though; I hadn't seen the link you posted, and it has a lot of good information that I didn't know about.  Perhaps I'm not the only one that doesn't know this, as I was never told about it when I was having problems.

But maybe one of my suggestions will also be useful, I hope.  :)

---

### Post by Ifaistos on 2007-06-16
Ok guys thank you all :-)

I have managed to solve the problem.  The most helpful link was the one provided by meborc.
Btw meborc... I think that I have stated on my original e-mail why I haven't moved to other distributions.  The main reason was : user friendliness and ease of upgrade.  Synaptic was one of the reasons.  I don't think though that if smt doesn't work you move to smt else...  Do you do the same, or you try to make it work?

This is what I did.  Although I edited the file, I could not "enforce" the 1280x1024 resolution.  I couldn't find either the manual with the Hor and Ver frequencies.  So what I did was to slap in the Knoppix 5.1 live CD and check the frequencies that it detected!!

So I used those frequencies in the edited file and then Ctrl+Alt+Backspace..!!  Problem solved !!

Thank you all :-)

Now I have to move to solving other problems, such as how to make my modem and fax software work together and others.

---

