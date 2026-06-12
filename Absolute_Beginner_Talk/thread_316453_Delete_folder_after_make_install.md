---
title: "Delete folder after make install?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by jstad on 2006-12-10
I have been using Ubuntu for a while now and have always wondered if after I install my own compiled application (example, my own wpa_supplicant). After I run "make install" can I just "rm -rf wpa_supplicantx.x" folder without worries? Also once I have it installed with make, if I want to remove it, how do I do this?

This may be a really stupid question but it is one I really want answered. In ubuntu should I really be using make or is there a better alternative that integrates better with Ubuntu's package management?

thanks in advance for any help!

---

### Post by igknighted on 2006-12-10
Instead of make install, there is a way to make a .deb package instead which you could then install via dpkg.  This is really the best integrating you can do.  I think Aysiu outlined how to do this somewhere, so search the forums or wait for him to post here.

---

### Post by PriceChild on 2006-12-10
If you make install, you may want to keep the folder so that you can make uninstall it later.

You can simply run "checkinstall" instead of make install to build a quick shabby deb for you to manage.

---

### Post by IYY on 2006-12-10
> I have been using Ubuntu for a while now and have always wondered if after I install my own compiled application (example, my own wpa_supplicant). After I run "make install" can I just "rm -rf wpa_supplicantx.x" folder without worries? Also once I have it installed with make, if I want to remove it, how do I do this?

Yes, you can safely remove the directory after doing 'make install', because this command basically moves all the compiled code, and data to the appropriate locations on the file-system. Now, the bad news: after compiling an application this way, you often can't "uninstall" the application. I think some applications could have a "make uninstall" command, but then you need to keep the original source directory. This is why it's always better to use apt-get to install your software whenever possible.

---

### Post by PriceChild on 2006-12-10
> **IYY said:**
> This is why it's always better to use apt-get to install your software whenever possible.Even better.

---

### Post by igknighted on 2006-12-10
> **IYY said:**
> This is why it's always better to use apt-get to install your software whenever possible.

Or even better, use aptitude instead of apt-get

---

### Post by jstad on 2006-12-10
> **PriceChild said:**
> If you make install, you may want to keep the folder so that you can make uninstall it later.

You can simply run "checkinstall" instead of make install to build a quick shabby deb for you to manage.

Now when I do this with dpkg, do I need to manage the .deb file and put that somewhere or is that taken care of by itself?

---

### Post by PriceChild on 2006-12-10
> **jstad said:**
> Now when I do this with dpkg, do I need to manage the .deb file and put that somewhere or is that taken care of by itself?Works like any other deb :) Manageable by apt, synaptic, aptitude etc.

---

### Post by jstad on 2006-12-10
Alright so I dont need to copy the .deb file anywhere and I can safely remove the directory?

---

### Post by PriceChild on 2006-12-10
> **jstad said:**
> Alright so I dont need to copy the .deb file anywhere and I can safely remove the directory?Indeed :)

---

