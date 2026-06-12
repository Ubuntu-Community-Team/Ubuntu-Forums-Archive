---
title: "I cant get widescreen resolution working this time"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by enharrin on 2007-03-15
Greetings all.  So I installed Ubuntu the other day and everything worked great.  I've got a 24" Acer monitor that runs at 1920x1600 and the LiveCD detected it, and after I installed and rebotted I was looking at the Ubuntu desktop in it's 24" glory.

Of course, I wasn't satisfied there.  I wanted to install Beryl.  So I did that and it worked too!  Unbelievable.  I have never had things work so well in Linux (I've tried and given up on many distributions since I first installed RedHat about a decade ago).

Here is were things started to go wrong.  The next day when I booted my computer and logged in something in X was busted because it wouldn't load the login screen, and I was getting this blue terminal-like screen that said my X settings were wrong, and would I like to look at the X output and debug it.  I started messing around, I uninstalled Beryl, went back to the original "nv" driver (I have an nVidia card, by the way), and was able to get back into Gnome.  I tried to install Beryl and get it working again, and ran into all kinds of weird problem, including the one where your desktop is all white, but you can still rotate the cube.  Anyway, I decided to give up on Beryl and try Compiz.  That didn't work any better, and after that I decided I would just try to re-install Ubuntu (I figured that with having Compiz and Beryl in their varying states of functionality it was a better idea to just wipe the whole thing; plus I decided I wanted to create a /home partition which I hadn't done the first time around).

So I guess all that is really just background, here is the real problem:  The LiveCD won't recognize my widescreen monitor any more!  Even though it didn't detect it with the second install, I figured I'd install anyway and see if it worked.  No dice.  Even after the install I'm running at 800x600.  I went to the screen resolution settings in the gnome menu, and the only other option available is 640x480...   I tried editing my xorg.conf file and just adding 1920x1600 to the list of modes, but that didn't work.

So does anyone know how the LiveCD could have figured out the correct monitor settings the first time but not the second?  Boy I wish I had saved that xorg.conf from the first install, but I figured it would work like a charm again...

Thanks!

---

### Post by John.Michael.Kane on 2007-03-15
Try running this: It should reset your xorg.
```
dpkg-reconfigure -phigh xserver-xorg
```

To install your nvidia drivers using edgy 6.10.

Run:
```
gksudo aptitude install linux-generic
```

Now install the gpu driver:
```
gksudo aptitude install nvidia-glx
```

Enable the driver in your xorg:
```
gksudo nvidia-xconfig
```

Nex step:
```
gksudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

Paste the following
```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;
```

Last step:
press CTRL+ALT+BACKSPACE 

To make any other screen adjustment read this: make sure you have your LCD manual.
[**Adjust refresh rate**]("http://ubuntuforums.org/showpost.php?p=1691257&postcount=2")

For beryl issue please post your issue here--->[**Desktop Effects & Customization**]("http://www.ubuntuforums.org/forumdisplay.php?f=223")

---

### Post by enharrin on 2007-03-15
Wow, thank you for the detailed response!  I will try all this when I get home from work.

I'm confused about the nvidia drivers though.  It seems like there are many options, and I don't know what the difference is between them.  I tried installing the nvidia drivers using Automatix, EasyUbuntu, and the Envy script.  Is installing nvidia-glx with aptitude the "best" way to get them?  Will that driver be sufficient to run Beryl...?  (If I can work up the courage to try installing it again.)

Also, with the NVIDIA-Settings.desktop file, will that become one of the sessions at the GDM login screen?  I don't really understand what that step is doing.

Thanks again!

---

### Post by John.Michael.Kane on 2007-03-15
NVIDIA-Settings.desktop file is just giving you a menu link to program that can used to adjust certain card settings. It should not interfere with beryl.

As for installing via the envy script i have tested that method and it works fine. If you want to re try using that script then just reset your xorg with the frist command.

Then download the lastest envy script--->[**envy_0.9.1**]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb") from there you should be able to setup your machine how you want.

The other two methods you listed i have not used.

---

### Post by enharrin on 2007-03-16
Well, I managed to get back to where I was.  I decided to try one last time to see if the LiveCD would detect my widescreen settings, and this time it worked!  I'm still totally confused as to why it would work the first and last time, but not the two times (at least) I tried in between...  I'm not sure if reinstalling from a LiveCD session with the right resolution helped in any way, but I figured it couldn't hurt!

Anyway, this time I decided to forgo Automatix and EasyUbuntu, opting instead to go with whatever repositories I get when enabling all the options in Synaptic.  So I tried installing nvidia the way you told me, and it worked.  Installed beryl again, and it worked too.  Again everyting was so easy up to this point!

So I restarted my machine to make sure everything was fine, and I got the blue X error screen again!  Why the heck would beryl work fine when initially installed, then make everything break on a restart?  And it's not just Beryl that broke, it was X in general, so it must have done something pretty bad.  I switched back to the "nv" driver and tried to reinstall nvidia drivers with synaptic, but the "nvidia" driver didn't' work when I restarted X, so then I decided to try Envy, which did end up working (I had to tweak my xorg.conf a little bit).

It seems to me like there is either something wrong with the nvidia drivers in the ubuntu repositories, or that it somehow matters which order you install beryl/nvidia drivers.

I'm just glad it's finally working again.  And I've restarted the machine a couple more times to make sure nothing wacky happens...  Thanks again!  =)

---

