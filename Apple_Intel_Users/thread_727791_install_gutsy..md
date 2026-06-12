---
title: "install gutsy."
date: 2008-03-18
forum: Apple Intel Users
---

### Post by jerraldo on 2008-03-18
When I try to install "Gutsy" on my I -Mac: I get a constant flickering back an forth to full screen.
Eventually there is a message saying that something bad is happening.(Not much of a surprise!).
Can anyone help?
I have had no problems with previous Ubuntu installs.
Jerraldo.

---

### Post by handy on 2008-03-18
Which model iMac?  I have Gutsy running well on the 24" Alu' job.

Can you use the disk as a LiveCD?

---

### Post by cyberdork33 on 2008-03-18
sounds like Xorg is trying to start several times then failing. You will need to start in safe graphics mode so that you can install the proprietary drivers.

---

### Post by jerraldo on 2008-03-18
Many thanks for the reply.
Sorry to be so newbie but how do I start in Graphic mode.
Jerraldo.

---

### Post by liberalist on 2008-03-18
Hi Jerraldo,

When you boot up your Gutsy Gibbon CD, you can select "Start Ubuntu in safe graphics mode" (just use the down arrow key).

---

### Post by jerraldo on 2008-03-19
Many thanks for the replies.
I have tried safe graphics mode but same results.
I have 20inch imac.

---

### Post by cyberdork33 on 2008-03-19
there are many different 20in iMacs, you need to be more specific.

I don't know why you are still getting issues with safe graphics mode, but you can install with the alt cd and that will get you going enough so that you can install the proprietary drivers on your machine, then Xorg should work.


And actually, if you wait until tomorrow, you can try the Hardy Beta release which will probably work better anyway.

---

### Post by hackersmovie on 2008-03-23
I get the same thing on my 17" 1.83Ghz Core Duo iMac with 2GB RAM. I actually have the CD's I ordered in the mail so they should be good. I've tried both the regular and safe graphics modes but, it comes up with the same weird screen saying something bad happened. I'm downloading the alternate CD now and will give that a go. I've already partitioned my drive with Boot Camp Utility in OS X and am trying to just get Ubuntu 7.10 installed.

**EDIT: The error code that comes up is:**
```
bcm43xx: Error: Microcode bcm43xx_microcode5.fw not available or load failed
```

**This happens with regular install, safe graphics mode and OEM install. I hit F6 when the screen loaded and checked the CD it said it's fine. I don't know what's going on. . . **

Any ideas? Please let me know if you need more info.

Thanks in advance.

---

### Post by hackersmovie on 2008-03-23
...from a few google searches, I've only become more confused. Apparently, I found on other Linux sites, the error code has something to do with the wireless card! WTF! why would that make it bug out the graphics? Not to mention not be able to be installed or even start the process? I'm confused, please help.

---

### Post by cyberdork33 on 2008-03-24
That error has nothing to do with the graphics.

---

### Post by hackersmovie on 2008-03-24
> **cyberdork33 said:**
> That error has nothing to do with the graphics.
Understood. My question is why is that coming up when it says it encountered a problem with the display server?

---

### Post by cyberdork33 on 2008-03-24
> **hackersmovie said:**
> Understood. My question is why is that coming up when it says it encountered a problem with the display server?because it can't find the wifi firmware that it is trying to load. Normally you cannot see this because you are not at the terminal. You can try to remove the bcm43xx driver since can't use it anyway:
```
sudo modprobe -r bcm43xx
```

This error message should not effect the function of your Mac at this point and can be ignored. Your graphics problem is a completely different issue.

---

### Post by hackersmovie on 2008-03-24
> **cyberdork33 said:**
> because it can't find the wifi firmware that it is trying to load. Normally you cannot see this because you are not at the terminal. You can try to remove the bcm43xx driver since can't use it anyway:
```
sudo modprobe -r bcm43xx
```

This error message should not effect the function of your Mac at this point and can be ignored. Your graphics problem is a completely different issue.

So, if I can correct the graphics issue, so it will acutally install and boot, I could fix the wifi issue. 

Any ideas on the graphics problem? I've tried both the live CD and alternate CD, as well as openSuse 10.3. I could install the alternate of both Ubuntu and openSuse but, when it reboots it just says "something bad happened" with the display server. (gnome I suppose)

Thanks!

---

### Post by cyberdork33 on 2008-03-25
> **hackersmovie said:**
> So, if I can correct the graphics issue, so it will acutally install and boot, I could fix the wifi issue. 

Any ideas on the graphics problem? I've tried both the live CD and alternate CD, as well as openSuse 10.3. I could install the alternate of both Ubuntu and openSuse but, when it reboots it just says "something bad happened" with the display server. (gnome I suppose)

Thanks!
You are at a terminal. Login and make changes... You do not have to have a GUI. 

If you install the system with the alt cd, you can then login at the terminal and fixe the graphics issue... likely forcing the vesa driver in xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```
Find the driver line and change the driver (probably from ati) to vesa and save. Then you should be able to restart into the normal gui (although probably ugly looking). Then you can use the driver manager to install the fglrx driver.

IDK why Xorg keeps failing on you, but you will have to view the log messages to get the real error message to get better help.

---

### Post by hackersmovie on 2008-03-25
> **cyberdork33 said:**
> You are at a terminal. Login and make changes... You do not have to have a GUI. 

If you install the system with the alt cd, you can then login at the terminal and fixe the graphics issue... likely forcing the vesa driver in xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```
Find the driver line and change the driver (probably from ati) to vesa and save. Then you should be able to restart into the normal gui (although probably ugly looking). Then you can use the driver manager to install the fglrx driver.

IDK why Xorg keeps failing on you, but you will have to view the log messages to get the real error message to get better help.

Thank you so much! However, I went ahead and tried the beta of Hardy and guess what?!? It works just fine! I'll give it a go for now.

Thanks again!

---

### Post by jerraldo on 2008-03-28
Thanks everyone for the replies about Gutsy install problems.
Still nobody has come up with a fix!!!
My disc came from OS Disc.com.
Surely someone must be able to solve this problem.
Newcomers to Linux are going to be thin on the ground if this is the 
normal state of play.
I am keen to use Linux,but this is no way to entice newbees.
Thanks in advance.
Jerraldo.

---

### Post by cyberdork33 on 2008-03-28
Get Hardy and try it. 

Or use the alt cd...

---

### Post by hackersmovie on 2008-03-28
> **jerraldo said:**
> Thanks everyone for the replies about Gutsy install problems.
Still nobody has come up with a fix!!!
My disc came from OS Disc.com.
Surely someone must be able to solve this problem.
Newcomers to Linux are going to be thin on the ground if this is the 
normal state of play.
I am keen to use Linux,but this is no way to entice newbees.
Thanks in advance.
Jerraldo.

What "fixed it" for me was this:

Downloaded the "Hardy beta Alternate CD for i386"
Burned the .iso image with Disk Utility in OS X at the SLOWEST SPEED

then it booted, and installed with ease.

You still have never said exactly which iMac you have. Depending on the specifications of the machine you may need to try a different version or even a different Distro.

an example of this: My Macbook wouldn't boot any of the Live CD's or  i386 versions, only the Alternate amd64 versions. . . .

---

