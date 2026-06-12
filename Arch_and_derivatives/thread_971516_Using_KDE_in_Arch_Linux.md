---
title: "Using KDE in Arch Linux"
date: 2008-11-05
forum: Arch and derivatives
---

### Post by BetaMaster on 2008-11-05
Okay, so, I'm *pretty* sure this would fit in here, as it's relating to a desktop environment, but since it isn't Ubuntu-related, I could be wrong. Feel free to move it, and my apologies if this was incorrectly placed.

At any rate, I've been trying out Arch Linux for the past 24 hours or so. I like the CLI, and I like the idea of installing everything, starting with a blank slate. I've also used Ubuntu exclusively for about five years now and wanted to try another distro (haven't tried Fedora, Suse, or Red Hat since like, '03).

I'm getting Arch set up quite nicely, but I'm a bit miffed by one particular thing with using KDE (or, it seems, any WM - same with Gnome), and that's the always-present xterm window. If you close it, I get kicked back to the xorg screen. Is there any way to hide it so it's not always there? It's just annoying since it takes up a good amount of space in KDE.

Thanks!

---

### Post by BetaMaster on 2008-11-05
Bump? If it's not possible, you can just tell me that and be done with it, I'd just like to know if it is or not.

---

### Post by mojoman on 2008-11-05
You're more likely to get an answer either in the ubuntuforum sub-forum for Arch or in a pure archlinux forum.

[_http://ubuntuforums.org/forumdisplay.php?f=321_]("http://ubuntuforums.org/forumdisplay.php?f=321")

[_http://bbs.archlinux.org/_]("http://bbs.archlinux.org/")

---

### Post by overdrank on 2008-11-05
Moved to  Arch :)

---

### Post by mips on 2008-11-05
I have no idea what you are talking about. Ever present xterm window? I don't have that.

Maybe elaborate a bit more or supply a screenshot.

How do you start KDE?

---

### Post by BetaMaster on 2008-11-05
Thanks for moving it, I actually wasn't aware there was an Arch forum!

I can supply a screenshot if need be - I'm back in Ubuntu right now though. As for how I start kde, I run 'startx' to get the basic xorg terminal (it shows up as a black screen with a grey terminal in the upper left corner) with a curser. In the terminal, I run 'startkde.' If I run startkde before running startx, I get an error that seems to mean it can't start KDE since Xorg isn't running.

Hope that helps!

---

### Post by m_duck on 2008-11-05
If you edit your ~/.xinitrc
```
sudo nano ~/.xinitrc
```
and make sure all lines are commented except for "exec startkde" or whatever it is for kde (i can't remember specifically). It seems like you still have "exec xterm" uncommented in this file which is what will be bringing up the xterm window in the upper left when you type startx. Once you have changed this, you should get kde when you type startx.

---

### Post by Rumor on 2008-11-05
That screen you are talking about it a default x-session screen. I would recommand starting KDE either by using kdm / gmd / slim in your daemons array to give you a graphical login or editing your ~/.xinitrc file and adding "exec startkde" without the quotes to is, commenting out any other DE/WM it may be trying to start.

---

### Post by handy on 2008-11-05
***@BetaMaster:***  It sounds like you did your installation without following the Arch Beginners Guide, which I have linked to at the install KDE section here:

***_[http://wiki.archlinux.org/index.php/Beginners_Guide#KDE](http://wiki.archlinux.org/index.php/Beginners_Guide#KDE)_***

Where you can check that you have not missed anything in the setup, after which it gives you a link to here:

***_[http://wiki.archlinux.org/index.php/Adding_a_login_manager_(KDM%2C_GDM%2C_or_XDM)_to_automatically_boot_on_startup](http://wiki.archlinux.org/index.php/Adding_a_login_manager_(KDM%2C_GDM%2C_or_XDM)_to_automatically_boot_on_startup)_***

Where you get the instructions for installing & setting up your login manager.

You won't have any problems after reading through those two.

---

### Post by SomeGuyDude on 2008-11-05
> **m_duck said:**
> If you edit your ~/.xinitrc
```
sudo nano ~/.xinitrc
```

Random note, you don't need the "sudo" because the file is in your home directory. No need for root access.

Also, are you using normal KDE or KDEmod? If the former, go for KDEmod.

---

### Post by BetaMaster on 2008-11-05
Okay, a lot to reply to. I had 'exec xterm' uncommented in ~/.xinitrc, so I commented it and now I'm in KDE without an xterm session running. So, thanks!

Now, @handy
I guess I didn't follow through the beginner's install guide entirely, but I did use it for a large portion of the install. Must have missed the part about a login manager!

@SomeGuyDude, I'm using normal KDE. I read a bit about KDEmod, but didn't *quite* understand what it was. Modifications to KDE3 so it's more like KDE4?
Also, if I switch to KDEmod, will that require uninstalling KDE4 and redownloading KDEmod?

Thanks!

---

### Post by m_duck on 2008-11-05
SomeGuyDude, good point - wasn't concentrating.

KDEmod has two versions, one based on KDE 3 and one based on KDE 4. Their current one is KDE 4. KDEmod is a "tweaked package set" of KDE, "optimised for arch" [from [KDEmod website](http://kdemod.ath.cx/about.html)].

Switching to KDEmod will mean that everything KDE and qt needs to be removed before you start (though programs, amarok etc, do not need to be removed), due to conflicts with the modified KDEmod packages. The "get it" link on the KDEmod website guides you through it all though.

---

### Post by mips on 2008-11-06
> **BetaMaster said:**
> 
@SomeGuyDude, I'm using normal KDE. I read a bit about KDEmod, but didn't *quite* understand what it was. Modifications to KDE3 so it's more like KDE4?
Also, if I switch to KDEmod, will that require uninstalling KDE4 and redownloading KDEmod?


kdemod is VERY modular. They took KDE and split it up into small components. So instead of installing a meta package you can choose to only install parts of the meta package in kdemod.

Example, normal KDE4 has a meta package called **kdegraphics** which installs several packages whether you like it or not.

KDEmod4 on the other hand splits the **kdegraphics** package up into it's individual components as listed below:

kdemod-core/kdemod-kdegraphics-common 4.1.1-1
kdemod-core/kdemod-kdegraphics-doc 4.1.1-1
kdemod-core/kdemod-kdegraphics-gwenview 4.1.1-1
kdemod-core/kdemod-kdegraphics-kamera 4.1.1-1
kdemod-core/kdemod-kdegraphics-kcolorchooser 4.1.1-1
kdemod-core/kdemod-kdegraphics-kolourpaint 4.1.1-1
kdemod-core/kdemod-kdegraphics-kruler 4.1.1-1
kdemod-core/kdemod-kdegraphics-ksnapshot 4.1.1-1
kdemod-core/kdemod-kdegraphics-okular 4.1.1-1

This allows you to only select the actual kdegraphics packages you want instead of installing all of them in normal KDE.

This is the MAIN difference.

The other slight difference is they applied about 3 patches to kdemod and these are purely cosmetic and it's basically to identify it as kdemod instead of kde. The old kdemod3.5 had plenty of patches applied but they are not going down that road again. Recently they backported a few features from 4.2 to 4.1 that provides more functionality, there were'nt many though.

Hope this makes sense.

You will have to Uninstall KDE4 & QT to install KDEmod4.

They also still have KDEmod3 available.

---

### Post by medic2000 on 2008-11-10
Mips can you suggest me KdeMod3 programs.Which ones do you use?

---

### Post by mips on 2008-11-11
> **medic2000 said:**
> Mips can you suggest me KdeMod3 programs.Which ones do you use?

I just pick what I 'need' from the kdemod repos. Maybe install Shaman and use it to browse through the packages as it has descriptions for all packages.

If you are still not sure maybe install kdemod-complete and have a look at all the packages then decide what you want to keep and what you want to remove.

---

### Post by medic2000 on 2008-11-11
Yes i have already looked at nearly all of them. It was time consuming but i saw all of them.And some programs are really crap. 

The thing i meant to ask you and other Kdemod users is for example there are some programs like Kview,Kuickshow,Gwenview doing nearly the same thing. Which one do you choose?

Kmplayer? Anyone like it i wonder?

---

### Post by SomeGuyDude on 2008-11-11
This is my big problem with DE's. I'd much rather discover I have a task that needs completed and install something for it than get two gigs of software I never intend on using because someone wanted to cover all the bases.

---

