---
title: "gnome to fluxbox and back: inviting problems?"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-03-15
Hi,

been using ubuntu for about two weeks now and love it.  trying to move full-time to linux...

i'd like to try fluxbox, but am worried that if i install it and switch back and forth b/t it and the default gnome desktop, something's going to break.  is this correct?

anyone using fluxbox and the default desktop?

thanks,

takayuki

---

### Post by Xian on 2006-03-15
[QUOTE=takayuki]anyone using fluxbox and the default desktop?[/QUOTE]

You will be fine. It's not like when you install KDE and all your prefs, environment look, and paths get intertangled with Gnome. I've run both Flux and Gnome since Hoary, and you will have no issues with this concern.

---

### Post by Brunellus on 2006-03-15
[QUOTE=takayuki]Hi,

been using ubuntu for about two weeks now and love it.  trying to move full-time to linux...

i'd like to try fluxbox, but am worried that if i install it and switch back and forth b/t it and the default gnome desktop, something's going to break.  is this correct?

anyone using fluxbox and the default desktop?

thanks,

takayuki[/QUOTE]
No problem at all.  

Check out the fluxbox howto in my .sig, as well.  there's a fair amount of post-install tweaking you need to do with flux.

also, I did replace Metacity (gnome's default wm) with Fluxbox once, as an experiment.  It worked, but very poorly. 

I have concluded that Fluxbox is best on its own as a wm/ultralight desktop, while OpenBox integrates better with GNOME as GNOME's w/m.

---

### Post by takayuki on 2006-03-15
cool!  thanks for the info.  installing fluxbox now.

---

### Post by takayuki on 2006-03-16
I installed fluxbox and love it.  here's a few followup questions...

1.  when i launch nautilus, i sort of lose fluxbox.  suddenly, the old desktop pic (gnome) displays, i lose control of workspaces via the scrollwheel, and the little dock thingy (tech term) at the bottom is gone.  the icons in nautilus are all a generic "curled corner" document icons whether it's a directory or a document.

anyone had this issue, or know how to fix it?

2.  i'd like to edit the menu...  the menu is automatically generated.  i know i have to copy the auto generated one, then change some settings somewhere...  could some kind person post cut and paste terminal commands ?

thanks,

takayuki

---

### Post by Brunellus on 2006-03-16
your menu issue is discussed at length in the fluxbox howto in my sig.

---

### Post by takayuki on 2006-03-16
[QUOTE=Brunellus]your menu issue is discussed at length in the fluxbox howto in my sig.[/QUOTE]

Brunellus, thanks for the reply.  i couldn't have gotten this far without your detailed how to. 

I *am* reading the how to while experimenting with fluxbox, but the "do not edit this page" warning had me momentarily confused.

[PHP]
# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.
# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (Fluxbox)

# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)[/PHP]

after some scratching around, i realized that you could, in fact, edit the menu page without copying it.  and you do not have to edit the init page, because it is already set.

thanks again for the great how to.

regards,

takayuki

---

### Post by takayuki on 2006-03-16
did some googling and found the answer to my buggy nautilus experience.  i needed to comment out the nautilus entry and change it like this:

#         [exec] (Nautilus) {/usr/bin/nautilus} </usr/share/pixmaps/nautilus.xpm>
	    [exec] (Filemanager) {nautilus --no-desktop} </usr/share/pixmaps/nautilus.xpm>

now nautilus works.  are the generic icons in the nautilus windows the way it's supposed to be?  any way to sneak in folder icons, etc.?

---

### Post by Brunellus on 2006-03-16
[QUOTE=takayuki]did some googling and found the answer to my buggy nautilus experience.  i needed to comment out the nautilus entry and change it like this:

#         [exec] (Nautilus) {/usr/bin/nautilus} </usr/share/pixmaps/nautilus.xpm>
	    [exec] (Filemanager) {nautilus --no-desktop} </usr/share/pixmaps/nautilus.xpm>

now nautilus works.  are the generic icons in the nautilus windows the way it's supposed to be?  any way to sneak in folder icons, etc.?[/QUOTE]
not sure, actually.  I tend to use rox-filer as my filemanager in fluxbox, anyway

---

### Post by rushibhai on 2006-03-16
If you are on a laptop, you might also want to start gnome-power-manager upon login. Otherwise, some of the nicest features of ubuntu+laptop won't work well..

---

### Post by Luke on 2006-03-17
[QUOTE=rushibhai]If you are on a laptop, you might also want to start gnome-power-manager upon login. Otherwise, some of the nicest features of ubuntu+laptop won't work well..[/QUOTE]
i had gnome-power-manager installed but didn't really like it too much. seemed a little buggy. so i removed it (also had to remove a package called "power-manager") and just made a script that starts 'laptop-mode' on boot and configured acpi to suspend on lid close. those two things make me pretty happy using ubuntu on my laptop. i should mention that i was using a very old version of gnome-power-manager because the newer one (which i had gotten from backports) was even worse on my machine.

back to fluxbox, between the nice wiki entry and the positive experiences in this thread, i'm looking forward to trying out fluxbox this weekend.

---

### Post by takayuki on 2006-03-17
Luke,

i've been using fluxbox for about 2 days now and love it.  super fast and a ton of small touches that help increase productivity.  switching b/t workspaces is instantaneous using the mouse scroller wheel.  

i just installed rox-filer (file manager) per Brunellus' suggestion and it looks nice.  

takayuki

---

### Post by IYY on 2006-03-17
Yes, it's possible to have your nice icons in Nautilus while using Fluxbox, and it's very simple:

All you need to do is add the following lines to your xsession file:

```

GSDPID=`pidof gnome-settings-daemon`
if [  "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi

```

The xsession file should be in /etc/X11/gdm/Xsession if I remember correctly. If you don't want to mess with that, I think you could also add the same to ~/.fluxbox/startup. In addition to showing nice icons, this will also allow you to have Gnome themes for your GTK apps. I think this bit of info should be added to the wiki.

---

