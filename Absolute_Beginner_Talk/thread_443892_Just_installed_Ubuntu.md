---
title: "Just installed Ubuntu"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-05-14
Hey, I just installed Ubuntu on my other PC and I need help with a few things;

When I insert a burnt DVD disc into to my dvd drive and double click on the drive in "Computer" it comes up with a message saying that there is no media in the drive...however when I insert genuine disks it has no problem.


I'm still getting used to Ubuntu, hoping it will be faster when I reformat since it was running slow I am re-formatting it with a random binary pass so it'll take some time so is there anything I should know about Ubutnu :)?

I mostly just surf online, gamble, torrent and I use a lot of proxies/vpn servers...do you think I will have any problems doing these things :p?

Thanks!


Regards;

---

### Post by jfinkels on 2007-05-14
> **tarchy said:**
> Hey, I just installed Ubuntu on my other PC and I need help with a few things;

When I insert a burnt DVD disc into to my dvd drive and double click on the drive in "Computer" it comes up with a message saying that there is no media in the drive...however when I insert genuine disks it has no problem.


I'm still getting used to Ubuntu, hoping it will be faster when I reformat since it was running slow I am re-formatting it with a random binary pass so it'll take some time so is there anything I should know about Ubutnu :)?

I mostly just surf online, gamble, torrent and I use a lot of proxies/vpn servers...do you think I will have any problems doing these things :p?

Thanks!


Regards;

Does wiping your hard drive before formatting it really make it faster?

I would say either the burnt DVD is no good, or perhaps Ubuntu doesn't like it because you burned it at too high a speed. Maybe try burning it again at a lower speed?

For lots of great information go here: [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) and here: [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by earobinson on 2007-05-14
> the drive...however when I insert genuine disks it has no problem. Im not sure I understand what a genuine disk is.

> I mostly just surf online, gamble, torrent and I use a lot of proxies/vpn servers...do you think I will have any problems doing these things ? Assuming you use the websites to gamble and not the installed versions there should be a new problem.

If you want to be a real pro look into using wine to install your gambling windows programs.

---

### Post by earobinson on 2007-05-14
> **jfinkels said:**
> Does wiping your hard drive before formatting it really make it faster?

I would say either the burnt DVD is no good, or perhaps Ubuntu doesn't like it because you burned it at too high a speed. Maybe try burning it again at a lower speed?

For lots of great information go here: [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) and here: [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
No I dont think it will, I compleatly missed that.

---

### Post by starcraft.man on 2007-05-14
> **tarchy said:**
> Hey, I just installed Ubuntu on my other PC and I need help with a few things;

When I insert a burnt DVD disc into to my dvd drive and double click on the drive in "Computer" it comes up with a message saying that there is no media in the drive...however when I insert genuine disks it has no problem.

Ummm, I don't know what you mean by "genuine disk". Can I ask if you burned these disks with Vista? If so did you use the default setting and burn with their stupid live file system? If thats the case, they are all incompatible... stupid MS messing with standard formats. If you didn't use vista, I assume it has to do with how they were burned... how did they get burned?

> **tarchy said:**
> 
I mostly just surf online, gamble, torrent and I use a lot of proxies/vpn servers...do you think I will have any problems doing these things :p?

Thanks!

Regards;

Nope, you can do all those things on Ubuntu with relative ease. We even have tor in the repos if your aiming at anonymity on the net... (I assume from proxy/vpn)

Edit: grumble, 3 posts down... arg >.>

---

### Post by tarchy on 2007-05-14
Thank you for the swift replies;

I don't think it will make it that much faster but it was running very slowly compared to Windows S2 so I presumed it might :)

I have heard about Wine...not sure how it works. Is it hard to install/work?

By genuine disk I mean not burnt and I burnt the disk with Nero.

---

### Post by tarchy on 2007-05-14
Yeah, I sometimes use Tor but I would rather stay on a VPN with one IP not a program that switches every 5 seconds :D

---

### Post by icechen1 on 2007-05-14
> **tarchy said:**
> 
I don't think it will make it that much faster but it was running very slowly compared to Windows S2 so I presumed it might :)


Did you install the video card drivers if you have an ATI video card  or NVDIA video card ?

---

### Post by tarchy on 2007-05-14
> **icechen1 said:**
> Did you install the video card drivers if you have an ATI video card  or NVDIA video card ?

Nope. I thought Ubuntu wouldn't support the drivers..

---

### Post by starcraft.man on 2007-05-14
> **tarchy said:**
> Nope. I thought Ubuntu wouldn't support the drivers..

[Envy]("http://albertomilone.com/nvidia_scripts1.html") is your friend then when you reinstall. Download 0.9.3 debian, double click it and install. Go to Applications > System Tools > Envy. Then select automatically install (nvidia or ati drivers). The answer yes to any prompts and reboot at end. You should see graphical improvements when you have your drivers working.

---

### Post by ccesare on 2007-05-14
Well, you need to make sure you have the correct versions of the drivers. What kind of video card do you have?

---

### Post by tarchy on 2007-05-14
Thank you very much :)

I will keep you posted on upcoming errors which I am sure to have :p

---

### Post by jfinkels on 2007-05-14
> **tarchy said:**
> 
I don't think it will make it that much faster but it was running very slowly compared to Windows S2 so I presumed it might :)


Wiping your disk should have no effect on the perceived 'speed' of your system. When you formatted your drive to install Ubuntu the first time, you lost the ability to access the bits that made up the original file table from your Windows install. Since you're now using a different filesystem (ext3) and therefore a different file table, your system will simply overwrite whatever bits comprised your data from the Windows NTFS filesystem. Your hard drive couldn't care less about the state of the bits on the hard drive: it can't read them until you write a file to them anyway.

That explanation may have been a little convoluted, but the summary is this: wiping your hard disk is only useful if you want to destroy (relatively securely) data. I don't see how it would affect the speed of your system. Most likely your problem is video drivers as starcraft.man and others suggest!

---

