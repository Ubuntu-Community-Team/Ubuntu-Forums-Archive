---
title: "Networking in Ubuntu"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-08
Years ago ( 2002 ), I gave RedHat 9 a try and found it easier to use then most of the Distros
at the time.  I'd say Linux has come a long way since then.

Back then you had to manually install Samba to do any type of
graphical networking.  Is this still the case or is every thing ready
right out of the box with Ubuntu 7.04?

Thanks

---

### Post by p_quarles on 2007-08-08
It really depends upon your goal. If you want a network shared directory on your Windows desktop, then you will need to install and configure Samba. 

There are, however, many other graphical networking tools available, including remote desktop, NFS and Webmin.

---

### Post by Orbital75 on 2007-08-08
Yeah, I just want to share files on my desktop machine  with other on my network.
So Installing Samba is still a requirement for this. :KS

So I looked in the repositories and didn't see Samba.
What Packages do I need for graphical file sharing.

Thanks

---

### Post by p_quarles on 2007-08-08
Only if you want to share files with a Windows or Apple machine. If your network happens to be all *nix, it's a lot easier to use NFS.

---

### Post by Orbital75 on 2007-08-08
hummm... Samba isn't in the repository's, is it named different?  :confused:

Well, I ended up clicking on Share Folders in the System / Administration part or the GUI
and it stated I would have to install SMB services.  I just hit ok and it did it for me.
Back in the day I remember a Huge SMB GUI with tons of options.  Where's that
at. I was using Red Hat 9 at the time.

I think I may be thinking of SWAT

Is that still around?

---

### Post by p_quarles on 2007-08-08
No, the package is definitely called samba. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list

---

### Post by por100pre1 on 2007-08-08
Look for System> Administration> Shared Folders. There you'll be prompted to install Samba. :)

---

### Post by Orbital75 on 2007-08-08
> **p_quarles said:**
> No, the package is definitely called samba. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list

Yep, there enabled.
So it will Say SAMBA not gsmaba or SMB or something else.

Thanks por100pre1, that did install the services.
Is there something that looks like SWAT that I can
use? Thanks

I think that I used something called SWAT back when I used RedHad
it was a gui for samba

This is all I see when I search for it Samba in the repositories. 

[IMG]http://img514.imageshack.us/img514/5103/01screenshotpy4.png[/IMG]

---

### Post by Orbital75 on 2007-08-08
Well, I found a website that said to do this.

apt-get install samba swat netkit-inetd

It didn't put an icon in my gui anywhere.
where is it and how do I start it?

I typed [http://localhost:901](http://localhost:901)
in my browser but that didn't work.

I'd like to install SWAT
or at least something Graphical thats close.
thanks

---

### Post by p_quarles on 2007-08-08
The Add/Remove Applications menu is pretty limited. The reason you don't see Samba there is because the *real* package manager is is under the System >> Administration menu. I know you got it installed already, but thought you might like to know that.

You may have to edit your applications menu for SWAT to show up. Right-click on Applications, and you'll see an option to edit the menu. 

Alternatively, you can run it from the command line:
```
gksudo swat
```

---

### Post by Orbital75 on 2007-08-08
hum.... it gave me some authentication error....
I'm logged in as root. 

Anyone know how I can get Swat running.
from the searches I've done, it seems to be
a nightmare.  When I was using redhat it
was 3 clicks and done.

---

