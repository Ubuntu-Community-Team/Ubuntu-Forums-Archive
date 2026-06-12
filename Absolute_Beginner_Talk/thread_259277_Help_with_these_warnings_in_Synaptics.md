---
title: "Help with these warnings in Synaptics"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by javierfh on 2006-09-17
Hello,

few days ago..maybe weeks i got these warnings in synaptics when tries to update the source list.

W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8AXXXX
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8AXXXX

(I masked the 4 last numbers, dont even know what are these keys)

So any idea what is going on here?
Does anyone know how can i fix that? and if that it is affecting m for something when updating my system?


Thanks in advance,

Javier

---

### Post by bikeboy on 2006-09-17
I can't help much but I can tell you the error keys are for verifying that the packages are genuine and have not been tampered with.

---

### Post by missmoondog on 2006-09-17
i get 3 errors like that all the time and i use the recommended repositorys from ubuntu_demon's list.

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by Ultra-Loser on 2006-09-17
That happens if you don't use "official" ubuntu repositories (those two sites are third-party). If you want to get rid of the errors, you have to disable the repositories (but then you won't be able to install software or update from them - just the original ubuntu repositories). 

You can disable the repositories by opening /etc/apt/sources.list (as root) and adding a # to the front of the lines the lines that look somewhat like this:

deb [http://xgl.compiz.info](http://xgl.compiz.info) dapper
deb [http://www.beerorkid.com](http://www.beerorkid.com) dapper

---

### Post by Dinerty on 2006-09-17
> **javierfh said:**
> Hello,

few days ago..maybe weeks i got these warnings in synaptics when tries to update the source list.

W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8AXXXX
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8AXXXX

(I masked the 4 last numbers, dont even know what are these keys)

So any idea what is going on here?
Does anyone know how can i fix that? and if that it is affecting m for something when updating my system?


Thanks in advance,

Javier

fire up the terminal batman !

```
gpg --keyserver subkeys.pgp.net --recv 31A5F97FED8AXXXX
```

then

```
gpg --export --armor 31A5F97FED8AXXXX | sudo apt-key add -
```


P.S

Obviously put the whole key in and not the XXXX

---

### Post by Klaidas on 2006-09-17
You ned to import keys - > wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -

---

### Post by javierfh on 2006-09-17
I did what dinerty suggested and guess what? :D 
It worked!!! i got rid of these annoying warnings.

Thanks a lot,

Javi

---

