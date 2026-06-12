---
title: "broken packages"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by robeec on 2007-03-18
hi good ppl--i haven't been here in a about a year...i'm running dapper drake and i just installed EasyUbuntu. i cannot get the codecs to install for browser plugins, 'cause it says "fix broken packages" totem-gstreamer and gstreamer-firefox-plugin need to be installed; i searched using synaptic but these plugins are already installed.

any idea what i'm doing wrong?

---

### Post by tipsqueal on 2007-03-18
I had the same problem with Easy Ubuntu when I was using Dapper. I then used Automatix, and that worked much better. I would suggest going into synaptic uninstalling all the stuff that is installed but isn't working, then installing Automatix and running it. That seemed to work for me, although that was a while ago.

---

### Post by IusedTObeSOMEONEelse on 2007-03-18
> **tipsqueal said:**
> I had the same problem with Easy Ubuntu when I was using Dapper. I then used Automatix, and that worked much better. I would suggest going into synaptic uninstalling all the stuff that is installed but isn't working, then installing Automatix and running it. That seemed to work for me, although that was a while ago.

Is Automatix back up and running again, as they were down for a bit?

---

### Post by ramjet_1953 on 2007-03-19
Have you tried opening Synaptic Package Manager, clicking on [COLOR="Blue"]Edit>Fix Broken Packages[/COLOR] ?

If this doesn't work, you may need to edit your /var/lib/dpkg/status file.

However before doing this, make sure that you back it up first!

To edit the file, I suggest you do this:

sudo kate /var/lib/dpkg/status 
if you don't like Kate as an editor, use the flavour that you prefer.

It is a fairly big file, but if you do a search for the relevant entrys, it will quickly find them.
CAREFULLY delete the offending entries and save the file.

Synaptic should then be happy again.

Remember, by doing this you haven't actually deleted the broken packages, but Synaptic doesn't know that they are there any more, so future disk activity will overwrite them. It is like deleting a file in Windows.

Reagards,
Roger :cool:

---

### Post by NyteGeek on 2007-03-22
> **tipsqueal said:**
> I had the same problem with Easy Ubuntu when I was using Dapper. I then used Automatix, and that worked much better. I would suggest going into synaptic uninstalling all the stuff that is installed but isn't working, then installing Automatix and running it. That seemed to work for me, although that was a while ago.

You should use synaptic to fix the broken packages first.

---

### Post by NyteGeek on 2007-03-22
> **MustangSallydd said:**
> Is Automatix back up and running again, as they were down for a bit?

They are having problems with their new server. I have been pointing to [http://www.ubuntuguide.org](http://www.ubuntuguide.org).. The instructions for installing applications and configuring the system there are great for new users.

---

