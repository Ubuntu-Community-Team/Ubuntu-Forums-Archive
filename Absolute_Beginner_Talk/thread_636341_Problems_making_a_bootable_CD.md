---
title: "Problems making a bootable CD"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Valok on 2007-12-09
So I've spent almost the entirety of today trying to get a working bootable CD and I'm still at a loss and quite frustrated at the moment.

I've downloaded the .iso, its on my desktop, and I burned it to a CD using exactly what I was told to on the ubuntu wiki site using InfraRecorder.  However, when I turn my computer on, it just doesn't seem to want to boot, and I'm not at a loss as to why this might be.

---

### Post by drs305 on 2007-12-09
Can you view the contents of the CD (i.e. see files/directories)?

Did you run a checksum to ensure the ISO file is not corrupted?

Did you burn to disk at a reasonably slow speed?

Apologies if you did but those are common mistakes.

---

### Post by Valok on 2007-12-09
I cannot see the contents of the CD via my computer in windows explorer.

But I did burn at 4x, and I did do a check sum before burning it onto a CD

---

### Post by taurus on 2007-12-09
Have you checked your BIOS to make sure you have CD-ROM as your first boot device?

---

### Post by Valok on 2007-12-09
> **taurus said:**
> Have you checked your BIOS to make sure you have CD-ROM as your first boot device?

Yeah, Ive even gone so far so as to only allow my CD drives to boot.  I got en error telling me to use a proper bootable device, or to insert bootable media into my CD-ROM

---

### Post by mcduck on 2007-12-09
> **Valok said:**
> I cannot see the contents of the CD via my computer in windows explorer.

But I did burn at 4x, and I did do a check sum before burning it onto a CD

If you can't see any contents on the disk then it wasn't burnt correctly.

Actually inserting a correctly burnt Ubuntu CD on Windows should pop up a window that allows you to install some popular Open Source applications on Windows.

---

### Post by rkd on 2007-12-09
If you can't see the files on the CD in Explorer, you either misunderstood something in the directions or you have a bad CD-R or CD writer.  Have you been able to write CDs successfully on that computer recently?

---

### Post by Valok on 2007-12-09
Hmmm ok, then that is where my problem lies.  Is there any other program someone can advise to use other than InfraRecorder?  Because that is the one I've use and it obviously hasn't been working.

---

### Post by Valok on 2007-12-09
> **rkd said:**
> If you can't see the files on the CD in Explorer, you either misunderstood something in the directions or you have a bad CD-R or CD writer.  Have you been able to write CDs successfully on that computer recently?

I'm going to try burning with my other CD-ROM and see what happens.  As for recent burns, I haven't really done any.

---

### Post by taurus on 2007-12-09
[http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

---

### Post by CaptainInsaneO on 2007-12-09
In a windows environment I usually use Alcohol 120% to burn .iso files with. You have to burn it as an image.

---

### Post by Valok on 2007-12-09
Is there a certain type of write method that should be used?

I can chose things like 

Session at Once
Track at Once
TAO with zero pregap
And varios "raw" types

---

### Post by drs305 on 2007-12-09
In InfraRecorder, in Actions there should be an option to select Burn Image. That is what you want to use. If it is burned correctly you will be able to see the files in Explorer (if you are using windows).

---

### Post by CaptainInsaneO on 2007-12-09
Edit: Never mind, I left my brain at home today. Disregard this post.

---

### Post by Valok on 2007-12-09
> **drs305 said:**
> In InfraRecorder, in Actions there should be an option to select Burn Image. That is what you want to use. If it is burned correctly you will be able to see the files in Explorer (if you are using windows).

Yeah thats the way I've been going about burning all my discs today.

---

### Post by Valok on 2007-12-09
> **CaptainInsaneO said:**
> Edit: Never mind, I left my brain at home today. Disregard this post.

lol

---

### Post by drs305 on 2007-12-09
The psychocat's page uses InfraRecorder to burn the ISO. If you look at that page maybe you can pick something up you are doing differently. We're all pulling for you ;-)

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Valok on 2007-12-09
Thats actually the page that I've been following to try and get this set up =)  A great resource indeed.

Update: I just finished burning a disc, and when I try to open it to see whats inside it in windows explorer, I get an error message saying "E:\ Is not Accessible.  Incorrect Function"

---

### Post by Valok on 2007-12-09
The only thing I can imagine that is messing things up is my CD-ROM drives and maybe they just can't burn things correctly. 

Just ordered a CD so it should be in a few weeks.  Thanks for everyone's help and putting up with my noobishness.

---

### Post by CaptainInsaneO on 2007-12-09
Maybe you should grab another disc (if you have one laying around) and slap it in your CD ROM and see if it is even recognized. I have this strange feeling that your drive is going bad... could be wrong though (don't forget... brain's at home.) :lolflag:

---

### Post by Valok on 2007-12-09
I tried burning with a different program (nero) that has a data verification process at the end, I got the following error.

"Read errors from 0 to 354813
Data verification failed."


I have a more detailed log saved to my computer if that would be of assistance.

---

### Post by Valok on 2007-12-09
Also, when I put a blank CD into a drive, I get the same error message saying that the drive is not accessible, Incorret Function

However, when I put in my Starcraft CD, it does pick that up and I'm able to view it in windows Explorer

---

### Post by CaptainInsaneO on 2007-12-09
[http://support.microsoft.com/kb/315350](http://support.microsoft.com/kb/315350)

This may be of interest.

---

### Post by Valok on 2007-12-09
Good info, thanks!  Maybe Ill try DLing that installer that microsoft suggests.

Err, I think I read that wrong.  Apparently if you do get that error its because of said program.  But there must be other sources because I don't have that program installed on my computer.

---

### Post by CaptainInsaneO on 2007-12-09
Are you sure you don't have Roxio installed? It's oftentimes part of a bloatware package. Be sure to double check in Add/Remove Programs.

---

### Post by Valok on 2007-12-09
Read my mind lol, just got done doing that, and after looking up the error I was getting on google, I think I might have found a solution to the problem I was having.

---

### Post by CaptainInsaneO on 2007-12-09
If the roxio fix is a no-go, try the following:

1. Go to the Start Menu, then click on Run...

2. Type in "regedit" and hit the Enter key or click the OK button.

3. Once the Registry Editor is up, navigate through the folders at the left (by clicking the "+" signs) until you get down to this location: HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer

4. Click on that Explorer folder/key.  In the right side of the registry editor you should have an entry/value called NoCDBurning.  Double-click that name.

5. In the window that opens you will see a place for "Value data."  A 1 here enables NoCDBurning, meaning you will have NO CD burning.  This will definitely stop you from being able to use your CD-RW drive to write.  So if you have a 1 here (as I did) then this may be your problem.  Replace the 1 with a 0 to disable NoCDBurning, thereby enabling CD Burning.  (Sheesh!  Did Microsoft really have to go about this backwards?)  Click on OK.

6. Close the Registry Editor and Restart your computer

7. Report back and let me know

---

### Post by Jerry N on 2007-12-09
For what it's worth, I find  the useful life of a CD/DVD writer to be fairly short and I toss them when I start getting burn errors.  The last one I threw away was a Plextor that was just out of warranty.  On the plus side, these things are cheap.

Jerry

---

### Post by Valok on 2007-12-09
In the registry editor, I don't have an option named "explorer" under policies.  I only have Nonenum, ratings, and system

---

### Post by Joeb454 on 2007-12-09
Have you tried imgburn? I use that all the time...google it, it'll be right at the top IIRC

---

### Post by Valok on 2007-12-09
I think Im just gonna give it a rest for a while, been at it all day and Im only getting more and more frustrated

---

### Post by CaptainInsaneO on 2007-12-09
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer]
"NoDriveTypeAutoRun"=dword:000000ff
"NoCDBurning"=dword:00000000
```

Copy this into notepad and save it as explorer.reg

Make sure it doesn't append a hidden .txt extension.

Double click the resulting file, it will fix your problem with your drive.

I know you're frustrated buddy... I am too. It's crap like this that made me switch to Linux in the first place.

Edit: Don't forget to reboot after this.

---

### Post by Valok on 2007-12-09
Alrighty, after taking a small break Im back on trying to fix this, I've succesfully added the registry file you gave me, about to restart my comp.  After I do that should I be able to burn the iso correctly?

---

### Post by CaptainInsaneO on 2007-12-09
If you burn the iso how the tutorial is telling you then, yes it should burn correctly. :)

The reason you were getting the error that you were was BECAUSE you had no "explorer" folder in the registry, thus you had no key to fix. The reg file I gave you added the entire folder in for you, so the key is in there and everything, with the correct values to boot.

P.S. I'd like to tell you... I really admire your tenacity. You'll go far in the Linux world. :)

---

### Post by Valok on 2007-12-09
Awesome!!  Im running a burn now, prolly gonna take about 20 mins or so, then Ill be able to tell whether or not it worked.

Thanks a ton for helping me out through all of this, much appreciated =)

---

### Post by Valok on 2007-12-09
> **CaptainInsaneO said:**
> 

P.S. I'd like to tell you... I really admire your tenacity. You'll go far in the Linux world. :)


Thanks :)  This is how I've learned almost everything I know about computers.  Trial and error.  While frustrating at times, it certainly gets the job done, and you learn a bunch of fun things in the meantime too.

---

### Post by CaptainInsaneO on 2007-12-09
I learned computers the exact same way. Of course, starting out when I was five on an Apple IIe didn't hurt. :P

And now I do this for a living. :)

---

### Post by Valok on 2007-12-09
I've only started more recently, for the past 5-6 years now playing with computers.  I wish I could make a living out of it cuz I love doing it, but I have no clue what I would do =P

---

### Post by CaptainInsaneO on 2007-12-09
There's actually loads of things you can do with computers... lots of different jobs out there. You should PM me if you want to talk more about it.

How'd the burn go? :guitar:

---

### Post by Valok on 2007-12-09
Burn is still going, had to start it over cuz it came out blank on the 1st try for some reason.  Using a dif drive now tho, the one that I've been using for most of my other burns.

---

### Post by CaptainInsaneO on 2007-12-09
You're still using the iso that I linked to you earlier, correct?

---

### Post by Valok on 2007-12-09
I was actually able to get a dif iso from bittorrent just before you linked that one :lolflag:

But I'm pretty sure its a correctly DLed .iso cuz the MDsum came out correctly

---

### Post by stchman on 2007-12-09
> **Valok said:**
> So I've spent almost the entirety of today trying to get a working bootable CD and I'm still at a loss and quite frustrated at the moment.

I've downloaded the .iso, its on my desktop, and I burned it to a CD using exactly what I was told to on the ubuntu wiki site using InfraRecorder.  However, when I turn my computer on, it just doesn't seem to want to boot, and I'm not at a loss as to why this might be.

I have a tutorial on how to make a bootable CD using K3B.

[http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html)

You need a boot image.

---

### Post by 3rdalbum on 2007-12-09
This might sound dumb, but try burning a CD and then leaving it to cool down before trying to use it. I speak from experience on this one :-)

---

### Post by CaptainInsaneO on 2007-12-09
Hi stchman,

I've been trying to get him hooked up with Ubuntu for most of the day... the problem we've been running into is he's running on windows right now, therefore has no access to k3b.

Great tutorial though, bookmarked it. :)

---

### Post by Valok on 2007-12-09
Well the burn finished a little while ago.  I used InfraRecorder to check that the CD had files on it, and it had the right amount of data.

But when I go into my computer, and click on the CD drive to ensure that all the files got put on the CD right, but the "My Computer" window freezes up


Edit - It didnt actually freeze up totally, just took forever.  Once I was finished, it said "Windows cannot read from the disk. The disk might be corrected, or it could be using a format that is not compatible with windows."

---

### Post by CaptainInsaneO on 2007-12-09
So what you're saying is, Windows is working same as normal? :lolflag:

No but really... maybe you could just try booting with it and seeing if that works? If the data actually burned correctly, you should now be able to boot with that disc.

---

### Post by spind on 2007-12-09
Have you tried wubi?  I had ubuntu downloaded to my laptop - i then downlaoded the trial version of wubi recommended by Frak and i double clicked wubi and it installed ubuntu on to the second partition of my harddrive - no cd hassles needed.

---

### Post by Valok on 2007-12-09
> **CaptainInsaneO said:**
> So what you're saying is, Windows is working same as normal? :lolflag:

No but really... maybe you could just try booting with it and seeing if that works? If the data actually burned correctly, you should now be able to boot with that disc.

I'll go ahead and give it a try.  If its still not working when I get back maybe I'll try that WUBI

---

### Post by Valok on 2007-12-09
Just came back from rebooting my computer and it didnt work.  Still saying the same things it has been.  I'm gonna look into the WUBI thing suggested above.

And it appears that 7.04 is the latest version available through WUBI, so I suppose Ill go with that.

---

### Post by stchman on 2007-12-09
> **Valok said:**
> So I've spent almost the entirety of today trying to get a working bootable CD and I'm still at a loss and quite frustrated at the moment.

I've downloaded the .iso, its on my desktop, and I burned it to a CD using exactly what I was told to on the ubuntu wiki site using InfraRecorder.  However, when I turn my computer on, it just doesn't seem to want to boot, and I'm not at a loss as to why this might be.

Sorry I mis-read the post.  When you fire up InfraRecorder go to

Actions--->Burn Image

Then point the browser to the Ubuntu .iso image.

---

### Post by Valok on 2007-12-09
Yeah thats what I was doing, but it still didnt want to work for me.  Im DLing WUBI right now and hopefully that will make things go a little smoother.

---

### Post by stchman on 2007-12-10
> **Valok said:**
> Yeah thats what I was doing, but it still didnt want to work for me.  Im DLing WUBI right now and hopefully that will make things go a little smoother.

Maybe your CD ROM is not set to boot off of in your BIOS.

---

### Post by dptxp on 2007-12-10
This is the longest thread I have seen on burning iso to CD.

Download torrent from Ubuntu download site.
In Infrarecorder just use burn image command and select your iso, do not change anything, even speed. The auto speed mode burns at about 18 to 20 X, dynamically changes speed. Fast and
reliable.

---

### Post by CaptainInsaneO on 2007-12-10
> **dptxp said:**
> This is the longest thread I have seen on burning iso to CD.

Download torrent from Ubuntu download site.
In Infrarecorder just use burn image command and select your iso, do not change anything, even speed. The auto speed mode burns at about 18 to 20 X, dynamically changes speed. Fast and
reliable.

This is why it's the longest thread on this; people keep telling him to do that when that's not really his problem.

---

### Post by dptxp on 2007-12-10
> **CaptainInsaneO said:**
> This is why it's the longest thread on this; people keep telling him to do that when that's not really his problem.

Maybe he is picking up torrents from wrong places. Maybe he is not burning with 'burn image' command. Maybe his CD drive is bad. Maybe his media is bad. Maybe his Window$ is bad. Maybe his bios is bad.

I can not think of anything else.

---

### Post by Valok on 2007-12-10
Yeah I've since given up on installing via a bootable disc.  I've got Ubuntu up and running through WUBI at the moment and I'm working on making into a full install with its own partition and what not.

---

