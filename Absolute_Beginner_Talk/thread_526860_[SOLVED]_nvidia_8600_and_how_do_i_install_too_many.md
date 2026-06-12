---
title: "[SOLVED] nvidia 8600 and how do i install? too many options show me one that works pl"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by kerrymorgan1 on 2007-08-16
my system is
500g sata hd, 2G ram, nvidia 8600gt
i want to install the graphics card please help someone
ive read a few  threads but didn't help me too much

ive typed in
glxinfo | grep rendering
the answer was no

sudo nvidia-glx-config enable 
the answer was 

command not found

can someone please help me???

---

### Post by Hobo Joe on 2007-08-16
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu7_all.deb

sudo aptitude update

sudo aptitude upgrade

envy -g

```
When Envy opens, select 'uninstall nVidia driver', and then when it's done, select 'install nVidia driver', make sure to let it configure your xorg for you.

---

### Post by kerrymorgan1 on 2007-08-16
can somebody please please help me im really really stuck here i don't know what to do

---

### Post by sysikon on 2007-08-16
Go into Add/Remove and search for your graphics card.

For example, I have a nVidia.
Search: nvidia
Results: nVidia Binary X.org Driver.

Caution: Make sure your getting the right one.

After that, then run "sudo nvidia-glx-config enable"

---

### Post by kerrymorgan1 on 2007-08-16
> **Hobo Joe said:**
> ```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu7_all.deb

sudo aptitude update

sudo aptitude upgrade

envy -g

```
When Envy opens, select 'uninstall nVidia driver', and then when it's done, select 'install nVidia driver', make sure to let it configure your xorg for you.

when envy opens? i entered that in the terminal but nothing yet has come up.......

---

### Post by kerrymorgan1 on 2007-08-16
does envy do old and new cards? my 8600gt isn't quite old i would have thought but in the the download discription of Envy says that it's for older cards will this work for me?

---

### Post by kerrymorgan1 on 2007-08-16
i have used envy it did something rebooted and started up fine
i went to system>admin>restricted drivers but it still says no hardware installed

where too from here? is it installed? how can i check which graphics card its using?

---

### Post by sysikon on 2007-08-16
Go to Terminal: type "sudo nvidia-settings" and it will tell you all of your newly installed nVidia junk.

---

### Post by kerrymorgan1 on 2007-08-16
my specs are 500GB SATA HD, 2gb ram, amd64 4000+ and i can't get my Nvidia 8600gt going
i have installed envy by advice from someone in a forum but then what?
have used envy it did something rebooted and started up fine
i went to system>admin>restricted drivers but it still says no hardware installed

where too from here? is it installed? how can i check if the graphics card is being used.... my ultimate goal is to run beryl but right now i just wanna make a stable foundation for it
HELP PLEASE!!!

---

### Post by sysikon on 2007-08-16
Look in your last topic!

---

### Post by z0mbie on 2007-08-16
Follow this guide. It's awesome:

[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)

---

### Post by kerrymorgan1 on 2007-08-16
> **z0mbie said:**
> Follow this guide. It's awesome:

[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)

how do i install the nvidia x driver?? it says something about run nvidia x driver and restart x? can you give me the code please?

---

### Post by sysikon on 2007-08-16
To run, just put ./ in front of the name of the file.

Example: "./nvidia-driver"

Then follow the instructions.

---

### Post by kerrymorgan1 on 2007-08-16
i followed instructions and it didn't help me ....... what did i do wrong and how do i fix it? it should say "rendering" no or yes right?
i entered
glxinfo | grep "direct rendering"
and got
Xlib:  extension "GLX" missing on display ":0.0".Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by kerrymorgan1 on 2007-08-16
oh man ive really done it this time.........

this is exactly what it says.....

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

can you pretty please explain what that means? or more importantly how to fix it

---

### Post by z0mbie on 2007-08-16
Now don't take this the wrong way, but I think should first calm down. I saw you having two threads started for the same question. As this isn't the first tutorial you will have to follow, have patients and read through the tutorial. Get use this type of self helping. Again don't get me wrong, I'd love to appear in front of your computer and give you hands on tech support, but since we can't do that we resort to things like guides.

These are some tips about the [Guide]("http://www.robdian.co.uk/content/view/56/27/"):

1. It says to download from this site:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

*Choose the right one. If your not using a 64 bit processor most likely it will be this one:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)

4. This will change your screen into a black/white command line screen: So press CTL+ALT+F6

---

### Post by kerrymorgan1 on 2007-08-16
NUF SED

You're amazing my friend issue solved i am celebrating out loud that first link you gave me 
[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)
 did the trick i just needed some help reading it thanks a heap

Ubuntu for life!

---

### Post by hikaricore on 2007-08-16
Merged threads.

---

### Post by elmz350 on 2007-12-28
Did this work for you?  I'm having a similar issue.  

Thanks in advance.

EDIT:  I just noticed the threads were merged.  I'm trying get it running on Gutsy 7.10.  Did you get the Nvidia 8600 drivers working on Fiesty or Gutsy?

---

