---
title: "&quot;sync. out of range&quot; problem solved"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-17
Hi, yesterday I wrot asking for help in hte configuration of my monitor, my monitor is a Samsung Syncmaster 551v, and the problem it showed was that when you started linux the screen turned black with a red square that said: "Sync. out of Range" moving everywhere slowly. I'll tell you the way I solved it if anytime anyone needs help.
First of all I installed the alternate disc for Ubuntu, in text mode. Once everything is installed, the computer will reboot and the program will start, (here it was were the message appeared) so when the message appears press Ctrl+Alt+F4, then enter yur user and password (the ones you created in the installation) and then type the following: "sudo dpkg-reconfigure xserver-xorg" it will send you to configure a lot of things, practically leave everything the way it was until you find the resolution for your monitor, there select the last three (1024x768 , 800x600, and 640x480) and continue, when it asks you about configuring the monitor in easy, medium, or advanced mode select advanced, then on the horizontal frequency or range change the 30-55 to 31.5-47.5, and on the vertical change the 50-120 to 40-70, and select 24 bit depth. When it finishes all and there appears the line to write a command below the configuration you made, type: "sudo /etc/init.d/gdm restart". This way it should work fine, but you will only achieve a maximun resolution of 800x600.
I hope this could help someone if he/she has the problem I had.
Cheers

---

### Post by Bachstelze on 2006-12-17
The ideal values for HorizSync and VertRefresh depend on your monitor. They should be mentioned in your monitor's doc so check in there if you want to use your monitor's best resolution.

---

### Post by Jorge32 on 2006-12-17
I already searched for them, but in the ones I had it doesn't says anything, I also searchen in the internet, and there it said it was the default 30-55 and 50-120, but if I tried with them it appeared the message again, anyway, thanks, I'll search more documents. maybe I have some of them somewhere.

---

### Post by jimrz on 2006-12-17
> **Jorge32 said:**
> Hi, yesterday I wrot asking for help in hte configuration of my monitor, my monitor is a Samsung Syncmaster 551v, and the problem it showed was that when you started linux the screen turned black with a red square that said: "Sync. out of Range" moving everywhere slowly. I'll tell you the way I solved it if anytime anyone needs help.
First of all I installed the alternate disc for Ubuntu, in text mode. Once everything is installed, the computer will reboot and the program will start, (here it was were the message appeared) so when the message appears press Ctrl+Alt+F4, then enter yur user and password (the ones you created in the installation) and then type the following: "sudo dpkg-reconfigure xserver-xorg" it will send you to configure a lot of things, practically leave everything the way it was until you find the resolution for your monitor, there select the last three (1024x768 , 800x600, and 640x480) and continue, when it asks you about configuring the monitor in easy, medium, or advanced mode select advanced, then on the horizontal frequency or range change the 30-55 to 31.5-47.5, and on the vertical change the 50-120 to 40-70, and select 24 bit depth. When it finishes all and there appears the line to write a command below the configuration you made, type: "sudo /etc/init.d/gdm restart". This way it should work fine, but you will only achieve a maximun resolution of 800x600.
I hope this could help someone if he/she has the problem I had.
Cheers

you may be able to achieve a higher resolution by selecting 16 bit depth rather than 24. this worked on an old laptop that I had.

---

### Post by don_m on 2007-01-29
This helped me with my Samsung 753DF monitor that was having the sync out of range problem after having to switch monitors.

I ended up logging in and doublechecking xorg.conf to see whether the configuration was fine. I had to correct a couple of things like putting a "-" between numbers and such.

I also found that the directory is /etc/X11 instead of /etc/x11.

I wish I could raise the frequency a bit though.

---

### Post by don_m on 2007-02-03
As an update to my post, for the Samsung 753DF monitor, I believe the optimal setting is 1024 X 768 at 85Hz. This is the same setting for the Windows 2000 installed on the same system.

I found that moving to higher resolutions would on max out a refresh rate of 60Hz, and that is hard on the eyes.

---

### Post by Rohen on 2007-08-14
Hey Guy:

This might be what I've been looking for, can I PM you and send you my specs?  Think you could help me out please.  I am a completely noob when it comes to configuring Linux stuff.  Let me know k?  Thanks in advance :)

---

