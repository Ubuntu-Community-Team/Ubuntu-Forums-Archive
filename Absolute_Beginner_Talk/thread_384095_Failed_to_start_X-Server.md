---
title: "Failed to start X-Server"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-03-14
Basically I was just trying to manually change the values of the refresh rate on my monitor, restarted x-server and it is now failing to load the graphics.

Anyone got the command to reset this?

---

### Post by charles.g.moore on 2007-03-14
If you get a command prompt you can reset your xorg.conf from the backup you hopefully made then startx

I think you gotta kill any x sessions bfore starting it up again I dont know the command to kill it though

---

### Post by meborc on 2007-03-14
if you don't have a backup, you can conf your X by-
```
sudo dpkg-reconfigure xserver-xorg
```
or you can manually edit your conf file by-
```
sudo nano /etc/X11/xorg.conf
```
after that-
```
startx
```
to start X again

---

### Post by siciliancasanova on 2007-03-14
Well I didn't make a back up.  I actually didn't think I had changed anything.  The values for the monitor were there, I know the specs on my monitor so I just changed the number.  

I should always create a back up, I know, but that's not a route I can take right now.

EDIT:  Thank you for the quick response.

---

### Post by siciliancasanova on 2007-03-14
The the is, I have an onboard intel video card that is not listed in that list.  I actually had a similar problem a while back with beryl when I hit the wrong setting.  I just can't remember the code I had to enter to get it back.

---

### Post by siciliancasanova on 2007-03-14
Bump

It's on the second page and I need to get this going (Work on my comp)

Essentially when I did the sudo nano command and looked at the x-server config, there is nothing there anymore.

If I do this ```
sudo dpkg-reconfigure xserver-xorg
``` It asks me for my video card which is built in, so It's something that I can't follow through on in that route.

---

### Post by siciliancasanova on 2007-03-14
Bump

---

### Post by siciliancasanova on 2007-03-14
Bump

---

### Post by DaveyG on 2007-03-14
i had the same prob with screen res.. messed with the xorg.conf with made X server fail.. at the end i gave up and re-installed :(

---

### Post by siciliancasanova on 2007-03-14
Well I will keep bumping this throughout the day until someone can at least tell me that it can't be done.

---

### Post by scxtt on 2007-03-14
just use "vesa" until you can get the card-specific driver working again ...

---

### Post by siciliancasanova on 2007-03-14
Vesa asks me to then enter the card information.  All HP support could tell me was that it's an Intel on Board, will it auto config if I'm manually entering this info?

---

### Post by scxtt on 2007-03-14
what's it asking you for?  i've used that command before (when working w/ fglrx) and am able to accept 99% of the default values, especially since it's only to get a working X until the card-specific settings are worked out [which i've got worked out well these days :)] ...

---

### Post by siciliancasanova on 2007-03-14
Well actually I hope this turns out good.  I'm to the point where it's asking me about the refresh rate which I needed to change.  So I'm doing that now, everything else i've set to default

---

### Post by scxtt on 2007-03-14
depending on what resolution you want, "vesa" can only do so much ... for instance, i can get 1600x1200 w/ fglrx, but only 1280x1024 w/ vesa ... so be realistic :p [ it's a generic driver ]

---

### Post by siciliancasanova on 2007-03-14
Got it working, thanks for the help :)

---

### Post by DaveyG on 2007-03-14
Right now ya got it working id recommend setting the refresh rate back to default... 
i thought you could change it via display settings?

---

### Post by STREETURCHINE on 2007-03-14
and make some backup

     ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```


    then to get it back just use 

    ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

saves a lot of heart ache

---

### Post by siciliancasanova on 2007-03-14
> **Davey Goudou said:**
> Right now ya got it working id recommend setting the refresh rate back to default... 
i thought you could change it via display settings?

On some monitors you can't change it by default, it's a static setting.  That's what I was trying to do.  My refresh rate was way to slow and it was killing my eyes.

---

### Post by deviouskoopa on 2007-03-14
Yeah i'm in the same predicament... i really dont wanna reinstall though haha. as for you sicilian, im not sure why youre xorg.conf was completely wiped... maybe you could try doing the dpkg-reconfigure command and selecting the universal "vesa" driver. its slow but if your intel graphics arent supported by X then try vesa... im a noob but from what ive poked around and read it might work.

---

### Post by siciliancasanova on 2007-03-14
Yeah I've already ran vesa, I actually have a follow up thread to get my resolution back going on right now, it's titled **X-server to Screen Resolution**

---

