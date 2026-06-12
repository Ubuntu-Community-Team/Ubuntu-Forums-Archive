---
title: "Video Card Problem"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by KB2HSH on 2008-01-28
Hello everyone.

I have a specific issue here.

I have a MS-6389 motherboard that wa made for Gateway in 2000.  It was intended to run Windows 98 and Windows Me, although it has run EVERYTHING I have put at it flawlessly...

I am running 7.10, and until I started playing with the video...it was perfect.  The motherboard's built-in video is Savage4-3D.  It was running fine, until I attempted to put an NVidia card in.  It didn't recognize the NVidia card I attempted...so when I took it out to go back to the onboard video, it started giving me the VESA video error.  Now, every time I start up, I can't switch it back to the Savage driver that was working.

Please help!!!!

John KB2HSH

---

### Post by forrestcupp on 2008-01-28
Boot to your recovery mode which is command line, and type:
```
sudo dpkg-reconfigure xserver-xorg
```
Go through the setup answering all of the questions.  This will reset X.  Make sure to choose plain vesa drivers.  Reboot and you should be ok.

Edit:
But when you installed the nvidia card, did you check your bios settings to see if there is an option to disable onboard video?  Maybe they were conflicting and you can just turn off onboard video.  If so, and you can get the nvidia card to recognize, you will still have to reconfigure X.

---

### Post by ptn107 on 2008-01-28
You may be able to restore an old X11 config file.  Check your /etc/X11 folder for any old configuration files particularly xorg.conf.# where # is any number.  If those files exist check out their contents to find which one was the working configuration  before you added the nvidia card.  Copy it over your existing xorg.conf (after you back it up of course) and give your system a restart.

---

### Post by syn` on 2008-01-28
> **forrestcupp said:**
> But when you installed the nvidia card, did you check your bios settings to see if there is an option to disable onboard video?  Maybe they were conflicting and you can just turn off onboard video.  If so, and you can get the nvidia card to recognize, you will still have to reconfigure X.

It doesn't matter because Linux doesn't use BIOS in the first place. It detects the hardware by itself as soon as it starts booting.

---

### Post by forrestcupp on 2008-01-28
> **syn` said:**
> It doesn't matter because Linux doesn't use BIOS in the first place. It detects the hardware by itself as soon as it starts booting.

That's not really true.  Every system checks the BIOS as soon as it is turned on.  The BIOS is accessed before a Linux boot loader is.  If there are BIOS level problems before Linux boots, it won't work in Linux or Windows or anything.  If what you said were true, then I wouldn't be able to disable my onboard audio chip in my BIOS; Linux would just recognize it no matter what the BIOS settings are.  But I can disable it, and when it is disabled in the BIOS, Linux doesn't recognize it.

---

### Post by syn` on 2008-01-28
> **forrestcupp said:**
> That's not really true.  Every system checks the BIOS as soon as it is turned on.  The BIOS is accessed before a Linux boot loader is.  If there are BIOS level problems before Linux boots, it won't work in Linux or Windows or anything.  If what you said were true, then I wouldn't be able to disable my onboard audio chip in my BIOS; Linux would just recognize it no matter what the BIOS settings are.  But I can disable it, and when it is disabled in the BIOS, Linux doesn't recognize it.

Have a look at LinuxBIOS, it's very interesting.

GNU/Linux does its own hardware detection independently of the BIOS settings. That's why people with onboard sound or graphics can have a lot of trouble disabling them in favour of PCI/AGP upgrades when they do it in BIOS. If it's disabled in BIOS how is the OS still using the hardware???? Answer: the OS ignores the BIOS and detects the hardware itself.

Traditional BIOS is hardly needed for Linux, all that is needed from the BIOS is to load a bootloader. There's a good article: [LinuxBIOS - A truly GPLed Free Software BIOS](http://linuxhelp.blogspot.com/2006/11/linuxbios-truly-gpled-free-software.html).

---

### Post by KB2HSH on 2008-01-29
Thank you!!!  The commands you gave me worked!!!

I am so thrilled!

This PC ran Ubuntu 4.10...and then nothing else.  It wasn't until 6.10 that I could use it again....and now 7.10 is working!

Count me in as an Ubuntu convert!

John

---

### Post by syn` on 2008-01-29
> **KB2HSH said:**
> Thank you!!!  The commands you gave me worked!!!

I am so thrilled!

This PC ran Ubuntu 4.10...and then nothing else.  It wasn't until 6.10 that I could use it again....and now 7.10 is working!

Count me in as an Ubuntu convert!

John

Glad it worked out for you.

---

