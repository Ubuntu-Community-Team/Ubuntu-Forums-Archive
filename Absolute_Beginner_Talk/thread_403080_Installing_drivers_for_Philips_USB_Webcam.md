---
title: "Installing drivers for Philips USB Webcam"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-06
I have a Logitech Quickcam Orbit.

I found [THIS SITE]("http://www.linux-sxs.org/hardware/pwc.html") which has the necessary drivers.

The instructions in the site are too complicated for me.

Please help me understand the instructions from [the site]("http://www.linux-sxs.org/hardware/pwc.html").

How do I know if  X has video4linux support?

What do I do if I do not have a /etc/X11/XF86Config and /etc/modules.conf file?

---

### Post by chili555 on 2007-04-06
Your default installation should include video4linux. Open up Synaptic and see if you have installed xserver-xorg-video-v4l, libpt-plugins-v4l and libpt-plugins-v4l2. If not, grab them.

> What do I do if I do not have a /etc/X11/XF86ConfigYou get down on your knees and thank your Supreme Being that you have a modern distribution that uses xorg rather than XFree86! Also, /etc/modules.conf is /etc/modules here in Ubuntu.

The good news is you may not have to do any of that stuff, or just a bit. Open up a terminal and type:```
sudo tail -f /var/log/messages
```This is so you can see what the kernel is doing or complaining about, while you try to coax your Orbit to life. Leave it open.

Open another terminal and issue a command:```
sudo modprobe pwc
```Look in the other terminal; does it look like your cam started up without complaint? Did the light come on? Post back and let us know.

---

### Post by wersdaluv on 2007-04-06
> **chili555 said:**
> Your default installation should include video4linux. Open up Synaptic and see if you have installed xserver-xorg-video-v4l, libpt-plugins-v4l and libpt-plugins-v4l2. If not, grab them.

You get down on your knees and thank your Supreme Being that you have a modern distribution that uses xorg rather than XFree86! Also, /etc/modules.conf is /etc/modules here in Ubuntu.

The good news is you may not have to do any of that stuff, or just a bit. Open up a terminal and type:```
sudo tail -f /var/log/messages
```This is so you can see what the kernel is doing or complaining about, while you try to coax your Orbit to life. Leave it open.

Open another terminal and issue a command:```
sudo modprobe pwc
```Look in the other terminal; does it look like your cam started up without complaint? Did the light come on? Post back and let us know.

Thank you very much for that. So apparently, I did not have to do much work. :)

Here is the output of **sudo tail -f /var/log/messages**
```

Apr  7 08:58:54 machine kernel: [17180237.636000] usb 2-2: configuration #1 chosen from 1 choice
Apr  7 08:58:54 machine kernel: [17180238.088000] Linux video capture interface: v1.00
Apr  7 08:58:54 machine kernel: [17180238.128000] pwc Philips webcam module version 9.0.2-unofficial loaded.
Apr  7 08:58:54 machine kernel: [17180238.128000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
Apr  7 08:58:54 machine kernel: [17180238.128000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
Apr  7 08:58:54 machine kernel: [17180238.128000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
Apr  7 08:58:54 machine kernel: [17180238.128000] pwc Logitech QuickCam Orbit/Sphere USB webcam detected.
Apr  7 08:58:54 machine kernel: [17180238.128000] pwc Registered as /dev/video0.
Apr  7 08:58:54 machine kernel: [17180238.128000] usbcore: registered new driver Philips webcam
Apr  7 08:58:55 machine kernel: [17180238.400000] usbcore: registered new driver snd-usb-audio

```

After entering **sudo modprobe pwc**, there was no output from the terminal and the camera did not react. How is that?

---

### Post by wersdaluv on 2007-04-06
I tried Ekiga and chose the option, "display images from camera device." Whenever I press that, the light in the Webcam turns off (which happens when it is properly configured in windows), but Ekiga does not display any video.

Why is it that way?

---

### Post by wersdaluv on 2007-04-06
I tried Kopete. My webcam was detected, but I could not see any video stream. There was just a black screen.

---

### Post by Maestro23 on 2007-04-06
Just throwing another help doc out here: [https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29](https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29)

Might help you track down your problem.

Good luck.

---

### Post by wersdaluv on 2007-04-06
> **Maestro23 said:**
> Just throwing another help doc out here: [https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29](https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29)

Might help you track down your problem.

Good luck.

Tried it, but it didn't work. :(

---

### Post by wersdaluv on 2007-04-07
> **Maestro23 said:**
> Just throwing another help doc out here: [https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29](https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29)

Might help you track down your problem.

Good luck.

There were some instructions on how to repair pwc that I did not follow.

After following them, my webcam worked liked magic! The video looks even better than with the real windows drivers! hahahahah

Thanks dude!

---

