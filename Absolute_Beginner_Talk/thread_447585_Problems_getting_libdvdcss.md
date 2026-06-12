---
title: "Problems getting libdvdcss"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by jbor7755 on 2007-05-18
HI again,

I have been trying to get the libdvdcss file so I can play dvds for some time now. I tried by typing

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

after having installed xine etc but there is a problem with my connection to the outside world.

I keep geting the error

failed: no route to host

I get the same error when I try to access the medibuntu repositiory.

Any ideas?

Cheers

---

### Post by AlexenderReez on 2007-05-18
> **jbor7755 said:**
> HI again,

I have been trying to get the libdvdcss file so I can play dvds for some time now. I tried by typing

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

after having installed xine etc but there is a problem with my connection to the outside world.

I keep geting the error

failed: no route to host

I get the same error when I try to access the medibuntu repositiory.

Any ideas?

Cheers

i suggest to use repositories to install those stuffs....(you can even find more than that)

> deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main



cd keys

> sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

> sudo  wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

> gpg --import automatix2.key

> gpg --export --armor E23C5FC3 | sudo apt-key add -


---

### Post by jbor7755 on 2007-05-20
This is not what I am talking about.

I do not have a problem using or entering the commands

My computer won't connect with the host. Doesn't matter whether I try medibuntu or any other remote repository, it will not connect with it.

---

