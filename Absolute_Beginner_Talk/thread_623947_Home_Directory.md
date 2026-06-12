---
title: "Home Directory"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-26
So I have one distro....Ubuntu 7.10 on one disk on one computer.
I intend to keep it that way.
I have read that for future updates it is a good idea to have a Home directory made that will contain all my own data!

Is that correct and how should i do it bearing in mind the attached very simple disk setup.

Thanks


Bern

---

### Post by nick_h on 2007-11-26
How big is your disk?

---

### Post by umattu on 2007-11-26
Just make a sepearate partition to mount your home directory to.

When I installed I created 3 partitions:
1 SWAP
2 /
3 /home

This way when I upgrade, I install to the "/" partition and mount /home, this way only the OS gets formatted and my home directory is left intact with all of my data. (of course you would not format the /home partition with the new install)

---

### Post by philinux on 2007-11-26
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

follow the instructions by copying and pasting

---

### Post by bodhi.zazen on 2007-11-26
Here is a link on  how to create a new home partition :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I personally like to make a data partition, which you can link into /home. I do this because of all the config files in /home (the . dot files) usually are not needed on a fresh install and the few that are can be easily copied.

HTH :)

---

