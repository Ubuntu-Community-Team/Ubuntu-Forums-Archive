---
title: "Uninstalling Desktop and installing Server"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by mamix0ye on 2008-01-31
I downloaded and installed ubuntu desktop and thought I had downloaded the server version.

How do I go about uninstalling and installing server?  I booted up and it is not progressing through the partitions area at this time... probably not doing what I'm suppose to do...

Thanks.

---

### Post by emarkd on 2008-01-31
You can "upgrade" your desktop install to include all of the server stuff by using Synaptic.  Click on Edit > Mark Packages by Task.. and select LAMP Server.

---

### Post by njparton on 2008-01-31
If you can live with gdm running then you can just use the desktop installion you have and install the extra apps you may need like php, apache etc. You could even disable it under services in the menu to save a few CPU cycles.

If you're not running on limited hardware this should be ok.  If you've got limited RAM etc then uninstall gnome etc. Use synaptic to search for all gnome related apps.

If you're new to linux leaving the desktop in place might actually be an advantage otherwise you'll just be "stuck" with the command line.

---

### Post by mamix0ye on 2008-01-31
thanks for all the quick advice.... but now I'm going to show my linux ignorance... what is synaptic and do I need to install it first?

---

### Post by randomjohn on 2008-01-31
and what about getting rid of all the extra stuff that comes with desktop?  openoffice, gimp, etc.... is there any easy way to do that so you just start with the clean/stripped down server distribution?

---

### Post by jrothwell97 on 2008-01-31
Synaptic is Ubuntu's front end to the Apt package management system. All you have to do is go into System/Administration/Synaptic Package Manager.

---

### Post by randomjohn on 2008-01-31
> **mamix0ye said:**
> thanks for all the quick advice.... but now I'm going to show my linux ignorance... what is synaptic and do I need to install it first?
 
it's the gui package manager.  you don't need to install it.  it's under administration.

---

### Post by mamix0ye on 2008-01-31
Thanks again....  I'm impressed at the quick feed back in this forum... I'm new to Ubuntu and trying to get up to speed on it and LAMP.  I'm a 20 year veteran Windows programmer and now moving into the DBA world...

Thanks...

---

### Post by njparton on 2008-01-31
Keep gnome - you won't regret it if you're a noob!

---

### Post by mamix0ye on 2008-01-31
I am... the last time I installed Linux on my pc was 7 years ago... Redhat..

Gnome was horrible and finding drivers for hardward was not easy...  So far, Ubuntu has been awesome and I'm considering using it primarily if I can setup VPN software on it..

Do you know of any good books for Ubuntu and LAMP?

---

### Post by kwacka on 2008-01-31
> **mamix0ye said:**
> I am... the last time I installed Linux on my pc was 7 years ago... Redhat..

Gnome was horrible and finding drivers for hardward was not easy...  So far, Ubuntu has been awesome and I'm considering using it primarily if I can setup VPN software on it..

Do you know of any good books for Ubuntu and LAMP?

Try the "howto" site for information on installing a LAMP setup (& other stuff): [http://www.howtoforge.com/](http://www.howtoforge.com/)

(I was flamed on another forum for posting this link - apparently its useless because it doesn't mention that you also need to be knowledgeable about MySQL, apache &PHP - I was stupid enough to assume that this would be taken as read. Dumb of me, I know)

There's plenty of information online (just search here, for example) that should answer just about anything you want to know.

Books you might want to check out - Ubuntu Linux Toolbox and Canonical ('parent company' of Ubuntu) produce their own book which is pretty good, just check Amazon for the title.

---

