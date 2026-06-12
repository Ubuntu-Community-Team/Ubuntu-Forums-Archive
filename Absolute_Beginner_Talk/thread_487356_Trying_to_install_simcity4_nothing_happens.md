---
title: "Trying to install simcity4 nothing happens"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-29
I copied the .exe file from the cd onto my desktop, I left the game disk in the cd drive, I went to the terminal entered the command ( wine" SimCity 4.exe")The terminal paused for like 30 seconds like it was doing something, but nothing happened, it just prompted me nolan@BIGMAN:~$ Can someone help me with this please? Thanks

---

### Post by farmera2005 on 2007-06-29
I tried to run SC4 under Wine once and failed at it.

I would love to help you with this issue however, so please either email me at [email]afarmer@farmernetworks.com[/email], or post it on my forum [http://farmwiki.org](http://farmwiki.org).

Adam

---

### Post by cogadh on 2007-06-29
Instead of copying the .exe locally, try running the install like this:
```
wine /media/cdrom0/setup.exe
```
That way you are running it directly off of the CD, so that install .exe doesn't have any problems finding the rest of the install files.

**farmera2005**, are you trying to poach users from the Ubuntu forums for your own site? We all appreciate you trying to expand the Linux community, but I'm sure there are plenty of people here who could benefit from the continued troubleshooting of swoll1980's problem in this thread. Much of the information new users get for Linux comes from reading the troubleshooting trail posted in threads on the forums, and shifting that process to an e-mail conversation or to another site while we are still in the early steps won't help anyone in the community.

---

### Post by swoll1980 on 2007-06-29
thanks I will try that

---

### Post by swoll1980 on 2007-06-29
Same thing happens any Ideas?

---

### Post by cogadh on 2007-06-29
Wait a minute, does the SimCity .exe file really have a space between "City" and "4" as you typed it above?

---

### Post by swoll1980 on 2007-06-29
yes the file is named "SimCity 4.exe"

---

### Post by cogadh on 2007-06-29
Chances are, it was failing because Linux doesn't like spaces. The command got as far as the end of the word "City" and didn't know what to do. Try this instead:
```
wine "D:\SimCity 4.exe"
```
Replace the "D:" with the letter your CD drive was assigned in Wine's config, if necessary. Make sure you keep the quotes, they matter.

If that doesn't work, try this:
```
wine /media/cdrom0/SimCity\ 4.exe
```

Lastly, if neither of those work, try browsing to the CD and double-clicking the .exe. Technically, wine should automatically launch it, but you won't get the console output of any errors.

---

### Post by swoll1980 on 2007-06-29
wine can not find either one of those commands D: is my cd rom

---

### Post by cogadh on 2007-06-29
Did you run "winecfg" after you installed Wine?

EDIT - It's way past bedtime here, if you are still working on this, I won't be able to help again until the morning. Hopefully someone else can be of assistance for now.

---

### Post by swoll1980 on 2007-06-29
Thanks for your help

---

