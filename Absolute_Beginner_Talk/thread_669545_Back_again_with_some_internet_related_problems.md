---
title: "Back again with some internet related problems"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Zaopunk on 2008-01-16
Well I recieved my CD's from Ubuntu, and by God they worked for me this time! Not a single problem with the installation, and only took me 15 minutes! 
Unfortunately when I started up Firefox and tried to browse to [www.yahoo.com](www.yahoo.com), I got no love. The connection almost seems sluggish when cruising around this site as well. 
Any suggestions for me?

Thanks for any and all help.
Josh

---

### Post by njparton on 2008-01-16
Please post your hardware details, specifically your motherboard and nic. Also, which distro are you using 32 or 64 bit?

---

### Post by Zaopunk on 2008-01-16
7.1 Gutsy 32bit <--(i'm pretty sure 32)
Intel P4 2.4ghz
Intel Desktop Board: D845PEBT2
NV11DDR [GeForce2 MX200]
1.5g DDR2

I also cannot connect to yahoo messenger through pidgin. And the connection seems to work fine one minute, slow the next, then not at all for a bit. Very strange.


Added question: Wanted to install Amarok from add/remove, but it says my computer type i386 is not supported...

---

### Post by njparton on 2008-01-17
Find out which onboard nic you have, then visit the manufacturers website to see if there are linux drivers available.

I did this for my intel nic and it worked a charm. I even learnt how to compile a driver and install it too :)

---

### Post by Zaopunk on 2008-01-17
well i installed a new DSL modem last night and my connectivity problem ceased to exhist, which is nice, 
Then I followed a different post to fix my ADD REMOVE list problem with i386.

[http://ubuntuforums.org/showthread.php?t=433355](http://ubuntuforums.org/showthread.php?t=433355)

Now when I click on Amarok it says its supported, YAY, but then I check the box and it gives me an error:

**[List of applications is not available, click on 'reload' to load it. You need to have a working internet connection to reload the list.]**

So I click the refresh button and it starts to download, then gets to 7 of 8 and stops giving me an error message:

[B]COULD NOT DOWNLOAD The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[/B]

BAH HUMBUG! lol. But seriously very frustrating. Any ideas?

Josh

---

### Post by Zaopunk on 2008-01-18
Any help people?

---

### Post by hyper_ch on 2008-01-18
deactivate IPv6

---

### Post by Zaopunk on 2008-01-18
And what will that do? (and how do I do it?) I'm sorry, I am quite wet behind the ears when it comes to Linux.

---

### Post by hyper_ch on 2008-01-18
it will deactive IPv6... how to do it: You can use the forum's search function ;)

---

### Post by Zaopunk on 2008-01-18
Ok. So I deactivated IPv6 and I am still getting the same error message I stated above. (Also had to figure out a couple other things along the way, which are always useful for future knowledge!) And now my internet speeds along faster than ever btw so thanks for that!

And I don't know if this will help identify the problem, but I also cannot install plugins for Firefox (flash), not sure if it is the same problem or not. Thank you for your help so far,
Josh

---

### Post by Zaopunk on 2008-01-19
I have worked out a few kinks now and have Amarok installed, and Flash installed. Thank you for all of your help!!

Josh:guitar:

---

