---
title: "Tweaking Ubuntu"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Mikey_MW on 2006-07-19
I have just reinstalled Ubuntu on an old machine, and would like to tweak it for more speed. Being a Uni student, I don't have the budget to upgrade the hardware. I tried Xubuntu, but it didn't run my CD-Rom properly, and other linux distros aren't as user friendly, so I'm back to using Ubuntu. 

I've got it running on
 - Celeron 400MHZ 66FSB
 - 320MB PC66 SDRAM
 - 6GB ATA/33 Hard Drive
 - 4MB Integrated Graphics

Its actually faster than windows, but still a bit slow, any ideas?

---

### Post by Kilz on 2006-07-19
> **Mikey_MW said:**
> I have just reinstalled Ubuntu on an old machine, and would like to tweak it for more speed. Being a Uni student, I don't have the budget to upgrade the hardware. I tried Xubuntu, but it didn't run my CD-Rom properly, and other linux distros aren't as user friendly, so I'm back to using Ubuntu. 

I've got it running on
 - Celeron 400MHZ 66FSB
 - 320MB PC66 SDRAM
 - 6GB ATA/33 Hard Drive
 - 4MB Integrated Graphics

Its actually faster than windows, but still a bit slow, any ideas?
Try and fix the cdrom issue with Xubuntu?

---

### Post by kris2pe on 2006-07-19
Kilz clearly the person is asking in how to fix it!!! 
You don't tell them "Try and fix the cdrom issue with Xubuntu?!" bcoz if he had he won't need to post it here!!! 
LIke what he said 

"I tried Xubuntu, but it didn't run my CD-Rom properly, and other linux distros aren't as user friendly, so I'm back to using Ubuntu."

---

### Post by Mangledbmx on 2006-07-19
well my tip doesnt apply to all of ubuntu but instead the speed of mozilla. just open up the web browser and in the address box type "about:config" without the "". find IPv6 and change its value from false to TRUE!

this will increase your web browsing speed, it worked for me anyway!
sorry i couldnt help with anything else

---

### Post by noynac on 2006-07-19
The following is a HowTo on improving performance:

[http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)

---

### Post by Landoln on 2006-07-19
> **Mikey_MW said:**
> I tried Xubuntu, but it didn't run my CD-Rom properly

You could always do a ```
sudo apt-get install xubuntu-desktop
``` after you have ubuntu installed.  That would give you the option of signing into xfce4 instead of gnome which should help with the speed quite a bit.

---

### Post by djsroknrol on 2006-07-19
I would recomend initNG. It helped save about 30sec. off my boot and shut down time.

Also, sysv-rc-conf works well as well....

---

### Post by Mikey_MW on 2006-07-19
Thanks, Mozilla works quicker now. I've just brought a Celeron 500Mhz, extra 256Mb Ram, and a 20GB hard drive (for $20!), so I hope to get some speed (on a budget). Now all I have to do is install them.

---

### Post by Turtle.net on 2006-07-19
You can also try epiphany instead of firefox it's faster.
Then you can also replace metacity by openbox or e16 or even e17. There is plenty of howtos in the forum that sould help you with that (for each solution proposed above you will have a pretty good speed increase).

Good luck ;)

---

### Post by Kilz on 2006-07-19
> **kris2pe said:**
> Kilz clearly the person is asking in how to fix it!!! 
You don't tell them "Try and fix the cdrom issue with Xubuntu?!" bcoz if he had he won't need to post it here!!! 
LIke what he said 

"I tried Xubuntu, but it didn't run my CD-Rom properly, and other linux distros aren't as user friendly, so I'm back to using Ubuntu."

In my experience, sometimes when something isn't working out right away. Some people do the distro hop hoping to find something that will work better. Sometimes it takes a little longer to figure out a problem. I'm not saying that's the case here, but he is looking for ways of trying to make gnome faster. It may be easier to fix the CD issue, hard to tell because we don't have more background.
But trying to fix the CD issue was an idea, and that's what he asked for was idea.

---

### Post by Mikey_MW on 2006-07-19
Ok, I think I understand what you are saying now Kilz. Sorry 'bout the misunderstanding before. 

I don't mind Xubuntu (its actually very good except the CD problem) Before I used a Xubuntu Disc to do a fresh install on the hard drive. but if I took a working Ubuntu install, and put Xfce on top, would it still keep working? Because that would give me speed AND a CD-Rom, right?

---

### Post by sarum on 2006-07-20
Hi djsroknrol, you suggested Mikey_MW should try the following:-

"I would recomend initNG. It helped save about 30sec. off my boot and shut down time.

Also, sysv-rc-conf works well as well...."

Mikey_MW may well understand what these do and how to do them; but I don't. I should like to know as I have a similar problem. So if you, or someone else would be kind enough to explain I'd be very grateful.
Thanks Sarum.

---

### Post by Mikey_MW on 2006-07-20
From what I understand initNG is a program / component of linux which loads and starts up the computer. I think that initNG loads things slightly differently, speeding it up. 

(I didn't really understand the technical stuff, but thats the gist of things as I understand :)

---

### Post by kinematic on 2006-07-20
i think the easiest solution for u is to install the server edition for ubuntu(since the xubuntu cd doesn't work).
that will give u the server install without the graphical environment.
after installation u log into the shell with the password you setup during install and issue the following commands:
sudo aptitude update
sudo aptitude install xubuntu-desktop.(these commands ask for the same password,you won't see anything being entered but that's normal)
that'll pull in and install/configure the xfce based xubuntu desktop wich you can log in to.
you could then remove some of the server stuff i you want and that way you should end up with a lightweight install.

---

### Post by djsroknrol on 2006-07-20
sorry guys if there wasn't enough detail. For initNG, check [this]("https://help.ubuntu.com/community/InitNG") out...and for sysv-rc-conf, look at [this]("http://ubuntuforums.org/showthread.php?t=89491")..I hope this clears up things for you...

---

### Post by sarum on 2006-07-21
Hi djsroknrol, thanks for those links. I feel a bit out of order asking a question inside someone else's.
Cheers Sarum

---

