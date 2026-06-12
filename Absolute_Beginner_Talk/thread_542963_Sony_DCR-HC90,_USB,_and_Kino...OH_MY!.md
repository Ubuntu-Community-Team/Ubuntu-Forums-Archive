---
title: "Sony DCR-HC90, USB, and Kino...OH MY!"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Daghita on 2007-09-04
I own a Sony Handycam DCR-HC90 and I'm trying to get the video from it into Kino. Using the following commands, I was able to obtain the photographs from it that I took:

fdisk -l (found out that it was on sdb1)

sudo mkdir /home/na/camera
sudo mount /dev/sdb1 /home/na/camera
sudo chmod 777 /home/na/camera

So, the camera will mount with a bit of wrestling in the terminal, but when I open Kino (using sudo) and go to capture the video...the message down below in the app says that it can't load or find raw1394. From what I've read, the raw1394 is for Firewire? Although, I'm trying to get it through USB. But, before I updated to Kino 1.1.1, it was trying to use dv1394, but gave the same message.

Can any experts lend some advice? I've looked around in the forums, but haven't seen anything yet on conquering this problem.

---

### Post by sbassett on 2007-09-04
Do you have the libraw1394 packages installed (libraw1394-8 & libraw1394-dev)?

---

### Post by Daghita on 2007-09-04
I had libraw1394-8 installed, but not libraw1394-dev. I installed the dev package...loaded up Kino again using sudo...but still no luck. A weird thing I noticed...I went to /etc/modules...but I couldn't find the modules folder.

I noticed people going into that folder to change up some items. But, again, I noticed it wasn't there...so maybe that will shed some light on a situation?

---

### Post by Daghita on 2007-09-05
So, for whatever reason that I couldn't see anything to do with raw1394...I finally decided to try this command to manually load the raw1394 module:

sudo modprobe raw1394

Luckily, I didn't get any error messages. So, somewhere along the way that I have yet to see...the module is in there. Then, I continued to load up Kino with the sudo command. I clicked the capture button and this time...no error message! Now we're cooking with Crisco.

But, with my camera, I have to connect it through the USB port. Which puts the camera's LCD into a different mode, so I can't actually play the tape. The camera came with a remote control, so I'm hoping while the capture is going...I can use that to play the tape. We'll see, I'll keep my progress updated in the future...

---

### Post by Daghita on 2007-09-11
So, I abandon the hope of USB with the camera. I go out and get a firewire cable and connect both to each other. I see that the port is listing, .but I have no idea if the computer is seeing the camera.

I update Kino to 1.1.1 and the module is loading. But now, it's not seeing the camera at all. Help!

---

### Post by Amazona aestiva on 2007-09-13
See the first link in my signature. Kino in the middle of the first post. It might help.

---

### Post by Daghita on 2007-09-25
Ok, after talking a little while off from that situation, I figured it out. Here's how I did it:

```
Make sure you have the plug completely plugged in...
```

Thank you, that is all.

=D>

---

### Post by ph3ar on 2008-02-18
Hello, I'm using kubuntu 7.04 kernel 2.6.20-16 kernel and I tried to export some video with kino 1.2.0 first and dvgrab 3.1 later. The thing is that the exported (raw) video wasn't a "normal" video, many clicks in sounds and the image was somehow crappy.

What options are you using??? and btw in which group the user should be to have access to the dv1394. :confused:

---

