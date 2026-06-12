---
title: "Help installing flash player 9"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2007-03-27
Hey, well it appears that I no longer have a good enough flash player version for the Internet and I've been putting off updating because of the hassle but now my version is near useless so I downloaded flash player 9 from adobe but I don't know how to install it. It would be much easier if there was a repository but ```
 sudo apt-get install flashplayer 
``` and many similar codes like that won't work, so please help me. I'm on Kubuntu 6.10. Thanks in advance.

---

### Post by DSn0wMan on 2007-03-27
It is in the repo's try flashplugin-nonfree

---

### Post by lordvolo on 2007-03-27
just decompress the file you downloaded and take the install file(forget the name) and drag it into the terminal, it worked for me

---

### Post by sushii. on 2007-03-27
Download flashplayer from Adobe's site, extract the tarball (if your using GNOME, right click > Extract Here). Open a terminal, cd to the created directory, then type "./configure". When that's done type "make" and then when that finishes type "make install". If you get some errors try putting "sudo" before some of the commands.

---

