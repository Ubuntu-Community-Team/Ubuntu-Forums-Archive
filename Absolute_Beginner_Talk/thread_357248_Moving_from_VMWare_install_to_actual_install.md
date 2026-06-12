---
title: "Moving from VMWare install to actual install"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Kamiyay on 2007-02-09
Ok, I have Ubuntu 6.06 installed and working on a virtual machine vmware on my dell inspiron 9100 laptop. I am pretty sure I will make a full switch when I get the time to (I am in the middle of my college semester and would rather I waited until after to make the switch). I basically have, or will have, Ubuntu set up the way I want. I was wondering what the easiest way to make the switch was. Do I just have to forget about the VMWare stuff and install it clean? Or can I save some of the settings done in it? Granted I think that some drivers may be a bit different. Is there a way to back up settings and then restore them after I did a brand new install? I don't think that a "Ghost" will work, though I am familiar with the software, but let me know if it will...

Anywho, thanks for your time.

---

### Post by Kethinov on 2007-02-09
I would suggest a clean install. But you could backup your home folder first and restore it after the installation to keep all your settings.

---

### Post by Kamiyay on 2007-02-09
How would I go about doing that?

---

### Post by G Morgan on 2007-02-09
I assume you are using firefox. Take the ~/.mozilla directory and copy it onto USB flash or equivalent. This will allow you to transfer bookmarks, extensions and other details to your native install by copying it back into your home directory. (to find it press CTRL+H in nautilus, it will be hidden by default as all files/directories starting with a . are, all your personal config files will be stored like this in your home directory).

Anything else you want to transfer can be done the same way. I don't think much else will be transferable. You are looking mainly at data (FWIW it is a good idea to have a separate partition that you mount in home in order to store data in case of an upgrade. If you install a new Ubuntu version or a different distro altogether it becomes trivial to port your data then since it becomes one line in fstab).

---

