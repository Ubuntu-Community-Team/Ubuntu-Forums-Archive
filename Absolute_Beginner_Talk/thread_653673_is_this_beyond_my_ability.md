---
title: "is this beyond my ability?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by anuroc on 2007-12-30
Hello, I can't say I am a new Ubuntu user because my problem is that I can't use Ubuntu (nor Suse or Sabayon, and I guess I  could not use any other distro with my current hardware). 

I don't consider myself a lamer, so I did the job, I searched about my problem and read a lot before coming here to post. And I found out that other people also got this message during the booting:
 "The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again" After those 2 minutes, the process starts again: 6 unsuccessful tries and the same message and so on.
And I found most of them had the same video card brand as mine: ATI (I have a Radeon X1600 Pro card)

I tried several things, but any of them works. I know this is a bit generic, but I really don't know what I did. I just followed what other people said in different forums. The good part is that now I have changed from one distro to another several times without deleting all my hard disk. And I know a bit more about using the terminal. But that's it. I just can use the terminal, and I think that's a rough start for a newbie like me. For this, I could just install the kernel and it would be the same :)

One thing I tried, when I knew a little more what I was doing, was editing the /etc/X11/xorg.config file to add my monitor and video card names and It didn't pan out. I tried as well the "sudo dpkg-reconfigure xserver.xorg" way but it seems that my card and monitor (LG FLATRON 774FT) are not very popular in LinuxWorld.
I read many people saying ATI drivers for Linux are no good but I know there are brand new drivers from last week. I would like to try with this ones and here comes my problem: I read I had to delete the old drivers in order to get the new ones working fine and I don't know how to search and destroy those drivers (remember I just can type in the terminal).
So, if someone could explain me how to do it through the terminal I will make a last try. If not, I'll declare myself not competent enough for this stuff and will take my spare time to read about the terminal code without losing so much time trying to use gnome.

---

### Post by overdrank on 2007-12-30
> **anuroc said:**
> Hello, I can't say I am a new Ubuntu user because my problem is that I can't use Ubuntu (nor Suse or Sabayon, and I guess I  could not use any other distro with my current hardware). 

I don't consider myself a lamer, so I did the job, I searched about my problem and read a lot before coming here to post. And I found out that other people also got this message during the booting:
 "The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again" After those 2 minutes, the process starts again: 6 unsuccessful tries and the same message and so on.
And I found most of them had the same video card brand as mine: ATI (I have a Radeon X1600 Pro card)

I tried several things, but any of them works. I know this is a bit generic, but I really don't know what I did. I just followed what other people said in different forums. The good part is that now I have changed from one distro to another several times without deleting all my hard disk. And I know a bit more about using the terminal. But that's it. I just can use the terminal, and I think that's a rough start for a newbie like me. For this, I could just install the kernel and it would be the same :)

One thing I tried, when I knew a little more what I was doing, was editing the /etc/X11/xorg.config file to add my monitor and video card names and It didn't pan out. I tried as well the "sudo dpkg-reconfigure xserver.xorg" way but it seems that my card and monitor (LG FLATRON 774FT) are not very popular in LinuxWorld.
I read many people saying ATI drivers for Linux are **** but I know there are brand new drivers from last week. I would like to try with this ones and here comes my problem: I read I had to delete the old drivers in order to get the new ones working fine and I don't know how to search and destroy those drivers (remember I just can type in the terminal).
So, if someone could explain me how to do it through the terminal I will make a last try. If not, I'll declare myself not competent enough for this stuff and will take my spare time to read about the terminal code without losing so much time trying to use gnome.

Ok it sounds like you have installed Ubuntu on  your system correct? If so did the live cd work at all? Did you try and choose the vesa driver when you reconfigured your xorg? Have you looked at Envy, It has helped some users, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

