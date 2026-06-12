---
title: "help with install of philips spc900nc webcam"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by StinkoMaximus on 2007-08-01
hello.  i have just purchased a philips spc900nc webcam.  i went to [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) and got the driver.  followed the instructions (as best as i could).  

im running ubuntu feisty 7.04 (i think), I installed the source for my kernel, 2.6.20-16-generic (i think), gcc was already installed (i don't know if its the version that compiled my kernel though)

when i got to the point where it says run "make" it throws a tizzie and spits out  

stinko@Wraith:~/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/stinko/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/stinko/pwc-10.0.12-rc1/pwc-if.o
In file included from /home/stinko/pwc-10.0.12-rc1/pwc-if.c:69:
/home/stinko/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:166: error: variable ‘pwc_template’ has initializer but incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:167: error: unknown field ‘owner’ specified in initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:167: warning: excess elements in struct initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:167: warning: (near initialization for ‘pwc_template’)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:168: error: unknown field ‘name’ specified in initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:168: warning: excess elements in struct initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:168: warning: (near initialization for ‘pwc_template’)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:169: error: unknown field ‘type’ specified in initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:169: warning: excess elements in struct initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:169: warning: (near initialization for ‘pwc_template’)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:170: error: unknown field ‘hardware’ specified in initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:170: warning: excess elements in struct initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:170: warning: (near initialization for ‘pwc_template’)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:171: error: unknown field ‘release’ specified in initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:171: error: ‘video_device_release’ undeclared here (not in a function)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:171: warning: excess elements in struct initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:171: warning: (near initialization for ‘pwc_template’)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:172: error: unknown field ‘fops’ specified in initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:172: warning: excess elements in struct initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:172: warning: (near initialization for ‘pwc_template’)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:173: error: unknown field ‘minor’ specified in initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:173: warning: excess elements in struct initializer
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:173: warning: (near initialization for ‘pwc_template’)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_isoc_init’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:921: warning: assignment from incompatible pointer type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘cd_to_pwc’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1019: warning: implicit declaration of function ‘to_video_device’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1019: warning: initialization makes pointer from integer without a cast
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1020: warning: implicit declaration of function ‘video_get_drvdata’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1020: warning: return makes pointer from integer without a cast
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_create_sysfs_files’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1062: warning: initialization makes pointer from integer without a cast
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1064: warning: implicit declaration of function ‘video_device_create_file’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_remove_sysfs_files’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1070: warning: initialization makes pointer from integer without a cast
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1072: warning: implicit declaration of function ‘video_device_remove_file’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_open’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1112: warning: implicit declaration of function ‘video_devdata’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1112: warning: initialization makes pointer from integer without a cast
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1117: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_close’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1231: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_read’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1292: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_poll’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1359: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_ioctl’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1375: warning: implicit declaration of function ‘video_usercopy’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_mmap’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1388: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_probe’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1722: warning: implicit declaration of function ‘video_device_alloc’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1722: warning: assignment makes pointer from integer without a cast
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1730: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1731: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1732: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1733: warning: implicit declaration of function ‘video_set_drvdata’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1756: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1757: warning: implicit declaration of function ‘video_register_device’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1757: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1757: error: (Each undeclared identifier is reported only once
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1757: error: for each function it appears in.)
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1760: warning: implicit declaration of function ‘video_device_release’
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1765: error: dereferencing pointer to incomplete type
/home/stinko/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_disconnect’:
/home/stinko/pwc-10.0.12-rc1/pwc-if.c:1819: warning: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/stinko/pwc-10.0.12-rc1/pwc-if.o] Error 1
make[1]: *** [_module_/home/stinko/pwc-10.0.12-rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

if someone can help please it would be much appreciated.  Thanks in advance.

---

### Post by aktiwers on 2007-08-01
I have used some of the tips from this page to check if it works out of the box.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

These 2 I liked:

> There is a nifty little application called [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] camorama]("http://camorama.fixedgear.org/") to view, alter and save images from a webcam. Simply install it via apt:  
```
  sudo apt-get install camorama
```
*xawtv* is another program you can use to test the camera.  
```
  sudo apt-get install xawtv
```
And also

> [ MPlayer]("https://help.ubuntu.com/community/MPlayer") is capaple of displaying a webcam video stream, for example with the command line ```
mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0
```
The resolution (width=??? & height=??? ) should be chosen to match the output of your device.  


Also if you want to use that driver you downloaded, first install build essensial:
```
sudo apt-get install build-essential
```

Then cd to the folder of the driver and:
```
./configure
make
sudo make install

```

and see if that works.

---

### Post by StinkoMaximus on 2007-08-01
oh my god that is soooo much easier than i thought it would be.  works out of the box.  thanks for telling me about camorama.  is there a way to test the microphone?

Thanks for replying so quickly (i thought i would have to wait a while) :-)
Cheers
Stinko

---

### Post by aktiwers on 2007-08-01
Is the microphone on the cam?
If so, take a look at the link above again.

> and with audio 
  ```
mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
```
Type 'man mencoder' for more info on the audio options. In the example, /dev/dsp1 refers to the webcam USB Audio device, while /dev/dsp would refer to the sound card 
 You may need to install these programs with  
  ```
sudo apt-get install mplayer mencoder
```
 




If its not on the cam it should work out if the box. Just double click on the sound icon in your top-right corner and look if its enabled.

You can also test it by going to
Applications => Sound & Video => Sound Recorder

And start recording :)

---

