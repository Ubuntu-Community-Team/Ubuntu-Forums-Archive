---
title: "how do i install gtkpod?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by kayas80 on 2006-02-25
Can someone explain how to install gtkopd. I don't want to install from synaptic - long story. I have gtkpod.tar.gz, what do I do next?

Cheers

---

### Post by Jucato on 2006-02-25
Short answer:
1. Untar the package in a directory
2. Go into that directory
3. In a terminal type these commands:
```
./configure
make
sudo make install
```
Of course you have to wait until each process is finished.

have you tried installing through apt-get rather than synaptic?

---

### Post by geekphreak on 2006-02-26
sudo apt-get update
sudo apt-get install gtkpod

---

### Post by xhie on 2006-02-26
[QUOTE=kayas80]Can someone explain how to install gtkopd. I don't want to install from synaptic - long story. I have gtkpod.tar.gz, what do I do next?

Cheers[/QUOTE]

Whats wrong with synapic? Just wondering.

---

### Post by kayas80 on 2006-02-26
[quote=xhie]Whats wrong with synapic? Just wondering.[/quote] 
I'm installing it on my cousins computer - I converted her from Windows to Ubuntu - and she doesn't have an internet connection. So I'm copying the file from my computer to hers and installing it offline.

Thanks to everyone for their help. :cool:

---

