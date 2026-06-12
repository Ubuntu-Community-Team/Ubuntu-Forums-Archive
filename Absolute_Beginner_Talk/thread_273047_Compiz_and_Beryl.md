---
title: "Compiz and Beryl"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-10-07
Hello all,

I've recently been reading on Compiz and hardware rendered window compositing. Hoiwever, everything I find assumes some basic knowledge and I don't have much.

so here are my questions and what I've understood so far. If someone oould correct me I would appreciate it.

NVIdia cards: Don't use AIGLX until the new Nvidia driver comes out

Dapper: Use XGL and Compiz and not AIGLX and Beryl

USe the compiz window manager

I use dapper at homw and I have an NVIDIA Geforce 400.



Is there a very very basic user guide or some exampoles I could look at to see exactly what compiz/beryl do?



Thanks a lot guys,

Cheers,

David K

---

### Post by baldy1324 on 2006-10-07
sounds pretty good heres what ive got-
compiz-window manager developed by novel that has all the cool effects that you want; needs accelerated x server (xgl or aiglx)
beryl-novell's policy for compiz is to keep it simple and keep novell's own developers in charge of it; beryl is just compiz with some patches that make it crazy, cool; split off branch of compiz from novell
xgl-whole new x server; many bugs and having to run whole new x server; some apps dont display on it; all video cards work well with it
aiglx-composite extension part of the X11 (regular x server) intoduced in X11R7.01; only works with open-source drivers (intel and ati will work w/ aiglx and nvidia will soon); more desirable than xgl b/c less bugs and 1 x server
hope that helped

---

### Post by PPAAUULL on 2006-10-07
Is it Compiz that is beta or AIGLX? anyways does anyone know when it will have a final version release?

---

### Post by white on 2006-10-07
I too have a question, can ATI cards run AIGXL and Beryl? If so, whats the difference between regular XGL and AIGLX?

So far the only differences I've noticed from Compiz and Beryl are that you get a nice little splash screen of Beryl on an Xgl session startup, you can change themes without having to install a manager for that, and you can load and reload the window manager and decorator with a couple clicks. I only spent 3 weeks running compiz so I odn't know if you could do the exact same thing.

---

### Post by PPAAUULL on 2006-10-07
Where Can I get a how to to install Beryl to replace Compiz?-

---

### Post by aktiwers on 2006-10-07
This guide got me onto the wonderful XGL + Beryl, with my ATI Radeon 9800 Pro. I have tried many guides, but this is the only one that worked for me.
[http://ubuntuforums.org/showpost.php?p=1561758&postcount=26](http://ubuntuforums.org/showpost.php?p=1561758&postcount=26)

I had to do a little Tweaking here and there after the install, but now it runs great!

The worst thing I had to do was to remove the Gnome Wireframe, which was slowing my hole system down:
[http://wiki.archlinux.org/index.php/Xgl#Remove_ugly_and_slow_GNOME.27s_wireframe_animations](http://wiki.archlinux.org/index.php/Xgl#Remove_ugly_and_slow_GNOME.27s_wireframe_animations)

---

### Post by dckirba on 2006-10-08
Hey guys, that did help. I'm still slightly fuzzy on the details, but I guess that'll clear up once I install and try them out.

However, I did have some problems with the Compiz packages. I was able to find compiz, but not able to find compiz-manager and other packages needed to run compiz.

Also, am I correct in assuming that if I have xserver-xorg installed, I have xgl?

Thanks a lot,
David K

---

### Post by jaboua on 2006-10-08
No. Xserver-xorg is the good, old xserver with AIGLX extensions; XGL is an new xserver built from scratch.

I believe there is an article in the ubuntu wiki describing everything how to set up compiz and XGL, I tried it once before on dapper and it worked fine.

---

### Post by dckirba on 2006-10-08
Thanks!

Those Wikis were useful. Unfortunately my modem is dead at home so I'm manually downloading all the packages and hope that I don't miss any dependencies. Too lazy to walk out again on a sunday afternoon :)

I'm going with compiz for now and will wait till a while for Beryl though it really sounds nice.

Cheers,
David K

---

### Post by dckirba on 2006-10-09
Hi again,

I installed xserver-xgl on my computer and it works. I followed the community wiki. I logged into my xgl session and to check I ran:

[COLOR="DarkRed"]david@home01:~$ ps -e | grep Xgl
13654 ?        00:00:03 Xgl
david@home01:~$[/COLOR]

since there is output, I assume it means xgl is running because that's what the wiki said.

I downloaded compiz and compiz-gnome from the ubuntu package mirrors. They installed successfully, didn't ask for any dependencies.

However, the compiz wiki says to run compiz-start after installing compiz and this is what I get:

[COLOR="DarkRed"]david@home01:~$ compiz-start
bash: compiz-start: command not found[/COLOR]

So I decided to run compiz to see what happened and this is what I got:

[COLOR="DarkRed"]david@home01:~$ compiz
david@home01:~$ compiz.real: Screen 0 on display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No manageable screens found on display :1.0[/COLOR]

So I'm a bit stuck at the moment. I'm running Dapper at home. I don't have internet access from that computer at the moment because my modem is fried so I'm manually downloading packages.

I have a NVidia Geforce MX 4000 Graphics card with the driver installed.

The wikis I followed are: Xgl and InstallingCompiz from wiki.ubuntu.com

I also noticed that from my Xgl session I don't have a shutdown option. Also, the graphics are a wee bit scratchy, if I scroll really fast, then there's some text left hanging in space...

Any help would be appreciated a lot.


--edit - much later in the night :D

The forums were off for maintenance so I thought maybe I'd downloaded older packages and I downloaded them again from [www.beerorkid.com](www.beerorkid.com)

The packages I downloaded were compiz, compiz-core, compiz-plugins and compiz-gnome.

The versions of compiz, compiz-core and compiz-gnome are: 0.0.13.38

compiz-plugins asks for a version of compiz-core>= 0.0.13.54
compiz asks for compiz-plugins

so my new question, thankyou for bearing with me this far, is, where do I find the newest packages?

I have to download the packages and take them home to install. No internet at home. So that's what's causing most of the problem.](*,) 


Thanks
David K

---

