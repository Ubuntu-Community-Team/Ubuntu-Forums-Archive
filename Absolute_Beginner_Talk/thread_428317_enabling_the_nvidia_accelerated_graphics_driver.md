---
title: "enabling the nvidia accelerated graphics driver"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by CraigRR on 2007-04-30
Hi, new user here, just installed 7.04 onto the hard disk, after the reboot I went into system>preferences>desktop settings and it told me that I must enable the nvidia accelerated graphics driver if I want 3D stuff etc (card is an AGP geforce 6800), so I clicked enable and it told me to restart desktop settings after the computer is restarted and the driver is active. So I rebooted, went into desktop settings, and the same message appears from before asking if I want to enable the nvidia accelerated graphics driver.

A few more reboots and the same thing happens each time. How do I make enabling this driver stick?

Thx

---

### Post by mikewhatever on 2007-04-30
That driver utility downloads and installs the restricted nvidia driver. It will not work if there is no internet connection, or if extra repositories are not enabled.
[Here is how to add extra repositories.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by lakersforce on 2007-04-30
Before doing anything I would recommand that you make a back-up of your Xorg.conf file, in case your X gets screwed up:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then you can easily revert your changes by replacing the xorg.conf.backup with xorg.conf at the comand -line, should your system get srewed up.

Sometime this command works when you want to enable 3d accel.:

```
sudo nvidia-glx-config enable
```

Maybe you will have to change your xorg configuration too:

```
sudo dpkg-reconfigure xserver-xorg
```

and choose the NVIDIA settings. The rest of the options need not to be changed.

---

### Post by CraigRR on 2007-04-30
thx for the reply I guess, but are you saying I have to enter many lines of commands just to enable the full driver for a graphics card?

How disheartening if this is the case.

I went into system>administration>software sources>third party, its empty, I clicked add and it asks me to type a complete APT line. I have no clue what this is, or where I would get it for the nvidia accelerated graphics driver.

I was under the impression that because it says in the messages quoted in my original post click to enable the driver etc, that the driver is already sitting on the machine. Is this not the case?

---

### Post by lakersforce on 2007-04-30
I am not using the english version so some of these may have different names on your system:

System -> Admin -> Synaptic
Settings -> Archieves/Repos

Enable all the repositories on this page, click ok and then update.

---

### Post by lakersforce on 2007-04-30
Also to install the download the nvidia driver you should do this at the command line:

```
sudo apt-get install nvidia-glx
```

and then follow the first post that I posted.

---

### Post by CraigRR on 2007-04-30
ok I went back into system>administration>software sources and clicked the updates tab, then I clicked recommended updates, and it downloaded some stuff, then installed the accelerated graphics driver presumably because I saw something about nvidia-glx flash up quickly - a few secs later it asked me to reboot, which I did.

Now after the reboot I'm getting a warning message about using restricted software. I went into it and see the nvidia driver is now enabled (confirmed by going back into desktop settings and seeing wobbly windows). But is the warning message correct?

Thx

---

### Post by CraigRR on 2007-04-30
hmm in addition to my last post, I go into screen resolution and there are a few more options there now compared to before the nvidia driver was installed. But the options are still crippled compared to what my hardware (graphics card & monitor) can do. The best resolution it will let me use is 1024*768@57Hz. My monitors optimal resolution is 1280*1024@85Hz. This can't be right surely? No wonder I'm getting dizzy!

Thx

---

### Post by lakersforce on 2007-04-30
Yes, that is normal.

Do a:

```
glxinfo | grep rendering
```

if the output is:

```
Direct Rendering: Yes
```

then you have succesfully setup 3D Accel.

---

### Post by lakersforce on 2007-04-30
> **CraigRR said:**
> hmm in addition to my last post, I go into screen resolution and there are a few more options there now compared to before the nvidia driver was installed. But the options are still crippled compared to what my hardware (graphics card & monitor) can do. The best resolution it will let me use is 1024*768@57Hz. My monitors optimal resolution is 1280*1024@85Hz. This can't be right surely? No wonder I'm getting dizzy!

Thx

To get higher resolutions you will have to:

```
sudo dpkg-reconfigure xserver-xorg
```

and choose the higher resolutions.

Back-up your xorg.conf file first, just in case something goes wrong.

---

### Post by CraigRR on 2007-04-30
This doesn't work for me. 

I can get into it and when I select the resolution 1280*1024 I can tick it, and move on to vsync rates both of which I type 85, then at the end i click yes to save to file.

Then when I go back into screen resolution the options are still as they were before (max 1024*768@57hz)

Thx

---

### Post by lakersforce on 2007-04-30
Did you restart your X windows system?

---

### Post by timseal on 2007-04-30
> **lakersforce said:**
> Yes, that is normal.

Do a:

```
glxinfo | grep rendering
```


Shouldn't that be 

```
glxinfo | grep Rendering
```
?

---

### Post by lakersforce on 2007-04-30
same thing. try it out!

---

### Post by Rich1386 on 2007-06-18
I tried what lakersforce recommended in the third post, but i forgot to make a backup beforehand, and now I'm getting a weird blue screen asking me if I want to see logs of the problem, and I can't boot normally.  Any ideas?

---

### Post by BigEagle21 on 2007-10-01
I had the same problem and followed the steps above...

randy@randy-desktop:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I tried the line "LIBGL_DEBUG=verbose" nothing happened.

This is my second try at this. My last try caused my computer not to reboot properly do to the x config file not working. So I reinstalled Linux and am back at it.

How can I get this to work? I am using a NVIDIA Geforce 5500.

---

### Post by BigEagle21 on 2007-10-01
Well, i tried it again, and no luck.  The NVIDIA GeForce 5500 is not listed in the supported list. Although, every other card above it and below it seams to be.

I did manage to get this to work once through a terminal code, but for some reason my Wireless card stopped working right after. ?!  I am not sure what the code was I have tried so many.

---

### Post by nadjavox on 2008-04-06
> **lakersforce said:**
> To get higher resolutions you will have to:

```
sudo dpkg-reconfigure xserver-xorg
```

and choose the higher resolutions.

Back-up your xorg.conf file first, just in case something goes wrong.

Thanks! This worked for my GeForce 6600+ perfectly.

---

