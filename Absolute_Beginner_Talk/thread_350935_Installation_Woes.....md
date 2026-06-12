---
title: "Installation Woes...."
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Minker17 on 2007-02-01
I tried installing Ubuntu yesterday and it just froze during installation. Today, I have downloaded the alternate CD install and am trying that. After I picked OEM setup, the languages, and set up the alt+shift thing, I'm at a blue screen with a grey bar at the bottom. It's been like this for about 10 minutes now. Am I frozen?

---

### Post by Minker17 on 2007-02-01
Wow, this forum moves fast! anyway, it's been about 45 minutes now with no change in the screen....

---

### Post by ATAQ on 2007-02-01
Give more information in your posts,
What are the specs of the machine you are trying to install on, also what version of ubuntu are you installing?

---

### Post by Minker17 on 2007-02-01
Forgive my lack of info. 

I'm running a 733mghz P3, with 192mb of ram and whatever onboard videocard it has (I think that's my problem) and I'm trying to run 6.10.

---

### Post by Beej on 2007-02-01
Also did you check the MD5 sum? What speed did you burn the cd at?

---

### Post by amar2d4 on 2007-02-01
I have got the same problems.Mine is a Dell Optiplex GX520.P4 machine,256 MB RAM.30 GB HDD space.

Please,help.

---

### Post by ATAQ on 2007-02-01
You tried the alternative cd, in text mode, maybe see what beej is saying, could be that your burned it too fast, try burning at 4X

---

### Post by Minker17 on 2007-02-01
I will try it at 4x.

---

### Post by ATAQ on 2007-02-01
or, try server install and then "sudo apt-get install ubuntu-desktop"

I had to do that on my old machine

---

### Post by Sef on 2007-02-01
> I'm running a 733mghz P3, with 192mb of ram 

You really should up your ram to 256 mb.  Less than that, Ubuntu runs rather slow.

---

### Post by ATAQ on 2007-02-01
Sef is right, maybe considering an install from the Xubuntu team would be a wise option

---

### Post by lyceum on 2007-02-01
I would go with Xubuntu or Fluxbuntu with those stats.

[http://www.xubuntu.org/](http://www.xubuntu.org/)

[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by Minker17 on 2007-02-01
The slowest I could burn was 8x. I did that and put it to 256mb of RAM and it still didn't work. I tried text only and OEM and am recieving the same blue screen.

What options do I have now?

---

### Post by lyceum on 2007-02-01
> **Minker17 said:**
> The slowest I could burn was 8x. I did that and put it to 256mb of RAM and it still didn't work.

What options do I have now?

Try a different 'buntu.

---

### Post by Minker17 on 2007-02-01
I guess I'll try xubuntu. Is Ubuntu not working because of my specs?

---

### Post by Minker17 on 2007-02-01
Well, I downloaded XUbuntu. Just for the heck of it, I reformatted my drive to make sure it was clean and didn't have anything left on it (Mandrake/XP remains).

Anyway, the same thing happens to me that was happening when I was installing regular Ubuntu: The icon with the rat/mouse comes up with the bar under it, it goes back and fourth for a minute or two, then freezes. I've tried this in both the regular and safe graphics mode....

Should I just let it sit?

---

### Post by lyceum on 2007-02-01
The only thing I can think of is that it is a hardware issue, as in what you have just does not want to work with Linux. If you are burning the disk at 4x or slower, the disks check out and you have 256 mb of ram... I am stumped. Sorry. Maybe this will bump your question and someone else w/ more know how than me can help you :confused:

---

### Post by lyceum on 2007-02-01
wait.. is the live cd not working, or can you get the live cd up- but not install? 

if you can get the live cd up and not install, how many partitions do you have? If you can't even get the live cd up, don't worry about that, the number of portions would not be the problem.

I read somewhere that you may not be able to install if you have more than 4 portions... never tried though so can't say for sure) but I realized you already have Mandrake/Linux on your PC? so I REALLY can't figure out what the deal is... sorry again...

---

### Post by kicker334 on 2007-02-01
I've had the exact same problem. I reformatted both hard drives so there's only 1 partition on each drive, there's nothing on the drives. It locks up after it detects drivers then goes to a grey bar at the bottom of the screen with a blue background and I can type stuff but it doesn't do anything. I had installed Suse and Windows XP on the machine but this won't install. I downloaded the 451 mb file for the Server edition of Ubuntu. Can anyone help?

---

### Post by Beej on 2007-02-02
Sorry to ask this again, but I don't think you answered this first time round. Did you check the MD5 sum? I ask because i had similar problems with installing dapper a while back and it turned out that i wasn't getting spot on burns of my disk. Normally this isn't so much of an issue for music, files etc, but apparently it causes major problems with install cds. Turns out my CD burner was on its way out.  

I think there is an option to check disk integrity at the first screen that comes up after inserting the cd. Have you done that also?

If you have errors I suggest trying different media, a different cd burner, and or finding a way to burn at 4x or less.

Sorry if you've done this already.

Beej.

---

### Post by tuttle88 on 2007-02-02
> **ATAQ said:**
> or, try server install and then "sudo apt-get install ubuntu-desktop"

I had to do that on my old machine

Thanks, you solved my problem too.  And before I got a chance to as a question, that's very efficient.

---

### Post by Minker17 on 2007-02-02
Huzzah!! I got it working. I had my CD-Drive sitting outside of the case and as I was looking at it I noticed that it was made in May of 1997! At that point it occured to me that even though it is reading the burned cd, it might not be able to read all of it. Changed it out and it booted right up.

So the question now is should I run Ubuntu or xubuntu?

---

### Post by lyceum on 2007-02-02
Congratz!! :guitar: 

Start with Ubuntu, if it is too slow (after loading, the live CD is not the best test for speed) then go for Xubuntu, unless you like the Xfce DE better...

---

