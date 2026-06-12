---
title: "Ubuntu CD Will Not Boot on iMac G3 333mhz (Tray Load)...What other options do I have?"
date: 2007-11-11
forum: Apple PPC Users
---

### Post by Luigi239 on 2007-11-11
Hello everybody. I am trying desperately to install Ubuntu 7.04 on an old iMac g3 for use as a jukebox with Banshee. Only problem is I cannot get the thing to boot from the install CD. No matter what I do, it just won't boot, and boots into OS 9. (After holding the C key down for about a minute) I have burnt about 15cd's from many difrerent images, and none of them have worked. The strange thing is I have been able to boot from an old OS 9 CD which works fine. Also, if I put in an Ubuntu CD after OS 9 has loaded, the Computer can read them.

Anybody have any ideas? Is it possible to boot from USB, no matter how slow?

Thanks

EDIT: Also, how could I go about doing a Netboot Install?

---

### Post by Midwest-Linux on 2007-11-11
I had a problem installing Ubuntu on my G3, my issue was a little different...but I must ask...did you use the PPC version?, did you use the Alternate installer ? burn the ISO at the slowest speed? If so read on....the post below is from the summer of this year from my post here on the Apple PPC Users forum.....hope this is of help.....

--------------------------------------------------------------------------------------------------------------------------




MYSTERY SOLVED or another episode of "As The Hard Drive Spins"

First off a big thank you for solving my problem! This has to be one of the most fustrating and mind numbing projects I have ever run into. I don't just have one video output, I have two. This is the kicker, I have been trying to install Ubuntu using the bottom (one of the two) video outputs.

I kept using the bottom one without even noticing the top one, without even thinking that this was a video output too! Why the heck would anyone have two video outputs is beyond me. See I figured that output has to be for something else because the bottom one is the video one and thats it. And even then who would have thought that both video outputs react differently!

It gets better, I had pretty much shelved the project until i had more time and I was going to try a different approach. I was going to try Yellow Dog 5.0 as my next option and if that did not work, then try Yellow Dog 3.0. I took the G3 out of the spare room again to get ready to burn the Yellow Dog ISO's and something told me to look at these posts again and I saw your post about the placement of the video cards.

I figured OK, yes i see TWO outputs and let me see if I can get video out of the other output (the top most one). So at this time I had the Mac OS 9.0 was running, I unplugged the monitor from the bottom output, and plugged it into the top one. well guess what? .....Well there was Mac OS 9.0 too! Why two video outputs? Surely they would be the same anyway...right? So then I figured It doesn't hurt to try again to attempt to install Ubuntu 7.04 using the alternate disc like I tried so many times in the past.

With the Ubuntu 7.04 Alternate disc into the CD Rom Drive, hold down C and hit power on. Now I have the monitor plugged into the top output. So the machine starts up and the screen goes white, blue and black...and then TEXT from the 7.04 Alternate Disc installer!

Yep that was the problem, There are TWO video outputs on this computer, they both WOULD display Mac OS 9.0 the same , but on boot or prompt or text one output would mute or go dark, and the other one would display it (the top output!).

Right now I am installing Ubuntu 7.04 on this machine. I hope I have enough HD space as it is only 3.2 gig. I am still installing the Ubuntu 7.04 and its at the point where it is installing "select and Install Hardware". Thanks to everyone else for their support and quick responses...I am sure I will have to do some tweaking and changing things and maybe adding another Hard drive at some point and all that should be a piece of cake compared to what I spent in hours, days and over a week of trying to get this running.

Hey, please by all means throw this solution in with the Installing Ubuntu thread, it very well could help others from this problem.

Again, thanks to everyone and a big thanks to pxwpxw and Tonyr for helping to solve this mystery.
__________________

---

### Post by Luigi239 on 2007-11-11
> **Midwest-Linux said:**
> I had a problem installing Ubuntu on my G3, my issue was a little different...but I must ask...did you use the PPC version?, did you use the Alternate installer ? burn the ISO at the slowest speed? If so read on....the post below is from the summer of this year from my post here on the Apple PPC Users forum.....hope this is of help.....

-------------------------------------------------------------------------------------------------------------------------

Yes, I have tried every install type under the sun, all are PPC. I even tried some Fedora and none of those worked either. Also, thank you for taking the time to find the solution, but I only have one video output, as well as when the Ubuntu Disk fails, it takes me to OS 9 and says it can't read this CD, and wants me to initialize it.

Thanks for the help though. :)

---

### Post by oswaldkelso on 2007-11-11
> **Luigi239 said:**
> Hello everybody. I am trying desperately to install Ubuntu 7.04 on an old iMac g3 for use as a jukebox with Banshee. Only problem is I cannot get the thing to boot from the install CD. No matter what I do, it just won't boot, and boots into OS 9. (After holding the C key down for about a minute) I have burnt about 15cd's from many difrerent images, and none of them have worked. The strange thing is I have been able to boot from an old OS 9 CD which works fine. Also, if I put in an Ubuntu CD after OS 9 has loaded, the Computer can read them.

Anybody have any ideas? Is it possible to boot from USB, no matter how slow?

Thanks

EDIT: Also, how could I go about doing a Netboot Install?

Read this thread lots of info re early imac problems 

[URL="http://ubuntuforums.org/showthread.php?t=605522"]
http://ubuntuforums.org/showthread.php?t=605522[/URL]

---

### Post by Luigi239 on 2007-11-11
Hey, thanks for the replies guys, but I actually solved my own problem.

After it refused to read my OS 9 disk, I took a qtip dampened with glasses cleaner and rubbed it on and around the lens of the CD drive, and dried it with the other side of the qtip. Turn it on, and first try, it boots from the CD :P

Thanks everybody.

---

