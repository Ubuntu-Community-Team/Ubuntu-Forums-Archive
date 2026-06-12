---
title: "Update manager and and synaptic will not connect"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by danyro on 2007-01-07
Hey all!

I am very much new at this and so far so good until today. 

I have a quick video to edit and trying to load a software package to do so. 

As soon as I try to do it it sits there and won't connect to the internet. 
I tried other software packages and same result. 

Also I have the exact same problem with update manager and I think that the two issues are related. 

FYI... I can browse the internet just fine with Firefox. 
Please help.

Regards.](*,)

---

### Post by Ozitraveller on 2007-01-07
Are you using Kubuntu or Ubuntu or Xubuntu? Are you using Dapper, Edgy, Feisty?


Could you please post you sources.list file. It's in /etc/apt/sources.list

if you are using Ubuntu, open a terminal and enter :

>sudo gedit /etc/apt/sources.list (return)

copy the contents of the file, then make a new post and paste them in.

this will open the sources.list file in gedit (gnome editor)

to exit the terminal
>exit (return) 


Could you please post any error messages too.

---

### Post by danyro on 2007-01-07
Thanks mate!

I am using Ubuntu 6.06 LTS

Here's my sources.list file:

__


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by danyro on 2007-01-07
bump](*,)

---

### Post by ajmorris on 2007-01-07
what happens if you do a: [PHP]sudo apt-get update[/PHP]?

---

### Post by danyro on 2007-01-07
57% waiting for header

and stays stuck...

---

### Post by ajmorris on 2007-01-07
do you use proxy servers at all?

---

### Post by danyro on 2007-01-07
No proxy server staight shot to my router...

---

### Post by ajmorris on 2007-01-07
this might be a long shot but, is it possible that your router blocks the port that synaptic and other package managers from getting out to the net?

---

### Post by danyro on 2007-01-07
Long shot indeed.

It used to work... and I did not change my router configuration. 

also....
 /etc/apt/apt.config  
looks like this...


Acquire::http::Proxy "false";

---

### Post by danyro on 2007-01-08
bump ](*,)

---

### Post by Ozitraveller on 2007-01-08
I generated this sources.list at:

Ubuntu sources.list generator
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


and compared it against yours



deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



And this is what I found

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted (generated)

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted (yours)
---------------------------------------------------^

yours has / after ubuntu

Hope this helps
:)

---

### Post by danyro on 2007-01-09
Ozzytraveller, first and foremost thanks for taking the time to help me out. 
I have updated source.list as shown below. No luck. 
Also, I have pasted in the bottom of this post the error messages I am getting when I hit cancel on the update which just does not go anywhere. Not sure if this gives you a better clue. 

Thanks again mate!

](*,) 

HEre's source.list
_________
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
______


Now the error messages

____

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20061004_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20061004_all.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20060927_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20060927_all.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.6-10ubuntu0.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.6-10ubuntu0.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb)

---

### Post by danyro on 2007-01-10
bump

---

### Post by danyro on 2007-01-12
bump again...
:twisted:

---

### Post by jas0 on 2007-01-12
This may sound like a stupid question but are you posting this (I mean here in the forums) from the same computer that's having this problem?

---

### Post by danyro on 2007-01-12
Yep...

As stated earlier in this post I have absolutely no issues connecting to the internet.
I am stumped!

---

### Post by Modernity on 2007-01-12
double check your sources list.

```

deb http://us.archive.ubuntu.com/ubuntu dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu dapper universe


```

There is a # on one but not the other. If you are going to comment it out, both have to be commented out. If you are trying to connect to that repository take out the #. So it reads like this:

```

deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe


```

---

### Post by danyro on 2007-01-12
made the update.
No change still broke.

---

### Post by nix4me on 2007-01-12
the us.ubuntu repository has been having problems lately....that could be why.

To verify you could get rid of the "us." in every line in the sources.list and try it.

nix4me

---

### Post by danyro on 2007-01-12
removed all of the "us."
Now it shows that my system does not need any new updates yet I cannot fetch/install any new software package (just tried Adobe Reader)

---

### Post by danyro on 2007-01-15
bump...bump:)

---

### Post by qamelian on 2007-01-15
> **Modernity said:**
> There is a # on one but not the other. If you are going to comment it out, both have to be commented out. If you are trying to connect to that repository take out the #.

You don't have to comment out both. The deb-src line indicates a repository for source packages. You don't need these repos active unless you need access to the source packages. I have all the deb-src repos commented out and only activate them when I need to otherwise I leave them inactive so the repos refresh faster.

---

