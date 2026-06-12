---
title: "Adding a repository"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Peanuter on 2008-02-24
Hi all, I am after a bit of guidance if possible.  I am trying to add the mirrored repositories provided by my ISP.  I use Internode in Australia and they have a mirror server that has the Ubuntu ditros on it.  The reason I am doing this is that they provide this for members so that we can download using this mirror and the downloads do not go against our monthly quota, as we here in Aus operate on monthly download limits and not on bandwidth used.  The mirrors are kept up to date and not only would it be what would be considered free downloads the speed would be greatly increased as well, being that the server is here in Aus.  If anyone can help me with this it would be greatly appreciated.

Cheers

Jason

---

### Post by timbounceback on 2008-02-24
Do you mean repositories, or mirrors for the ISOs?

---

### Post by tango_ninja on 2008-02-24
are you talking about mirrored repositories ? if so, just add them to your sources text file:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by Peanuter on 2008-02-24
Hi again, sorry, yes I mean repositories provided on the mirrored server.  I have tried to enter what I think is the correct format into the sources.list, but it does not work.  I am sorry if I was not clear on what I wanted, I am still finding my feet with Linux.  So yeah I would like to add the repositories provided by my ISP into the sources.list doc but I do not know the correct format for entering it in.  Thanks for your help

Cheers


Jason

---

### Post by 3rdalbum on 2008-02-24
I'm not on Ubuntu at the moment, but if you go to System > Administration > Software Sources, you should be able to change the repos to other local Australian ones. Possibly Internode is among them.

---

### Post by warbird on 2008-02-24
easy way:
 
step1: open software sources dialog (pic)


step 2: Add your repo line under 3rd party software (pic)

step 3: disable the official mirrors you have your own mirrors for, so it wont download from them

Hard way:
configure your sources manually
sudo gedit /etc/apt/sources.list

edit: if you have a link or something from your isp about this, why don't you show it, and some of us will tell you the exact line you need to add.

---

### Post by Peanuter on 2008-02-25
Hi all, and thankyou for your replies.  Here is a link to my isp and their repositories. I can not seem to get the software manager thing to work, so hopefully someone can help with editing the sources.list.   Thanks again

"http://mirror.internode.on.net/pub/ubuntu/"


Jason

---

### Post by aztektum on 2008-02-25
> **Peanuter said:**
> Hi all, and thankyou for your replies.  Here is a link to my isp and their repositories. I can not seem to get the software manager thing to work, so hopefully someone can help with editing the sources.list.   Thanks again

"http://mirror.internode.on.net/pub/ubuntu/"


Jason

```
deb [http://mirror.internode.on.net/pub/ubuntu](http://mirror.internode.on.net/pub/ubuntu) gutsy main
```

also

```
deb [http://mirror.internode.on.net/pub/ubuntu](http://mirror.internode.on.net/pub/ubuntu) gutsy-security main
deb [http://mirror.internode.on.net/pub/ubuntu](http://mirror.internode.on.net/pub/ubuntu) gutsy-updates main
```

if you want updates and security fixes

add multiverse restricted universe after main if you so choose, like so:

```
deb [http://mirror.internode.on.net/pub/ubuntu](http://mirror.internode.on.net/pub/ubuntu) gutsy main multiverse restricted universe
```

and

> deb [http://mirror.internode.on.net/pub/ubuntu](http://mirror.internode.on.net/pub/ubuntu) gutsy-security main multiverse restricted universe
deb [http://mirror.internode.on.net/pub/ubuntu](http://mirror.internode.on.net/pub/ubuntu) gutsy-updates main multiverse restricted universe

---

### Post by Peanuter on 2008-02-28
Thanks aztektum,  tried that but came up with error about resolving name and 404 errors, thinks it may be something with there server.  I off OS for 6 months so I will work on this when I get back.  Thanks all for your help and input.

Regards


Jason

---

### Post by PegMonster on 2008-06-03
O.K, so I am a bit late on this one, but hopefully it will come in handy for when you get back from o/s.
I too am with Internode and here is my /etc/apt/sources.list

```
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ hardy main restricted universe multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ hardy-updates main restricted universe multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ hardy-security main restricted universe multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ hardy-backports main restricted universe multiverse
```

and when you switch to 7.10 Intrepid Ibex just substitute hardy with intrepid.
Also, if you don't want multiverse, universe or backports just leave them out.

PM

---

### Post by Bubba64 on 2008-06-03
> **warbird said:**
> easy way:
 
step1: open software sources dialog (pic)


step 2: Add your repo line under 3rd party software (pic)

step 3: disable the official mirrors you have your own mirrors for, so it wont download from them

Hard way:
configure your sources manually
sudo gedit /etc/apt/sources.list

edit: if you have a link or something from your isp about this, why don't you show it, and some of us will tell you the exact line you need to add.

Excellent observation the 3rd party in software allows you to turn of the repository while still having it available when needed.

---

