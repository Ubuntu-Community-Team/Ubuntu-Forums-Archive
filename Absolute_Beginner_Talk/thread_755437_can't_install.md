---
title: "can't install"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Sanoski on 2008-04-14
I went to books-a-million and bought The official Ubuntu Book. I love this book! Unfortunately though, the included DVD wont work. I put it in my CD tray, shut down my computer, and Windows loads normally. I followed the books advice, and I checked my BiOs settings. Sure enough the hard drive was set to boot first, so I raised it up the hierarchy. Saved the setting and shut did a restart. And behold! Windows loads as usual. I messed around with it for awhile. Then came to the conclusion that I should do a system restore. I wiped all my files and started from how it was when I bought it. 

Now I try it, and it either wont load at all, or it just loads into windows as usual. I even tried hitting the escape key as windows starts, and then trying to force it to boot from the DVD. Still no luck, in fact when I do that it wont load windows at all. It'll just go to that black screen where you either select "Start Windows Normally, Safe Mode, Safe mode with command prompt" ... etc. If I keep these setting and try and force it to boot from that disk it'll just keep going back to that screen. 

That's when it hit me. Maybe there is something wrong with the disk. So I downloaded the ISO, nd I tried to burn it. Guess what? That's right! It wont burn!! It'll burn for 4 to 10 seconds and then eject the disk. I tried several different ISO files from several different locations. I did the hash check, everything went fine. It just wont burn the disk. I tried it from every burn speed I had. 

Now here is the weird part. That partly burned ISO file, if I were to put it in my drive, the Ubuntu splash screen pops up! I almost fainted. But then it disappeared. Obviously because it wasn't the whole disk. I used to be able to burn ISO files perfectly fine. But today nothing has worked right. You guys have no idea how much I'd appreciate some assistance on this one. Do you have any idea how frustrating it is to have a brand new toy, and you can't get the damned thing turned on? Gosh! It's the simplest of things that get to you.

---

### Post by sowelie on 2008-04-14
Dumb question, do you have a DVD drive (could that be why the DVD won't work).  Also, when you edited the BIOS were the settings actually saved?  Go back in and make sure.  As far as the burning goes it sounds like either your burning software is no good, or the drive is hosed.  I have had no trouble burning any of the ISOs.  What burning software are you using?

---

### Post by Sanoski on 2008-04-14
I have a CD - RW, DVD ROM. I'm not trying to write to the disk. I just want to read from it. DVD ROM would seem sufficient. I wish it was that simple. I'd just go buy a new drive. But I don't want to if it's not needed. 

And yes, as I stated: I saved the BIOS settings and then restarted. If the drive is toast, how come it can still burn CDs? 

As for the burning program I'm using. I followed the guidelines on the How to burn ISO page. I downloaded InfraRecorder.

---

### Post by Sanoski on 2008-04-14
Is there a way to work around this?

---

### Post by alzie on 2008-04-14
Try a DVD movie.  If it works its a bad disk.  Take the book back and try to exchange. If it doesn't work its a drive issue.  You could still download and burn an iso tho

I hope this helps :)

---

### Post by bumanie on 2008-04-14
Firstly, make sure you are burning the iso at a slow speed and make sure you are choosing to burn an image, not a data cd. Secondly, it might be a good idea to download the alternate install cd which is a text based installer and often will install on computers when the live cd/dvd won't.

---

### Post by Sanoski on 2008-04-14
I returned the book I bought and exchanged it for another. Still having the same problem. I tried ISO Recorder, and it went further than usual. About 8%. Then it spits it out. Like I said, I've tried every speed on the list. And yes, I'm sure I'm burning an ISO. I'll try the alternative and see what happens.

---

### Post by Sanoski on 2008-04-14
Oh, and by-the-way. DVDs, most of them, play fine.

---

### Post by Sanoski on 2008-04-14
tried alternative ISO at a speed of 8. Same story. It burns a little and then spits it out. At least ISO recorder gives me an error, though. The other one just says "task complete".

ISO recorder says,

"Operation has failed. Code 8004020e, reason: a generic error occurred." 

Any idea what this means? I even tried with different Linux distributions, and I'm still exactly where I started.

---

### Post by bumanie on 2008-04-15
This is the only site I can find that may help, unfortunately, none of the links seem to operate anymore. [http://www.tutorials-win.com/MediaPlayer/Cant-burn-128830/](http://www.tutorials-win.com/MediaPlayer/Cant-burn-128830/)
What are you trying to burn the iso with? Why not try deep burner free or nero or go to a friends house and try their computer/burner. The little bit on the above site indicates it is an error that occasionally occurs in windows media player, but as there is so little about it on the internet, it seems to be a rare error. May be a new dvd burner would be in order. Have you checked out whether you can get a firmware upgrade for your cdrw-dvd rom? That may work if one is available.

---

### Post by Pasty-Flawss on 2008-04-15
noob comment : Er.. I only skimmed the post but this maybe what your looking for. Restart comp as soon as computer turns on press F2. (goes into the Setup menu Note: It may not be as soon as the computer turns on) then press right and go into boot. then you can put in start up priorities. highlight the CD/DVD one and press F6 this should put your CD/DVD one first in priority. then press escape and save changes. Hope this helps :)

---

### Post by 3rdalbum on 2008-04-15
If your drive is failing to burn, and not recognising discs on bootup, then there's something wrong with it. A CD or DVD burner doesn't care whether it's a Linux distribution, a movie, or a Bill Gates autographed copy of Windows Vista Ultimate: It will burn or boot unless there's something wrong with it.

---

### Post by Sanoski on 2008-04-16
The weird thing is CDs and some DVDs play fine. Every once and awhile there's a DVD it doesn't recognize though. Could there be some kind of codec I'm missing? Keep in mind; I just did a system restore, and the distribution on this DvD is significantly older. 

As for why it wont burn ISO files. I'm thinking oldboy is right. It has to be my CD drive. And if that's what's wrong then maybe I can just replace it and things will be peachy. However, it still doesn't really explain why it works for other stuff. I guess because it's such a sensitive file. Burning MP3s is easy. I've manged to burn ISO's before, but my computer was way younger then. It's going on 6 or 7 now. 

Anyway, thanks for all you guys help. I guess this one is pretty much handled. It's most likely my CD drive. In fact, it's probably a combination of various things.That's why we can't pinpoint it. My computer is doing some weird things, so not booting from disk, and not being able to burn ISO's shouldn't surprise me. My monitor is still acting up too, and I pulled that Nvidia mx 4000. I even did a system restore. When I restart, 98% of the time the monitor stays black. I'll have to turn it off again, turn it on, turn it off, turn it on, turn it off, over and over. A new piece to the puzzle revealed itself though. I hear the Windows startup theme (even though it doesn't always show). The monitor is black, but the system is on, and it boots into Windows normally. So that's telling me it's either one or two different things. It's either the monitor, or the cord has gone bad.

So I guess that's where I stand. I need a new CD burner. I'll probably just get a DVD/CD RW reader/writer combo. After the boot from disk, and writing ISO files is fixed, I must determine why the monitor is screwing up on restart. It looks like if the monitor was bad, it would be messing up more often than just when I restart, so that's kind of throwing me off. But what else would it be? It's not the video card, and I don't think the hard drive would make it do that. Yea, it has to be either the monitor or the cable. I'll try the cable first. If that don't work, I'll try replacing the monitor. And if that don't work, I might as well just build a new computer!

Thanks for all your help everyone. This community rocks. I'm sort of broke right now, but as soon as I get things working I'll post the results and what the problem was, in case anyone else has this problem, they'll know what it was.

Sincerely,
Sanoski

---

