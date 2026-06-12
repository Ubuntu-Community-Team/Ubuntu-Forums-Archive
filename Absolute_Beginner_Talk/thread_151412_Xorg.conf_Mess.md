---
title: "Xorg.conf Mess"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Brightrock on 2006-03-27
Hi,

I was trying to get my Alps touchpad to work and I seem to have messed up my ubuntu kubuntu system royally.  I now need to know how to revert to my old xorg.conf settings from the command line.  I'm definitely still in the "paint by numbers" stage with the command line, as well.

The touchpad thing is the last thorn in the side of my linux system.  After that I'll be able to operate quite comfortably for most of my stuff in Linux.  Yay!  

But for now I'm STUCK.  Like I said the graphical interface won't work at all right now.  So, please help.

Thanks in advance,

Brightrock

---

### Post by Brightrock on 2006-03-27
A bit more background might be helpful, I realized.  Here's the process that led up to the present crisis.  

1. I read the instructions on the Ubuntu Blog and copied the modifications from there (apparently imprefectly).

2. When I first tried to edit the xorg.conf I was in a regular user account so I saved the xorg.conf file as xorg.conf.alps on a drive the I share between all accounts and OSs.

3. I logged out and back in as root.  

4. I moved my xorg.conf.alps file to /etc/x11/ and I saved the existing xorg.conf as xorg.conf.nonalps.

5. Then I saved the xorg.conf.alps as xorg.conf and confirmed the overwrite.

6. Upon reboot I got a series of messed up blue screens that mainly said my xorg.conf didn't work (to tell the truth I didn't pay very much attention to what they said, hoping that it would start anyhow). 

Hope that helps some of you linux experts figure out how I can get my GDM back.

---

### Post by sn123 on 2006-03-27
[QUOTE=Brightrock]A bit more background might be helpful, I realized.  Here's the process that led up to the present crisis.  

1. I read the instructions on the Ubuntu Blog and copied the modifications from there (apparently imprefectly).

2. When I first tried to edit the xorg.conf I was in a regular user account so I saved the xorg.conf file as xorg.conf.alps on a drive the I share between all accounts and OSs.

3. I logged out and back in as root.  

4. I moved my xorg.conf.alps file to /etc/x11/ and I saved the existing xorg.conf as xorg.conf.nonalps.

5. Then I saved the xorg.conf.alps as xorg.conf and confirmed the overwrite.

6. Upon reboot I got a series of messed up blue screens that mainly said my xorg.conf didn't work (to tell the truth I didn't pay very much attention to what they said, hoping that it would start anyhow). 

Hope that helps some of you linux experts figure out how I can get my GDM back.[/QUOTE]
Firstly it's a bad idea to use root a/c, whenever you need admin priveleges use sudo instead of logging in as root. Now if I understand your case correctly, you still have the backup of working xorg.conf file as xorg.conf.noalps. If this is true, then from terminal do this:
```

$ sudo cp /etc/X11/xorg.conf.noalps /etc/X11/xorg.conf

```
enter your root password when prompted and your original conf file should be restored, restart X (if you're already running X, then you can kill it using CTRL-ALT-BackSpace) and from the terminal issue startx command (or easier still reboot the system :) )

S

---

### Post by Brightrock on 2006-03-27
Thanks....  I'll try that... if it works the next post will be from kubuntu.

---

### Post by Brightrock on 2006-03-27
Hooray!!

It worked.  Thanks so much.  Any tips for continuing to get the touchpad to work properly?

Thanks Again!

Brightrock

---

### Post by sn123 on 2006-03-27
[QUOTE=Brightrock]Hooray!!

It worked.  Thanks so much.  Any tips for continuing to get the touchpad to work properly?

Thanks Again!

Brightrock[/QUOTE]
What's the problem that you're facing with your touchpad? Is it not working at all or is it just some bit of it which is not working (like scrolling)?
Take a look at this thread, it might provide you some help:
[http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)
Sorry, I can't be of much help on the touchpad if it relates to scrolling, I've been struggling myself for past 1 month to get that darn thing work!](*,) 

S

---

### Post by Brightrock on 2006-03-27
My touchpad works "ok."  The scrolling function is not working, and the tap sensativity is really too high.  I am constantly clicking things I don't want and moving my cursor where I don't want it etc.  Rather annoying.  

The touchpad and a network printer are the last major hurdles to getting my Kubuntu desktop to be basically as function as my XP.  I like the gnome desktop but I couldn't get my audio capture to work there, and it works fine in Kubuntu.  

I'll check out the link you gave.

Thanks Again!    

Brightrock

---

### Post by Brightrock on 2006-03-28
One last thing.  How would you sudo your xorg.conf.  I'm sure I could dig up the command on the internet somewhere but it might take me hours.  Thanks again for your help.

---

### Post by xhie on 2006-03-28
*sudo gedit xorg.conf*


or replace gedit with the text editor of your choice. 

Yeah I mess with mine all the time too, make sure you back it up, remember that even if you royaly screw it up so bad that you cant even get X to start you can always revert to your backup from the terminal.

---

### Post by sn123 on 2006-03-28
[QUOTE=Brightrock]One last thing.  How would you sudo your xorg.conf.  I'm sure I could dig up the command on the internet somewhere but it might take me hours.  Thanks again for your help.[/QUOTE]
what do you mean by sudo the xorg file? do you mean editing it? If yes, you can open it in gedit
```

$ sudo gedit /etc/X11/xorg.conf

```

S

ps: it's always a good idea to make a backup before playing around with conf files.

---

### Post by Brightrock on 2006-03-28
Hey,

It works... at least the scrolling part.  The mouse still seems a little rambunctious, but the link you provided was the helpful one.  Thanks Again!

---

