---
title: "Automatix2"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by chrispche on 2007-10-29
I notice on there website they have withdrawn support for Dapper. I really need this app to be up and running. Can any one help. Or should I go for the Ubuntu download version of automatix is it just as good?

Can any one point me to the website for the Ubuntu one.

---

### Post by aysiu on 2007-10-29
I don't think you really *need* the app to be up and running, but you may just like it for whatever reason.

The Dapper version is here, I think:
[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-4.2-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-4.2-6.06dapper_i386.deb)

---

### Post by chrispche on 2007-10-29
So anything you can get on Automatix you can get on synaptic? Including the codecs for mp3 and divx playback? If I can get away from using automatix please enlighten me. How do i install the codecs from synaptic?

Thanks.

---

### Post by zvacet on 2007-10-29
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

```
gksudo gedit /etc/apt/sources.list
```

add this 

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

Save and close.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo aptitude update
```

After this you will find w32codecs in synaptic.

---

### Post by jaybombalous on 2007-10-29
[http://ubuntuforums.org/showthread.php?t=583014&highlight=w32codecs](http://ubuntuforums.org/showthread.php?t=583014&highlight=w32codecs)

---

### Post by jaybombalous on 2007-10-29
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) **dapper** free non-free


make sure u put the OS version u are using here, the newest release 7.10 is gutsy and should be changed accordingly.

> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

---

### Post by Crafty Kisses on 2007-10-29
> **chrispche said:**
> I notice on there website they have withdrawn support for Dapper. I really need this app to be up and running. Can any one help. Or should I go for the Ubuntu download version of automatix is it just as good?

Can any one point me to the website for the Ubuntu one.

You don't really need Automatix.

---

