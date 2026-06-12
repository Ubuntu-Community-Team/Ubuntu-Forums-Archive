---
title: "Amarok 1.4 in Ubuntu?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-06-03
How do I install Amarok 1.4 in Ubuntu? I Installed 1.3 from the Ubuntu repositories but as I pretty much exclusively listen to *classical* music, I really want to have composer tags.

Thanks!

---

### Post by barbarian on 2006-06-03
hi, check it out:

[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

---

### Post by arendm on 2006-06-03
You can find a howto on this page...
[http://lunapark6.com/?p=1235]("http://lunapark6.com/?p=1235")

---

### Post by bluevoodoo1 on 2006-06-03
Anything for classical music. I'm with you there.

You could add these repositories to get amaroK 1.4 (I'm running ubuntu too and it has worked fine)
```

deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/amarok-latest dapper main
```

[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto) and/or [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) can aid in help (only if you need it)

---

### Post by Belathor on 2006-06-03
[QUOTE=bluevoodoo1]Anything for classical music. I'm with you there.

You could add these repositories to get amaroK 1.4 (I'm running ubuntu too and it has worked fine)
```

deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/amarok-latest dapper main
```

[https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto) and/or [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) can aid in help (only if you need it)[/QUOTE]

Grrr, I got an error:

> W: GPG error: [http://kubuntu.org](http://kubuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

I ignored it, installed Amorak 1.40a and then launched it. Unfortunately, help -> about Amorak still says the version is 1.3.9 and it looks the same too. :( 

I'm also concerned about the version number. Is it 1.4 alpha?

Thanks bluevoodoo1!


P.S. Thanks barbarian and arendm for the links, too!

---

### Post by dralaroc on 2006-06-03
Speaking of Amarok 1.4, I just dl'ed it. I opened it up to see if everything installed ok then closed it and got this message any ideas.

---

### Post by bluevoodoo1 on 2006-06-03
The GPG key should be DD4D5088. (which is from [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)) 

you could also try the link that was mentioned above too, [http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php) . I used that to get 1.4 when it was beta. 

I checked my amaroK version and it was 1.4...
```

bluevoodoo1@ubuntu:~$ amarok --version
amaroK: 1.4.0
```

---

