---
title: "Nvidia 8800 GTS Drivers in Feisty Ubuntu 64bit"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by pthickett on 2007-07-28
Guys,

I have just installed ubuntu on my desktop pc, its a intel core 2 duo with an nvidia 8800 GTS graphics card, the only problem I had when I first installed Ubuntu was that the max res was 1024 x 768, so I am assuming it hasnt got the correct drivers for my card. So i installed automatix and installed the nvidia drivers from there and on reboot came back with a load of x-server errors and wouldnt boot. So now I have re-installed ubuntu but I dont know what to do to correct the driver issue. Everything else however seems to be running fine.

Thanks

Pete

---

### Post by jimbob on 2007-07-28
Make sure you have nvidia-glx installed along with the linux-restricted modules for your particular 
kernel.  Automatix should have taken care of this but you never know.

Regenerate your xorg.conf file with  dpkg-reconfigure -phigh xserver-xorg
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by pthickett on 2007-07-28
So as i have a fresh install of ubuntu what do i do first? Should i install the drivers with automatix and then regenerate the xorg.conf file? i am quite new to this linux stuff so i need as step by step as possible! :-)

---

### Post by jimbob on 2007-07-29
Check this post related to your graphics card:

[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

Also you might want to try using envy which is mentioned in the link above and with which
many have had success.

The forum is rich with threads on the 8800.  Just do a search on it and read what others have done to get it going.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by pthickett on 2007-08-04
Success!! I used envy, and it seems to have worked fine. Now i am doing this through a nice crisp resolution and have funky wobbly windows all over the place! very impressed!

However I do have a couple of issues, just that when i configure the resolution in the nvidia tools program, it does not retain them for the next time I reboot, and if I choose to save to the x server function it says it cannot remove the backup???

Also I seem to not have a ubuntu loading or shutdown screen for some reason, my monitor goes into standby for those times, although I think that was happening before envy got involved.

Any advice would be gladly received!

---

### Post by jimbob on 2007-08-05
What resolution is the one you want to be permanent?

Please post a copy of your /etc/X11/xorg.conf file.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by pthickett on 2007-08-05
It always restarts in 1024 x 768, but I then have to change it to the max resolution of my lcd monitor, which is 1280 x 1024.

Attached is a text file with the contents of my xorg.conf file.

Thanks for your help

---

### Post by jimbob on 2007-08-05
Save the current copy of your xorg.conf file as xorg.conf.save then change all of the modes lines in the Screen section to look like the following:

Modes      "1280x1024" "1024x768" "800x600" "640x480"

Now reboot and it should come up as 1280x1024.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

