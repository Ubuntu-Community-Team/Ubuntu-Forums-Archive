---
title: "Getting Newer Version of VLC Media Player"
date: 2011-10-04
forum: Any Other OS
---

### Post by craig10x on 2011-10-04
Hi: Question...how can i get a deb file for the latest VLC media player they show on their website?  I notice they don't offer a deb and that is the only type of file i know how to install...This would be for Ubuntu 11.04 (i use linux mint 11 but as you know, it is 11.04 underneath and uses the same type of files)...
      Of course, i would want a file that is safe and reliable....any suggestions?

Thanks in advance for all feedback...:)

---

### Post by Claus7 on 2011-10-04
Hello,

hope it helps:
[http://packages.ubuntu.com/natty/vlc](http://packages.ubuntu.com/natty/vlc)
otherwise you have to use the repositories they propose.

edit: the package for oneiric might help you as well:
[http://packages.ubuntu.com/oneiric/vlc](http://packages.ubuntu.com/oneiric/vlc)

Regards!

---

### Post by uRock on 2011-10-04
You can add the PPA for VLC by following the instructions in this link [http://www.absolutelytech.com/2010/06/23/howto-install-vlc-1-1-via-ppa-on-ubuntu/](http://www.absolutelytech.com/2010/06/23/howto-install-vlc-1-1-via-ppa-on-ubuntu/)

---

### Post by ajgreeny on 2011-10-04
You can use the ubuntu ppa [https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc) for version 1.1.11.

---

### Post by zhogan85 on 2011-10-04
You can follow the steps on this [site]("http://www.linuxnov.com/vlc-1-1-11-released-install-in-ubuntu-11-04-natty-narwhal-and-ubuntu-11-10-oneiric-ocelot/"). I did this recently too.

```
sudo apt-add-repository ppa:chimerarevo/vlc/ubuntu
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc vlc-plugin-pulse
```

You have to add a ppa to your repositories though.

If you'd like to wait a week, you can upgrade to ubuntu 11.10, I think it will have the most up-to-date VLC.

---

### Post by zhogan85 on 2011-10-04
Wow, two people posted while I was typing! Now that's fast service!

---

### Post by ubupirate on 2011-10-04
> **ajgreeny said:**
> You can use the ubuntu ppa [https://launchpad.net/~n-muench/+archive/vlc]("https://launchpad.net/%7En-muench/+archive/vlc") for version 1.1.11.

> **zhogan85 said:**
> You can follow the steps on this [site]("http://www.linuxnov.com/vlc-1-1-11-released-install-in-ubuntu-11-04-natty-narwhal-and-ubuntu-11-10-oneiric-ocelot/"). I did this recently too.

```
sudo apt-add-repository ppa:chimerarevo/vlc/ubuntu
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc vlc-plugin-pulse
```You have to add a ppa to your repositories though.

If you'd like to wait a week, you can upgrade to ubuntu 11.10, I think it will have the most up-to-date VLC.

Both of these PPA will not provide updated VLC in either 10.04 or 10.10, as I've read on Google searches.

I've tried most of the PPA related to getting updated VLC from default in 10.10, and even after adding repo and updating it still reports back the same version and there are no updates.

I believe VLC 1.1.11 has to be manually compiled by you on 10.04 or 10.10, as it seems only the PPA work for 11.04 and soon 11.10.

---

### Post by craig10x on 2011-10-04
wow...all kinds of great responses...thank you so much :)
so many choices...which one to pick? (lol)

yes, i am sure then new 11.10 coming out next week will have the newest version no doubt....as will Mint 12 which will come out roughly a month or so after 11.10 is out...but in the meantime i was hoping to get the newer version of VLC going on my Mint 11 install...

the problem i encountered with the older version it has (which is same as you have in 11.04) is that the soundtrack on videos is "out of synch" with the video portion and the newer version does not have that problem...

i guess i will do one of the terminal suggestions to add it on...perhaps the last one shown here in the posts...

maybe i should try it on a live dvd session of mint 11 first before i attempt it on my hard install ;)

---

### Post by zhogan85 on 2011-10-05
> **ubupirate said:**
> Both of these PPA will not provide updated VLC in either 10.04 or 10.10, as I've read on Google searches.
 
While that may be, the op said he/she is using 11.04, and the method I posted absolutely works for 11.04. But I've no experience with updating from the older versions, so compiling may be the only answer.

---

### Post by ubupirate on 2011-10-05
> **zhogan85 said:**
> the op said he/she is using 11.04.

Oh right, I see now. Apologies, been having trouble seeing text on my screen lately. :(

But nonetheless, from what I've seen VLC 1.1.11 will only be available in 11.10 for the time. Can't update it on 10.04, 10.10 or seemingly 11.04...

Best just to compile 1.1.11 yourself or wait until 11.10 is released.

---

### Post by zhogan85 on 2011-10-05
> **ubupirate said:**
> But nonetheless, from what I've seen VLC 1.1.11 will only be available in 11.10 for the time. Can't update it on 10.04, 10.10 or seemingly 11.04...

Not true for 11.04, the method I posted works very simply in 11.04 and is way easier than compiling.

---

### Post by ubupirate on 2011-10-05
> **zhogan85 said:**
> Not true for 11.04, the method I posted works very simply in 11.04.

Eh? I just tried it on my 11.04 partition and didn't seem to work for me and was still stuck on older version of VLC. Maybe I failed at doing something, let me go try again.

EDIT: Ok so it does work, seems my apt-get update didn't want to work right but pressing reload in synaptic seemed to work.

---

### Post by zhogan85 on 2011-10-05
Glad to hear!!

---

### Post by craig10x on 2011-10-05
> **zhogan85 said:**
> While that may be, the op said he/she is using 11.04, and the method I posted absolutely works for 11.04. But I've no experience with updating from the older versions, so compiling may be the only answer.

Right...i'm using Linux Mint 11 which is ubuntu 11.04....i just tried it on a live dvd session of mint 11 and it worked great...so i will do it on my actual install now...thanks so much...

Let me ask though:  do i need to leave that added repository it adds to my software source list in the mint update manager once i have the vlc installed?  Any advantage to keeping it on there?

Also, i primarily use Chrome rather then Firefox, so do i need to to all 3 lines in the terminal or could i leave the mozilla plug in line off when i put it in the terminal?

Or is best to put in all 3 lines to avoid any problems?

And i am a "he" by the way (lol)...

---

### Post by zhogan85 on 2011-10-05
> **craig10x said:**
> do i need to leave that added repository it adds to my software source list in the mint update manager once i have the vlc installed?  Any advantage to keeping it on there?

I'm not positive, but I think you need to keep repositories that you are using software from. Maybe someone will come with a firm answer.

> **craig10x said:**
> Also, i primarily use Chrome rather then Firefox, so do i need to to all 3 lines in the terminal or could i leave the mozilla plug in line off when i put it in the terminal?

I think here, if you use chrome, ignoring the mozilla line would be fine, but if you use firefox at all, you may as well include it, I'm sure it's a fairly small package.

> **craig10x said:**
> And i am a "he" by the way (lol)...

Good day sir!

---

### Post by craig10x on 2011-10-05
thanks zhogan85...i guess i will add the firefox line too...even though i mostly use Chrome, as you said can't hurt to have it and it is a small file ;)

i guess i can just leave that repo in there then...unless someone advises different..you may be right about needing to have it in there, like you i am not sure about that myself...unless someone here can enlighten us ;)

looks like a nice easy way to get that newer version on here....mostly i am changing because of the sound synch problem i had on the older version which i know is definitely corrected in this newer version...

---

### Post by craig10x on 2011-10-05
Oh...just one more question...in my update manager it shows that "repo" twice...do you have it listed once or twice in yours?  (was wondering if it needs to be listed twice like that)....

---

### Post by zhogan85 on 2011-10-05
I don't know, I just did a reinstall last weekend, and hadn't added the ppa again, mainly just since I haven't gotten around to it. But I don't think having it in there twice really hurts anything.

---

### Post by craig10x on 2011-10-06
Ok thanks...no problem...guess i will just leave it then...in fact, i just noticed that a ppa i had added for getting updates for pidgin messenger is also in their twice, too...

---

### Post by zhogan85 on 2011-10-06
Hmm, that's odd. Maybe some minor bug that'll be fixed in 11.10?

---

### Post by ajgreeny on 2011-10-06
It is possibly listed twice with one for the binaries and the second for the source files.  If that is so, you can delete the source listing, or comment it out if you prefer.

---

