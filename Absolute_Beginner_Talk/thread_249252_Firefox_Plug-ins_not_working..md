---
title: "Firefox Plug-ins not working."
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Sp00ne on 2006-09-02
I've had Ubuntu for some time now, and for reasons unknown, many Firefox plug-ins refuse to work for me.

For instance, if i go a website which requires a plug-in that i do not have, i click "install plugins". The box comes up but says "unkown plugin" or some other rediculous crap. And what annoys me most, is that FF works perfectly (well almost) on my mother's laptop.

So, anywho, how do i get these stupid things to work?

Any help would be appriciated.

---

### Post by Perfect Storm on 2006-09-02
Well, you can't do that in linux. If you need the eg. java plugin you have to install java through eg. synaptic if you have set up your sourcelist. The easist way is to get Automatix or easy ubuntu. Same goes to Flash player, mplayerplug-in etc.

---

### Post by Sp00ne on 2006-09-02
Well that makes sense... now.

Anywho, what would i add to/change the sourcelist to allow java to work?

---

### Post by Perfect Storm on 2006-09-02
```
sudo nano /etc/apt/sources.list
```

go to [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to make a sourcelist that fits you and exchange it with your old one.

Save and exit <ctrl> + <o>, <ctrl> + <x>
```
sudo aptitude update
```

It might complain about some keys, then use this to solve it:
```
gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -
```

Where KEY is the number for each of each souce complain (it's actual a security device that tells you it's an unofficial source(s) you have added).
then again:
```
sudo aptitude update
```

Now you can search in synaptic for the diffrent stuff your browser needs.

---

### Post by Sp00ne on 2006-09-02
On the source-o-matic, i've got no idea what my country's 2 letter code is... so yeah.

---

### Post by Perfect Storm on 2006-09-02
Which country are you from?

---

### Post by Sp00ne on 2006-09-03
Sorry for long reply, Australia.

Also, sound in firefox and epiphany works on and off.

---

