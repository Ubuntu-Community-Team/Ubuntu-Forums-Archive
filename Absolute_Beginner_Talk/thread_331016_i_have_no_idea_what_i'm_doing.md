---
title: "i have no idea what i'm doing"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by cesara on 2007-01-04
i have no idea what i'm doing when it comes to installing.. i don't know where to start.. i'm extremely bored and decided to download stepmania and i just don't know what to do. i have the .gz thing and extracted it. i have a huge problem with this.. i can't even update my flash player or whatever.. my friend has been doing everything for me lately but he hasn't been around so i can't ask him for help.. somebody please help me out. i like ubuntu but installing stuff seems like wayy too much work

---

### Post by bodhi.zazen on 2007-01-04
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by taurus on 2007-01-04
Look at Section 4...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by taurus on 2007-01-04
> **bodhi.zazen said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Maybe it's me but I think the link is dead for now!!!

---

### Post by bodhi.zazen on 2007-01-04
> **taurus said:**
> Maybe it's me but I think the link is dead for now!!!

I hate it when that happens ! Such a good link too .... 

I'll PM the site's author and see if I can find out what's up :p

---

### Post by cesara on 2007-01-04
thanks a lot for the help but i still don't know what i'm doing.. my terminal is acting up it doesn't ever find anything or allow me to do anything i have no idea i'm probably doing something wrong

---

### Post by taurus on 2007-01-04
> **bodhi.zazen said:**
> I hate it when that happens ! Such a good link too .... 

I'll PM the site's author and see if I can find out what's up :p

That's why I included asyiu's site...  ;)

---

### Post by cesara on 2007-01-04
sudo aptitude update
sudo aptitude install build-essential

placed that in the terminal and..

E: Type 'http://users.musicbrainz.org/~luks/ubuntu' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.
cesar@ubuntu:~$ sudo aptitude install build-essential

came up what the hell is thiss

---

### Post by BarfBag on 2007-01-04
Installing things in Linux may seem a little confusing at first, but believe me - it's much more efficient then installing things in Windows.

Synaptic Package Manager is one way to install things easily.  It works by contacting servers called repositories (you can edit the list and add your own) and downloading the package you want.  If it has dependencies (other packages or files that the package requires to run), it also downloads those.  All you have to do is sit back and watch.  You can find it in System -> Administration -> Synaptic Package Manager.

Apt-get and Aptitude are basically the same thing as Synaptic, except text based.

Maybe someone else could explain how to install a tar.gz.  I'm not very good at it.

---

### Post by taurus on 2007-01-04
Apparently, you added that line, [http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu), in /etc/apt/sources.list wrong!  That's why the error message is about.  Therefore, open a terminal and paste the output of this command here then.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
Or edit /etc/apt/sources.list and remove that line before you run those commands again.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by bodhi.zazen on 2007-01-04
> **taurus said:**
> That's why I included asyiu's site...  ;)

;)

---

### Post by BarfBag on 2007-01-04
> **cesara said:**
> sudo aptitude update
sudo aptitude install build-essential

placed that in the terminal and..

E: Type 'http://users.musicbrainz.org/~luks/ubuntu' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.
cesar@ubuntu:~$ sudo aptitude install build-essential

came up what the hell is thiss

Either one of your repositories is failing, you mis-typed it, or you forgot to put deb in front of the url.

---

### Post by cesara on 2007-01-04
what??

---

### Post by taurus on 2007-01-04
> **cesara said:**
> what??

:confused:

---

### Post by cesara on 2007-01-04
[http://prdownloads.sourceforge.net/stepmania/StepMania-3.9-src.tar.gz](http://prdownloads.sourceforge.net/stepmania/StepMania-3.9-src.tar.gz) 

how do i install this

---

### Post by taurus on 2007-01-04
Before you can build StepMania or whatever, you first need to install build-essential package and to install the build-essential package, you must fix the problem with your /etc/apt/sources.list...

Please look at my post #10 on how to fix it.

---

### Post by Hendrixski on 2007-01-04
Oh dude, that program dance dance revolution all of ten years after the trend died.

When you unzip it you won't that give you the sourcecode?  I mean, you can compile it,  That's the nerdy way to do things.  I think somewhere on SourceForge you will find complete binaries, or an actual install script.  it will look like  longname.tar.gz without a .src. in there.  When you extract that just type in ./longname into the terminal and it will run, and TADA.

If you want the easy way, just go to System->administration->package manager-> synaptic, and search for it in there, because it does all of the steps for you.  Then you the user don't have to worry about all the stuff we nerdy types like to do in the terminal.  If it's not in Synaptic then keep reading this thread.

:)

---

### Post by lexrexus on 2007-01-17
> **taurus said:**
> Apparently, you added that line, [http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu), in /etc/apt/sources.list wrong!  That's why the error message is about.  Therefore, open a terminal and paste the output of this command here then.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
Or edit /etc/apt/sources.list and remove that line before you run those commands again.

```
gksudo gedit /etc/apt/sources.list
```

Sorry, boss, you lost me.  Uby Newbie who is waiting for a modem via snail-mail that will hopefully work w/lnx;  but has been trying to get my partitioning nailed w/gparted downloaded w/windowscrap, but can't find on many posts addressing this issue (so far) how to get it in usable form in my Ubuntu Dapper thingy.

---

