---
title: "Updated to Studio, Now X Won't Start"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by carpola on 2007-05-15
So I installed ubuntu studio over Feisty by using the package manager and I rebooted once everything had finished downloading. When I reboot, it takes me to the command line username@computer and says that X cannot start. 


**How do I start X and/or what else should I do?**

---

### Post by Happy_Man on 2007-05-15
Over Feisty, you say? As in there is no real official Feisty install on your comp anymore? Ok, we can work with that. What's your graphics card? Also, could you post the ouput of
```
cat /etc/X11/xorg.conf
```

---

### Post by MetalMusicAddict on 2007-05-15
You cannot "update" to Ubuntu Studio. You can however install packages that might install another kernel. Boot into your -generic kernel. Install the restricted modules for the -lowlatency kernel that was most likely installed.

---

### Post by Josey on 2007-05-15
```
sudo dpkg-reconfigure xserver-xorg
```

defaults work for most everything.

---

### Post by carpola on 2007-05-15
It seems as though Feisty is still on my computer but I would have to start X. 

Metal - How would I go about doing any of that? I don't know what that means.

---

### Post by MetalMusicAddict on 2007-05-15
> **carpola said:**
> It seems as though Feisty is still on my computer but I would have to start X. 

Metal - How would I go about doing any of that? I don't know what that means.

Tell me exactly how you "upgraded" to Ubuntu Studio. What did you install?

---

### Post by carpola on 2007-05-15
Well, now I'm decided to run the generic kernel, instead of the -lowlatency and ubuntu studio is working. why wouldn't it work when i ran lowlatency? (x serv wouldnt start)

---

### Post by MetalMusicAddict on 2007-05-15
> **carpola said:**
> Well, now I'm decided to run the generic kernel, instead of the -lowlatency and ubuntu studio is working. why wouldn't it work when i ran lowlatency? (x serv wouldnt start)

Re-read my 1st post then type: **sudo apt-get install linux-lowlatency** in a terminal.

---

### Post by carpola on 2007-05-15
Just wondering, what's the difference between installing this and running lowlatency and just running the generic kernel?

---

### Post by MetalMusicAddict on 2007-05-15
-lowlatency is for audio work. Gives you better preformance.

---

### Post by carpola on 2007-05-15
How come when I updated from the terminal earlier, the lowlatency materials didn't install?

---

### Post by pataphysician on 2007-05-15
> **MetalMusicAddict said:**
> Tell me exactly how you "upgraded" to Ubuntu Studio. What did you install?

[http://www.ubustu.com/](http://www.ubustu.com/) says:

How to add Studio to an existing Ubuntu install

First you’ll want to add the Ubuntu Studio repository to your Sources list and update :

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Now fire up Synaptic Package Manager. Search for ubuntustudio. All the packages except -screensaver and -launcher are official Studio packages. Cue them up for install and you’re good to go!

---

### Post by carpola on 2007-05-15
That's the exact site and instructions I used, except that when I rebooted, X wouldn't start in the lowlatency kernel.

---

### Post by MetalMusicAddict on 2007-05-15
> **carpola said:**
> That's the exact site and instructions I used, except that when I rebooted, X wouldn't start in the lowlatency kernel.

Please do what I have instructed to do.

BTW "ubuntustudio-screensaver" is official. I made it 2 weeks ago. :)

---

### Post by carpola on 2007-05-15
I DID do what you had instructed. It's fine now. Thank you.

---

### Post by trentrolf on 2007-05-15
I am having a similar problem.  I did a clean install of Studio from Fiesty, and everything in the installation went smoothly but now when I try to boot I just get a lot of random characters when X tries to start.  After X fails I can see the tail end of a login, so I log in and try to reconfigure X but nothing happens.  

From other posts it seems like the installer is supposed to automatically check resolutions (during the screen resolution step of Studio installation) that are compatible with my video card, but there were none automatically checked, so I just checked the normal 1280x1024.  I have a plain vanilla intel video card that Ubuntu has never had problems with.

Can anyone help?

---

### Post by Pastorn on 2007-05-16
Hello

If I do this code
```
sudo apt-get install linux-lowlatency
```

will there be any "negative consequences" to the rest of my system?
I mean will it e.g. affect my videoediting software in any way?  ;)

/Thomas

---

