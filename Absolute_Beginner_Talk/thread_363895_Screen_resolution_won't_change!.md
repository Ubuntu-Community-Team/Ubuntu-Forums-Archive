---
title: "Screen resolution won't change!"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Troubled on 2007-02-17
I have a widescreen monitor that can run at 1280x768, but from the start, Ubuntu has used a 1024x768 resolution, causing my screen to be stretched. Naturally, I checked to see if there were any alternatives, going to System > Screen Resolution, but there were none.

So I checked the file at /etc/X11/xorg.conf, and the only resolution listed was the proper, fullscreen 1280x768! :O
Now I don't know what to do -- all of the tips for changing screen resolution hinged around adjusting the xorg file, but it appears to already be adjusted! And yet, it is inconsistent with what the Screen Resolution window offers, which is what I actually see.

Is there any (other) way to get a full screen resolution?

---

### Post by Troubled on 2007-02-17
bump after edit

---

### Post by annda on 2007-02-17
what is your video card? for many cards, you will have to install an appropriate driver.

---

### Post by ubix on 2007-02-19
Perhaps I messed terribly, but it looks you haven't found the **[COLOR="Blue"]Systems -> Preferences -> Screen Resolution[/COLOR]** at all? Ideally, one should not mess around with /etc/... files directly. If everything is installed correctly, one should be able to simply change the resolution from GUI menus.

---

### Post by joshkidd on 2007-02-19
I don't know if this helps at all.  I once had the same problem that I was able to fix by setting HorizSync and VertRefresh to the appropriate range in the "Monitor" section of xorg.conf.  What kind of monitor do you have specificly?  Knowing that may help determine if this is the issue and what ranges to set the options to.

---

### Post by ubix on 2007-02-19
Check out similar issue in this thread: [http://ubuntuforums.org/showthread.php?t=365232]("http://ubuntuforums.org/showthread.php?t=365232")

---

### Post by Cheddarhead on 2007-02-19
I have tried f'n everything... same problem as the thread starter.. I am about ready to dump linux altogether because of this resolution issue. I have a geforce4 ti, I've done everything I have found on dozens of forums and STILL cant get ebtter than 1024x768 crap rez. I paid buku bucks for a nice 19" lcd and ubuntu looks like crap. The basic native rez running windows, even with onboard video was 1280x1024... I am really bummed, I see this is an issue with many users, not just me... ANY more ideas would be welcomed...

C

---

### Post by Bachstelze on 2007-02-19
Have you tried to follow [these instructions](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) to install your nvidia drivers ?

---

### Post by Cheddarhead on 2007-02-19
Yep, one of the first things I tried. I have the nvidia driver installed fine... just that the highest rez option I get is 1024x768

---

### Post by dfreer on 2007-02-19
Post your /etc/X11/xorg.conf file here and we might be able to help you out more :)

---

### Post by aktiwers on 2007-02-19
Try Envy, it should install your drivers automaticly!
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And follow the instructions on the page. Worked great for me.

---

### Post by ubix on 2007-02-19
> **Cheddarhead said:**
> ... I am about ready to dump linux altogether because of this resolution issue ...My sentiment exactly. I like Ubuntu very much, for many reasons, but it just isn't good enough for serious work. However, I do believe we should try to help it fight the commercial trends. It is not surprising that graphical cards are at the forefront where the most important battles are fought.  It is more than disgusting how hardware vendors are helping Micro$oft in their dirty ways that are if not illegal certainly unethical, whereby they exploit the features of their legacy proprietary device drivers, using old libraries, and compilers in newer OS releases. I think we should not try to accommodate the vendors, by including older header files, libraries and compilers to compile new kernels into old environment, instead we should declare which drivers and which vendors are the culprits and strongly suggest to users to avoid using the offending hardware and glamorize the makers of this crap! 
:guitar: [-X

---

### Post by Cheddarhead on 2007-02-19
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

Fixed it with this thread... boy, what a hassle though, shouldnt be that difficult to change screen rez... I like linux, but this is why its not mainstream... maybe 1 in 50 average pc users could do it... if that...

C

---

### Post by Troubled on 2007-02-22
I've finally fixed this problem, using the more detailed instructions I found here:
[http://ubuntuforums.org/showthread.php?p=2163641&posted=1#post2163528](http://ubuntuforums.org/showthread.php?p=2163641&posted=1#post2163528)

However, it seems that either my refresh rate has gone down significantly, or (what I believe is more likely) that my graphics card no longer has sufficient RAM to process the graphics.

I believe that I can fix this with another round of reconfiguring xorg. Does anyone have any suggestions as to how much memory I might feasibly devote to graphics (without compromising the rest of the system)?

---

### Post by Zimmer on 2007-02-22
> **Troubled said:**
> I have a widescreen monitor that can run at 1280x768, but from the start, Ubuntu has used a 1024x768 resolution, causing my screen to be stretched. Naturally, I checked to see if there were any alternatives, going to System > Screen Resolution, but there were none.

So I checked the file at /etc/X11/xorg.conf, and the only resolution listed was the proper, fullscreen 1280x768! :O
Now I don't know what to do -- all of the tips for changing screen resolution hinged around adjusting the xorg file, but it appears to already be adjusted! And yet, it is inconsistent with what the Screen Resolution window offers, which is what I actually see.

Is there any (other) way to get a full screen resolution?

Have a look at this thread to see if it will help you with the screen resolutions.... using the monitor info from the /var/log/xorg.0.log  file...
[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

---

