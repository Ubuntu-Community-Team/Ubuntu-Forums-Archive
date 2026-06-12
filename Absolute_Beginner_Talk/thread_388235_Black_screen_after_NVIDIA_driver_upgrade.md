---
title: "Black screen after NVIDIA driver upgrade"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by RodneyW on 2007-03-19
Hello,

Please help.
Ive tried installing an updated driver 9755 for my geforce6150 onboard card and now when I restarted after installation was complete, i have a totally black screen, no flashing cursor or anything. I had driver 8174 working perfectly and now am regretting trying to update it but I guess its something I need to learn. I followed exactly the instructions posted here [http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)   which is directly from nvidia. Any ideas?

---

### Post by renzokuken on 2007-03-19
can you access a TTY terminal screen?

try pressing Ctrl+Alt+F1 (or F2/F3/F4 up to F6).

it should move you to a black terminal screen where it will ask you to log in. from there you can change to the generic "vesa" driver which should give you back grafix so you can try reinstalling the nvidia driver.....i recommend using Envy

to revert to the vesa driver, log in at the termial screen and type

```
sudo dpkg-reconfigure xserver-xorg
```

just keep the defaults for most of them but when you get to the driver section select "vesa" instead of "nvidia". keep selecting defaults then reboot when finished

then you can more easily try and repair/reinstall the nvidia driver

---

### Post by RodneyW on 2007-03-19
I can f1, ill try that now thx

I have envy on flash drive

---

### Post by renzokuken on 2007-03-19
check out [www.albertomilone.com](www.albertomilone.com) (the Projects and Guides sections) for more detail on how to use envy.

---

### Post by renzokuken on 2007-03-19
an alternative to envy which i actually use is albert's bleeding edge repos.

[http://www.albertomilone.com/instructions.html](http://www.albertomilone.com/instructions.html)

---

### Post by RodneyW on 2007-03-19
Unfortunately changing to vesa has made no difference. Still a totally black screen. Any other ideas? I dont want to have to reformat because I had just finally got it all set up how I like it.

---

### Post by RodneyW on 2007-03-19
Ive also tried with the nv driver in reconfig, also doesnt work. 
Does this mean I have to reformat now? I hope not because I was just starting to get to like linux and I dont have the time to do it all again.

---

### Post by Najand on 2007-03-19
Probably not. Look in /etc/X11/ folder for back ups of /etc/X11/xorg.conf and try to change the filenames to xorg.conf and restart your X using ctrl+alt+backspace. If the gdm has been already disabled use terminal in tty1~6 and run "startx" command.

---

### Post by RodneyW on 2007-03-19
How do i look in /etc/X11/ from within the Ctrl F1 terminal. And then how do I rename the backup file xorg.conf_backup to /etc/X11/xorg.conf if I do have it there. If not can I copy the file /etc/X11/xorg.conf from the boot cd and replace the one on the hdd with it? Can I do this from within the boot CD when it has loaded, I cant find my drive if I load the boot cd?

---

### Post by Najand on 2007-03-19
For viewing files in Terminal you can use any of these commands:
cat
more
less
And for editing files you can use:
nano
vi
emacs
Well, just do
```

ls -l /etc/X11

```
and see any files starting with: xorg.conf there.
If there is one... first backup you current xorg using
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.070319235424

```
which 070319235424 is the time now or anything else you  like.
Then select one of backups which seems you were using before the upgrade
and then use
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

---

### Post by RodneyW on 2007-03-19
No I cant seem to get it to work. Im fairly sure I edited the commands above to point to the relevant oldest file in that directory.

Is the problem definatley _only_ my xorg.conf file?
Or did the directions I followed on link at top of post change something else?
If they are the same, can I just take the xorg.conf file off the cd and at least get it to boot with vesa driver and start again from there? If so how is it done?
I dont understand why it takes hours to get a video card to work. I just want to install the driver and it works? What am I doing wrong. Maybe I shouldnt have updated a working driver already that I had going, but if it is going to take me hours every time I need to do something with a video card driver it is going to cause me a lot of stress so I really need to work this out. Are the drivers faulty for my video card, it says they are for my card at nvidia, but maybe dont work with efty?
Any help greatly appreciated.

---

### Post by renzokuken on 2007-03-19
no it may not be. did you unload the old nvidia driver module before updating to the new one?

did you blacklist the "nv" module?

there could be a few processes causing the problem

go to the CTRL+Alt+F1 terminal again and type

```
dmesg
```

see if there are any error messages in there containing "nvidia" or "vga" or grafix related terms like that

could try

```
dmesg | grep vga
```

to shorten the output

---

