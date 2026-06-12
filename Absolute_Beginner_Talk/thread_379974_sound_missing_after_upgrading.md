---
title: "sound missing after upgrading"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by deepbluegene on 2007-03-09
Hi
i just instated ubuntu updates and now i can not hear sounds from any video sites like youtube, google video and others. i can use skype with pefectly clear voice but no sound for videos.


another problem is that i have GeForce4 MX 4000 AGP 8x card but i can not set resolution to 1280.highest available is 1024. in windows it perfectly working at 1280. 
please help.

---

### Post by overdrank on 2007-03-09
> **deepbluegene said:**
> Hi
i just instated ubuntu updates and now i can not hear sounds from any video sites like youtube, google video and others. i can use skype with pefectly clear voice but no sound for videos.


another problem is that i have GeForce4 MX 4000 AGP 8x card but i can not set resolution to 1280.highest available is 1024. in windows it perfectly working at 1280. 
please help.

Hi if you are using ubuntu dapper, You can go to system,preferences, sounds, and make sure you sound card is set to defautlt.
On your video do you have the right drivers installed.
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Good luck! Hope this helps. :)

---

### Post by deepbluegene on 2007-03-14
sound is working.

i installed latest nvidia drivers it enabled me to go for 1280 resolution but refresh rate was not good.i could feel the blinking effect.

how i can solve this problem of refresh rate i have dell e771 monitor.
thanx

---

### Post by silhouette on 2007-03-14
Try opening a terminal window and running "sudo dpkg-reconfigure xserver-xorg". I forget exactly what this asks you (I'm not at my machine right now) but you should just be able to accept the defaults. At some point you'll come to the list of screen resolutions and refresh rates. Use the space bar to select 1280x1024 (it will probably be followed by 75 Hz). I believe there are more screens after that, but again, you can accept the defaults. Then log out and press Ctrl-Alt-Backspace to restart X.

If you are not able to see the login screen after that and the screen flickers, it means that Linux was really not able to set those options for you. In this case, press Ctrl-Alt-F1 to switch to the first xterm, log in, and type "sudo dpkg-reconfigure xserver-xorg" again, disabling the resolution/refresh rate that was unsuccessful.

Note: I think you can run the risk of ruining your monitor if you choose incorrect settings, though I've never had it happen to me. In any case it's a good idea to be doubly sure that the settings are recommended for your monitor.

---

