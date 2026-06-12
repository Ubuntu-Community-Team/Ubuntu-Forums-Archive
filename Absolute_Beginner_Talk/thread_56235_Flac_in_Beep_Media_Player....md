---
title: "Flac in Beep Media Player..."
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Rajnyrb on 2005-08-11
I'm trying to compile .flac in Beep Media Player but it dosn't work. I would appreciate if someone could make a HOWTO-guide or something.

---

### Post by Kyral on 2005-08-11
have you tried installing the xmms-flac package? It should work

---

### Post by Rajnyrb on 2005-08-12
[QUOTE=Kyral]have you tried installing the xmms-flac package? It should work[/QUOTE]
 Yes, I have tried that, but it does not work.

---

### Post by ero-sennin on 2005-08-21
:)  Hey I had the same problem you did, this is what i did to have bmp play flac files. install the xmms-flac package off synaptic like the previous person said. Now go into console and type

sudo cp /usr/lib/input/libxmms-flac.la /usr/lib/bmp/Input/
sudo cp /usr/lib/input/libxmms-flac.so /usr/lib/bmp/Input/

then fire up bmp and look in the prefs plugins and see if its in there.    :grin: 

In case of failure or you get errors,   ](*,)  
What i told you to do in console was to copy and paste libxmms-flac.so and xlibxmms-flac.la from /usr/lib/xmms to usr/lib/bmp/Input/

---

### Post by ubuntu_demon on 2005-12-13
in breezy :
$ sudo apt-get install xmms-flac
$ sudo cp /usr/lib/xmms/Input/*flac* /usr/lib/bmp/Input/

---

