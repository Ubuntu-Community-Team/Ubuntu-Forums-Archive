---
title: "I'm looking for a miricale..."
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by vamp4life666 on 2008-01-16
Hello, my name is Michael.

I am a student at the University of Florida.
I am developing a render farm for student use.
I am using 3DStudio Max 9 as the primary rendering engine. 
It comes with its own built in manager, server software designed to run on XP pro.
Early on, I was distributing the image files to the machines doing the rendering from a XP machine opened up to all the machine on the work group. 
 I was quick to realize that XP could only host ten open network connections when my rendering servers started crashing the moment I added the eleventh machine.

A friend clued me into Ubuntu server edition 7.10 Gutsy Gibbon, and told me that I would be able to share files with the twenty+ machines I am working with.
I have been reading articles and browsing different websites, looking for more detail instruction on how to set up a simple file server and I must say there is so much information out there I am having trouble finding a guide for getting started.

I am not a complete newcomer to networking or file sharing, I am though pretty green with command line though. 

I would greatly appreciate and direction or links to good tutorials.
Thanks,
Michael

---

### Post by thisismalhotra on 2008-01-16
Me a GATOR too !!

GO GATORS !! come to the rihg tplace help here is amazing .. check back in 30 minutes should have lot of posts. I will look up some stuff for you too ...

---

### Post by Rotaj on 2008-01-16
Hopefully this link to a previous post will help.

[http://ubuntuforums.org/showthread.php?t=308891]("http://ubuntuforums.org/showthread.php?t=308891")

---

### Post by vamp4life666 on 2008-01-16
Are you still at UF or have already graduated?

---

### Post by vamp4life666 on 2008-01-16
I looked at the link you sent me, and followed a few from there, I think I may be off in my terminology or I am confused in terms of what I am really looking for.

The link contained info on mail servers and webservers, maybe I am not completly understanding the diffrence...

I need to share image files to multiple machines, nothing more. I am under the impression that constitutes file sharing, not to be confused with an FTP server (is that correct?).

---

### Post by sloggerkhan on 2008-01-16
maybe look up clonezilla? Or by image to you mean graphics image like png or jpeg?
If you mean graphics image, a file server and a webserver can be quite similar.
Please clarify. Are you wanting a file server to store rendered images, a server for people use to render remotely, or what?

---

### Post by vamp4life666 on 2008-01-16
As I mentioned beofre I am developing a render farm.
In order to run the farm I need a machine that for all intensive purposes is a network acessible hard drive. This machine needs to be able to host images to 20+ rendering units, In that is must be able to support 20+ open network conections.

For example if you modeled a picture frame sitting on a table and wanted the picture to be of you, your neighbor, spouse, pet, whatever... that image need to be on a mapped network drive. The picture must be on a netwrok drive available to all machines set for rendering, thus the image can't be stored locally.

Ideally, I will be able to configure the machine running server edition 7.10 with a web interface so I can add the images (jpg) that need to be shared from my laptop.

Ideally when Gutsy is configured I can go to any of the win XP boxes that are set for rendering with 3ds max and simply go: map network drive and select the the Gutsy box with the nessary images on it. 

That is of coure the high hope.....

The way this netowrk should run (ideally) is:
A student, classmate, could walk up, connect to the network. I will copy any of the images they need that are not material defualt built into the program to this server i am trying to build, and then release their job to the render manager. They walk away, while the rendering boxes get the job done.

I hope that explains my situation better.
I am pretty computer friendly in that I have experience with OSX, XP, Vista and I have already setup and netowrked all the other machines to make this work. All that is left is to get this server up and running.

---

