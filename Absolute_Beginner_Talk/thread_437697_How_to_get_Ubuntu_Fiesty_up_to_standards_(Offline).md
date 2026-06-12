---
title: "How to get Ubuntu Fiesty up to standards (Offline)"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by andrew.co.za on 2007-05-09
I thought it might be useful to have a post where people can share their experiences on how they got Ubuntu to be the operating system of choice.
I live in South Africa (the origin of Ubuntu for those who don't know) and in South Africa there exists what's known as a communication monopoly (Telkom, for those who want to start up hate blogs). Those of us who pay the unacceptably high monthly costs are then subjected a minimum 3 month installation waiting period, unreliable connection speeds and a complete lack of customer service. And that is why this is an (offine) post version. I do have a connection at work, albeit unreliable and a flash drive.

My first question in this post:
I want to experience all the visual advantages that Ubuntu has to offer but for now i can't even get a resolution higher than 800x600. I downloaded the 9755 drivers from the nvidia site (.run file, about 11Mb) as well as the package file (about 8Mb). I have a 7900GTX and i have not had any results with either of these files. I would really appreciate it if someone could give me the step by step process of how to get 3D acceleration up and running and maybe any troubleshooting tips that might help along the way. I haven't given specifics of my problem because i want to make sure that it's not because i've gone about it the wrong way.

---

### Post by DirtDawg on 2007-05-09
Nevermind. I didnt answer the question. :D

---

### Post by andrew.co.za on 2007-05-09
No need to specifically answer questions. Anything that might be useful to "Absolute Beginners" is welcome

---

### Post by felicity on 2007-05-09
Have you tried using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

---

### Post by Delkster on 2007-05-09
Pardon my ignorance, but doesn't Ubuntu come with the restricted modules packages installed (but not enabled) by default?

Have you tried just going to System > Administration > Restricted Drivers Manager and enabling the NVidia driver? Does that require a network connection?

---

### Post by teddybairs1 on 2007-05-09
I used to have to download packages by hand on another system, burn them to a disk, and then manually install them on my Ubuntu breezy system. It's a pain because of the dependencies but it is possible. You have to go to:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

And trudge through all the package lists and dependencies for the software you want. Install them with GDebi (right-click on the package file) because it will check for dependencies and let you know what you need before it tries installing anything.

The biggest problem you may have is the updates, because Ubuntu is updated fairly frequently, but it shouldn't be too bad.

Where your drivers are concerned, you'll probably want the nvidia-glx-new(?) package. This should have the right drivers for your system.

---

### Post by andrew.co.za on 2007-05-09
Yes, i did go to the Restricted Driver Manager and noticed that there were nvidia drivers installed (and disabled). When i tried to enable them, it asked for confirmation and after accepting, it still said that the drivers are disabled. I tried pressing ctrl+alt+backspace and logging back in but they were still disabled.

---

### Post by andrew.co.za on 2007-05-09
Thanks for the info but so far i havn't had trouble finding the necessary files, just installing them. But if you have any other URLs for important files i'm sure they'll be useful in the future.

---

### Post by andrew.co.za on 2007-05-09
I have heard of envy, i was just under the impression that it needed a connection so i didn't look in to it. Should i have?

---

### Post by felicity on 2007-05-09
Oops, my bad, you're right, envy does need a connection. Maybe you can smuggle your Ubuntu computer into your work? :)

---

### Post by dcstar on 2007-05-10
The easiest way of getting packages would be to have a PC at your work with Ubuntu installed on it, and then you install whatever packages you need at home on that PC.

The actual package .deb files will be in /var/cache/apt/archives, simply copy these files from the work PC to your PC, and install them by double-clicking on them.

You can manually download the actual .deb files from the repository web sites, but it may be more involved than using another Ubuntu machine to do it for you.

---

### Post by andrew.co.za on 2007-05-10
Unfortunately i can't put Ubuntu on my work PC.

I tried double clicking the .deb file but i gave me some error, i can't really remember but i think it was: "Dependency not satisfiable". As for the .run file; it told me it needed to compile something but then complained that the libc headers (or something like that) were missing. If someone could please help me out here, i'd really appreciate it.

---

