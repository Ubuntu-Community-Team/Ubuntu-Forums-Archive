---
title: "Very slow wireless internet"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-17
I'm running wireless on my HP nx6310 and while I got wifi out of the box, 
it's very slow. It is plenty fast from the window partition on it so I'm thinking 
it's a driver issue on my Ubuntu partition. If I were to use Ndiswrapper, 
is there a possibility I would lose my wifi capabilities altogether? I know that 
wireless is sketchy with linux and I don't want to lose what I already got. 
I'm assuming there would be no harm in trying, but I just wanted to make 
sure. 

Also, if you know of any other simply fixes to speed up a wireless network 
card, do share!

I appreciate your patience!

---

### Post by nyinge on 2006-11-17
Mine works much better with ndiswrapper somehow.  Though, I could be doing something wrong with the setup with the firmware that comes on Ubuntu, but I got better results with ndiswrapper.

>  I'm assuming there would be no harm in trying, but I just wanted to make 
sure.
Unless you do something really out of the line.  :P

There are plenty of HOWTOs on this forum.  I personally followed the instructions on its website (ndiswrapper.sourceforge.net), which requires a user to compile from source.

---

### Post by shanepardue on 2006-11-17
Cool, are you using the same wireless setup or are you just saying your 
particular setup worked better? Either way, I should probably give it a shot. 
I'll post results for fellow nx6310 users.

---

### Post by shanepardue on 2006-11-18
I tried Ndiswrapper, but it didn't help. I saw somewhere say that I had to 
patch my kernel with [this]("http://www.linuxant.com/driverloader/wlan/downloads-patches.php") patch. Could someone guide me on how to do that?

Thanks!

---

### Post by nyinge on 2006-11-20
> **shanepardue said:**
> I tried Ndiswrapper, but it didn't help. I saw somewhere say that I had to 
patch my kernel with [this]("http://www.linuxant.com/driverloader/wlan/downloads-patches.php") patch. Could someone guide me on how to do that?

Thanks!

I don't believe that patch is required for Ubuntu.  AFAIK, Fedora's kernel needs that patch, but that was a couple of years back.

If you still want to continue trying with Ndiswrapper, I'll help you out with your problems.  But I'm not sure of how to troubleshoot the problems with the firmware shipped in Ubuntu.  

So, what's not working out for you with ndiswrapper?  Post the errors that you're getting.

---

### Post by shanepardue on 2006-11-20
Well, my first question is for Ndiswrapper, do I have to remove the driver 
that gives me the little connection I have now? I've tried ndiswrapper 
without removing any driver first and it didn't change the connection speed.

---

### Post by nyinge on 2006-11-20
> **shanepardue said:**
> Well, my first question is for Ndiswrapper, do I have to remove the driver 
that gives me the little connection I have now? I've tried ndiswrapper 
without removing any driver first and it didn't change the connection speed.

Yes.  Append the following at the end of the file /etc/modprobe.d/blacklist  :
```
blacklist bcm43xx
```
Don't forget that you have to be root or use sudo to edit that file.  Save the file, then, reboot.

---

### Post by shanepardue on 2006-11-20
Cool. I think I got it working. I'll let you know if I have a  
problem once I run it a little more. Thanks for your help!

---

