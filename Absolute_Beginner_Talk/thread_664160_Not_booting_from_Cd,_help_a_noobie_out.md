---
title: "Not booting from Cd, help a noobie out"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by jkman82 on 2008-01-10
**I posted this in the Apple ppc forum, but thought it was suitable here:**

I have been trying to get ubuntu to run off of a cd I burned ( iso image with toast) my computer recognizes the cd, and a menu comes up to select how to run ubuntu (live, live-powerpc64 ect..) When I choose one, it goes to another screen and says loading kernal, and it is at this point the computer just shuts down and powers off. When I restart and hold option and select the linux cd image, it still does the same thing. Im running an older G4 with osx 10.2.8. Should I just wipe the computer clean and try to install ubuntu?

Could it be the cd? I wouldnt think so because it comes up with the black screen still with the command to put in 'live' or what ever else I want to enter. Am I just doing something thing wrong?

I made a video of what is going on, dont mind the camera focusing in and out, its a piece

**[http://www.youtube.com/watch?v=Psn6yGxaLc0]("http://www.youtube.com/watch?v=Psn6yGxaLc0")**

I tried other options when trying to boot ubuntu

when I tried to use live-nosplash-powerpc, it went through more, verifying things and what not, but after, nothing happened, but about 2 minutes after I stopped the video, a little sound chimed from my mac, which I left up to see if anything happened after the screen went blank, it wasnt a mac sound, but I still had no video.

**[http://www.youtube.com/watch?v=UqFofKSJ0yY]("http://www.youtube.com/watch?v=UqFofKSJ0yY")**

---

### Post by Xavieran on 2008-01-10
You should check the md5sum...an md5sum is a string of letters which can be used to verify the integrity of the .iso file you downloaded...I'm not sure how to d o this on Macs but a quick google should tell you...:)

Alternatively select the Check Disc for Defects in the Main Menu...

95% of times when a user has problems booting up a LiveCD or other installation media the cd has defects...remember that even though you can access the main boot menu a part of the kernel that it tries to load could be corrupted...

---

### Post by jkman82 on 2008-01-10
Found Checksum (mac md5sum) in disk utility.

It came up with this 

Unable to checksum  “disk2s1s2” - Invalid argument


I am guessing It was invalid :)

I used toast to burn the iso by dragging the iso to toast, selecting mac only, and then selecting iso 9660. Is this wrong?

---

### Post by Xavieran on 2008-01-10
No that would be fine...the syntax of md5sum check may have been off which is why it gave you invalid argument...

try```
checksum youriso.iso
```

---

### Post by jkman82 on 2008-01-10
I feel like a complete idiot asking this, but it has to be done!

were abouts to I enter that check sum code?



Really sorry if that is a stupid question, I have been reading up on linux, and I got this g4 off my dad a few days ago and thought the best way to jump into linux is just try it myself and see what happens, obviously I was wrong

---

### Post by Xavieran on 2008-01-10
> **jkman82 said:**
> I feel like a complete idiot asking this, but it has to be done!

were abouts to I enter that check sum code?



Really sorry if that is a stupid question, I have been reading up on linux, and I got this g4 off my dad a few days ago and thought the best way to jump into linux is just try it myself and see what happens, obviously I was wrong

No you weren't wrong!:)
I myself only started using *nix myself a year ago and it's been a great experience!

Does MacOS have a terminal?
If so I think you would type the command in there...there may be a GUI app for it,also try the check disk integrity option on the cd...

---

### Post by jkman82 on 2008-01-10
I tried entering the above code into the terminal and I come up with this:


-bash: checksum: command not found

---

### Post by Xavieran on 2008-01-10
try md5sum instead of checksum with the same syntax as above...:)

Sorry for the slow reply...I've been trying to write a script to move a heap of my music files around...xD

---

### Post by jkman82 on 2008-01-10
I was going to burn a new iso image using macs disk utility. I ran out of blank cd's, but I was just messing around and when I mounted the Iso of Ubuntu 7.10 onto disk utility it said 

"Unable to attach &#8220;ubuntu-7.10-desktop-powerpc.iso&#8221; - no mountable file systems."

does that just mean, it couldnt mount becuase I had no cd to burn it onto, or is the iso corrupt?

---

### Post by jkman82 on 2008-01-10
Tried the md4sum instead, still no good

---

### Post by Xavieran on 2008-01-10
I think that the .iso is corrupt...also when you burn make sure it is at the lowest write speed possible (less likely to be errors...)

---

### Post by buccaneere on 2008-01-10
> **jkman82 said:**
> I was going to burn a new iso image using macs disk utility. I ran out of blank cd's, but I was just messing around and when I mounted the Iso of Ubuntu 7.10 onto disk utility it said 

"Unable to attach “ubuntu-7.10-desktop-powerpc.iso” - no mountable file systems."

does that just mean, it couldnt mount becuase I had no cd to burn it onto, or is the iso corrupt?

Doesn't that mean it can't mount the local disk?

What is the native file system? (on the local drive)

---

### Post by jkman82 on 2008-01-10
I guess I'll try and find a new install off the internet, but I wouldnt know which version of 7.10 to use on my g4, I got this version off  this site (for power pc) Should I just try and burn the same one over again? or do I need to d/l a new one?

---

### Post by jkman82 on 2008-01-10
> **buccaneere said:**
> Doesn't that mean it can't mount the local disk?

What is the native file system? (on the local drive)


How would I go about checking this?

---

### Post by Xavieran on 2008-01-10
I'd say you need to download a new one...it sounds as if you didn't download the PPC one! :)

Select PowerPC option from this link [http://cdimage.ubuntu.com/ports/releases/gutsy/release/]("http://cdimage.ubuntu.com/ports/releases/gutsy/release/")

Also there is a PowerPC faq [here]("https://wiki.ubuntu.com/PowerPCFAQ")

EDIT:When it says the local disk could not be mounted I think it *was* referring to no disk being in the drive...

---

### Post by jkman82 on 2008-01-10
Thats the same one I downloaded :), should I just dowload the sameone over again? I mean if  people are downloading it and having no problems, maybe it was just something that happened while downloading it or burning the iso? ill try tomorow with the write speed on 1x !




Thanks Xavieran for all the help :KS , most people would love to burn a noobie like me




EDIT: I found another version Marked "File: ubuntu-7.10-desktop-powerpc.iso" so hopefully when I get some cdr's tomorow Its gunna work, if this thread gets engulfed down to the bottom of the forum ill just send you a PM

---

### Post by Xavieran on 2008-01-10
No problem:) I'm always happy to help...

Yes,it could have been a download problem...bits sometimes do just *dissappear* :)

---

### Post by zabien1970 on 2008-01-10
Just wondering if you can run the live cd without installing it, you'll have to make sure your computer is set up to boot from cd first then restart the computer with the live cd in the drive, then run it instead of installing it

---

### Post by jkman82 on 2008-01-11
thats what I am trying to do but Its not working. I am now trying to install ubuntu just yet, just trying to run it off the cd

---

