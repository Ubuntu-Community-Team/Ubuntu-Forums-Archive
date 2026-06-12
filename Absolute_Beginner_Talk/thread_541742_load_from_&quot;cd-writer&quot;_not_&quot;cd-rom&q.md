---
title: "load from &quot;cd-writer&quot; not &quot;cd-rom&quot;"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2007-09-03
I am trying to add some software from synaptic, it asks me to insert Feisty into the CD-Rom which I do but when I click OK it just asks me over an over to insert it?

I know why but don't know how to fix it.

I don't have a CD-Rom I only have a CD-Writer so I need to change the setting some ware to tell ubuntu to expect feisty to be inserted into the writer and not Rom.

I think this happened due to the install method (back with Dapper), due to no USB support at boot I had to install by putting my HDD into another laptop that did have a CD-Rom.

---

### Post by lisati on 2007-09-03
"CD-ROM" refers to a disk. You need to put your *ubuntu CD into your CD writer.

---

### Post by kudos1uk on 2007-09-03
> **lisati said:**
> "CD-ROM" refers to a disk. You need to put your *ubuntu CD into your CD writer.

Thats what I do but it can't see it.

When I put the CD in a new folder appears on the desktop for my "CD-Writer" and a window opend with the contents. I click "OK" on the message that says inset CD, it goes away then reappears asking me the same question  "please insert CD into CD-Rom".

I assumed the problem was that it wanted me to insert it into a CD-Rom and not a CD-Writer but I was only guessing.

---

### Post by nowshining on 2007-09-03
actually synaptic shouldn't be asking you that it should go out to the internet to download from the repos...  (repositories)...



edit: what are you trying to install??

---

### Post by kudos1uk on 2007-09-03
> **nowshining said:**
> actually synaptic shouldn't be asking you that it should go out to the internet to download from the repos...  (repositories)...



edit: what are you trying to install??

I was trying to install mythtv it has a lot of extras that get listed that have to be installed along with it.

I'm trying to find software that will work with my Sony Motion eye built in can effectv works well but is only a bit of fun and motioneye works too but again its not very advanced for taking pics and taking mjpeg.

I tried xawtv, motv & camerama nether of which can detect the cam so really just trying other software, i don't know why some work and some dont detect the cam.

---

### Post by nowshining on 2007-09-03
again the extras should download from the internet with the application also they are called dependencies.... :)

---

### Post by nowshining on 2007-09-03
try this 
system - administration - software sources
click a check box and uncheck it click close it should ask you to reload if so - click reload...

---

### Post by kudos1uk on 2007-09-03
sorry my error, it was mythtv and its dependencies that caused this error not motv.

I downloaded motv and that would not work with my can either I got the usual "v4l-conf had some trouble, trying to continue anyway" so for its only effectv and motioneye that will work, its always this v4l-cofig problem with other software.

---

### Post by kudos1uk on 2007-09-03
> **nowshining said:**
> try this 
system - administration - software sources
click a check box and uncheck it click close it should ask you to reload if so - click reload...


Thanks, have just done that and will now try mythtv again, out of interest listed under "third party software" is listed "cd-rom feisty fawn" and "skype".

Should I untick cd-rom feisty?

---

### Post by nowshining on 2007-09-03
yes if it says that, I never saw nothing that asked that I believe..but again uncheck and give that a try as it could be the source of your problem...

---

### Post by AndyCooll on 2007-09-03
It's asking for a CD-ROM because you used that to install Ubuntu and by default Synaptic also sees the disk as  a "repository", i.e. a source which contains the files needed to install the apps you want. If you put the original Ubuntu CD back in the drive and then tried installing an app Synaptic it will work fine. 

Ideally however you want to remove this need to put the CD in each time and just use the Internet, hence the reason for unticking the "cd-rom feisty fawn".

:cool:

---

### Post by kudos1uk on 2007-09-03
Many thanks, un-checking the cd-rom entry in third party software solved the problem. I think it was there because I had to upgrade to Feisty via cdrom.

---

