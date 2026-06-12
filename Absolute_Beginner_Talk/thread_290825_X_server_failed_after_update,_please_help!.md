---
title: "X server failed after update, please help!"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-01
So I just upgraded from Ubuntu Dapper to Edgy Elf, rebooted and faced with scrren saying x server failed. How does this noob fix this problem quickly? 

Thanks :)

---

### Post by %hMa@?b&lt;C on 2006-11-01
drop into a console, alt+ctrl+f1 and then try typing in
sudo dpkg-reconfigure xserver-xorg

---

### Post by slibuntu on 2006-11-01
Happened to me and i had to type "sudo apt-get install xorg", dunno why the update 'forgot' to install the xorg server, but it worked after that

---

### Post by spamzilla on 2006-11-01
Ok I entered that into termial and I got a messgae saying

/usr/sbin/dpkg-reconfigure: xserver-org is broken or not fully installed

Now what do I do?

Thanks for the speedy reply :)

---

### Post by spamzilla on 2006-11-01
> **slibuntu said:**
> Happened to me and i had to type "sudo apt-get install xorg", dunno why the update 'forgot' to install the xorg server, but it worked after that


Ok I'll try that now

edit I also keep getting a message saying

cpufreq: change failed with new _state 1 and result 0

What does that mean?

---

### Post by spamzilla on 2006-11-01
> **slibuntu said:**
> Happened to me and i had to type "sudo apt-get install xorg", dunno why the update 'forgot' to install the xorg server, but it worked after that

My laptop won't connect to the internet (wireless), so I cannot get the required files :(

Any other ideas?

---

### Post by slibuntu on 2006-11-01
To be honest, no clue, but i did have a similar errror message, something to do with states, let me know how the sudo apt-get install xorg goes, cos its what solved all my problems

---

### Post by spamzilla on 2006-11-01
> **slibuntu said:**
> To be honest, no clue, but i did have a similar errror message, something to do with states, let me know how the sudo apt-get install xorg goes, cos its what solved all my problems

I get loads of messages saying 

failed to fetch [http://blah](http://blah)...

using the apt-get install xorg command. I get similar results using other commands where I need to download packages :(

---

### Post by slibuntu on 2006-11-01
Is the problem that you don't have an internet connection? or that you do but it won't connect?

---

### Post by spamzilla on 2006-11-01
> **slibuntu said:**
> Is the problem that you don't have an internet connection? or that you do but it won't connect?

I have a wireless connection, but for some reason it's not conencting to the internet (connection timeout). This laptop i am using at the moment is conencting fine wirelessly.

Is there a way I can edit a file to get things working again?

---

### Post by slibuntu on 2006-11-01
Hmm, there have been some issues with edgy and wireless cards, a wired connection would be best, i don't know about editing files and all that, i'm only slightly less of a noob than you are, maybe someone else will jump in and help??!!

---

