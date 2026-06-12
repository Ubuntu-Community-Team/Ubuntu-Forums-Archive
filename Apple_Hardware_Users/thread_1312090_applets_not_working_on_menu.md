---
title: "applets not working on menu"
date: 2009-11-02
forum: Apple Hardware Users
---

### Post by natgab on 2009-11-02
Ok,

I have been using Ubuntu 9.04 for about 2 wks now.  I am having trouble with the applets on Gnome. I boot fine, but I get:

```
OAFIID:GNOME_WorkspaceSwitcherApplet
```

I get this for the clock, log off, workspace switcher,desktop applets. Then i get the "delete or don't delete box along with the error message.  I sometimes do a reboot, and all comes back, but that isn't a solution. ;)

(I will reboot and copy/paste full error msg. here)

I looked and found several pages, some point to it as a Gnome problem, since the user was on fedora. Other where old post here, but no solution.

Is there a fix I missed, or would swaping to Xubuntu desktop fix it? Can I use KDE 3.5, that seems ok on my iMac, it just the new KDE 4.0 on Kubuntu 9.04 that was too flaky for me.  I can live with out some of the eyecandy for now.

---

### Post by natgab on 2009-11-03
Answering myself:

I rebooted to write down the complete error message.  And of course like taking your car to the mechanic, everything was fine and I had all my applets this time.  

I noticed the trash can, workspace switcher and desktop applet gave you the option to lock to panel when you right click. I locked ALL of my applets, and that seems to have done the trick.  I rebooted several times and they no longer disappeared.

Hope this helps other switchers.  These little annoyances are probably the ones that bug the most when switching.

I will keep looking on how to add KDE 3.5 or XFCE to my choices of Desk Environment. Just to have a choice.

---

### Post by lidex on 2009-11-03
I would go ahead and delete when presented the option. Then in synaptic "mark for complete removal" these packages:
```
gnome-applets
gnome-applets-data
gnome-panel
gnome-panel-data
```
Click apply to execute changes. Finally, reinstall those packages and reboot.

---

### Post by natgab on 2009-11-04
You know, I still have the problem with the applets. I rebooted into Ubuntu and still had the error boxes.

I thought I had fixed it with checking the lock in place box. But again I got the error codes. So I will try what you suggest.  But do I then just "sudo apt-get intall" the 4 items listed?

I did get the XFCE desktop working.  The DE only w/o the Xubuntu apps, and so far that seems to be keeping its applets. :D

---

### Post by lidex on 2009-11-04
> **natgab said:**
> You know, I still have the problem with the applets. I rebooted into Ubuntu and still had the error boxes.

I thought I had fixed it with checking the lock in place box. But again I got the error codes. So I will try what you suggest.  But do I then just "sudo apt-get intall" the 4 items listed?

I did get the XFCE desktop working.  The DE only w/o the Xubuntu apps, and so far that seems to be keeping its applets. :D

Yes. Make sure you spell install correctly though.;)

---

