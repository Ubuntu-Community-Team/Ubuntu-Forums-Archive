---
title: "Problem with apt-get"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Mazehero55 on 2007-06-17
Whenever I try to do anything with debs at all it comes up with an error:

> The package alien-arena-data needs to be reinstalled, but I can't find an archive for it.


Then it quits, I don't know how to fix it.

Whether it's apt-get, synaptic, or the updater it does this. I even tried removing it but it doesn't work.

someone please help me

---

### Post by forestpixie on 2007-06-17
I had a similar problem a while back had to do 

```
sudo apt-get --purge remove file_name
```

and if that works - you can then reinstall

---

### Post by Mazehero55 on 2007-06-17
It didn't work, her's the output:

> rave@forever:~/Desktop$ sudo apt-get --purge remove alien-arena-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package alien-arena-data needs to be reinstalled, but I can't find an archive for it.


trying to install any deb doesn't work now.

any ideas?

---

### Post by RomeReactor on 2007-06-17
Hi. You might want to try:
```
sudo apt-get --purge remove alien-arena
```
If you installed from [GetDeb]("http://www.getdeb.net/").

---

### Post by Mazehero55 on 2007-06-17
same thing
> 
rave@forever:~$ sudo apt-get --purge remove alien-arena
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package alien-arena-data needs to be reinstalled, but I can't find an archive for it.



Is there something wrong with GetDeb? I've been having problems with their builds.

---

### Post by meborc on 2007-06-17
usually when you download a deb from getdeb.net and you encounter problems you can fix them by doing ```
sudo apt-get -f install
```this will force the installation of dependencies... it seems that the alien-arena-data is missing... 

be sure to download alien-arena.deb AND alien-arena-data.deb 

then install them ```
sudo dpkg -i alien*
```(in the folder where you have the debs)

if it now fails try the -f install command again

---

### Post by Mazehero55 on 2007-06-17
same thing. it won't do it.

> rave@forever:~$ sudo dpkg -i install alien-arena-data_6.05-1~getdeb1_all.deb alien-arena_6.05-1~getdeb1_i386.deb
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package alien-arena-data needs to be reinstalled, but I can't find an archive for it.


---

### Post by Mazehero55 on 2007-06-17
Anybody? Anything? 


........


I really want to install something  and it sucks.

---

### Post by Mazehero55 on 2007-06-17
Has this ever happened before? 
There has to be someone who knows what to do.

Please anybody I'm desperate here, I've tried everything and it keeps coming out with the same thing over and over. Like it's stuck in some kind of loop. It just keeps asking for me to reinstall alien-arena-dev but when I try it won't do it and then it tells me to reinstall alien-arena-dev again! 

It says it can't find an archive for it, can I put the archive somewhere so it can find it?

---

### Post by Mazehero55 on 2007-06-19
I have an idea. 

Does ubuntu have a config file thats has all installed packeges on it?

Cause I checked and no files were installed of alien arena, so all I have to do is remove it from that file.

---

### Post by forestpixie on 2007-06-19
Hi I was given this command once by Bapoumba when my apt-get was stuck in a never ending cycle

dpkg --remove --force-remove-reinstreq <package name>

not sure what the commands do 

man dpkg would tell you.

Not sure if this will help I'm just regurgitating from my own errors! This was the thread

[http://ubuntuforums.org/showthread.php?t=445014](http://ubuntuforums.org/showthread.php?t=445014)

Good luck 
:)

---

### Post by Mazehero55 on 2007-06-19
it's fixed, thanks forestpixie

---

### Post by forestpixie on 2007-06-19
If I helped that's cool. 

:D

---

### Post by TFrog on 2007-07-02
I'm curious as to where you got the alien-arena deb files at in the first place.  I've been hunting them down for days and only found a link to how to create them.  However, that link information doesn't work in Fiesty.  Any help would be appreciated.

---

### Post by Seisen on 2007-07-02
[http://www.getdeb.net/app.php?name=Alien+Arena+2007]("http://www.getdeb.net/app.php?name=Alien+Arena+2007")

---

### Post by TFrog on 2007-07-03
> **Seisen said:**
> [http://www.getdeb.net/app.php?name=Alien+Arena+2007]("http://www.getdeb.net/app.php?name=Alien+Arena+2007")

Seisen,

Thanks so much for the link.  I've been looking for a native format for my Kubuntu install so I could play this FPS game since I now have a joystick to toy with it.  Games are only a sideline to my computing but a welcome diversion.  Hopefully, I won't have any issue with this.

---

