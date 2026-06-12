---
title: "Can't get rid of Xubuntu bootup &amp; shutdown screens"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by al_black on 2006-10-10
I recently decided to make the switch from "an operating system we won't mention here" to Ubuntu for my home use... I've been experimenting with Ubuntu (Dapper 6.06) for several weeks now and have been quite happy with it... This evening I decided to try several of the alternative window managers (Xfce and KDE)... so first I used Synaptic to install the package "xubuntu-desktop"... then I used it to install "kubuntu-desktop"... I thought that this would simply give me extra choices for "Sessions" when I logged in... but it seems to have turned my PC into a Xubuntu machine and I can't get it back to being a Ubuntu machine... what I mean is that when the PC boots up or shuts down now it always displays the Xubuntu blue graphics instead of the Ubuntu orange graphics... I was able to use System->Administration->BootUp-Manager to at least get the login screen back to the normal Ubuntu login screen... but the blue Xubuntu bootup and shutdown screens remain... 

My questions are:

1. Is it just a question of alternative colors and graphics being used during the bootup and shutdown of the PC? ... or is something different actually happening (Xubuntu vs. Ubuntu) (i.e. - different services being started up, etc.???)...

2. Can I get my PC back to "how it used to be" or do I have to do a fresh installation of Ubuntu from CD?

3. In the future, if I just want to have the option of occasionally starting an Xfce or KDE session (but don't want them to mess with the default Ubuntu/Gnome behavior) what package(s) should I install? (i.e. - I don't think I would ever try to install "xubuntu-desktop" or "kubuntu-desktop" packages again... should I just install the "xfce4" and/or "kde" packages after a fresh Ubuntu installation???)

Thanks!!!
Al Black

---

### Post by PriceChild on 2006-10-10
You may still log into whatever DE you want by choosing it from the "sessions" menu on the login screen.

---

### Post by al_black on 2006-10-10
Thanks for the quick reply...

I realize I can still get to the various desktops (Gnome, Xfce, or KDE) at login... I just want to get rid of the blue Xubuntu screens at bootup and shutdown and most of all I want to know if something "different" is happening because I'm now seeing the blue Xubuntu screens at bootup and shutdown (rather than the orange Ubuntu screens I used to see).

---

### Post by blendmaster on 2006-10-10
I know what you mean, same prob here.

This is a simple thing that doesn't really affect your system, but if you're a perfectionist like me (or maybe al_black here) you want this tweaked.

What he means is that, at startup, when you have a fresh install of Ubuntu, it shows the ubuntu sign (with brown letters) and shows startup processes. It does this for shutdown too. But, when you install KDE, It will say Kubuntu instead, and have the blue lettering.

This may be a case where we have to edit the files for startup/shutdown, but I haven't yet explored this very much.

---

### Post by al_black on 2006-10-10
that's exactly it, blendmaster...

I'm guessing that it's probably just a "cosmetic" issue... but being a bit OCD/perfectionistic, I gotta know if there's something different happening (during a blue screen Xubuntu bootup and shutdown vs. an orange screen Ubuntu bootup and shutdown)... and I will probably take the time to do a complete reinstall/reconfigure if that's what it takes to get things "back to normal"... I hope I don't have to do that though...

Thanks!!!

P.S. - and again, if I do end up doing a complete/fresh reinstall of Ubuntu, what packages should I install ("xfce4" and "kde"???) so I don't accidentally mess with the bootup and shutdown screens next time (while still getting the capability to occasionally run Xfce and KDE sessions)???

---

### Post by econobeing on 2006-10-10
i would think that if you are going to install it again, start with kubuntu/xubuntu then install xfce4/kde, then install gnome LAST.

haven't tried it but my system has the kubuntu startup screen too, since i installed KDE. i'm just assuming that the startup screen is for whatever package you installed last.

---

### Post by ClarkePeters on 2006-10-10
I think what your concerne is that; does the different boot-up/shut down screens mean that something has changed "under the hood" right?

Well, not sure. I run Ubuntu on Xubuntu (installed Xubuntu first) and I swear there's something different happening under the hood. For instance, when I did an Ubuntu install I had bad graphics and even after an EasyUbuntu install I couldn't get all my things working. 
However, when I went back, reformatted everything and did a fresh Xubuntu install and then Ubuntu via synaptic, all things work well. So, something is definitely different, however, can't put a finger on it, but I'd like to know as well what's happening under the hood-- is there something signifcantly different between Xubuntu and Ubuntu?

sorry can't help though.

---

### Post by blendmaster on 2006-10-10
Though you shouldn't quote me on this, as it's coming from assumption.

If you install KDE and XFCE4 first, and then install Ubuntu, the Ubuntu startup/shutdown screen should come up.

I'm guessing this is so because I installed KDE after Ubuntu, and KDE overrided Ubuntu, so I think the last installation will be the final screen.

However, I don't think you have to reinstall the entire Ubuntu OS, because now that I'm looking through the files installed from KDE, I see packages. So, because I see this, I'm guessing the deletion of one of these files will fix this.

Sorry I'm not of more help!

---

### Post by al_black on 2006-10-10
hmmmmm... it sounds like this might actually be an "issue" (i.e. - if something other than cosmetic graphics is different between an Ubuntu or Kubuntu or Xubuntu bootup and shutdown activities)... I am totally a "newbie" to the Ubuntu community (although I've played a little with other Linux distros over the years)... should this question be posed in a more specific forum??? (which one?)

---

### Post by Medieval_Creations on 2006-10-10
Run these two commands from the terminal.  It will change the start & shutdown bootsplash screens back to the original Ubuntu...

sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

and the bootsplash screen has no effect on the system as to what's being loaded, it just makes it look pretty... My guess is that all the same major things are loaded for the different versions...  You can always check to see what is being loaded at startup and change things if needed with a boot manager (if needed)... You shouldn't need to reinstall...

Got the command from this HOWTO - [http://ubuntuos.com/2006/02/howto-change-the-default-usplash-colors](http://ubuntuos.com/2006/02/howto-change-the-default-usplash-colors)

---

