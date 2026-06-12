---
title: "Student looking for an equivalent of LogicWorks for Linux"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by DianWei on 2006-01-28
As the topic implies, I am just looking for something equal to or greater than Logicworks. My class has provided windows software, but I would be so happy if someone could point me in the direction of the best linux substitute. I browsed possible programs in Synaptic, but I don't like trying out programs without a reccomendation.

   For those who do not know what Logic Works is, it is a program that allows one to simulate a circuit made on a breadboard, so that one can design, and fiddle around with a circuit on the computer to see if it works correctly, before accidently killing oneself in a lab.

   I thank anyone in advance, and also apologize in advance if thier has already been a similar topic. (I tried the search to no avail)

---

### Post by psomas on 2006-01-28
if you have wine installed,you can run it...of course you should first mount your windows partition...then select the exe file of logic works,right click>open with wine... 
it worked for me... 
(wine is a program for running windows execs in Linux)

---

### Post by DianWei on 2006-01-28
Ah, thanks so much. I never even attempted it, because in past experience wine didn't work too well with very many programs, but I suppose I could give it a shot. Thanks so much. I would still be interested in some Linux native (and free, as in price) alternatives if anyone has them.

---

### Post by mips on 2006-01-28
Another option would be VMPlayer where you establish a virtual machine from linux. This way you dont even need a windows partition.

[https://wiki.ubuntu.com/VMwarePlayerAndQemu](https://wiki.ubuntu.com/VMwarePlayerAndQemu)

---

### Post by psomas on 2006-01-28
[QUOTE=DianWei]Ah, thanks so much. I never even attempted it, because in past experience wine didn't work too well with very many programs, but I suppose I could give it a shot. Thanks so much. I would still be interested in some Linux native (and free, as in price) alternatives if anyone has them.[/QUOTE]
i think i found something...
it's a program calld Qucs...you might find it in synaptic...
if not then you need to add some repositories...
here's my source.list file,so check which repositories you don't have and copy them to your source.list(make a backup first):

> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


---

