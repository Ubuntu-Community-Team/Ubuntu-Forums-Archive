---
title: "Bit Torrent"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-11
How do you get the fastest download speed from Bit torrent? I am using Deluge.People are uploading faster than I am downloading. I have Comcast Cable. One other computer is networked through a cabled router.

---

### Post by stalker145 on 2007-11-12
> **bgast1 said:**
> How do you get the fastest download speed from Bit torrent? I am using Deluge.People are uploading faster than I am downloading. I have Comcast Cable. One other computer is networked through a cabled router.

There is some discussion about this [over here]("http://ubuntuforums.org/showthread.php?t=581327"). Seems quite a few people are disgruntled with this problem. Also seems that packet encryption has helped a few.

---

### Post by bgast1 on 2007-11-12
Well, I don't know much about bit torrent. Or really how to set up Deluge. I used the wizard but didn't know how to answer their questions or what to do in preferences. I both inbound and outbound encryption boxes checked.But it seems I am downloading incredibly slow. Does it make a difference how many files you are trying to download? what about port forwarding would that make a difference?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **bgast1 said:**
> How do you get the fastest download speed from Bit torrent? I am using Deluge.People are uploading faster than I am downloading. I have Comcast Cable. One other computer is networked through a cabled router.

well comcast f*ck you they dont like it when you dont use your band with for there stuff .torrent files are not there stuff there for your f*ck by them the just killed your speed 

note may not be true depending on were you live and stuff but i think that it was like there intire network they did it to

---

### Post by bgast1 on 2007-11-12
You'd think there would be something we could do to fight back.:twisted:

I'm thinking though that it could still be something in the way I have deluge set up, I'd try Azuerus or however you spell it buy I don't know how to get it set up. I used in windows a little bit.

---

### Post by x64Jimbo on 2007-11-12
ktorrent is a pretty decent torrent app for Linux and it has its own port forwarding built in. You just have to enable UPnP in your router.

---

### Post by stalker145 on 2007-11-12
> **bgast1 said:**
> Well, I don't know much about bit torrent. Or really how to set up Deluge. I used the wizard but didn't know how to answer their questions or what to do in preferences. I both inbound and outbound encryption boxes checked.But it seems I am downloading incredibly slow. Does it make a difference how many files you are trying to download? what about port forwarding would that make a difference?

The number of files you are downloading at a time does (kinda) make a difference. If you are downloading a bunch, then the individual progress will seem slower since your bandwidth is being divided among all those files. Drop it to one or two and see if that makes things appear faster... or just check the overall transfer rate.

Port forwarding shouldn't make so much of a difference so long as you have uPnP set on your router. That allows your router to dynamically allocate ports requested from inside your network.

If you have encryption all checked already, that's pretty much all you can do from my (minimal) experience.

---

### Post by bgast1 on 2007-11-12
How do I know whether uPnP is set on my router? I had a program that would forward my ports in windows.

---

### Post by x64Jimbo on 2007-11-12
The router does the work whether you're in Windows or Linux. The program you had was probably a UPnP service, so to speak.  It most likely sent the UPnP signals to the router in the place of programs that don't speak UPnP. 
Setting up UPnP in your router varies by brand. I suggest reading your user's manual or searching for "UPnP setup <router model>" in google.

---

