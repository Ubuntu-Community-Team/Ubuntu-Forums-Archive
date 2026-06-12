---
title: "Just Starting &amp; Need Help"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by w1smc on 2006-04-11
I had an extra laptop and I just finished installing ubuntu.  Being a newbie I assumed I would be presented a gui to start but all I have is a command screen with the standard user prompt (in my case it is: w1smc@w1smc:~$).

Question:  How can I get the giu to run?

---

### Post by mscman on 2006-04-11
You need to reconfigure xserver.  Login to the computer, run the following command and go through the steps it leads you through:
```
sudo dpkg-reconfigure xserver-xorg
```
Then you can either restart your computer or type```
sudo startx
```

---

### Post by w1smc on 2006-04-11
Thanks.

I ran the 1st command, was asked to enter my password, which I did and received the following:

Package 'xserver-org" is not installed and no info is available.

Use dpkg --info to examine archive files.
and dpkg --contects to list their contents.
/user/sbin/dpkg-reconfigure: xserver-xorg is not installed

I then get the command prompt:

w1smc@w1smc:~$

I'm missing something here, what is it?

BTW, thanks for the help.

---

### Post by htinn on 2006-04-11
How much RAM does your laptop have? Just curious. :)

---

### Post by w1smc on 2006-04-11
i have a 1/2 a gig on a dell latitude c800.

---

### Post by nalmeth on 2006-04-11
Sounds like you just did a server install, which leaves you with only the core of ubuntu.
if you know the difference between gnome and kde, decide which one you want, and install them with the following. (if you did in fact do full install, we will see right away, it will say it is the newest version. Gnome is the default gui for ubuntu)

[for gnome] ```
sudo apt-get install ubuntu-desktop
``` 
[for kde] ```
sudo apt-get install kubuntu-desktop
```

---

### Post by w1smc on 2006-04-11
Yes I only did a server install.

I ran the gnome install command, it asked me to insert my istall cd and right now it's chugging away.

I'll let you know what the result is in a few.

Thanks again for the help.

---

### Post by steve.horsley on 2006-04-11
Ha! Fooled you! 

With Windows, Server means same bloated GUI but with extra expensive bits that you need to run a server added that you don't get with the standard O/S. Server is the extra-heavy version. 

In Ubuntu you are always allowed those server type applications, and server means you don't need all that desktop GUI bloat 'cos it's going to sit in a rack somewhere. Server is the cut-down version.

Good luck.

---

### Post by w1smc on 2006-04-11
Ok, I now have the gui running.

I'm still going to refresh my memory on the standard command process (I did the  UNIX thing many moons ago at AT&T).

But this is a start.

Thanks for all the help.

Now I'm going to try and connect to the web.  Lets see if I can get lucky.

---

### Post by nalmeth on 2006-04-11
I think installing ubuntu-desktop should have used some online repositories, and if you have a wired ethernet connection you shouldn't run into too much trouble with that (knock on wood).
Don't expect to have to use the command line too much, though it is good to know how to get around, and the terminal is quite effecient for doing a lot of things over a gui.

---

