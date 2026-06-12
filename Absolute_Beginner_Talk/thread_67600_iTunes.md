---
title: "iTunes"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by zoob on 2005-09-20
Is there a way to run itunes on ubuntu or any other linux?

Thanks,

zoob

---

### Post by xequence on 2005-09-20
Yes, crossover office supports it. Unfortunatly, it isnt free. I got it to work but it was VERY slow and wouldent play music.

If you want to just play music, Rythmbox, the default media player on ubuntu, is great.

If you want to connect to an ipod, there are many ways from linux, though I have no experience with them.

---

### Post by PsyberOneZero on 2005-09-21
You can also get SharpMusique ([http://www.nanocrew.net/sw/sharpmusique/sharpmusique_1.0-1_i386.deb)](http://www.nanocrew.net/sw/sharpmusique/sharpmusique_1.0-1_i386.deb)), it will let you download, purchase, redeem codes, and other things with iTMS, and then   use either rhythmbox or banshee (or music player of your choice).  Hopefully soon it will be integrated with one of the two.

---

### Post by davio on 2005-09-21
i'm sorry to interrupt but how to install rythmbox? apt-get what? or is there another way to install?

davio

---

### Post by PsyberOneZero on 2005-09-21
You can use Synaptic (System->Administration->Synaptic Package Manager)
Search for rhythmbox, click on the box next to the title and select Install, then click Apply.  After this is done it *should* be in the man application menu.

However it should be in there already, I believe that it is the default music player when Ubuntu is installed.

and for SharpMusique, Open up a terminal, go to the directory that you downloaded the file to and run:
#sudo dpkg -i SharpMusique*.deb
(you may have to use synaptic to get some of the dependencies, but dpkg will tell you which packages it needs)

---

### Post by davio on 2005-09-21
thanks!

---

