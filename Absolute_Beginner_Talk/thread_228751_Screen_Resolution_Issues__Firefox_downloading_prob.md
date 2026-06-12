---
title: "Screen Resolution Issues / Firefox downloading problem.. Please help a newbie!"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by CBTF on 2006-08-03
Hi there. After using Windows all my life, I finally decided to give LInux/Ubuntu a try today. I must say that i'm extremely impressed at how advanced this OS is and i'm looking forward to learning how to use it.

That being said, I am having some difficulties that are keeping me from feeling totally comfortable with my experience. I know nothing about Linux terminology, and even less about the terminal. Please bear with me here.

That out of the way, here are my issues:

My resolution won't go any higher than 1024. Because my monitor seems to cut off things with lower resolutions (does this in windows too, for some reason about 20 pixels on either side are cut.. but that's neither here or there) it's essential that I can up the res. I would like 1280x720. 

Does anyone know what I can do here? I have a Compaq PC with an ATI radeon xpress 200 card. I installed easyubuntu with the ATI drivers selected but I cannot change my res to be higher. Perhaps there is something I can enter in terminal to tinker with this?


My second, less important issue is that when I try to download a file from firefox, it won't. For example, I select "save as" for an image, and select desktop or a folder on my desktop as the destination it will automatically move to "done" but the file will not be present in the location. CLicking "open" in the FF download window gives me an error saying the file is not there.

Thanks again for any help in advance. :-k

---

### Post by zxee on 2006-08-03
I don't know exactly what's happening with firefox's downloads. Can you provide more info e.g the type of file you're trying to download.

About your screen resolution issue: You have options. If you feel comfortable enough editing files you can use gedit to edit your /etc/X11/xorg.conf file or, probably better for now, you can open Applications>Acessories>Terminal and type > sudo dpkg-reconfigure xserver-xorg and follow through the configuration program. For values you don't know just push the enter key for the default. You will eventually get to the screen resolution section and then you can enter the values for your monitor.
Ubuntu has plans for a easier to use xserver set up tool but we have what we have now. Welcome aboard!!

---

### Post by darrenm on 2006-08-03
are you actually using the fglrx driver rather than a mesa driver?

open a terminal and type fglrxinfo, check that it says ATi technologies rather than MESA.

With your firefox problem sounds like you don't have permissions to write to your own desktop somehow. Open a terminal and type ```
sudo chown -R $USERNAME:$USERNAME ~
```

That should give you ownership of all your /home/ directory.

---

### Post by CBTF on 2006-08-03
THanks for the replies. I'll tie this into another thread I have going so it's all in one place.

Basically I did the whole sudo dpkg-reconfigure xserver-xorg thing, and the login menu is now at 1280 resolution. The problem is that when I enter my username and password, it moves on to load up Ubuntu.. my monitor turns off and gives me the message "input signal out of range." How can I fix this? When I hook another monitor up to the comp, ubuntu runs fine.. its something to do with hardware.

If it means anything im using an Optiquest Q7 LCD.

THanks for the firefox tips. I will try that once this monitor is sorted out. Im praying something will work, I havent found a solution yet..

---

### Post by CBTF on 2006-08-03
Ok scratch that. It's working now. For some odd reason, the resolution that was set in the system menu wasnt the same as what I had set in the terminal.

NOW I have another problem :-k 

The resolution is correct, but many pixels are cut off on the right side. ENough so that I cannot see the "X" button on this firefox window.

I heard that it may be because my BIOS would be set for a CRT monitor and im using an LCD widescreen. Is this possible? If so, how would I modify that?

I really do appreciate your time and patience.

---

### Post by darrenm on 2006-08-03
You need to find the correct refresh rates for the monitor (should say in the handbook) and pass them to X in the xorg.conf file or rerun the xserver reconfigure and enter them there. 

Unfortunately I don't have anything like that in my xorg.conf file as its just got DPMS as the only monitor option, however I'm sure someone who knows will be along soon to clear it up ;)

If you follow the ATi binary driver wiki [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and follow the instructions for using the driver from ati.com then see if it supports the modelines correctly.

---

### Post by CBTF on 2006-08-03
"You need to find the correct refresh rates for the monitor (should say in the handbook) and pass them to X in the xorg.conf file or rerun the xserver reconfigure and enter them there."

Uh oh.. I lost my handbook. What relation do refresh rates have to the monitor cutting off 10 pixels though?

---

### Post by lennyjames on 2006-08-03
> **darrenm said:**
> are you actually using the fglrx driver rather than a mesa driver?

open a terminal and type fglrxinfo, check that it says ATi technologies rather than MESA.



Hi darrenm, I came across this post and I too wanted to check which ATI drivers I have as my system freezes when 3D applications run and my resolution maz is 1024x768. However, when I entered 'fglrxinfo' into the terminal, I got: 'bash: fglrxinfo: command not found'. I'm new to Linux but believe my system freeze is a driver problem. How do I proceed from here? I'm running an ATI 9800 pro.

---

### Post by CBTF on 2006-08-03
UPDATE: My issue was solved. After sitting around trying to figure out, my friend realized it was a simple monitor setting... how embarassing :p

---

### Post by darrenm on 2006-08-04
Hi Lenny.

Just follow the wiki. Works every time:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by lennyjames on 2006-08-07
> **darrenm said:**
> Hi Lenny.

Just follow the wiki. Works every time:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Thanks darren! I had sweaty hands while doing this but it worked! :D

---

