---
title: "Intsalling Flash on Opera"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Guus on 2007-02-15
how do i install Flash on Opera?

i get linked to the download page by Opera itself, but both pacakges (tar.gz and rpm) arent working for me

any suggestions?

---

### Post by croppyboy on 2007-02-15
You can either add the following to your /etc/apt/sources.lst

```
## Seveas&#8217; packages
## (GPG key: 1135D466)
deb http://mirror.ubuntulinux.nl edgy-seveas all
deb-src http://mirror.ubuntulinux.nl edgy-seveas all
```

and the in terminal type
```
sudo aptitude install flashplugin-nonfree
```

or go directly to the following website ([Seveas' Ubuntu packages]("http://seveas.imbrandon.com/")), choose your version of Ubuntu (dapper/edgy) and look through the packages for the flash plugin . . .

---

### Post by Marsolin on 2007-02-15
For me installing flashplugin-nonfree from the Ubuntu multiverse repository and then restarting Opera worked great.

---

### Post by jonathanku on 2007-02-17
Guys, I've been trying to get Flash in Opera (in Edgy) to work, but am struggling.

I'm new to Linux, but getting there. Once I figured out how to get Multiverse packages in Synaptic, I tried to install the flash-nonfree package, but always get an error:

E: flashplugin-nonfree: subprocess post-installation script returned error exit status 1

Any advice anyone?
THANKS!
JK

---

### Post by jonathanku on 2007-02-24
Well got flash working after a lot of searching.... now struggling to get embedded video like realplayer/WMV working.... trying to play videos from here: [http://news.bbc.co.uk](http://news.bbc.co.uk)

I installed Kaffeine with these instructions,

[http://ubuntuforums.org/showpost.php?p=353481](http://ubuntuforums.org/showpost.php?p=353481)
 but no joy.....:confused:

---

### Post by divi on 2007-03-12
Thanks this works just fine and straight away.

---

