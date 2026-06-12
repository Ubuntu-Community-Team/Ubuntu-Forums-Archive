---
title: "HELP! I need drivers!!"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by superxao on 2007-09-19
I managed to dual boot Ubuntu! Problem though, is I don't know what drivers to get for my sound card and video card.

My sound card is a RealTek HD something.. :mad:

And my video card is an ATI Radeon  Xpress 1100

Would the appropriate drivers be in the repository? If so, under what name?

Thanks for the help!!

---

### Post by mattskr on 2007-09-19
Sound should be installed with that card. Check preferences -> sound -> test sound

For the video you can use the restricted drivers:

System -> Administration -> Restricted Drivers Manager

You should see an option for your ATI card. Enable it.

---

### Post by quixotic-cynic on 2007-09-19
The package *xserver-xorg-video-ati* contains the usual ATI drivers. This is installed by default.

If you want to play 3d games you probaby need the closed-source driver contained in the package *xorg-driver-fglrx*.

To install the package you could use the command
```
sudo aptitude install xorg-driver-fglrx
``` from within a terminal.

```
sudo asoundconf list
``` may help you identify your sound card.

---

### Post by superxao on 2007-09-19
Thanks for the quick reply!

Well, I've done what you both said, and the sound is extremely quiet, even with the mixer on full, and when I try to do desktop effects it says 'The Composite Extension is not available"..

So I dunno what that means :(

---

### Post by quixotic-cynic on 2007-09-19
**Sound**
Try typing alsamixer and adjusting your volume control there. Edit: I guess you have allready tried this actually?

**Gfx**
Type *glxinfo* to see if you have 3d acceleration currenly enabled - you need it for the Composite extension. "direct rendering: No" is bad, "direct rendering: Yes" is good.

Also have a look at the "And finally add the following two sections..." part of [this]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon"). You need the 
```

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```
part in your xorg.conf file.

---

### Post by alienexplorers on 2007-09-19
Add this to the bottom of your xorg.conf file.

> Section "Extensions"
    Option "Composite" "Enable"
EndSection

---

### Post by superxao on 2007-09-19
I seem to have got the sound done.. just need to do the mic then the sound is fine.

Just I have the video drivers.. but can't get Beryl/Desktop Effects to work...

---

### Post by Maestro23 on 2007-09-19
> **superxao said:**
> Thanks for the quick reply!

Well, I've done what you both said, and the sound is extremely quiet, even with the mixer on full, and when I try to do desktop effects it says 'The Composite Extension is not available"..

So I dunno what that means :(

You need to enable "Composite" to ON in your** /etc/X11/xorg.conf** file.

Open it up in an editor: gksudo gedit /etc/X11/xorg.conf

Look for the following section and make it look like this:

> Section "Extensions"
        Option "Composite" "Enable"
EndSection

Make your changes to the file and save it.

---

### Post by superxao on 2007-09-19
It's read-only.. won't let me save?

Oh, root, lol.

Never mind :P

---

### Post by mysticmatrix on 2007-09-19
> **superxao said:**
> It's read-only.. won't let me save?
Well you'll need to use this command to oopen the file with Administrative right so that you can change it.

```
gksudo /etc/X11/xorg.conf
```

BTW, ATI doesn't thinks that running Desktop effects would be a good idea for end user. So they have no support for running Compiz/Beryl by default.

As a workaround, you'll have to install XGL from here [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Then start the Desktop Effects as usual.

PS: Nvidia and Intel think that it's good idea to run Desktop effects, and don't need such workarounds.

---

### Post by Maestro23 on 2007-09-19
> **superxao said:**
> It's read-only.. won't let me save?

Oh, root, lol.

Never mind :P

Did you use **gksudo **(gives root access) like I posted earlier?

---

### Post by superxao on 2007-09-19
Yup. Still says the same thing... Did exactly what you all told me...

EDIT: Woo! That error message has gone.. BUT, now it says; Desktop Effects could not be enabled O_o

---

### Post by maharbA on 2007-09-19
> **superxao said:**
> BUT, now it says; Desktop Effects could not be enabled O_o

Unfortunately, ATI cards do not support composite window managers (like Compiz Fusion/Beryl) so you need to set up XGL.

I used the guide here ( [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) )  to install COmpiz Fusion and it worked for me.

(AMD recently promised to work with the open source community to create drivers for ATI cards, support for AIGLX -- which is what Compiz Fusion needs -- should be coming soon)

---

### Post by superxao on 2007-09-19
Okay..  I tried that. And when I type in Beryl-manager, I got this;

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

---

### Post by mysticmatrix on 2007-09-19
> **superxao said:**
> Okay..  I tried that. And when I type in Beryl-manager, I got this;

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

[COLOR="Sienna"]Detected xserver                                : AIGLX[/COLOR]

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

Indicates XGL is not working properly. See my previous post in this regard

---

### Post by superxao on 2007-09-19
Nope; 

```
gareth@gareth-laptop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 115 not upgraded.
gareth@gareth-laptop:~$ 

``` :(

---

### Post by superxao on 2007-09-19
Sorry for the double post, but;

I THINK I'VE DONE IT! :)

I logged in with GNOME with XGL, and.. apart from the ubuntu loading screen having a black background, everything is all wobbly!

Thanks for the help guys!

---

### Post by mysticmatrix on 2007-09-20
> **superxao said:**
> Sorry for the double post, but;

I THINK I'VE DONE IT! :)

I logged in with GNOME with XGL, and.. apart from the ubuntu loading screen having a black background, everything is all wobbly!

Thanks for the help guys!

Wow you got a ATI working!!!
Great victory indeed!!!

---

