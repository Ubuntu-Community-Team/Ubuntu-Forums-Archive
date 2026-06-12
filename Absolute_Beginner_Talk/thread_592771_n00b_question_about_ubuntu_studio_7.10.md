---
title: "n00b question about ubuntu studio 7.10"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by luckyluca on 2007-10-26
Hello,

First of all Hi,
I've made the big decision to install linux to my newly purchased second hand laptop (fujitsu tablet t4215).
I'm confident I 'll able to run all my necessary applications in linux without the need to switch back to windows and since I've used linux at work for about 2 years now I feel confident using it as a user, but I'm still a complete n00b in regards to installing and setting it up.

So here's to the questions :)
I'm going to use ubuntu mainly for 3D apps and video compositing and editing and sometimes photo retouching(cinerella gimp houdini and my trusted company's maya and shake).
What version would you recommend installing?
I was thinking ubuntu studio 7.10 since I have my 3d and video data on external ntfs disks and I could do with the write access (as long as this is 100% safe).
Would you recommend ubuntu studio 7.10 over 7.04 and is there anything I should be aware of in terms of stability issues bugs?

Thanks a lot!

Luca

---

### Post by bren on 2007-10-26
3d stuff  - if your hardware supports it 7.10 should be slightly easier to set up advanced graphics support.....7.04 will still work but might need a little more googling

NTFS - either 7.10 or 7.04 is fine.   In 7.10 NTFS read-write support is installed as default.   In 7.04 read NTFS is default but read-write is trivial to install (sudo apt-get install nfts-3g ntfs-config or something similar)

Ubuntu studio - don't know havent used it

bren

---

### Post by LowSky on 2007-10-26
I love studio its my current OS, try a live CD of regular ubuntu before installing studio (studio doesn't have a live cd yet... also it need a dvd as its too big to fit on a cd


just so you know, 
Regular ubuntu can have all the same applications as studio. you can also add studio features to ubuntu through synaptic

---

### Post by por100pre1 on 2007-10-26
Yes, try Ubuntu Gutsy first. If it works fine you can install it and then add the extra Ubuntu Studio packages [this]("http://ubuntuforums.org/showpost.php?p=3639492&postcount=7") way.

---

### Post by luckyluca on 2007-10-27
Thanks for the warm welcome!

I think I'll stick to 7.10 and I think I'll give ubuntuStudio a go.
The only thing I was wondering is the real-time (RT) kernel is shipped with ubuntu studio, and how useful that would be on a laptop with integrated sound and video chips. The same thing applies to cinerella as there is a choice to install the default or the opengl optimized builds..

Also I was wondering if it possible to run cinerella built for 7.04 on 7.10 ([from here]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu"))

Lastly is beryl installed by default ? (although I don't think the intelGMA950 would do a great job at opengl handling ehehehehe)

Thanks again for the replies. I'll get hold of the new laptop next weekend, so all I can do now is just gathering informations before the real job begins :)

R
Luca

---

### Post by wawarren on 2007-10-29
You may want to dig around and make sure Houdini works fine under 7.10.  I've only seen one post regarding it, but a few people are having some relatively minor issues with their libraries.  You may want to watch this thread at least. 

[Link to Post]("http://ubuntuforums.org/showthread.php?p=3646880#post3646880")

If you run into a road block with any of your applications there's always the option of running 7.04 Fiesty with the Ubuntu Studio theme and installing all the other stuff yourself.  

I don't know much about Beryl since I'm pretty new to Linux, but I think you need to have "Compostite" turned on in your xorg.conf to use it?   I'm not sure about that, but I know Maya requires you to disable Composte, so things like Desktop effects don't work.

---

### Post by tdrusk on 2007-10-29
> **luckyluca said:**
> Thanks for the warm welcome!

I think I'll stick to 7.10 and I think I'll give ubuntuStudio a go.
The only thing I was wondering is the real-time (RT) kernel is shipped with ubuntu studio, and how useful that would be on a laptop with integrated sound and video chips. The same thing applies to cinerella as there is a choice to install the default or the opengl optimized builds..

Also I was wondering if it possible to run cinerella built for 7.04 on 7.10 ([from here]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu"))

Lastly is beryl installed by default ? (although I don't think the intelGMA950 would do a great job at opengl handling ehehehehe)

Thanks again for the replies. I'll get hold of the new laptop next weekend, so all I can do now is just gathering informations before the real job begins :)

R
Luca

Ubuntu Studio has the realtime kernel.
You may encounter hibernation problems and stuff like that, but it works well.

---

### Post by luckyluca on 2007-11-05
Hello,

I've just freshly installed ubuntu gutsy 7.10 and all seems well, except for a warning that said 
something from /etc/apt/sources.list couldn't be installed and the lines would be commented out instead. I understand this since I was not connected to the network when I first installed ubuntu.

So after I finished the installation I checked the file and I can see about 6-7 commented out lines.
How can I fix this? if I remove the comments should the lines be pickedup at the next reboot or should I run a command to re-run sources.list?

thanks a lot
Luca

---

### Post by CatKiller on 2007-11-05
> **luckyluca said:**
> So after I finished the installation I checked the file and I can see about 6-7 commented out lines. How can I fix this? if I remove the comments should the lines be pickedup at the next reboot or should I run a command to re-run sources.list?

You can edit that file by pressing Alt-F2 and entering```
gksudo gedit /etc/apt/sources.list
``` After you've uncommented the lines that you want uncommented (removing the # from the front of the line) you can either hit the reload button in Synaptic (System -> Administration -> Synaptic) or run ```
sudo aptitude update
``` to refresh the package information based on the new repositories.

Alternatively, you can edit your repositories list in Synaptic itself.

---

### Post by luckyluca on 2007-11-06
> **CatKiller said:**
> You can edit that file by pressing Alt-F2 and entering```
gksudo gedit /etc/apt/sources.list
``` After you've uncommented the lines that you want uncommented (removing the # from the front of the line) you can either hit the reload button in Synaptic (System -> Administration -> Synaptic) or run ```
sudo aptitude update
``` to refresh the package information based on the new repositories.

Alternatively, you can edit your repositories list in Synaptic itself.


Thanks! that helped me quite a lot.
However what I did in the end I have reinstalled ubuntustudio because, since I upgraded to ubuntu studio, I was getting a gnome error everytime I booted up.

Thanks again
Luca

---

### Post by luckyluca on 2007-11-06
> **luckyluca said:**
> Thanks! that helped me quite a lot.
However what I did in the end I have reinstalled ubuntustudio because, since I upgraded to ubuntu studio, I was getting a gnome error everytime I booted up.

Thanks again
Luca

BTW, do you know of a good tutorial to set the tablet pc wacom up and running?
For instance by typing 'wacdump -f tpc /dev/ttyS0' I have a working tablet with working buttons and pressure limited to the terminal window. I just need to find out how to enable it.

Thanks
Luca

---

