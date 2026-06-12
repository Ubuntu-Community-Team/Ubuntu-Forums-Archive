---
title: "NVIDIA GeForce 610M on ASUS K55VD"
date: 2013-01-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kenweill on 2013-01-04
Currenly, I'm dual booting Windows 7 and Ubuntu 12.10 64bit on my ASUS K55VD.

I can't or won't completely ditch Windows 7 unless the video card is installable on my Ubuntu partition.

I can't make the best of my laptop or use it's full features if video card is not detected and installed.

Last time, on my old laptop, ASUS K43SV, it's video card is also not detected on older versions of Ubuntu. But with the release of Ubuntu 12.04 and the later 12.10, video card is not detected and can be installed via additional drivers.

My wife is now using my K43SV and so I bought a new one for me, K55VD.

Currently, existing Ubuntu versions are not able to detect the video card I have on my new laptop. Should I wait for the next version of Ubuntu before my video is detected and installable?

Currently, Ubuntu only detected Intel video card on this laptop, no NVIDIA card.

Also, on Windows 7, Intel driver is required to install first before installing the NVIDIA driver. NVIDIA driver won't even install if Intel driver is installed first, on Windows 7. Don't know why.

Is it possible that it's also the same reason why NVIDIA is not detected on Ubuntu? Currently, Intel is detected and installed on Ubuntu 12.10 64bit (as it has 4gb RAM) but NVIDIA is not.

Does anyone have the same machine and was able to install NVIDIA drivers? Can someone share their methods on how to install it?

---

### Post by John_Swing on 2013-01-05
Hello,

I have the same laptop and I'm able to use the NVIDIA card without any problem after installing [Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

With Bumblebee the NVIDIA card is disabled by default and therefore the battery life is extended, whenever I want to use the card with a program I just use the command optirun <nameoftheprogram> and it works.

I hope this will help you.

John

PS: You can read this [article]("https://en.wikipedia.org/wiki/Nvidia_Optimus") if you want to understand how works NVIDIA optimus and why its linux support is complicated.

---

### Post by kenweill on 2013-01-06
> **John_Swing said:**
> Hello,

I have the same laptop and I'm able to use the NVIDIA card without any problem after installing [Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

With Bumblebee the NVIDIA card is disabled by default and therefore the battery life is extended, whenever I want to use the card with a program I just use the command optirun <nameoftheprogram> and it works.

I hope this will help you.

John

PS: You can read this [article]("https://en.wikipedia.org/wiki/Nvidia_Optimus") if you want to understand how works NVIDIA optimus and why its linux support is complicated.

Thanks for the article John. If it wasn't for this, I wouldn't know about NVIDIA optimus. Now I understand now why my laptop needs both intel and nvidia drivers installed.

As for Bumblebee, I don't know why you need to run the command optirun <nameoftheprogram> while it's stated on on Bumblebee website that "Since Bumblebee 3.0, this feature is enabled by default, using bbswitch."

---

### Post by John_Swing on 2013-01-06
bbswitch is a module that disable the NVIDIA card when not used, without bbswitch the NVIDIA card is always running even when you don't use it.
I quote the Bumblebee wiki :
> 
(optional) bbswitch (or dkms-bbswitch) - recommended for saving power by disable the Nvidia card


If you want to use your NVIDIA card with a program you are required to use optirun <nameoftheprogram> because for now bumblebee can't automatically switch from the Intel card to the NVIDIA card when needed.

I quote the bumblebee wiki again :
> 
The present releases only support rendering on-demand, automatically starting a program with the discrete video card based on workload is not implemented
[...]
The command line program optirun shipped with Bumblebee is your best friend for running applications on your Optimus NVIDIA card.

Test Bumblebee if it works with your Optimus system:
[QUOTE]$ optirun glxgears -info
If it succeeds and the terminal you are running from mentions something about your NVIDIA - Optimus with Bumblebee is working!
General Usage:
> $ optirun [options] <application> [application-parameters]

[/QUOTE]

Regards.

John

---

### Post by kenweill on 2013-01-07
@John,

How did you install this? I tried this on LiveDVD (just for testing purposes) but bumblebee won't install. Dependency error that it lacks virtualgl. I tried to install virtualgl but it also needs libturbojpeg which is not installable.

Or perhaps it won't work on 64bit version of Ubuntu 12.10?

---

### Post by John_Swing on 2013-01-07
I'm using Ubuntu 12.10 64bits and it works just fine doing :
```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia

```

If I understand correctly you're trying to install it on a Live Ubuntu ? Maybe the problem come from that, I know you can install programs on a Live Ubuntu but I never heard of installing drivers on it..

John

---

### Post by kenweill on 2013-01-08
Running > $ optirun glxgears -info 
and I get
> 
[  395.731135] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[  395.731217] [ERROR]Aborting because fallback start is disabled.


---

### Post by John_Swing on 2013-01-08
I don't understand, we have the same laptop and it works perfectly for me. 

Here the steps I did :

1) Install Ubuntu 12.10
2) ```
sudo apt-get update && sudo apt-get dist-upgrade -y
```
3) ```
sudo add-apt-repository ppa:bumblebee/stable
```
4) ```
sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia
```
5) Add bumblebeed --deamon in startup applications
6) ```
sudo reboot
```
[...]
7) ```
optirun glxgears
```
and it works..
```

optirun glxgears
6456 frames in 5.0 seconds = 1290.925 FPS
glxgears
304 frames in 5.0 seconds = 60.677 FPS

```

---

### Post by kenweill on 2013-01-08
I just did reinstall my entire system after having fixed my GPT problems and install bumblebee again.

Running "optirun firefox" I get
> NOTE: child process received `Goodbye', closing down
Though, firefox was loaded, I got that message in the terminal.

Running "optirun glxgears", I get 
> /usr/bin/vglrun: 303: exec: glxgears: not found

And now, I can't get to desktop. I'm stuck with "you are using low resolution" with some option box that not working. It must be related to bumblebee. It won't go to GUI.

---

