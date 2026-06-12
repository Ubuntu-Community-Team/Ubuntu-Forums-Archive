---
title: "Powerbook G4 - two issues: Mac-on-Linux and Opera"
date: 2006-10-07
forum: Apple PPC Users
---

### Post by eubielicious on 2006-10-07
Hi all,

I've got Dapper Drake running beautifully on my Powerbook G4 dualbooting with OS X 10.4 (Tiger) and have two queries re. Mac-on-Linux and Opera:

Mac-on-Linux works well except for one small problem - the screen colours do not work well. If I run MOL in a window I can only have 256 colours, if I have it full screen then it looks awful no matter what I do - it seems to reject even 256 colours and appears to be running in 16 colours only.

Also has anyone managed to get Opera loaded on a Mac on Linux? I cannot get it to load the conventional way using the Ubuntu Software Install utility as when I select Opera to install, the program then tries to add a repository which seems to fail, putting me into a loop. I also tried downloading a Debian package from the Opera web site and installing it - it installs but then fails to run giving error messages. I'd just like to hear if anyone else has it running and how they installed it!

I have been using Opera as my primary web browser and e-mail program for some time under OS X and would like to have that on Ubuntu - I would much rather use that than the Firefox/Thunderbird pairing.

Thanks all...

Euan

---

### Post by eubielicious on 2006-10-08
I should have said in the above message - I have run through molvconfig and tried to get all the working modes, but very few come up as working. It may be a case of manually editing the video config file but beyond changing the screen resolution and maximum colour depth, I'm out of ideas.

Again, I'd like to hear from anyone who's got this all working well on a Powerbook G4 (it's the original 12" 768MHz version) and perhaps have a look at their settings...

Thanks again,

Euan

---

### Post by pauljwells on 2006-10-08
The problem with MOL is the screen driver for the nvidia graphics card - there is only the open source nv driver, which simply can't give you better than 16 colours for MOL. I find fullscreen to be 'useable' (just) but windowed is terrible.

As for Opera, I had no problem at all using the .deb from the opera site - look for opera_9.02-20060919.3-shared-qt_en_powerpc.deb - I think it was Debian Sid in the pulldown

---

### Post by eubielicious on 2006-10-10
Re. MOL - I suppose that's why I have dualboot! It works, so I guess I can't complain too much...

I tried loading the opera .deb file using dpkg -i and when I run Opera from the command line, this is what I get:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.02-20060919.3/opera: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Any ideas?

Thanks,

Euan

---

### Post by salguod on 2006-10-10
You can install opera with apt-get (adept/synaptic). I think Opera has its own source list though, so you will have to edit the /etc/apt/sources.list file

Check out this source list generator:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

now my question: how/where did you get MOL working? 
salguod

---

### Post by eubielicious on 2006-10-11
I will have a look at the source-o-matic, although I'm thinking of trying Edgy Eft so might wait and see on the Opera front.

On the subject of Mac-on-Linux, I followed the instructions, which were, as far as I remember:

1 - install mol and associated packages, also mol-osx
2 - run molvconfig
3 - in a terminal run 'startmol --osx'

It seemed to work, albeit with the problems mentioned above...

Euan

---

### Post by eubielicious on 2006-10-15
Good news on the Opera front. I got this version:

[ftp://ftp.opera.com/pub/opera/linux/902/final/en/ppc/static/opera-static_9.02-20060919.1-qt_en_powerpc.deb](ftp://ftp.opera.com/pub/opera/linux/902/final/en/ppc/static/opera-static_9.02-20060919.1-qt_en_powerpc.deb)

And it worked just fine when I installed it. I am using it now to type this message in fact!

Euan

---

### Post by eubielicious on 2006-10-15
I should say, I've upgraded the system to the beta version of Edgy Eft. I don't think that should have any bearing on the matter though.

Euan

---

### Post by morphet on 2007-01-05
Thanks Euan! :D  I couldn't log into the forums using Firefox, so I decided to give Opera a try.  I'ts, IMO, better than Firefox.

---

