---
title: "Widescreen problem"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by *desk* on 2006-11-15
With my 19" widescreen and switched to digital input I get a 1cm vertical border down the right hand side of the screen running at 1280 x 1024 resolution. This does not happen with an analogue signal.
Any ideas anyone? This is not apparent with XP or Suse 10.1

---

### Post by macdo on 2006-11-15
Why don't you run at a widescreen resolution? I'm at 1440x900.

On your question, it's always been my experience that when you change resolutions (or OSs, for that matter), you need to readjust your screen geometry. My screen has an 'automatic' button (marked A) on the side that does the job just fine. 

Take care,

---

### Post by *desk* on 2006-11-15
Why don't you run at a widescreen resolution? I'm at 1440x900

Of course Macdo that is the answer, I was stupidly thinking that it was 1280 x 1024.
Trouble is there is not a 1440 x 900 in the resolution preferences.
What next?

---

### Post by Chown_Root on 2006-11-15
you can do the following

vi /etc/X11/x.org, add your resolution to the list, save, and restart X.


Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     16
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes    [COLOR="Red"]"1440x900"[/COLOR] "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480" 
        EndSubSection

---

### Post by *desk* on 2006-11-15
Thank you so much....all is well.
It is now working perfectly, thank you for an extremely quick response.
I must say I have gone full circle with distros and there's no doubt about it  Ubuntu is the best by far.

---

### Post by macdo on 2006-11-15
> **Chown_Root said:**
> 
        DefaultDepth     16
        

As a matter of interest, why aren't you using a 24 bit depth? (or is it a typo?)

---

### Post by chlorinekid on 2006-11-21
i managed to find the file that you're talking about in this thread but i dont know how to get root access to modify it... 

can someone help??

---

### Post by scc4fun on 2006-11-21
> **chlorinekid said:**
> i managed to find the file that you're talking about in this thread but i dont know how to get root access to modify it... 

can someone help??
use "sudo" and your **user** password before any command that you need root access to view/edit.

---

### Post by chlorinekid on 2006-11-21
nevermind, managed to sort it :) thanks for the tip though, thats a better way of doing it!

cheers

dave

---

### Post by macdo on 2006-11-21
```
sduo nano /etc/X11/x.org
```

The p/w you need is your user p/w

---

### Post by chlorinekid on 2006-11-21
ive edited the file and added "1280x1024" to all the depth options but when i go to system > prefs > screen resolution there isnt the 1280x1024 option...

ive restarted the machine a few times but its still not apearing as an option in the drop down list...

anyone help??

thanks

---

### Post by chlorinekid on 2006-11-21
im running 6.10 by the way, im not sure if that makes a difference?

---

