---
title: "set up shared /home, how to?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-12-22
Does anyone know what is the best way to set up a shared /home partition between gutsy  and feisty so that anything written/saved on one will go to the shared /home partition. Will this cause conflicts or work OK?There seems to be very little info. about this.
Also is there a need to have different username and password on the seperate installs? I asssume the password should be different but aren't sure about this (have read conflicting viewpoints). Is there anyhting else that needs to be changed edited such as grub or fstab or anything else?
Instructions would be appreciated.

---

### Post by bodhi.zazen on 2007-12-22
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I personally do not like this in the event your config (. files) conflict, but some peole do this.

I suggest a data partition, /media/data or what not.

You can link to home

---

### Post by jken146 on 2007-12-22
The hidden config files for many applications would confilct with one another if you used the same /home directory and the same user name for multiple distros.

As for how to use the same partition as /home in both distros, just use the installer to specify that this partition is /home.

---

### Post by bumanie on 2007-12-22
Thanks for the answers guys. I have actually set tried to set this up, but am not sure whether I have done it correctly. Have not had conflicts as yet. Was not sure whether there was an accepted method for doing this. Thanks for the psychocats link, I will read it when I get home from work. I had looked, but had not found a 'how to' as such.
Thanks for your help.

---

