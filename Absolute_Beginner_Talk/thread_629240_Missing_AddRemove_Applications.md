---
title: "Missing Add/Remove Applications"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by deathblossom on 2007-12-02
So, I finally got Ubuntu installed for the second time (the first time I installed over it because I screwed up the volume, big mistake) and now that it's installed, I have a problem.

The CD I was using to install gave me a lot of problems (installer had trouble reading from it) and I don't really have ready access to another copy, so none of the software installed and it was pretty much a server install that I had to install ubuntu-desktop over using the command prompt.

I did that and now that I have, I've noticed the Add/Remove Applications under the Applications menu has gone missing. There's no way for me to access it from the command prompt (gnome-app-install just gives me command not found). I went to Synaptic and saw the application, but when I clicked on it and said okay, it asked me to input the CD and knowing the CD is on the fritz, I clicked cancel. Now, gnome-app-install is completely gone from Synaptic.

I tried to install it using "sudo apt-get install gnome-app-install" but I'm told there's no installation candidate. I download the tar file from the Ubutu Help site and tried to follow the instructions provided, but I get an error with the "./configure" where it says command is not found.

Does anyone else have any ideas on how to re-install it (or if necessary, clean install Ubuntu without having to use the CD with as little pain involved as possible. Is it possible to make it install all the packages it was supposed to have at the beginning without having to clean install?

---

### Post by cypry on 2007-12-02
*The CD I was using to install gave me a lot of problems (installer had trouble reading from it)*.
 I had a similar problem, when I installed Gusty. Try the live CD, without ACPI. To do this, when you boot from it, add acpi=off in the boot options line.

---

### Post by GGLucas on 2007-12-02
You can force it to not get packages from the CD by unchecking it in Software Sources, that will make it download all the packages and never request the CD.

---

### Post by deathblossom on 2007-12-02
Well, my CD burner isn't working, so I actually got this CD from a friend of a friend. I emailed my actual friend a little bit ago and asked if he could make me the LiveCD version. 

Yeah, I actually don't have Software Sources listed, but I went to Synaptic Repositories and unchecked the cdrom. It's why I clicked no to installing gnome-app-install (since I forgot to do it before applying updates), but after I did and went back, gnome-app-install was gone. Is there any way to set up the actual CD that way?

---

