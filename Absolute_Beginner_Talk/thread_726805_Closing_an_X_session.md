---
title: "Closing an X session?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by jprophet420 on 2008-03-17
The driver for my nvidia card (8600gt) requires that no X session be open during install. I remember I scripted my bash rc file a while ago to start in run level 3. I opened up my terminal and did a sudo init 3 but nothing happens. How do I close out the X session so that I can install the drivers?

I swear I saw a guide to installing nvidia drivers here but I cant it now, sorry.

---

### Post by Rocket2DMn on 2008-03-17
You should be able to do
```
sudo /etc/init.d/gdm stop
//do your stuff
sudo /etc/init.d/gdm start
```

I think I have some directions around for installing nvidia drivers from their site, let me dig them up.

edit: here they are:

download from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) - choose the driver based on your processor architecture (IA32e is for 32 bit processors and AMD64 is if you are using a 64 bit processor with the 64 bit Ubuntu version).

```
sudo apt-get remove nvidia-glx nvidia-new-glx
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
^^ignore any file not found errors ^^
sudo apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev
```
do CTRL+ALT+F1 to get to a tty and login there, then run
```
sudo /etc/init.d/gdm stop
sudo chmod +x /path/to/NVIDIA*
sudo sh /path/to/NVIDIA*
sudo /etc/init.d/gdm start
```
In this case /path/to/NVIDIA* is pointing you to where you svaed the .run file you downloaded from nvidia's website ( ex: your desktop path: ~/Desktop/NVIDIA* )
Now in the GUI, open a terminal and run
```
gksu nvidia-settings
```

---

### Post by jprophet420 on 2008-03-17
thank you very much for the help. The install went on without a hitch.

Now i cant configure the dual monitors, and again i know i've seen the thread around here and i cant find it atm. as a matter of fact i think its the same thread i couldnt find in the first place.

If someone could either point me to the thread or walk me thru the configuration that would be stellar. I know theres a problem with the settings not saving once you get them there and I know theres a fix for it. Thanks again.

*edit* Also, apparently none of my games can find the gl drivers now. I had Driver running in wine and openarena working natively, any suggestions on this?

> SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


---

### Post by Rocket2DMn on 2008-03-17
A brief search discovers this thread: [http://ubuntuforums.org/showthread.php?t=563809](http://ubuntuforums.org/showthread.php?t=563809) (Search google for "site:ubuntuforums.org nvidia dual head" for more results).
There are a number of ways to get dual head working, so you may have to dig around a bit for programs like xinerama, twinview, etc until you get one that works for you.
I suggest disabling Compiz when you run 3d games so you can get better performance out of them.  To disable CF, you can run
```
metacity --replace
```
and to bring it back
```
compiz --replace
```
If that doesn't solve your GL problem, you may need to reconfigure X or install xserver-xgl, or you may just have to tweak some wine settings.

---

### Post by jprophet420 on 2008-03-17
thanks for the help. i will read that thread and try to get my configuration skills down. the original problem of this thread is solved.

---

### Post by bodhi.zazen on 2008-03-17
To configure your monitors :

```
gksu nvidia-settings
```

If you like the settings, choose the save button. If you break X, restart it with Ctrl-Alt-Backspace.

---

### Post by jprophet420 on 2008-03-17
thank you, i managed to get 2 displays working and im still having the problem with the gl not working but i may have to reinstall the apps, not sure yet. right now im downloading all of the updates for gutsy. 

what is the difference between 

$suso nvidia-settings
and
$gksu nvidia-settings
?
I found that thread about not being able to save the config file and it said to use the former. just wondering.

---

### Post by bodhi.zazen on 2008-03-17
Both sudo and gksu (kdesu for KDE) give root access. 

sudo is used from the command line, gksu is used for graphical apps (like synaptic or nvidia-settings).

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

And for general reference : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jprophet420 on 2008-03-17
ahh, i see, because sudo loads the user config file sometimes rather than the root config. so i suppose i could just use root also, just not sudo.

---

### Post by bodhi.zazen on 2008-03-17
If you would like a root shell, use :

```
sudo -i
```

---

