---
title: "Azureus update fail."
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by dag0 on 2007-01-13
how to make this writeable ? 
 ( "/opt/azureus' isn't writable, this update will probaly fail. Check permissions and retry the update.")

Dag

---

### Post by jordanmthomas on 2007-01-13
open a terminal
type this:
```
cd /opt
sudo chown *yourusername*:users azureus

```
See if that helps

**edit** what this will do is give the azureus directory to you instead of to root so you will be able to write to it.

---

### Post by dag0 on 2007-01-13
Thanks alot...It works :-)


Take Care


Dag

---

### Post by croc1 on 2007-01-15
:-D  thanks worked for me too

---

### Post by BioGene on 2007-01-20
Hey guys I tried this but it did not update to 2.5.0.2 for me. It gives me an error that reads:

> Instalation of at least one component failed - see 'update.log' for details

I have no clue why it does thsi and bigest issue I have is that I can't seem to find update.log not even in /opt/azureus! Anyone know where I can find it?

---

### Post by JamieC on 2007-01-20
> **BioGene said:**
> Hey guys I tried this but it did not update to 2.5.0.2 for me. It gives me an error that reads:



I have no clue why it does thsi and bigest issue I have is that I can't seem to find update.log not even in /opt/azureus! Anyone know where I can find it?

I don't use Azureus but you could try and search for it, open a new terminal and type the following commands:
```

sudo updatedb
locate update.log

```

---

### Post by shareMenaPeace on 2007-01-20
Open a terminal and type > locate update.log 
Than check if 1 of those has todo with azureus and open it to find what is missing.

Like here it is:
/home/user/.azureus/update.log

> gedit /home/user/.azureus/update.log


---

### Post by BioGene on 2007-01-20
k I tried using it but none of them give me an azureus folder, just some other files called updatedb.conf or some other like updatedb1.gz.tar!

EDIT:
Just tried to find it using the GUI search tool that came with ubuntu and it could not find anything in file system! This is pretty weird!

---

### Post by daverave999 on 2007-01-20
Thanks jordanmthomas, worked for me too!

---

### Post by OsakaWilson on 2007-01-23
I tried jordanmthomas's suggestion, but I got the following:

chown: cannot access `azureus': No such file or directory

---

### Post by OsakaWilson on 2007-01-23
I did this:

sudo chown -R username:username /opt/azureus

and it worked for me. Of course, replace username with your username.

---

### Post by Darko Beta on 2007-01-23
Alternately, what i did was "sudo nautilus" and went to the opt/azureus folder and right clicked empty space then properties.  I gave "read & write" access to all sections, and then ran the azureus update.  After that, i ran sudo nautilus again and changed everything back to how it was, so only root could write.  I'll have to do this each time there's an update, but I prefer to keep the security buttoned down--especially with a p2p prog.

---

### Post by tommcd on 2007-01-23
> **jordanmthomas said:**
> open a terminal
type this:
```
cd /opt
sudo chown *yourusername*:users azureus

```
See if that helps

**edit** what this will do is give the azureus directory to you instead of to root so you will be able to write to it.

Thanks, I had the same problem. I figured it was probably a permissions issue. I installed azureus using the "alternative method" listed here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)
I have now updated my azueus!

---

### Post by beefcurry on 2007-01-25
I did a fresh install of ubuntu 6.10, installed 2.5.0.0 Azureus and updated to 2.5.0.2 with no problems using this. Thanks.

---

