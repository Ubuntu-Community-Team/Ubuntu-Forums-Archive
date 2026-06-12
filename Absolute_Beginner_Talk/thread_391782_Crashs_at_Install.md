---
title: "Crashs at Install"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Epis0de on 2007-03-23
At the last section of installation, were it ejects the CD, the asks you to hit enter, it always crashs, I think thats corrupting my install and leading to the "GRUB loading..." thing lasting forever. 

CD's clean, checked integrity, any ideas guys?

---

### Post by Epis0de on 2007-03-23
Bump for great justice.

---

### Post by Epis0de on 2007-03-23
This is killing me :( I dont even have an XP disc to fall back on. Any ideas whatsoever? Ive checked the support but nothing mentions this.

---

### Post by martinw89 on 2007-03-23
Don't worry, it seems like you have access to another PC, that's the only thing you need to know that you'll get back on your feet.  We need some more information though.  What is your hardware?  What version are you trying to install?

It sounds like the MBR is corrupted, leading GRUB to not being loaded.  But, I'm not sure.  GRUB itself could also be corrupted.  First I would suggest using a live disc to make sure that your harddrive isn't foobared.  So, use a live disc (such as Knoppix etc, Ubuntu disc is great but Knoppix has more tools available) and make sure you can mount your partitions. 

Good luck!

---

### Post by Epis0de on 2007-03-23
Nope, no access to another PC, I'm writing here via live disc, I checked to make sure that ubuntu would operate well from this before Installing. Unfortunately the Install Process is hurting. 

The Ubuntu version is 6.10. Was the most up to date stable release I could find.

Ive checked the gnome partition device and it seems that its mounting the SDA partition correctly, SDB is "unallocated" but I assume thats correct.

---

### Post by martinw89 on 2007-03-23
Try installing again, there could have just been a mishap in the installation process that led to Grub not starting correctly.  But it sounds like from you're first post that you've installed more than once.  I'm stumped if trying again doesn't work.

Edit: [This]("http://ubuntuforums.org/showthread.php?t=2689") sounds somewhat like you're situation.

---

### Post by Epis0de on 2007-03-23
Tell me about it. It crashs and stalls after the install, when its in the middle of beginning to restart, it ejects the cd, says "press enter to restart" then never restarts. On like my 5th time now.

---

### Post by martinw89 on 2007-03-23
That happened with me also.  But when I manually powered down after the install it was working after that :? The two might just be an unrelated coincidence. Do you have a means to try what I said in my last post?  I don't know if Edgy's livedisc can do that or not ([http://ubuntuforums.org/showthread.php?t=2689)](http://ubuntuforums.org/showthread.php?t=2689)).

---

### Post by Epis0de on 2007-03-23
Well...its not really the same, I THINK ive already deleted windows, I dont want it at all on my computer, so I used the GNOME partition device to clear them.

Anyway, it gets to the Loading GRUB thing at startup then just keeps saying that forever and ever... :(

I don't have any blank CD-R's at the minute so this is agony.

---

### Post by Epis0de on 2007-03-23
[http://i12.tinypic.com/4doq4rb.png](http://i12.tinypic.com/4doq4rb.png)  <<< There is a screenie of what the partitions look like, I dont see HD0 etc anywhere so I assume im doing something wrong.

Remember my Hard Disks are raided.

---

### Post by Epis0de on 2007-03-23
Tried to install Grub natively but the command lines dont seem to work, constantly getting "unrecognised" etc..

---

### Post by martinw89 on 2007-03-23
Oh I believe RAID setups make things more complicated but I don't have one, someone else will have to help you out with that.

---

### Post by Epis0de on 2007-03-23
Halp! :(

---

### Post by Epis0de on 2007-03-23
Last and final bump, looking for any sources of data, I cant find much on the site except for cmd lines that dont seem to function (most likely my fault), this is going to leave me without a computer for 3 days until I get my damn windows XP cd back.

Aghhhhh, does ANYONE have any idea how to run Raid install, I checked the nvidia raid setup in bios, apparently its striped, but, I didnt see RAID 1 or RAID 0 anywhere.

/beg

---

### Post by Epis0de on 2007-03-23
Not sure how relevent this is but I got ERROR 22  a couple of times.

---

