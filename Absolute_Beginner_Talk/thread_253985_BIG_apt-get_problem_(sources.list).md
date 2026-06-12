---
title: "BIG apt-get problem (sources.list)"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-09-09
Hello all,
I had modified my sources.list file so that i fetch packages from a nearby mirror rather than the ubuntu-archives.. I think everything went OK..because i downloaded the k7 kernel after this.. 
But now, i cant run apt-get install now...it says this: (example)

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package timidity
----------------------------------------
i ran apt-get update and i get these error messages:

 sudo apt-get update
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/universe Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/multiverse Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
.
.
a long list of similar errors
.
.
Failed to fetch [http://ubuntu.csie.ntu.edu.tw/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://ubuntu.csie.ntu.edu.tw/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
.
.
.
.
E: Some index files failed to download, they have been ignored, or old ones used instead.
-------------------------------------------------------------------------
So, what do i do now to get out of this mess?? I would appreciate any help.

---

### Post by Dinerty on 2006-09-09
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Allows you to go back to the default settings :)

---

### Post by Dinerty on 2006-09-09
Sorry for double post, mod please delete this one :)

---

### Post by calvinthomas on 2006-09-09
Try this:

Go to a terminal and type gksudo nautilus

Go to filesystem, then etc, then apt, in there you will find your sources.list file and also you should find a backup file, copy and paste your backup over the sources.list file and you'll have restored what you had previously.

Calv

---

### Post by kitt on 2006-09-09
i tried as instructed..and get the same error output... :-(

---

### Post by kitt on 2006-09-09
i have even tried the source-o-matic ... same error output

---

### Post by trebor on 2006-09-09
> **kitt said:**
> i have even tried the source-o-matic ... same error output

You could try this thread and see if it helps.  I changed my source list as well and got the same erros, but this got rid of that.

---

### Post by kitt on 2006-09-12
Someone please help me with this..i think that the problem may not be in sources.list but rather apt-get itself..
I feel cut-off without apt-get & synaptic ...

PS: trebor, whats the link to that thread??

---

### Post by ruedu on 2006-09-12
Actually, it sounds to me like there is a problem with the sources.list file.  I would edit the sources.list file and comment out each entry (put a # in front of each one) and then save it.  Run apt-get update and it should do nearly nothing.  Then, one by one uncomment the source lines in the file and run apt-get update each time until it errors again.  Once it does, you know you've found the problem line.

---

### Post by davebgimp on 2006-09-12
Can you post the contents of your sources.list file?
With Gnome **gksudo gedit /etc/apt/sources.list**

With KDE **kdesu kate /etc/apt/sources.list**

---

### Post by kitt on 2006-09-12
Heres my sources.list file:

#deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by kitt on 2006-09-12
I just remembered : in order to make axel work, i had added export_HTTP_proxy to my bash config file...is that the cause of the problem??
And what is this line supposed to mean (error output) 
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)

---

### Post by ruedu on 2006-09-12
Probably, I would unset HTTP_PROXY and see what happens

---

### Post by kitt on 2006-09-13
Ive tried commenting the export_http_proxy lines in .bashrc file, and i still get the same error meassages.

---

### Post by ruedu on 2006-09-13
Did you get out of the shell first?

---

### Post by kitt on 2006-09-18
Yes, i exited the shell..
Some-one with a knowledge of apt-get..PLEASE help me out..im stranded without apt-get- and cannnot afford to do a fresh install 
Thanks

---

### Post by kitt on 2006-09-21
Can some apt-get expert please help me out??

---

### Post by OceanSoul on 2006-09-23
Greetings.

I have the same problem as you, also with timidity. We both need help. 
I didn't change anything in my sources.list. This happens with alot of stuff that I want to download. Some things I want to download with apt-get that are on manuals about Ubuntu, I can't download. This is weird. 

Could anyone help? Thanks. :D

---

### Post by OceanSoul on 2006-09-23
Well, I solved my problem. The problem was that I couldn't download timidity with apt-get. I just edited the sources.list, uncommenting the last 2 sources (universe's ones), and done. It worked.
Now I'm having some problems with making timidity work, but that's another story. I think I'll just give up. lol
I'm pleased if it works for you.

Later.

---

