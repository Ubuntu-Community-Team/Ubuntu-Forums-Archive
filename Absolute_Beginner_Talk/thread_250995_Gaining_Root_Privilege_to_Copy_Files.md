---
title: "Gaining Root Privilege to Copy Files"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by dabolay on 2006-09-04
I am a brand new user, having successfully downloaded and am running Ubuntu 6.06.

I have also successfully enabled Thunderbird, having used it previously in XP.  I have a copy of my profile on a CD.  I have opened two file browsers and want to move the files from my CD to /etc/mozilla-thunderbird.  The current documentation says that I should be able to move the files like I have been used to in Windows.

However, whenever I attempt to perform this function, I am told that I do not have root privilege.  I am logged in as an administrator.  I have attempted to use sudo in terminal.  All to no avail.

What am I doing wrong?  What should I do to move my email and preferences to Ubuntu?

Thanks,

Dennis

---

### Post by Anonii on 2006-09-04
gksudo nautilus

in the terminal, that will give your nautilus sudo powahs!!~!

Also, dont forget to close nautilus when you finish your job, root applications shouldnt be left open.

---

### Post by dabolay on 2006-09-04
Ok... gksudo nautilus.

Do I still need to have the two browsers open?  Will I still use my mouse to physically move the files from the cdrom to /etc/mozilla-thunderbird?

Thanks,

Dennis

---

### Post by Anonii on 2006-09-04
> **dabolay said:**
> Ok... gksudo nautilus.

Do I still need to have the two browsers open?  Will I still use my mouse to physically move the files from the cdrom to /etc/mozilla-thunderbird?

Thanks,

Dennis
You will have a Nautilus, your file browser if you are using GNOME, with root access, and yes you will be able to use your mouse, it involves zero command line, except the first command.

---

### Post by dabolay on 2006-09-04
Thank you Anonii.  I followed your advice and everything worked.  I did get a response in terminal that caused me to wonder what is being said: (nautilus:10976): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

Now... how do I close out of Nautilus?

Thanks again.

Dennis

---

### Post by skymt on 2006-09-04
That error message is meaningless. It just means it couldn't connect to a session manager, which you don't want it to.

If the root Nautilus doesn't exit when you close the window, hit Control-C in the terminal you ran it from.

---

