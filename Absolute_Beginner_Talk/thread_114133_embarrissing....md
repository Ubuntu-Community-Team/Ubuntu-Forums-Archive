---
title: "embarrissing..."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by protomammal on 2006-01-07
This should give other Linux newbies a laugh.
Don't believe I'm having to ask this.
My screen resolution seems to be "stuck" at 640X480. Change screen resolution offers no other option. Cannot manually alter the settings.
I'm using an AMD processor with a nvidia 5700LE card. Not having this problem with Windows or Knopplix (also newly installed).
Driving me nuts. Can't navigate in this resolution. Keep having to switch back to Windows or Knopplix to find answers.
My geeky 12 year old is starting to hint that I should ride the special yellow bus.
Help.

---

### Post by dcast on 2006-01-07
are the correct drivers installed? you need to find what drivers you need and then take it from there. Try searching looking around for the correct drivers. Also you might try this: [http://http://www.ubuntuforums.org/showthread.php?t=75074]("http://http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by protomammal on 2006-01-07
[QUOTE=dcast]are the correct drivers installed? you need to find what drivers you need and then take it from there. Try searching looking around for the correct drivers. Also you might try this: [http://http://www.ubuntuforums.org/showthread.php?t=75074]("http://http://www.ubuntuforums.org/showthread.php?t=75074")[/QUOTE]

 I have indeed attemped to install the proper drivers. It's somewhat difficult to navigate the 62 pages of posts in the hardware forum in this resolution. Don't really understand why my default settings are  640 X 480. Even without nvidia drivers Knopplix and SuSe start out at 1024 X 768 or so. Prehaps I have a bad download?
Is there any particular reason your link carries me to Microsoft.com? Are you trying to tell me something?:)

---

### Post by hen3rz on 2006-01-07
.

---

### Post by matthew on 2006-01-07
Exit the graphic interface by hitting Ctrl+Alt+F1

Log in again at the new login prompt

Type this to stop xserver (your graphic desktop interface control program which we are about to reconfigure)```
sudo /etc/init.d/gdm stop
``` 
Type ```
 sudo dpkg-reconfigure xserver-xorg
```Follow the prompts. If you aren't sure what to choose just hit enter to keep whatever is there. At some point you will have a chance to choose several display resolutions. Highlight the ones you want using the spacebar. NOTE: for this process, spacebar highlights, tab moves from choice to choice, and enter selects...this will make sense when you run it.

When finished and back at the command prompt type```
sudo /etc/init.d/gdm start
```and all should be well with the world. If it's not, post a followup and if I'm not here someone else is sure to jump in and help out. Good luck!!

---

### Post by racecat on 2006-01-07
Try this thread:

[HTML]http://ubuntuforums.org/showthread.php?t=83973[/HTML]

Also note that when you boot, Linux detects your monitor. I have a KVM switch and it got me a couple of times before I figured it out. I was switched to the other system while Ubuntu booted up. Only 640X480 was available.

Good Luck,
Bill

---

