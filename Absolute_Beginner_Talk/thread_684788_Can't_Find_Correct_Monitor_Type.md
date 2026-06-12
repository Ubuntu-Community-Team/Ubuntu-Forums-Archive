---
title: "Can't Find Correct Monitor Type"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by sidspappy on 2008-02-01
Hello.

I'm a first time poster, and absolute noob at Linux and Ubuntu. I just installed 7.10 with the LiveCD on a second SATA HD (first HD has Win XP installed). I got most things working well, even the nvidia restricted drivers for my onboard GeForce 6150LE. At first startup, Ubuntu said it could not detect my monitor type. It chose the default plug-n-play type. So, I went in and looked for my monitor, a Gateway LCD 17" widescreen (FPD1775W), which has a native res of 1280x720. Well, under Gateway, there was NO FPD1775W. So I took a wild guess, and chose a FPD1730 (r9) and clicked on "widescreen" (the FPD 1730, it turns out, is not widescreen).  Luckily, Ubuntu seemed to like it, and started up in 1280x720 @ 50hz. When I go into resolutions, it shows that I can use 640x480, 800x600, 1280x720, and 1280x1024. Unfortunately, I cannot change the refresh (my native is 60hz) to native. I only have 50 and 52hz as choices.

Is there a way to download the correct monitor driver, like .inf files in Windows? My searches turn up a lot about modelines, but I don't know if that is what I need to fuss with.

Should I consider myself lucky that the install seems to have gone off with relatively few problems? Aside from having to swap out my USB wireless adapter to an older Netgear that Ubuntu could actually recognize, everything important seems to be functioning. Well, I don't want to speak too soon...I still need to test network printing...

Thanks for reading, sorry for the rambling, and I hope someone can help me out.

---

### Post by Thelasko on 2008-02-01
Ok, this may seem a little scary for a noob but the best way to reconfigure your screen is by going into the terminal and entering: ```
sudo dpkg-reconfigure xserver-xorg
```  This will give you a bunch of setup screens in which you can configure your monitor and video card.  I would recommend writing down this command before you do this so if you screw up you can fix it later, because if it doesn't work you will be stuck in the terminal next time you boot.  

Make sure you know your monitor's settings (resolution, refresh rate, horizontal and vertical rate too if you can find it) and which video driver you use.  Your first time through it I recommend choosing all of the default choices with exception to the video driver.  Make sure you use the Nvidia driver that you installed earlier.  If you still aren't happy with your setup using the default settings try it again, this time entering them manually.  It guides you through everything pretty nicely, just follow the directions on the screen.

When you are finished with your configuration you can simply hit Ctrl+Alt+backspace to restart X and find out if you got it correct.

---

### Post by sidspappy on 2008-02-01
Thank you for your response, Thelasko. I will try out your suggestion after I get back home.

Does anyone think using the monitor settings for a different monitor increase chances of damaging the monitor?

---

### Post by Thelasko on 2008-02-01
Something I should mention, on newer LCD monitors if you press the menu button it should tell you what it's default resolution and refresh rate is.  It might also complain if your computer isn't giving it the same settings.   Different resolutions won't hurt the monitor, but having too high of a refresh rate might.  [Wikipedia has a good article.]("http://en.wikipedia.org/wiki/Refresh_rate")

---

