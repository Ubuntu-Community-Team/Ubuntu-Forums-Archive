---
title: "Blender troubles.... Dunno where else to post this."
date: 2008-09-20
forum: Art &amp; Design
---

### Post by xakh on 2008-09-20
I saw a Blender article here, thought, what the heck, I'll ask. I installed the blender from the repos, since I used it often when I was on windows. So, now I'm in blender, the package is outdated, but oh well, but when I try to enter edit mode, by hitting "tab" it closes instantly. I tried getting the new one, but it did the same. Ironically, the only way I get functionality out of it is using it in Wine, but it has its own errors, so that is not a permanent solution. I'm trying to use it to prove its credibility for enterprise use, but it seems like that's not going to be easy to do with this problem. Anyway, I've installed it on other Ubuntu machines and it's worked, but just not on this laptop, a toshiba satellite from last year, with a 17" screen, AMD Turion X2 64, some form of ATI, and Atheros wireless. Please, don't suggest alternatives, I have three years of work in .blend files, and I really don't want to export them all. 
[http://www.tvsdepot.com/product.php?id=170542&ref=froogle](http://www.tvsdepot.com/product.php?id=170542&ref=froogle) <-for reference, that's my laptop, I think, if not, it's really similar, down to the color, though that doesn't matter.

---

### Post by eye208 on 2008-09-20
Have you installed the accelerated 3D display driver? (System -> Administration -> Hardware Drivers)

---

### Post by unutbu on 2008-09-20
If you open a terminal, type
```

blender
```
and then press 'TAB' to induce a crash, what output do you get?

---

### Post by xakh on 2008-09-20
Segmentation Fault
that's all.

and to above me, yes, I have installed a 3D graphics driver.

---

### Post by unutbu on 2008-09-20
Please post```

apt-cache policy blender
```

---

### Post by digitalis_vulgaris on 2008-09-21
[http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

Try to download and run the newest blender. It doesn't need to be compiled or installed. Just start application.
Maybe this could works for you.

---

### Post by xakh on 2008-09-21
blender:
  Installed: 2.45-4ubuntu1
  Candidate: 2.45-4ubuntu1
  Version table:
 *** 2.45-4ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status
     2.45-1ubuntu2~gutsy1 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-backports/universe Packages
 is the output, and I've tried getting the newest one, it didn't work either.

---

### Post by unutbu on 2008-09-21
It appears you have both Gutsy and Hardy repositories enabled. 
Mixing packages from different distributions could lead to the kind of instability you are experiencing.

Go to System>Administration>Software Sources. 
If you have a Gutsy system, disable all Hardy repos.
Likewise, if you have a Hardy system, disable all Gutsy repos.

Then open a terminal and type
```

sudo apt-get update    # Reset what the APT system thinks are the available packages
sudo apt-get purge blender
sudo apt-get install blender
```

This still may not work if other packages on your system are a mix of Hardy and Gutsy versions. I don't know an easy way to fix this problem. If it is just a few packages, perhaps you can uninstall them, and then reinstall the versions from the proper distro. If the mix of Hardy and Gutsy is very great, then you may want to think about backing up your data and then reinstalling.

---

### Post by xakh on 2008-09-21
Okay, it seems that almost all of my repos are gutsy, and if I disabled them, there wouldn't be a hardy update server, even for security updates. Is this because I upgraded my distribution, instead of clean installing it?
Edit: They're all in the third party area, does that mean that with the main sources just aren't listed there? That makes sense, but I want to check. If this is the case, it might explain a lot of problems I've been having. Thanks in advance! 
Another Edit: Turned off the gutsy stuff,
blender:
  Installed: 2.45-4ubuntu1
  Candidate: 2.45-4ubuntu1
  Version table:
 *** 2.45-4ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status
so now it seems like that's gone, but it seg faulted again.

---

### Post by unutbu on 2008-09-21
Let's try to save this situation without reinstalling.

Try 
```

cp /etc/apt/sources.list /etc/apt/sources.list-20080921   # Make a backup of your sources.list to be safe
gksu gedit /etc/apt/sources.list
```
Do a search and replace to change every occurrence of "gutsy" to "hardy"

If you have two lines like
```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe

```
then you can just delete the gutsy line.

Then try```


sudo apt-get update
sudo apt-get purge blender
sudo apt-get install blender
```

If you run into any problems, please post your /etc/apt/sources.list

---

### Post by xakh on 2008-09-21
> **unutbu said:**
> Let's try to save this situation without reinstalling.

Try 
```

cp /etc/apt/sources.list /etc/apt/sources.list-20080921   # Make a backup of your sources.list to be safe
gksu gedit /etc/apt/sources.list
```
Do a search and replace to change every occurrence of "gutsy" to "hardy"

If you have two lines like
```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe

```
then you can just delete the gutsy line.

Then try```


sudo apt-get update
sudo apt-get purge blender
sudo apt-get install blender
```

If you run into any problems, please post your /etc/apt/sources.list

Actually, looking at it, all of the Gutsy files are now commented out, so they don't seem to be a problem. If I need to change the comments, let me know, but that seems odd, and sort of tedious. If I have to, I have to, but I really wouldn't want to do this if it's not necessary.

---

### Post by unutbu on 2008-09-21
Let's backup a second. 

Try typing
```

mv ~/.blender ~/.blender-20080921

```
Then try running blender again:
```

blender
```

Does it still crash?

When I launch blender from the terminal I get this output:
```
% blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
```

Do you see any output at all?

---

### Post by xakh on 2008-09-21
yes, it still crashed.
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Segmentation fault
There's my entire output.

---

### Post by unutbu on 2008-09-21
Okay, one more try: Please post the output of
```
ldd /usr/bin/blender-bin
```

---

### Post by xakh on 2008-09-21
linux-vdso.so.1 =>  (0x00007fff813fe000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x00007ffb78f21000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007ffb78cfc000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007ffb78ae5000)
	libpython2.5.so.1.0 => /usr/lib/libpython2.5.so.1.0 (0x00007ffb78775000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007ffb784f8000)
	libgettextpo.so.0 => /usr/lib/libgettextpo.so.0 (0x00007ffb782b6000)
	libHalf.so.2 => /usr/lib/libHalf.so.2 (0x00007ffb78074000)
	libIlmImf.so.2 => /usr/lib/libIlmImf.so.2 (0x00007ffb77e04000)
	libIex.so.2 => /usr/lib/libIex.so.2 (0x00007ffb77be6000)
	libImath.so.2 => /usr/lib/libImath.so.2 (0x00007ffb779e1000)
	libavformat.so.1d => /usr/lib/libavformat.so.1d (0x00007ffb7775a000)
	libavcodec.so.1d => /usr/lib/libavcodec.so.1d (0x00007ffb7711f000)
	libtheora.so.0 => /usr/lib/libtheora.so.0 (0x00007ffb76edc000)
	libraw1394.so.8 => /usr/lib/libraw1394.so.8 (0x00007ffb76cd6000)
	libavutil.so.1d => /usr/lib/libavutil.so.1d (0x00007ffb76acd000)
	libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0x00007ffb766f5000)
	libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x00007ffb764c9000)
	libm.so.6 => /lib/libm.so.6 (0x00007ffb76248000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0x00007ffb76043000)
	libgsm.so.1 => /usr/lib/libgsm.so.1 (0x00007ffb75e36000)
	libdc1394_control.so.13 => /usr/lib/libdc1394_control.so.13 (0x00007ffb75c26000)
	libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x00007ffb75991000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x00007ffb791ac000)
	libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00007ffb7570d000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007ffb7540a000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007ffb75201000)
	libutil.so.1 => /lib/libutil.so.1 (0x00007ffb74ffe000)
	libc.so.6 => /lib/libc.so.6 (0x00007ffb74c9c000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007ffb74a98000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007ffb7487c000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007ffb7466e000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007ffb74363000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0x00007ffb74088000)
	libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0x00007ffb73e1a000)
	libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0x00007ffb73c12000)
	libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0x00007ffb739fd000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007ffb737ec000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007ffb735eb000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007ffb733d0000)
	/lib64/ld-linux-x86-64.so.2 (0x00007ffb79144000)
	librt.so.1 => /lib/librt.so.1 (0x00007ffb731c7000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007ffb72fc5000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007ffb72dc0000)

---

### Post by unutbu on 2008-09-21
Please run```

strace blender 2>&1 | bzip2 > blender.out.bz2
```
Then post blender.out.bz2 as an attachment.

---

### Post by xakh on 2008-09-21
[ATTACH]86004[/ATTACH]
There.

---

### Post by unutbu on 2008-09-21
I've looked through blender.out.bz2, but was unable to find an error which points to the underlying problem.

I'm unfortunately out of ideas on how to fix this gracefully.

I have a suspicion -- but really nothing more than a suspicion -- that if you were to do a clean install of Hardy, you would not have this problem. But that seems like a pretty drastic way to solve a blender problem. On the other hand, if you are experiencing other mysterious problems, perhaps a clean install may be worth it.

---

### Post by xakh on 2008-09-21
well, I don't seem to have any other mysterious problems, and by the way, when I was on gutsy, blender did the same thing, I just didn't want to raise a fuss, since I had no wireless, and little productivity. I've been having this issue for a while, I've just been focusing on fixing everything else first.

---

### Post by SreckoMicic on 2008-09-22
What graphic card you have?
ATI?

---

### Post by Chainz on 2008-09-22
I got into the same problem after upgrading from Feisty to Gutsy.
Reinstalling Gutsy from scratch just solved it all.

Now if you have Hardy in option (and even Intrepid coming soon), use one of these.

---

### Post by hessiess on 2008-09-22
> some form of ATI

its lickly a driver problem with the ati card, try manualy upgrading to the latist driver

---

### Post by Zsola on 2008-09-22
Do you use any particular repositories for Blender, or just the main repos for hardy?

Edit:
Asking because my synaptic only found the 2.45 version of Blender not the newest one...

---

### Post by xakh on 2008-09-22
okay, for everyone. I use ATI, so maybe. I'm also having troubles with Firefox, so I think a clean install of Intrepid may take care of things. I really don't like Opera.

---

