---
title: "Recommendations partition size, structure etc."
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ccfjeff on 2007-09-08
Hi,

I've gradually been putting the pieces into place to get started with Linux.  I got a new (used) computer with more memory & speed, have been running the LiveCD of Feisty Fawn for a little while, and got a large new USB2 external drive.  

Because of programs I need for my work I won't be able to completely ditch Windows.  I would like to eventually set it up using Linux for my main operating system and using a virtual box to run the necessary Windows programs.  For now, however, I think I'll try to set it up as a dual boot system so I don't have to try and learn too many things at once, and can see how well things work etc.

I'm not sure, however, whether I should partition my one and only 80G internal IDE hard drive to hold both Win XP-Pro which is pre-installed on the Dell AND Ubuntu, or whether I should just let Windows keep that drive to itself and partition the external 500GB USB drive to hold Ubuntu and data for both operating systems.

The system currently has 1GB of RAM with 2GB max if upgraded.   The computer I have been using has ~376 MB RAM and it seems to bog down with Win XP at times.  Firefox seems to grow in RAM usage the longer it's open and occasionally gets up over 200MB.

I would like to set up and use a database, a bit of word processing, minor spread sheet stuff and a few company specific programs.  Much of my work is interacting with other companies over the web.  Some of them require the use of Internet Explorer only.

I also have quite few pictures I have stored on the hard drives on my older computer and I would like to do a bit of photo editing, touching up etc.  I would also like to do some video capture if I could, but haven't done so yet as I don't have a video capture card and I didn't have enough memory to run [Media Portal]("http://team-mediaportal.com/") on this computer for screen captures etc.

I also have done a bit of recording & minor editing of live stream audio, primarily of college sports.

Any recommendations would be most appreciated.

I just made a GParted copy of my "C:" drive on the newer computer.  I've been afraid to make any changes or even use it until I had a backup as on my older computer the hard drive had crashed and like the newer one, it didn't come with a CD for the OS.  I'll probably try to make a PartImage copy as well before starting just to be safe, assuming I can figure out how to do so.

Thanks again for any help/recommendations.

---

### Post by alan_daniel on 2007-09-08
I don't know if I can offer much help, but reading through your post brought two things to my mind. First of all, if your firefox ends up using >200MB of RAM when it's left open, it sounds like you have some sort of memory leak in it. Do you have any extensions installed on it? Some of them are notorious for their poor use of memory.

Second, I can say from my own experience that installing on an external hard drive is a viable option, as long as your computer's BIOS can handle booting from USB (it would have to be fairly old not to have that capability). Here's a post about it: [http://ubuntuforums.org/showthread.php?t=531554&highlight=install+external+hard+drive]("http://ubuntuforums.org/showthread.php?t=531554&highlight=install+external+hard+drive")

---

### Post by chrome307 on 2007-09-09
You need to make up your mind and be specific in your needs.

What difference does it make to you how your PC boots ie to Windows or Ubuntu?

Linux is not too hot for media tools and this is an area that it is lacking in.

If you do not have a capture card your doing a lot of 'supposing'

Be more specific in your requests and be realistic with your hardware/software.

You seem to be hanging between a wish list (buy more hardware) for hardware/softare.

---

