---
title: "ditching windows installing ubuntu laptop"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Atonk on 2007-03-26
Hi,
I apologize if this has been covered somewhere already (I'm sure it has but I couldn't find exactly what I was looking for). I have a Dell 1100 Inspiron laptop that I used to use for work; now it's going to be my "personal" computer. I want to completely remove windows and install
ubuntu. Is there anything in particular I should know before I start removing windows? I've looked through a few forums on the topic; some made it sound difficult to get rid of windows and some sounded easy. Any help would be greatly appreciated by this recently "converted" newbie!
thanks 
Atonk

---

### Post by zvacet on 2007-03-26
You can uninstall Windows with it´s own CD or download Gparted Live CD.I recommend second choice,simply because you will work with gparted in the future(resizing partitions and so),and it is easy to use and get job done.

---

### Post by poohbear1616 on 2007-03-26
Burn yourself a live disk and boot it up.
Then click install. It is very simple to install (baring hardware issues) which will show up with the live disk before you install.
This gives very good directions:
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by arron on 2007-03-26
Laptops can give a issue or 2.  here are a ople of sites with some info:

[http://www.linux-laptop.net/](http://www.linux-laptop.net/)
[http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

And here is some info on the forum here:

[http://www.ubuntuforums.org/showthread.php?t=190022&highlight=dell+1100](http://www.ubuntuforums.org/showthread.php?t=190022&highlight=dell+1100)

Im sure if you look more on here you will find everything you ever need to get it running smoothly.  Windows is easy to get rid of, just format with the install cd (select use whole drive).  As simple as that to say bye to M$.

Good luck, and welcome to the Ubuntu Community!

---

### Post by bodhi.zazen on 2007-03-26
Yea, you will have some trouble with the video.

1. Update the bios before you remove windows.

2. Install Daper (6.06) as Edgy did not work so well ...

See this post ...

[http://www.ubuntuforums.org/showpost.php?p=1799642&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1799642&postcount=15)

---

### Post by Atonk on 2007-03-26
thank you so much for the advice - i can't wait to get windows off this computer! one of the first things i loved about linux was the forums; so helpful and so quick to respond! goodbye M$!!!!

---

### Post by brion@cbkidder.com on 2007-03-26
I installed 6.10 on my Dell Inspiron 1100 laptop last night, and am having no end of trouble with the screen resolution. A fix called 915resolution is supposed to fix the problem, but it hasn't worked for me. So be prepared to do a lot of work tweaking your X gui.

If you have Windows already installed and running (even if barely so), I recommend you use the live CD to install Ubuntu without disturbing Windows just yet. I was unable to create a separate partition for my install due to a bad sector, so when I reformatted I just said sayonara to the Windows but am starting to regret it.

I have 6.10 running on my desktop at home, and it installed with no immediate hassles, but it is frustrating when the media players won't play my audios or videos, the printer setup can't detect my network printer, and the email program can't import PST files directly from Outlook.

Ubuntu is awesome, but be prepared to give it time to ripen on your machine.

Brion Kidder
Orange, California

---

### Post by arron on 2007-03-26
Yes this forum is awesome.  I have been on many other linux forums, and if your not l337 (elite) or have a "silly" question to some you got flamed.  I have grown to love Ubuntu, and the community around it.  I have switched from other distros that i have used for over 10 years to Ubuntu to have a nice place to call home.

I remember well the day i formatted off windows totally, there was a huge learning curve but worth it.  Good luck!

---

### Post by houstonbofh on 2007-03-26
I have this laptop.  Dapper installs out of the box with no issues at all.  I did not try Edgy.  Grab Live CDs of both, and boot.  Remember that with a live CD you can fix a broken install.  You can also look at what config files "should" be.  Do flash to the latest bios before starting, however.

---

### Post by brion@cbkidder.com on 2007-03-27
Follow-up:

6.10 Edgy works fine on my Inspiron 1100, and I did not need to use 915resolution to fix the screen resolution.

Thanks a million to [bodhi.zazen]("http://www.ubuntuforums.org/member.php?u=89054") for the clear and best of all EFFECTIVE technique to set the screen resolution on my 1100. See it at
[http://www.ubuntuforums.org/showpost.php?p=1799642]("http://www.ubuntuforums.org/showpost.php?p=1799642")

Just be sure you
[LIST=1]
[*]to save your xorg.conf to xorg.conf.backup or the like before you start
[*]print out [bodhi.zazen]("http://www.ubuntuforums.org/member.php?u=89054")'s xorg.conf (he attached it to his post)
[*]amend your xorg.conf to look like bodhi's (or replace yours with bodhi's)
[*]press Ctrl+Alt+backspace to restart X
[*]confirm your desired default screen resolution in the settings window
[/LIST]

Also: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") is a great place to get most of your codecs (some but not all of your wmvs, avis, mpegs, et al will work but it's a good start)

Brion Kidder
Orange, California

---

### Post by Atonk on 2007-03-28
Brion,
that's encouraging to hear! Since I run 6.10 on my desktop, I was hoping to get it on my laptop as well. I was able to get 6.06 installed and fixed the screen resolution with a fix I found in different forum (xserver reconfigure xorg - something like that) and it worked like
a charm. I will try the steps you outlined in your post and see if I can get Edgy going.
Thanks!
Atonk

---

