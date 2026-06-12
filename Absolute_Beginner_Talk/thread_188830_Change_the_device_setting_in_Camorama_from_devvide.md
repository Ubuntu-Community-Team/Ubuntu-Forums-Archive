---
title: "Change the device setting in Camorama from /dev/video0 to /dev/video1"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Jah Jah Binks on 2006-06-04
Can someone guide me on how to do this?

---

### Post by meng on 2006-06-04
Have you tried from the terminal
camorama --device=/dev/video1

I'm not saying that the setting will stick the next time you run camorama, but it's good for a test run anyway.

---

### Post by Jah Jah Binks on 2006-06-04
[QUOTE=meng]Have you tried from the terminal
camorama --device=/dev/video1

I'm not saying that the setting will stick the next time you run camorama, but it's good for a test run anyway.[/QUOTE]
Gives me an error:

Could not connect to video device (/dev/video1)

I'm trying to connect my LOGITECH QUICKAM 5000 and it will not work any suggestions?

---

### Post by meng on 2006-06-04
Then I have two questions for you:
1. Are you sure that your Quickcam is /dev/video1?
2. (assuming you are sure) What are the permissions on /dev/video1?

---

### Post by Jah Jah Binks on 2006-06-04
No I am not sure of anything on UBUNTU :-D but whenever I try to open CAMORAMA I get an error cannot connect to video device (/dev/video0) and someone in another thread suggested doing the topic of this heading.

---

### Post by meng on 2006-06-04
Okay, well then rather than trying to guess blindly, could you please outline what you've already tried to do (I recall from one of your earlier posts it involved easycam) and I'll do my best to help.

---

### Post by Jah Jah Binks on 2006-06-04
Well I tried using EASYCAM2 and after a long while I got it to install. I am assuming that the next step is to open CAMORAMA where I can view my webcam. Now when I try to open CAMORAMA it gives me the error:

 Could not connect to video device (/dev/video0)

So that's where I am now. Maybe I am wrong in assuming that CAMORAMA is my next step though.

P.S. I don't know if this is relevant but when going through the EASYCAM2 installation it shows my camera as:

Bus 001 Device 002: ID 046d:08c5 Logitech, Inc.

---

### Post by meng on 2006-06-04
Sorry to take so long, I've been researching your problem. I believe the answer is that your model of camera does not have Linux driver support. It is not one of the models supported by Easycam/Easycam2. There is an experimental driver here, using v4l2 (video4linux2)
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
but so far as I can tell, this is far from a completed project, you have to compile from source and it's not that simple to download the source code.

While many Logitech cameras are supported, many aren't too. Yours seems to be in the latter category. (If anyone else knows better, please speak up.)

I'm not going to rant about hardware vendors and cross-platform compatibility, but I will simply state that this is why I select my hardware purchases based on how easily they can be configured to work with Linux.

---

### Post by Jah Jah Binks on 2006-06-04
Oh boy. Thanks anyway MENG.

---

### Post by meng on 2006-06-04
There is at least some hope:
[http://www.ubuntuforums.org/showthread.php?t=118517](http://www.ubuntuforums.org/showthread.php?t=118517)
look at post #8, you could do worse than following those instructions

and if you search the forums for quickcam 5000, there are several other threads. Good luck with it.

---

### Post by Jah Jah Binks on 2006-06-04
[QUOTE=meng]There is at least some hope:
[http://www.ubuntuforums.org/showthread.php?t=118517](http://www.ubuntuforums.org/showthread.php?t=118517)
look at post #8, you could do worse than following those instructions

and if you search the forums for quickcam 5000, there are several other threads. Good luck with it.[/QUOTE]
That's all too complicated for me I don't think I'm ready for UBUNTU just quite yet.

---

### Post by Rul on 2006-10-22
maybe you can try this

[http://www.ubuntuforums.org/showthread.php?t=280121&highlight=hp+webcam](http://www.ubuntuforums.org/showthread.php?t=280121&highlight=hp+webcam)

---

