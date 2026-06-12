---
title: "Webcam works in Ekiga, Skype, but not camorama"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-11-17
I have a Logitech QuickCam Ultra Vision and the webcam's sound / video works both for Ekiga / Skype but camorama can't start because it can't connect to /dev/video0.

It exists, and the camera isn't used by any other program but camorama refuses to work.

---

### Post by Superfish on 2008-01-25
I have a similar problem - I have a 1420N, and the integrated webcam works fine for Cheese and Skype (and I think for Ekiga), but Camorama gives "Could not connect to video device (/dev/video0). Please check connection."
Upon opening Skype and Cheese, the blue light by the webcam blinks and stays on. With Camorama, the light blinks before giving the error message, then blinks again when I close it, which seems to indicate that Camorama is getting at least some communication through.

---

### Post by LaRoza on 2008-01-25
You can't have more than app try to access it at a time.

If something is using it (even if it is not obvious) it won't work in other apps.

Close the other applications.

---

### Post by Superfish on 2008-01-26
I've tried it right on bootup without opening any other camera applications, and I still get the same error.
 
As an experiment, I tried opening Camorama with the Camera Monitor applet running. When Camorama comes up, Camera Monitor pops up with the message: "Camera is on, video device = /dev/video0"
Again, it appears that Camorama is making some initial communication, but not connecting.

AncientPC, does your webcam give any sort of visual feedback when it's on and being used, and does it respond in any way when you open Camorama?

---

### Post by mdsmedia on 2008-01-26
Does Skype open at startup? It could be that Skype is open without you knowing it and the camera is tied to Skype.

Look for any instances of other programs that might be open in the background.

---

### Post by Superfish on 2008-01-26
No, I have Skype's auto-startup disabled, and it's not running right now. I checked my 'ps aux' and I don't see anything camera related.

I also just tried Xawtv, and that gives similar performance - the camera blinks when the program opens, but the screen is black. Then, when I close the program, the camera blinks again. Could this have anything to do with v4l?

---

### Post by Rumpty on 2008-01-29
I couldn't get Camorama to work either, and I believe it is to do with Camorama and v4l2 not working together?

---

### Post by octoberdan on 2008-04-10
I'm having the same issue. fuser is supporting that there truly aren't other processes accessing the device. But while ekiga works, 

daniel@octop:~$ vgrabbj
Can't open "/dev/video" as VideoDevice!
Fatal Error (non-daemon), exiting...
There was no map allocated to be freed...
Device /dev/video was already closed...

daniel@octop:~$ webcam 
reading config file: /home/daniel/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [16 bit YUV 4:2:2 (packed, YUYV)]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
ioctl: VIDIOC_REQBUFS(count=1;type=VIDEO_CAPTURE;memory=MMAP): Device or resource busy
capturing image failed

With webcam, the light of my webcam lights up briefly before it shuts down. This may be a similar issue.

---

### Post by octoberdan on 2008-04-10
Found a program that works!!!

gqcam also doesn't work;

daniel@octop:/opt$ gqcam 
/dev/video: No such file or directory
daniel@octop:/opt$ gqcam -v /dev/video0
Error reading image...

but **cheese** works.

So working: cheese, skype, ekiga. 
Not working: video4linux's webcam, gqcam, and vgrabjj

---

