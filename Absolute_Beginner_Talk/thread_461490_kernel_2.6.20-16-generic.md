---
title: "kernel 2.6.20-16-generic"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ironmike on 2007-06-01
I recently attempted to logon to my PC and it locks right after the initial Ubuntu splash screen. Actually after the initial splash screen the screen just goes black with the cursor blinking in the upper left hand corner. I am running kernel 2.6.20-16-generic. I even get locked up in recovery mode. I can however log in perfectly fine using the previous kernel (2.6.20-15-generic).

My question is how do I either repair the kernel 2.6.20-16 or uninstall and reinstall it. The only updates I have made for the computer are from the automatic updates. Any help would be appreciated.

---

### Post by old_geekster on 2007-06-01
There are several other posts on the forum about this problem.  There has been a bug report submitted.

I suggest that you select kernel -15 in GRUB and boot to it or which ever kernel is accessible.  Then, using "Synaptic Package Manater", you can delete kernel -16.

---

### Post by jonward0690 on 2007-06-01
This new kernal has been giving a lot of people trouble I wonder why

---

### Post by HereInOz on 2007-06-01
Just to cover the uninstall, search for "linux-image" in Synaptic, that will find it.

Then mark it for complete removal.

---

### Post by Repent on 2007-06-01
All I had to do to fix it was to reinstall my nvidia drivers, and all is well now.:D

---

### Post by ironmike on 2007-06-02
Once i uninstall the .16 kernel, how do I reinstall it.

---

### Post by Inxsible on 2007-06-02
I would suggest that you dont remove the -16 kernel, and simply keep using the -15 until you get more kernel updates which fixes the problem

---

### Post by Inxsible on 2007-06-02
if you still would not like to see the entries in your grub, you can comment them out in the /boot/grub/menu.lst

and it will show you only your -15 entries, that way you will still have the -16 kernel but it wont show up in the grub.

Later when more updates are done to -16 and all is rectified, you can uncomment those entries and start using -16 kernel

---

### Post by Repent on 2007-06-02
This is what I did, it worked for me but there's no saying it will work for you.
1. Boot into recovery mode.
2. type sudo aptitude install Envy
3. type Envy -t
4. I picked install nvidia drivers, if you do this choose what ever driver you need.

When I picked Envy the program looked at my graphics card and installed the correct drivers for it.
I hope this helps
P.S.
I see now you said you even got locked out of recovery mode,  if thats the case you should do as Inxsible advised.

---

