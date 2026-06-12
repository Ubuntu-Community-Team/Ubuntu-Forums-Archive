---
title: "Monitor Resolution"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2006-11-04
I told my friend yesterday to send a post for me about this problem, but i can't see it anywhere.
Here's the problem:
-I have a SAMSUNG 793DF mnitor which is 17".I didn't had this kind of problem in windows, so i know this is a linux problem. When i go to the screen resolution option (in Ubuntu) the default setting is 1280x768 with 61 Hz refresh rate. This resolution is too big for my monitor and the flashing make's my eyes burn after i look about 5 minutes on the monitor. I tried a thousand times to reset my resolution to 1024x768, but it won't work. After i press the OK button it screw's up the screen and jump's back to the log in screen where i have to sign in my user name and password. and the resolution is the same. I'm also afraid that this can destroy my monitor and graphich card . I'm totally hopeless...](*,)

---

### Post by bulldog on 2006-11-04
Did you install any graphics drivers?

If your graphics are recognized properly and you have the drivers installed,you should be able to choose the right refresh rate and resolution.

Did you try to reconfigure your xorg?```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` and choose the preferences you want.

---

### Post by Portable_Jim on 2006-11-04
Does this help?

[http://www.ubuntuforums.org/showthread.php?t=138370&highlight=60Hz](http://www.ubuntuforums.org/showthread.php?t=138370&highlight=60Hz)

---

### Post by Sterbik on 2006-11-04
I'm new to linux (i like it even more than windows) so the two operating systems are totally different. I have two questions:
1.you write me a code: sudo dpkg-reconfigure -phigh  xserver-xorg
-what do i have to do with it, how and where do i have to type it.
2. My graphic card is ASUS Ati radeon 9600se. Will the drivers work which came with the card?

---

### Post by bulldog on 2006-11-04
The command you should copy and paste into a terminal

For your graphics driver you should do a search on the forum,I am a nVidia user,but there's a lot of info in the Wiki as well.

[http://www.ubuntuforums.org/showthread.php?t=292013&highlight=Ati+drivers](http://www.ubuntuforums.org/showthread.php?t=292013&highlight=Ati+drivers)

---

### Post by Sterbik on 2006-11-08
A few days earlier i tried your suggestion, to do look around in the terminal. I succesfully installed the drivers,now i can choose even more type of resolutions and refresh rates. Theres a problem in the refresh rate. Even if i choose 85hz or 87hz the screen is working like it would be only 70 Hz. In windows i'm only using 75Hz, but it's working perfectly and my eyes don't hurt. I didn't find any update driver on the internet. I forgot to say that mmy graphic card id Ati Radeon 9600SE with 128 mb.:-? ](*,)

---

### Post by Sterbik on 2006-11-09
Someone please help me! If i use ubuntu with this refresh rate i have to buy me some glasses.8)

---

