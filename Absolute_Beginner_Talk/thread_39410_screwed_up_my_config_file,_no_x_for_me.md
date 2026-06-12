---
title: "screwed up my config file, no x for me"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by meat on 2005-06-04
Well, trying to update my video driver, so I could pick a higher resolution, I messed up my xorg.conf file, so it won't load x.  I figure I could use my backup file, but I have no idea how to do it in terminal mode.

I can't believe how dificult it is just to install a video driver.  I tried doing it by using sh *.nv in terminal, but then I got some error that the kernal wasn't compiled.  Then I did it using the repositories and packages and it worked, I got the logo, but still couldn't change the resolution.  Then I read I had to edit my xorg.conf file, so I did.

---

### Post by crane on 2005-06-04
Just log in in terminal the you can edit the xorg.conf with [color=blue]
sudo vi /etc/X11/xorg.conf[/color]

Or if you have a back up use the mv command
[color=blue]mv /etc/X11/xorg.conf.bak /etc/X11xorg.conf[/color]
That will rename the file. 
As far as resolution setting, just edit the monitor section of the file. Change the vert and horz refresh rates to what ever your monitor specs are.

Good Luck

---

### Post by Kyral on 2005-06-04
to copy a file is easy (in this case you are also renaming)

```
 sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 
```

Of course, if your backup is named something other than xorg.conf.backup, use that :D

---

### Post by meat on 2005-06-04
Woo Hoo, I'm back in X.  For some reason when I try to change to the X11 directory it keeps saying directory does not exist.  I know it is case sensitive, but it won't let me in.  I am in root /etc and I type cd /X11 and it says no such directory exists.

I still can not change my resolution though.  I got the nvidia screen and I changed the resolutions in the conf file and changed nv to nvidia and I still get the same o'l 1024x768

---

### Post by meat on 2005-06-04
I finally fixed it.  I had to update my refresh rates in my xorg.conf file to the same as my monitor and it worked.

---

### Post by crane on 2005-06-05
[QUOTE=meat]I finally fixed it.  I had to update my refresh rates in my xorg.conf file to the same as my monitor and it worked.[/QUOTE]


Congrats.

Don't know if you figured it out or not but when you were in  /etc all you have to type to get to X11 is [color=blue]cd X11[/color]

---

### Post by meat on 2005-06-05
I figured another way, but I will try that.  Thanks.  I need all the help I can get!

---

