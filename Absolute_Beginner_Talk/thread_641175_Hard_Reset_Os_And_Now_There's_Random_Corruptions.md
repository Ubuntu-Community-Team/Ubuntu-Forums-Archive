---
title: "Hard Reset Os And Now There's Random Corruptions"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-15
... -_- help me out....I had a lockup and I could only hold down the power button and reset that way. When I booted back up my console sessions show up solid white, my balloon tips show up solid white, and all my top-window bars are gone from my windows. HELP! 


what happened? and how do I fix it/!!?!!?!

---

### Post by khurrum1990 on 2007-12-15
> **B34ST1Y said:**
> ... -_- help me out....I had a lockup and I could only hold down the power button and reset that way. When I booted back up my console sessions show up solid white, my balloon tips show up solid white, and all my top-window bars are gone from my windows. HELP! 


what happened? and how do I fix it/!!?!!?!
did u just install drivers or something? I doubt there is any corruption. What were u doing before the lockup?

---

### Post by B34ST1Y on 2007-12-15
running a bash command to charge my blackberry (using barry, a blackberry usb tool)    anyway, gutsy locked up on me and all I knew to do was push my power button :(  ....when I booted back into linux, random  things were just....white. however they were still functional (i.e. i could type 'exit' into my white screen of my console and it would exit. )       but if I disable compiz, and go to no visual effects, it goes back to basically normal. >.<

---

### Post by khurrum1990 on 2007-12-15
Actually compiz crashed on ur computer. Can we have details of ur hardware specs? I know compiz crashed cause as u said it goes back to normal as soon turn them off. Thats what must have caused a system lock up.Also which version of Ubuntu r u using? Don't worry ur OS is fine, its just compiz I think from ur description.

---

### Post by B34ST1Y on 2007-12-15
yea, I have an Everex XT5000T ([http://www.everex.com/products/xt5000t/xt5000t.htm](http://www.everex.com/products/xt5000t/xt5000t.htm)) running Ubuntu Gutsy 7.10  . Ok, so how do I fix this up then??

---

### Post by khurrum1990 on 2007-12-15
Try entering these commands in terminal, restart ur computer and enable effects:
sudo nvidia-xconfig --composite
sudo nvidia-xconfig --allow-glx-with-composite
sudo nvidia-xconfig --render-accel
sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by B34ST1Y on 2007-12-15
ran them all, rebooted...and no go, same problem :(


but I just noticed my compiz effects dont work anymore...so youre probably right that compiz crashed out..

---

### Post by khurrum1990 on 2007-12-15
Well one last thing I can think of to get compiz fusion working for u is by either reinstalling ur nvidia drivers. You could also try disabling nvidia drivers, then re enable them by reconfiguring xserver with the command "sudo dpkg-reconfigure xserver-xorg". Choose the vesa driver here if u try this.

One more thing that u can try is reinstalling compiz fusion:
1.sudo apt-get remove compiz compizconfig-settings-manager then do this:
2.sudo apt-get install compiz compizconfig-settings-manager

Try reinstalling compiz fusion first.

---

### Post by daimaru on 2007-12-15
> **B34ST1Y said:**
> gutsy locked up on me and all I knew to do was push my power button :(  ....
for future reference if it happens again --> "**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**oring"  check [this thread]("http://ubuntuforums.org/showthread.php?t=617349&highlight=raising+elephants") for alternative to holding down your power key.

hope it helps with your next lockup :D

---

### Post by B34ST1Y on 2007-12-15
thx daimaru. i'll try that next time.




I tried both of your methods, and neither worked >.< I reinstalled gfx driver, after I tried the compiz reinstall....no go -_-

---

### Post by khurrum1990 on 2007-12-15
have u installed emerald?
sudo apt-get install emerald
Now restart and enable desktop effects and in ur terminal type in:
emerald --replace
tell me what happens?

---

### Post by khurrum1990 on 2007-12-15
try this as well after enabling compiz:
gtk-window-decorator --replace

---

### Post by B34ST1Y on 2007-12-15
I tried both commands...and after hitting enter to execute the command, it returns to the next line...and just sits there...apparently doing nothing..?

---

### Post by khurrum1990 on 2007-12-15
Hi, what happenned? Its been a long time. Anyway turn of ur effects and in terminal type in:
compiz --replace
Post here the output of that command in the terminal.

---

### Post by khurrum1990 on 2007-12-15
Can u try creating another user and enabling compiz fusion for that account and see what happens?

---

### Post by B34ST1Y on 2007-12-15
b34st1y@zer0cool:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0398 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure

---

### Post by B34ST1Y on 2007-12-15
I made a new acct, and it gets the same problems

---

### Post by khurrum1990 on 2007-12-15
It seems that emerald is the problem, remove it by:
sudo apt-get remove emerald and try compiz --replace if this doesn't work then install emerald again and see what happens.

---

### Post by B34ST1Y on 2007-12-15
I tried both of those...and still nothing changes. -_-    

here's the output of compiz --replace btw:

```
b34st1y@zer0cool:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0398 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
compiz.real: /build/buildd/libcairo-1.4.10/src/cairo.c:259: cairo_destroy: Assertion `cr->ref_count > 0' failed.
Aborted (core dumped)



```

---

### Post by khurrum1990 on 2007-12-15
u can check ur file system for corruptions using the fsck command or something. u may need to repair installation.

---

### Post by B34ST1Y on 2007-12-15
do I run fsck at the grub command line options?

---

### Post by khurrum1990 on 2007-12-16
no in recovery mode

---

