---
title: "Linux Folder Rules (or: WHERE are my programs)"
date: 2005-07-02
forum: Absolute Beginner Talk
---

### Post by Jela on 2005-07-02
Hallo!

Having a good deal of Windows-related abilities and common sense (sounds paradox... *g*), but no Linux experience or help (apart from google), I am managing fine so far; installing, cheating and sudo-ing happily all around my new Ubuntu -- but as I start to think about a more serious relationship (= switching to Linux), I would love to find a little general information about:

WHERE are programs installed in Linux?
WHICH folders do WHAT?

Before I do terrible shit placing executables everywhere, adding a lot of stuff to my PATH and so on, perhaps somebody could care to tell me:

Which is the thing that is similar to the "Program Files" Folder in Win? If it exists?
If some installation-readme tells me to "put this in the plugin-folder of your firefox-installation-directory", which of the things that I get from "whereis firefox" is right? Or the .programname stuff in my homedir? But this is then only for the user, not for the whole system? Not important now, as I have only one user, but still I would like to understand?

And what is the difference between /bin and  /usr/bin?

I would be incredibly grateful fpr somebody that can give me a short overview about the structure of Information and programs in Linux -- or a link to such overview, as I belive that this exists, but won't find sth useful with google...

Thanks in Advance,
Jela

---

### Post by hardwarder on 2005-07-02
According with my Ubuntu experiences, here's a small list of what the folders mean to me.

/bin - executable stuff
/boot - where grub is located, also the kernels
/dev - Do not tamper
/etc - config files and such
/home - You know what this is
/lib - where libraries are located
/media - where i mount stuff
/opt - other programs. Put in here usually if I compiled from source.
/proc - Do not touch
/root - root home
/sbin - same as /bin
/sys - Do not touch
/tmp - temporary things
/usr - Unix System Resources
/var - variable stuff, e.g. changes most of the time

I use synaptic to check where program files are located using the properties dialog.

---

### Post by rpgcyco on 2005-07-02
This website may also help: [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

- Rpg Cyco

---

### Post by Jela on 2005-07-03
Thanks to both of you - Already much clearer!
Beautiful... Every day a new world!   :smile: 
Jela

---

