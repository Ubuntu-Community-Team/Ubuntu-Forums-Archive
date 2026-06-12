---
title: "Beryl window manager wont show.."
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Robbey on 2007-12-16
Ok...I finally got around to installing beryl D:. Only one problem, beryl window manager wont work. Eveytime I change to beryl it goes back to 'metacity'.  When I ru beryl manager in terminal, i noticed this-
Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
beryl: glXCreateContext failed
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


Could this be the reason???
Also I did the command '  aptitude show beryl-manager''
this is what shows up.
Package: beryl-manager
State: installed
Automatically installed: no
Version: 0.2.1-0ubuntu1
Priority: optional
Section: universe/x11
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 610k
Depends: libatk1.0-0 (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.0),
         libfontconfig1 (>= 2.4.0), libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>=
         2.10.3), libpango1.0-0 (>= 1.16.1), libx11-6, libxcursor1 (> 1.1.2),
         libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2 (>=
         2:1.2.0), libxrender1
Description: Tray application launcher tool - Beryl Project
 The Beryl Project brings 3D desktop visual effects that improve usability of
 the X Window System and provide increased productivity though plugins and
 themes contributed by the community giving a rich desktop experience. 
 
 This package contains a tray application tool to launch beryl, start different
 window decorators or window managers. The tool can also fallback to a window
 manager if beryl crashes.

So yea little help guys?? I really want beryl!

---

### Post by PmDematagoda on 2007-12-16
What is the VGA card you have? 

And did you give Compiz-Fusion a try? Beryl is outdated now and has been replaced by Compiz-Fusion, so if you want up-to-date eyecandy then I suggest that you use Compiz-Fusion.

---

### Post by Robbey on 2007-12-16
> **PmDematagoda said:**
> What is the VGA card you have? 

And did you give Compiz-Fusion a try? Beryl is outdated now and has been replaced by Compiz-Fusion, so if you want up-to-date eyecandy then I suggest that you use Compiz-Fusion.

I rahter just use beryl, Im more familiar D; oh and I have a geforce 8500 gt 512mb.

---

### Post by overdrank on 2007-12-16
> **Robbey said:**
> I rahter just use beryl, Im more familiar D; oh and I have a geforce 8500 gt 512mb.

Hi and what version of ubuntu are you using? Do you have the drivers for your graphics card installed? You may need to add some things to your xorg like this 
```
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
   [COLOR="Red"] Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True[/COLOR]"
EndSection

```

---

### Post by Robbey on 2007-12-16
> **overdrank said:**
> Hi and what version of ubuntu are you using? Do you have the drivers for your graphics card installed? You may need to add some things to your xorg like this 
```
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
   [COLOR="Red"] Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True[/COLOR]"
EndSection

```

How do I add that to my xorg. Im running 7.04 btw.. and yes im pretty sure i have got the drivers installed. Also will this give me graphical error again. I have had it 3 times installing beryl alone..and its  a pain in the bum to fix

---

### Post by overdrank on 2007-12-16
> **Robbey said:**
> How do I add that to my xorg. Im running 7.04 btw.. and yes im pretty sure i have got the drivers installed. Also will this give me graphical error again. I have had it 3 times installing beryl alone..and its  a pain in the bum to fix

Can you post the output of this command ```
cat /etc/X11/xorg.conf
```
Before you edit it 
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and to edit your xorg use ```
gksudo gedit /etc/X11/xorg.conf
``` and yes you may have to reconfigure your xorg

---

### Post by Robbey on 2007-12-16
> **overdrank said:**
> Can you post the output of this command ```
cat /etc/X11/xog.conf
```
Before you edit it 
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and to edit your xorg use ```
gksudo gedit /etc/X11/xorg.conf
``` and yes you may have to reconfigure your xorg

cat /etc/X11/xog.conf

got

cat: /etc/X11/xog.conf: No such file or directory


????

---

### Post by overdrank on 2007-12-16
DId you copy and paste that command the x must be capital X
Edit I left out the r xorg.conf

---

### Post by Robbey on 2007-12-16
> **overdrank said:**
> DId you copy and paste that command the x must be capital X

Yes I copied and paste? whats the exact command lol D:

---

### Post by overdrank on 2007-12-16
> **Robbey said:**
> Yes I copied and paste? whats the exact command lol D:

Yes I am sorry, as you see I have edited my post command ```
cat /etc/X11/xorg.conf
```

---

### Post by Robbey on 2007-12-16
> **overdrank said:**
> Yes I am sorry, as you see I have edited my post command ```
cat /etc/X11/xorg.conf
```

robert@Roberts-Computer:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
robert@Roberts-Computer:~$ cat /etc/X11/xorg.conf

Are you sure?

---

### Post by overdrank on 2007-12-16
> **Robbey said:**
> robert@Roberts-Computer:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
robert@Roberts-Computer:~$ cat /etc/X11/xorg.conf

Are you sure?

Yep real sure, try this
```
gksudo gedit /etc/X11/xorg.conf

```

---

### Post by Robbey on 2007-12-16
> **overdrank said:**
> Yep real sure, try this
```
gksudo gedit /etc/X11/xorg.conf

```

Yes Im in D:. What do I do from here?

---

### Post by overdrank on 2007-12-16
> **Robbey said:**
> Yes Im in D:. What do I do from here?

Copy and paste the output here  and wrap it will the code tags in the reply. Then little  #  in the top right hand corner of the reply. That way it will limit the space taken.

---

### Post by Robbey on 2007-12-16
So basically copy and paste-
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
EndSection

Then save? can you please show me what exactly I need to copy and paste and edit..That will help heaps :) Thanks in advance

---

### Post by overdrank on 2007-12-16
> **Robbey said:**
> So basically copy and paste-
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
EndSection

Then save? can you please show me what exactly I need to copy and paste and edit..That will help heaps :) Thanks in advance

No that was an example. That was my xorg. you will need to make sure the driver is nvidia not nv or something else. Also you may need to add the extra option to the section. If you need to install the driver for that card I would recommend Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Robbey on 2007-12-16
I used Envy. Installed the Driver. Still got the same problem :(

---

### Post by PmDematagoda on 2007-12-16
Post the results of:-

```
cat /etc/X11/xorg.conf
```

And could you please copy and paste this.

---

### Post by PmDematagoda on 2007-12-16
Sorry, I did not see this:-

> robert@Roberts-Computer:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
robert@Roberts-Computer:~$ cat /etc/X11/xorg.conf


It may seem that you do not have a xorg.conf file and is currently running the bullet-proof X-server. 

This is what you can do:-

1) Remove the Nvidia drivers by using Envy.

2) Download the Nvidia driver from [here.]("http://www.nvidia.com/object/unix.html")

3) Install the build-essential package using:-

```
sudo apt-get install build-essential
```

4) Kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

5) Navigate to where the driver is and execute it using:-
```

sudo sh nameofinstaller
```

6) After the driver is successfully installed do:-

```
sudo dpkg-reconfigure xserver-xorg
```

7) After install check if the GUI works by using:-

```
sudo /etc/init.d/gdm start
```

If the GUI works then try doing:-
```

cat /etc/X11/xorg.conf
```

---

### Post by overdrank on 2007-12-16
> **Robbey said:**
> I used Envy. Installed the Driver. Still got the same problem :(

Would you by chance be using Hardy 8.04?

---

### Post by Robbey on 2007-12-16
robert@Roberts-Computer:~$ sudo sh nameofinstaller
sh: Can't open nameofinstaller

---

### Post by Robbey on 2007-12-16
omfg...lol when I run beryl manager now. The beryl logo pops up and it changes to beryl Although my screes is just fully white. but I can still see my mouse hover over stuff etc. LOL

---

### Post by PmDematagoda on 2007-12-16
> robert@Roberts-Computer:~$ sudo sh nameofinstaller
sh: Can't open nameofinstaller

Hmm, you do realise that the nameofinstaller is the name of the file you downloaded from the Nvidia site don't you?

---

