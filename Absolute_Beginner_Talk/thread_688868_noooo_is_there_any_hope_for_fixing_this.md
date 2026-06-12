---
title: "noooo is there any hope for fixing this??"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-02-05
ok so wtf?

I just set up the cube stuff, and then shut my computer down
When I came back on I pressed my buttons to go to the cube
and when I let go it goes all shaky and effing up, it wont stop
so I have to shut it off, it did it like 3 times.... and now when I turn
it on it doesnt even boot, the screen just stays black


what do I dooo??? I had files from school I need (just got wrote the notes today so didnt have any time to backup)

whats wrong what could this be, can I fix this?

---

### Post by Linux_Man on 2008-02-05
Well, to answer your first question, yes it is fixable and no your files aren't in danger because the GUI (what you see on the screen) isn't Linux it is just a program. As for how to stop it, try pressing CTRL+ALT+Backspace and that should restart X, log back in and see if that fixes it, if not then try killing compiz.

---

### Post by sirfonners on 2008-02-05
alright well im logged back in, but still when I try to go to the cube it messes up
do I just have to get rid of it...or is there something I can do to fix this?

---

### Post by Linux_Man on 2008-02-05
What graphics card/drivers are you using? That could help us solve the problem. As for compiz I don't really know as I have older hardware that really doesn't support it. Have you tried installing the compiz manager (don't know the exact name but it lets you customize the desktop effects) and disabling some features until you fix it?

---

### Post by steveneddy on 2008-02-05
Why don't you turn off Compiz until you learn a little about why this is happening.

What type of video card do you have?

---

### Post by sirfonners on 2008-02-05
I have an ATI Radeon X1250 I heard lots of people have problems with ATI??

---

### Post by Linux_Man on 2008-02-05
Which drivers are you using? Free or proprietary? Also did you install them from ATI's website or the restricted drivers menu?

---

### Post by steveneddy on 2008-02-05
Good luck with ATI.

I dumped ATI years ago, even before I discovered Linux.

Just read the forums about everything ATI and maybe you will get lucky.

Someone may be able to point you in the right direction.

If it is a desktop, why don't you just buy an nVidia card?

EDIT:

See - someone came to the rescue already

---

### Post by emarkd on 2008-02-05
Some ATI drivers have to use xgl for rendering.  You can install this by installing the xserver-xgl package, but make sure you back up your /etc/X11/xorg.conf file beforehand because that package will overwrite everything and you'll need a backup to go back if it doesn't work.

---

### Post by sirfonners on 2008-02-05
> **Linux_Man said:**
> Which drivers are you using? Free or proprietary? Also did you install them from ATI's website or the restricted drivers menu?

I just enabled it from the ristricted drivers menu and it installed something automatically

---

### Post by sirfonners on 2008-02-05
> **emarkd said:**
> Some ATI drivers have to use xgl for rendering.  You can install this by installing the xserver-xgl package, but make sure you back up your /etc/X11/xorg.conf file beforehand because that package will overwrite everything and you'll need a backup to go back if it doesn't work.

When I go to Systems>>Administration>>Screen and Graphics it says 

Driver: fglxr

so I need the xserver-xgl one?

---

### Post by emarkd on 2008-02-05
fglrx is the propietary binary bit from ati.  xgl is the rendering layer.  They're different and work together to do the job - for some cards.  You can try installing the xserver-xgl to see if things straighten out, but make sure you do that backup!

---

### Post by sirfonners on 2008-02-05
> **emarkd said:**
> fglrx is the propietary binary bit from ati.  xgl is the rendering layer.  They're different and work together to do the job - for some cards.  You can try installing the xserver-xgl to see if things straighten out, but make sure you do that backup!

Where do I get the XGL ......and how would i back up the other one if it didnt work??

---

### Post by vinutux on 2008-02-05
Ok .... i am a Ati user ...................i explain thing worked for me.....

1. disable desktop effects (if u can)---optional

2. install latest "ATI Catalyst driver" (version 8.01 now) from AMD/ATI website [
fglrx u r currently using or installing automatically a bit outdated because ATI released new drivers every month] 

3. right click the downloaded ".run" package and change the permission --optional

4. double click and install it

5. restart system

6.if u want compiz back  (ATI driver disable the desktop effects) install xgl-server and log out and login back.

7...........DONE    :guitar:                 :lolflag:

---

### Post by emarkd on 2008-02-05
You can back up your xorg by running

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

then you can install xgl by running

```
sudo apt-get install xserver-xgl
```

You can also install it from Synaptic by just using the search function to find the package, right-clicking and selecting install

---

### Post by sirfonners on 2008-02-05
> **emarkd said:**
> You can back up your xorg by running

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

then you can install xgl by running

```
sudo apt-get install xserver-xgl
```

You can also install it from Synaptic by just using the search function to find the package, right-clicking and selecting install

it says its already installed, do I have to do something to get it running?

---

### Post by emarkd on 2008-02-05
I don't think so.  You can run

```
ps -e | grep -i xgl
```

to see if it's running.

---

### Post by sirfonners on 2008-02-05
```
 6300 ?        00:00:00 Xgl-lockfile-wr
 6305 ?        00:30:55 Xgl

```

---

### Post by emarkd on 2008-02-05
It's already running.  That's not your problem...

---

### Post by vinutux on 2008-02-05
> **vinutux said:**
> Ok .... i am a Ati user ...................i explain thing worked for me.....

1. disable desktop effects (if u can)---optional

2. install latest "ATI Catalyst driver" (version 8.01 now) from AMD/ATI website [
fglrx u r currently using or installing automatically a bit outdated because ATI released new drivers every month] 

3. right click the downloaded ".run" package and change the permission --optional

4. double click and install it

5. restart system

6.if u want compiz back  (ATI driver disable the desktop effects) install xgl-server and log out and login back.

7...........DONE    :guitar:                 :lolflag:


Try this one now..................plzzzzzzzzzzz

---

### Post by sirfonners on 2008-02-05
> **vinutux said:**
> Try this one now..................plzzzzzzzzzzz

is this it? [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

how do i run it, when I click on the icon it says it doesnt know what language its in
and to check that its not a binary file??

---

### Post by sirfonners on 2008-02-05
bump?

---

### Post by sirfonners on 2008-02-05
can anyone tell me how to install it?

---

### Post by sirfonners on 2008-02-06
bump?

---

### Post by vinutux on 2008-02-06
1. right click file -->properties -->permissions--> and Active "[COLOR="Blue"]allow executing[/COLOR]"

2. open gnome terminal and type sudo and drag file here (it is look like "[COLOR="Red"]sudo /home/vinu/Desktop/ati-driver-installer-8-01-x86.x86_64.run[/COLOR]" now) --> enter

3. may have some problems on front but don't care always click right side buttion and finish install

4. restart system

---

