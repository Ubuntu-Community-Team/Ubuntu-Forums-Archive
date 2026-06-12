---
title: "Unzip is slow + No progressbar"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-11-11
I regulary get confronted with large zipfiles (600Mb plus). Now I found that unzipping seems to take longer than in Windows. Now, I know that my current machine is lower spec than my windows machine, so that might be the problem. But if there is a program that is more efficient than the basic archivemanager that is built in, that would be very nice.
Just for reference, unzipping a file of 396mb took 3 minuts.
Spec: XP1800 with 768mb ram. Now this is way longer than I am used to on Windows. The unzipproces also doesn't seem to take up much of the processor power. Maybe there I can tweak something. 

The other thing that bothers me, is that I don't get a progressbar. I get a bar that goes from left to right, but no percentage and no visual progress. Again, any other way to do this so I see progress.

---

### Post by 3rdalbum on 2006-11-11
You could try "re-nicing" the Archive Manager program (which is actually called File Roller). Go to System > Administration > System Monitor and find the file-roller program there. Right-click on it, choose Change Priority, and move the slider a couple of notches to the left.

I always get a proper progress bar when using large archives, so I don't know what the problem could be. Do these archives have more than one file in them?

---

### Post by Belgatom on 2006-11-11
> **3rdalbum said:**
> You could try "re-nicing" the Archive Manager program (which is actually called File Roller). Go to System > Administration > System Monitor and find the file-roller program there. Right-click on it, choose Change Priority, and move the slider a couple of notches to the left.

I always get a proper progress bar when using large archives, so I don't know what the problem could be. Do these archives have more than one file in them?


Hmmm, I am running Dapper with Beryl on top. When I unzip, it hardly uses 5% of the resources, while in windows, it soaks up as much as it can. 
I did as you told and put fileroller's "niceties" (what a word) up to -10, whatever that means but that didn't seem to help much. I upped it all the way to -20, without really  noticing a difference. 

Maybe I should do this via the terminal, I probably will at least see a progress there. How would I do that?  

This is a bit of a disappointment. This pc was more efficient with the heavy work under XP. I am sure I must be doing something wrong or else my expectations are too high...

---

### Post by Belgatom on 2006-11-14
OK, let's bump this baby. 

I've figured out that the speed is correct. It's just I was so used to my PIV 3.2 1 Gig Mb machine that decompressing on this XP1800 768Mb machine is slower. So no problem there. 

But I am still not having a nice progressbar when I decompress different files. I deal mainly with zips of large sizes (700Mb or higher). 

Two screenshots show you what I have and what I expected. 

[IMG]http://users.telenet.be/belgatom/ubuntu/uncompress.jpg[/IMG]
This little bar just slides from left to right like a silon's singular red eye. Not telling me nothing, exept "I'm busy, leave me alone".

[IMG]http://users.telenet.be/belgatom/ubuntu/transfer.jpg[/IMG]
This is the bar I get when transfering a file from one folder to another. I clearly get progress information. It gently says: "hang on just a bit longer". 

Help please, it's doin' my head in...

---

### Post by Belgatom on 2006-11-15
That's the problem with a really popular forum. Threads fall to the third page after just one hour and I got exactly one extra view.

---

