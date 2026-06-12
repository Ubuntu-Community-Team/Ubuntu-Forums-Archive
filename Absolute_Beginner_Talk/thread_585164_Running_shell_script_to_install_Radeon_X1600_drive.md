---
title: "Running shell script to install Radeon X1600 driver"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Unicycle on 2007-10-21
I am trying to get 3D to work smoothly with my ATI Radeon X1600 512mb AGP card.  I'm running Feisty.

I downloaded the driver from ATI's website.  It's called *ati-driver-installer-8.40.4-x86.x86_64.run*.

So, I'm trying to run it and make it work.  How do I do this?  Also, can anybody give me some tips on how to make the the whole process work?

I did find that in my "Restricted Drivers Manager" there is an "ATI accelerated graphics driver" that is not in use.  So, I enabled it, rebooted, and my system did nothing short of freak out.  I was, however, able to disable it again, returning things to normal.

Anyway, thanks for any help you can provide! :D

---

### Post by digital_exhaust on 2007-10-21
Don't use the driver from ATI's web site.. try using [Envy]("http://albertomilone.com/nvidia_scripts1.html") instead...

---

### Post by Unicycle on 2007-10-21
Thanks, digital!  I'll give it a try and post the result.

---

### Post by bodhi.zazen on 2007-10-21
> **Unicycle said:**
> I am trying to get 3D to work smoothly with my ATI Radeon X1600 512mb AGP card.  I'm running Feisty.

I downloaded the driver from ATI's website.  It's called *ati-driver-installer-8.40.4-x86.x86_64.run*.

So, I'm trying to run it and make it work.  How do I do this?  Also, can anybody give me some tips on how to make the the whole process work?

I did find that in my "Restricted Drivers Manager" there is an "ATI accelerated graphics driver" that is not in use.  So, I enabled it, rebooted, and my system did nothing short of freak out.  I was, however, able to disable it again, returning things to normal.

Anyway, thanks for any help you can provide! :D

Open a terminal :

```
cd to location of ati-driver-installer-8.40.4-x86.x86_64.run
# ? cd ~/Desktop

sudo chmod a+x ati-driver-installer-8.40.4-x86.x86_64.run

sudo sh ati-driver-installer-8.40.4-x86.x86_64.run
```

Use tab completion to make life easier (ie type ati<tab> )

If that fails see here : [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

Or Envy is also nice ...

---

### Post by Unicycle on 2007-10-21
I'm currently on the XP partition of my HDD, because Envy caused Ubuntu to black-screen on reboot.

What do I do?! ](*,)

---

### Post by Unicycle on 2007-10-21
Ok, I found a thread that helped.  I went to the recovery mode and entered:

```
cd /etc/X11

sudeo dpkg-reconfigure -phigh xserver-xorg
```

...and then went back to vesa.

Now I'll try bodhi.zazen's recomendation. #-o

---

### Post by bodhi.zazen on 2007-10-21
Back up your working xorg.conf

They you can easily restore it without needing to re-configure ...

---

### Post by Unicycle on 2007-10-21
bodhi, you're recommendation did bring up the ATI installation screen.  So, I completed it, restarted, and it still is running lower than 1 fps on even the simplest 3D games.  No improvement that I can see.  Any more ideas? :(

---

### Post by Unicycle on 2007-10-21
After the installation ended, I tried to run:

```
aticonfig --initial -f
```

...like it said to do, and then I got an error you can see in the first attachment.

For reference, I also attached the final ATI installation screen that told me to do all of this.

P.S.
Would installing Gutsy help things?

---

### Post by Unicycle on 2007-10-21
BUMP!  I still need help, please. :)

---

### Post by bodhi.zazen on 2007-10-21
Sorry but I have told you more then I know about ATI :)

I nvidia, so we will need to await help from someone with more ATI experience.

I do not think updating to gutsy will help, but I do not know for sure.

---

### Post by schorsch on 2007-10-21
Try
```
sudo aticonfig --initial -f
```

---

### Post by Unicycle on 2007-10-21
Howdy folks.  I just got done upgrading to Gutsy, and overall, I love it.  And...bom badda bom...my ATI card works!  I don't know what did it, but it does, indeed, 

:guitar:   ***maka da free-dee go!***   :guitar:

---

