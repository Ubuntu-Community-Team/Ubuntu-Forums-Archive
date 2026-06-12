---
title: "[SOLVED] help, My Synaptic Package Manager broke"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Schinoble on 2007-10-10
each time i load it i get this error message 

please help, how can i fix it

E: The package bittorrent-4.0.1.linux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

than just closes, I tried to re-download the package and run it again, but it gave me an error message about the file being currupt or i do not have permission to use it

---

### Post by juantovarm on 2007-10-10
this should remove synaptic plus all the configuration files:

sudo apt-get remove --purge synaptic

then reinstall synaptic:

sudo apt-get install synaptic


hope it helps

---

### Post by Schinoble on 2007-10-10
tried the sudo apt-get remove --purge synaptic

it gives me this 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package bittorrent-4.0.1.linux needs to be reinstalled, but I can't find an archive for it.

any ideas how i can get rid of bittorrent-4.0.1 its not even installed, downloading it again doesnt seem to work, even put it in my home folder before trying to run it still gives me a corrupt or dont have permission error

---

### Post by Schinoble on 2007-10-10
anyone ?

---

### Post by Anicka on 2007-10-10
OK, the package you're talking about should be installed (it is an indirect dependency of ubuntu-desktop). There are two possibilities: either gnome-btdownload (this package is depending on bittorrent) iis broken or the repo is temporarily down (or was when you installed, which puts us back in scenario 1). In your shoes I would try to run the following commands: ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get reinstall bittorrent
sudo apt-get install bittorent
```

If you still get get errors after this, it is time for the heavy guns: ```
sudo apt-get -f install bittorrent
```
I hope this solves it, or someone with more experience than me has to help.

---

### Post by phr0ze on 2007-10-10
Did you just install ubuntu? Your CD could have been corrupt.

---

### Post by Schinoble on 2007-10-10
the apt-get reinstall bittorrent gives me an error invalid opperation error, the apt-get install options all give me this error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package bittorrent-4.0.1.linux needs to be reinstalled, but I can't find an archive for it.

not a new instalation, have used this CD on a laptop too works fine,

---

### Post by Anicka on 2007-10-10
Sorry for that one, I don't use apt-get very often and made a mistake. It should be: ```
sudo apt-get install --reinstall bittorrent
```, but since all install commands fail (even with -f ?), I don't know if it would work. Give it a try and post the out-come.

---

### Post by zvacet on 2007-10-10
```
sudo apt-get remove --purge bittorrent-4.0.1.linux
```

If that doesn´t help 

```
locate bittorrent-4.0.1.linux
```

and you will see where that package is.Remove it manualy by go to the every folder with that package and 

```
sudo rm -r packagename
```

---

### Post by Schinoble on 2007-10-10
thanks for all the replies everyone, the apt-get stuff didnt seem to work it got to a stage where it kept saying i had a broken installation

eventually through a lot searching i came accross dpkg and did this which fixed it 

sudo dpkg -r --force-all bittorrent-4.0.1.linux

thanks again all for replying

---

