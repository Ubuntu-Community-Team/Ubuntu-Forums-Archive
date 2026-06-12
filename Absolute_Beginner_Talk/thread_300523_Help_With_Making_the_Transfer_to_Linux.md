---
title: "Help With Making the Transfer to Linux?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by autumnsfallxx on 2006-11-15
I've heard alot of good things about ubuntu, so I decided to rest my feet here. Hopefully people aren't negative here and can help me.

I've been reading and researching linux most of the day today, and I've learned alot compared to this morning and knowing nothing. Cut to the chase, I have yet to make a transition. I'm in the process of determining whether my computer's hardware is ubuntu compatible.

This should be the part I explain the hardware of my computer, but I'm unsure which drivers I really need to worry about in this situation (I'm currently trying to research whether my mobo is compatible, perhaps I'm not searching correctly). But I have a link  to my exact computer model: 

[http://www.epinions.com/Sony_VAIO_PCV_RS710G_PC_Desktop/display_~full_specs](http://www.epinions.com/Sony_VAIO_PCV_RS710G_PC_Desktop/display_~full_specs)

I hope that helps.. I'll be monitoring this thread pretty closely in hopes of some answers. I also ran Belarc Advisor for my exact system specifications (if that is needed), but I was unsure what to post without incriminating myself.

Cheers :-D

---

### Post by yurtfg89327tfg0o on 2006-11-15
It looks OK although I'm not sure about the integrated graphics.
Do you have an Ubuntu CD?
If so you can just boot the CD and 'pretend' to use Linux. Nothing will be installed to your hard drive.
It's a great way to try things out and its totally safe.

---

### Post by halitech on 2006-11-15
I've looked over the specs that are on the link and the only 2 things I'm seeing that might be an issue is the media card reader (haven't heard anyone geting them working) and it doesn't really say what model your NIC is. My best suggestion would be to try to boot the live cd and see if everything works (Interl video seems to be an easy way to get video so no worries there) and go from there.

---

### Post by Linuturk on 2006-11-15
I have a similar Intel Graphics Chipset, and was very happy to have Direct 3D rendering out of the box with Dapper and Edgy.

---

### Post by ljpm on 2006-11-15
> **halitech said:**
> ... might be an issue is the media card reader (haven't heard anyone geting them working)...

Here's my specs,
[http://www.cisnetpc.com/spec/spec_ca-8001b%20c102.pdf](http://www.cisnetpc.com/spec/spec_ca-8001b%20c102.pdf)

I installed 6.06 (4 or 5 times :) ) and subsequently 6.10 and never had an issue with the media reader. Trouble with video and an added TV card yes, but, media reader worked fine with basic install (i386).

---

### Post by halitech on 2006-11-15
> **ljpm said:**
> Here's my specs,
[http://www.cisnetpc.com/spec/spec_ca-8001b%20c102.pdf](http://www.cisnetpc.com/spec/spec_ca-8001b%20c102.pdf)

I installed 6.06 (4 or 5 times :) ) and subsequently 6.10 and never had an issue with the media reader. Trouble with video and an added TV card yes, but, media reader worked fine with basic install (i386).

ok, haven't had much experience with them and the people I have heard with them haven't had much luck so I guess you proved me wrong which I don't mind at all :D

---

### Post by pissedoffdude on 2006-11-15
You should download a copy of ubuntu and try the livecd to check if your hardware is compatible

---

### Post by autumnsfallxx on 2006-11-15
Thanks for the help so far guys.

Okay I have downloaded the .cdi and burn it to a cd (I use Padus DiscJuggler and have used this countless times for burning sega dreamcast homebrew software.. so I'm pretty confident I've burned the image correctly). It won't boot the live cd. I doubt the cd is the problem though.

I don't think the option to boot from a cd drive is checked on my bios screen.. which should be an easy fix right? Yeah, we would hope.. and this is one reason why I'm trying to stray about from winblows in the first place.

According to every thing I have found I should just hold down the 'f2' or the 'f3' key during startup to access the bios screen for a sony vaio. Well I'm not sure if it is because I am using a Microsoft Wireless Comfort Keyboard 1.0a or what.. but this does work.. and I've tried every bios key I've ever had to use on a computer including those.

Any ideas? is there a way I can access the bios key through another medium? Am I just going to be stuck waiting on the phone for 3 hours for Sony Tech Support?

---

### Post by pissedoffdude on 2006-11-15
as soon as you turn on your computer and you see the splash screen try pushing delete

---

### Post by eighthate on 2006-11-15
at what speed have you burnt the iso?

---

### Post by autumnsfallxx on 2006-11-15
I tried the 'delete' key.. alas, no such luck. I think I tried that before too, but no guarantees. Thanks for the help though. Anyone else with any ideas? I'm pretty desperate.

I think I burnt the image at 4x. I usually burn them slow so I know I won't have errors. I think that is about the slowest option I have too.

---

### Post by autumnsfallxx on 2006-11-15
Well, if nobody has a clue on how to access the bios screen..

Then maybe I should try something else. I was thinking it may be a good idea to try to boot from a thumbdrive? How would I go about this? It is possible, isn't it?

---

### Post by seshomaru samma on 2006-11-16
What I sually do is try to push all of the F buttons during the first few seconds of boot , if you want to be scientific you can try pressing each one seperately , if any of the f keys dont work , try Esc and Delete and backspace. 
You can also try to google BIOS and your computer model, its not really an OS related question.
I think it would be easier to find how to enter the BIOS than boot from a thumbdrive.
BTW- do you have a Windows CD or any other bootable CDs? Can you boot from them?

---

### Post by autumnsfallxx on 2006-11-16
I always approach google before polling the audience. I use a Sony Vaio PCV-RS710G and it said that the Vaio bios usually redirects with either 'f2' or 'f3' but neither of those worked. Problem is, I know I've been in this boat before.. I needed to alter my bios for whatever reason for my Windows setup probably 6 months ago. Here I am again.

I thought maybe I could try burning the image with alcohol 120% instead of DiscJuggler Pro like I was using. For some reason, it won't burn within 120 properly. It always has an error within the first 45 seconds and then asks for another disk to burn to. Although the live cd is plenty small enough to fit onto a cd.

Maybe it was the setup I used in 120? I'm far more familiar with DJ than 120. I used DAO TAO at 4x. Am I doing something wrong?

I HAD bootable cds. Then I lost my Windows. My computer actually shipped with a recovery disk. Would that count? I was being stupid and installing pirated Windows Media Center and got a corrupt download.. and for whatever reason my Windows ended up being partitioned Media Center and Professional. So I had to start over.. As I did this. I guess Media Center altered whatever registry I needed and my recovery disks became coasters.

I should have researched Sony before going Vaio. Most companies will allow a download of the recovery disk over the internet. Not Sony. They wanted me to cough up $40.00. I'm tired of the money ploys of Microsoft and Sony. My cpu came with a cable tuner on it. I haven't really researched linux for compatiblity as of yet. I also have a remote and remote sensor that came with the package.. which I also have YET to research. I'd be willing to sacrifice those to get away from this. I've been hacked, infected with spyware, infected with viruses, and paid thousands for too long.

Maybe (this is probably me speaking out of rage), I'll just skip the live CD and dive right in.

---

### Post by pissedoffdude on 2006-11-16
> **autumnsfallxx said:**
> I always approach google before polling the audience. I use a Sony Vaio PCV-RS710G and it said that the Vaio bios usually redirects with either 'f2' or 'f3' but neither of those worked. Problem is, I know I've been in this boat before.. I needed to alter my bios for whatever reason for my Windows setup probably 6 months ago. Here I am again.

I thought maybe I could try burning the image with alcohol 120% instead of DiscJuggler Pro like I was using. For some reason, it won't burn within 120 properly. It always has an error within the first 45 seconds and then asks for another disk to burn to. Although the live cd is plenty small enough to fit onto a cd.

Maybe it was the setup I used in 120? I'm far more familiar with DJ than 120. I used DAO TAO at 4x. Am I doing something wrong?

Have you tried booting off another cd such as a windows cd to check if your bios is configured to boot from the cdrom drive

---

### Post by autumnsfallxx on 2006-11-16
I will first thing in the morning and update this thread and let you know the status. I really do hope this is my error and I can just get around not knowing the bios key again.

Composition I in the morning :-| Yes, time for sleep.

I'd like to thank everyone with a response for... well.. your response :D  It's very appreciated. I love how helpful you guys have been! I always heard the linux community was much more helpful than Microsoft ever thought about being. But, I didn't imagine I'd ever get sometimes 2 or 3 minutes until a response in a forum!

Thanks again and cheers,

---

### Post by aktiwers on 2006-11-16
You dont happend to have a Logitech Keyboard with F-Luck button ?
If so, try pressing that button and then the F keys..  

I always forget that stupid button..

---

### Post by seshomaru samma on 2006-11-16
> **autumnsfallxx said:**
> . My computer actually shipped with a recovery disk. Would that count? .

I dont know about Vaio but I think it should be a bootable CD. If you can boot from the recovery disc it will show your Bios settings.

---

### Post by Castigate on 2006-11-16
Hi, I'm not sure if it will work but why don't you create a bootable floppy disk.  If I remeber right in win xp you can make it from control panel add/remove programs.  It's a link on the left side of  window.  Then reboot with disk to dos.  Then maybe someone on this board can tell you how to run the cd from dos.

---

