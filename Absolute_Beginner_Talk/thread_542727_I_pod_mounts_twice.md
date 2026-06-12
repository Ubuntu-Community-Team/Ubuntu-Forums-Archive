---
title: "I pod mounts twice?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-09-04
I have a slightly unusual problem in that my Ipod seems to mount twice, after connecting my ipod I have a device called "IPOD" which seems to actually be the ipod with all my data and things on it. But, theres another device called "apple IPOD music player" which gives mount errors if I try and open it in thunar (im using Xubuntu) Does any have any idea how to get rid of the phantom Ipod?

---

### Post by felicity on 2007-09-04
You might want to look at this bug report and try the patches included: [http://bugzilla.xfce.org/show_bug.cgi?id=2789]("http://bugzilla.xfce.org/show_bug.cgi?id=2789")

---

### Post by guardsman85 on 2007-09-04
> **tabithaboof said:**
> another device called "apple IPOD music player" which gives mount errors if I try and open it
Can you be more specific?  I'm not an ipod buff, but it might be that there is a separate read-only partition on the ipod hard drive (or other embedded storage) which has operating system files.

---

### Post by tabithaboof on 2007-09-04
> **felicity said:**
> You might want to look at this bug report and try the patches included: [http://bugzilla.xfce.org/show_bug.cgi?id=2789]("http://bugzilla.xfce.org/show_bug.cgi?id=2789")

That looks like exactly the right thing, unfortunately, without meaning to seem terribly lazy, I honestly can't work out how to apply the patch!

---

### Post by felicity on 2007-09-04
I don't know much about patching myself but I believe this should work..

First you download both thunar and thunar-volman:
[http://thunar.xfce.org/download/sources/Thunar/0.8.0/Thunar-0.8.0.tar.bz2]("http://thunar.xfce.org/download/sources/Thunar/0.8.0/Thunar-0.8.0.tar.bz2")
[http://prdownload.berlios.de/xfce-goodies/thunar-volman-0.1.2.tar.bz2]("http://prdownload.berlios.de/xfce-goodies/thunar-volman-0.1.2.tar.bz2")

Extract them and you will have two seperate folders to work from, a thunar folder and a thunar-volman folder.

Take the thunar-vfs-add-is-mountable.diff patch and put it in the thunar folder. (to do this you will probably need to make a new file in the folder, call it thunar.diff for instance, and enter the text of thunar-vfs-add-is-mountable.diff in it.

Open a terminal in the folder and use this command:
patch -p0 <  thunar.diff

Then go to the thunar-volman folder, and make a new file called thunar-volman.diff and paste the contents of thunar-volman-mount-only-mountable.diff into it.
Then open a terminal in the thunar-volman folder and use this command:
patch -p0 < thunar-volman.diff

Now both should be patched.. so you have to install them. You should probably remove thunar and thunar-volman first if you have them installed. 

The 90-ipod-ignore-fw-part.diff should be put in /etc/hal/fdi/policy/  .. I can't verify as I'm not on Ubuntu right now. Check if /etc/hal/fdi/policy/ has other files that look similar in it, if so it's the correct folder to put it in:
ls /etc/hal/fdi/policy/

---

