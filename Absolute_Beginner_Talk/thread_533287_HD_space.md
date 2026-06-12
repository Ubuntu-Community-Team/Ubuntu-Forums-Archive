---
title: "HD space"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by williamHH on 2007-08-23
I am thinking of dual-booting ubuntu on my 80-gig hard-drive. I have about 27 gigs left. How much do you suggest I partition for ubuntu?:confused:

---

### Post by Hobo Joe on 2007-08-23
Well, if you can spare it, 25 would be good.

---

### Post by southernman on 2007-08-23
10-27GB you decide.

Although it's recommended at least 2.5gb for / don't fall for it if you really want to play around and install various other software on top of Ubuntu.

Welcome to the forum by the way... :)

---

### Post by williamHH on 2007-08-23
I was thinking more in the 5-7gb range. All i need linux for is web browsing/basic use. Would it run comfortably? Also i know there are about a thousand tutorials out there for dual booting, but which one is the best?

---

### Post by dwhitney67 on 2007-08-23
> **williamHH said:**
> I am thinking of dual-booting ubuntu on my 80-gig hard-drive. I have about 27 gigs left. How much do you suggest I partition for ubuntu?:confused:
I just installed Ubuntu moments ago on a spare system I had... the default space it wanted was 21GB, but I think it would operate with less.

In your case, 27 GB is more than enough.  If you are just experimenting, then try manually specifying the following:

[FONT="Courier New"]/boot       0.5 GB
/            10.0 GB
/swap    1.0 GB   (or twice your amount of RAM)[/FONT]

You can always leave the remaining space on your drive for use on another day.  Or just accept the default partitioning schema offered by the Ubuntu installer.  Be careful not to delete your primary partition (other Linux distro or Windoze).

---

### Post by williamHH on 2007-08-23
> **dwhitney67 said:**
> /boot       0.5 GB
/            10.0 GB
/swap    1.0 GB   (or twice your amount of RAM)[/FONT]

what?

---

### Post by schorsch on 2007-08-23
I'd suggest a separate partition for /home as all your personal stuff and configurations like bookmarks will go there. If you reinstall the OS you will not loose any of them ....

---

### Post by dwhitney67 on 2007-08-23
Ouch... you are a newbie if you don't understand what I posted.  No problem... just accept the Ubuntu defaults concerning partitioning the remaining 27GB on your HDD.

---

### Post by williamHH on 2007-08-23
ok thanks.

---

### Post by bjarneh on 2007-08-23
/boot 0.5 GB
/ 10.0 GB
/swap 1.0 GB

this is supposed to be a setup of your partitions, or an adviced setup, not really sure what you mean by "what?", but was that of any help :-)

ie. create 3 partitions (1 you already have with Windows on it i guess), then create these mountpoint for them...(swap doesn't have a mount point)

---

