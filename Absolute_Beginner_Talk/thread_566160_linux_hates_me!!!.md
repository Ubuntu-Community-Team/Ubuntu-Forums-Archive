---
title: "linux hates me!!!"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2007-10-03
i have been tryin for over 3 years to install linux and i still cant get it to happen...it either eats up my disk (and everybody says NO WAY YOU CAN USE PARTITION MAGIC) or refuses to recognize my video card ( 12 month old ati radeon x300, or it doesnt allow me to install a network .  i have tried it with the distros installer(g-parted, i persume). so far this wonderful linux partitioner has eaten my disk up on 9 occasions in the past 6 weeks. what i want to do next is: take drive c: 160gb and steal approx 20-30gb(unnamed) from windows, then make a swap parition (inside the 30gb i just stole) and a /home partition and that is all...documentation says ya gotta have somewhere btwn 2 and 9 depending on who ya ask, me i want it to be extremely simple. how can i get this d*** thing installed and actually keep my windows stuff(cause i just dont trust linux or i'd give it the whole 160gb, but not until it behaves a lot better. mahalo and aloha

---

### Post by funpop on 2007-10-03
1. have a backup of you important data
2. if you have no free partitions or unallocated disk-space then let the installer resize your windows partition. it _should_ work like a charm..make sure your windows is defragmented before

if this screws up dont give windows the hole disk on your next install.

edit:

there are lots of great straighforward guides of installing and dual booting ubuntu

for example: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by staticvoid on 2007-10-03
download the ubuntu "alternate" cd. it is a text based installer, you can set up partitions manually. You just need to know what you are doing, which it seems you do. Just use your arrow key :). First install windows, then install ubuntu. Windows does not give you much choice for partitioning though...

Do you have "Samba" installed? you need that or "putty" to get a good netwaork set up :). 
for your ATI graphics card try "envy", it installs drivers for graphics cards.

So yeah... What exactly did you use to install linux? an ubuntu 7.04 live cd? like I said, try the alternate cd.

it appears that you hate linux ;) lilnux does not hate you :P. And this is not the place to be ranting about your bad expiriences with Linux, hehehe. You'd get a lot more friendly anwsers to this post if ya would titled it "Help with dual boot setup and getting ATI and networking to work" heheh... just a suggestion.

linux does not love me, i love linux,
StatiC VOID

---

### Post by por100pre1 on 2007-10-03
You can use Partition Magic. Just create an ext3 partition for Ubuntu and create a small logical partition for swap (the linux pagefile). In fact you can use any tutorial for installing Ubuntu, just ignore gparted and use Partition Magic instead.

---

