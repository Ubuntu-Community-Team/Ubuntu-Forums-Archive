---
title: "Debian vs Ubunutu"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-04-19
Going against the judgement of some linux-using friends (who swear by debian), I installed ubunut as i found it to be an easy introduction for a virgin user. And since it was a debian based system i figured i'd have access to all the debian packages...

however i was attemting to install grace (XMGR) and couldn't get motiff from Ubuntu..and had to move to Debian in the end (although i still have a boot option for ubuntu)...i like Ubunutu and want to stick with it..but in debian i was able to download Rasmol and Grace as packages..no fuss at all...

Why can't i do this (via synaptic) in Ubuntu...or was i screwing it all up???

The guy who helped in my attempt to work on Ubuntu has been rubbing slackware for the last 3 yrs...so i guess he knows what he's doing...

---

### Post by _linux_ on 2006-04-19
Have you tried putting in more sources for Synaptic (such as the Backports)?

---

### Post by henriquemaia on 2006-04-19
Have you enabled other repositories apart from the default ones?

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by nalmeth on 2006-04-19
Enable the extra repositories and try 
apt-cache search grace xmgr whatever
I prefer this to searching synaptic. It all seems so distracting to me. It might be there under another name. 
Maybe not.
If you're willing to wage a little risk, I've heard you can add "some" debian repos to your sources and get a little 'hybrid' debian-ubuntu.
Could be dangerous and lead to depenendency trouble though.
Your linux-friends may be impressed

---

### Post by localzuk on 2006-04-19
Also, if you want to take a look at what is in the repo's for Ubuntu take a look at [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by neelabhro on 2006-04-19
I tried this with the back port key

gpg --keyserver subkeys.pgp.net --recv KEY


but still no luck...how to i get access to the debian repository..will their website have that info??

---

### Post by mjziegle on 2006-04-19
I have no problems with xmgrace.  I use it for research.  It works fine with Ubuntu.  Most likely you didn't install all the appropriate libraries for the configure script to find motif (or lesstif a motif alternative).

Do a synaptic search for lesstif or motif and install the libraries.  

When you compile the program make sure you do a "make clean".  The archive contains some settings that have to be purged.  

If all doesn't work send me a pm along with the output of your configure script.

No reason to use debian here.

I think you just need to

>sudo apt-get install libmotif-dev libmotif3    (or)
>sudo apt-get install lesstif-bin lesstif-doc lesstif-dev lesstif1 lesstif2 lesstif2-dev
>cd /<xmgrace source dir>
>./make clean
>./make dist-clean (I can't remember the syntax)
>./make clean-all
>./configure
>./make
>./make install

(Edit)

Better yet.  Just enable the multiverse and universe repositories

>sudo apt-get update
>sudo apt-get install grace    (or)
>sudo apt-get install grace6

-Matt
 




[QUOTE=neelabhro]Going against the judgement of some linux-using friends (who swear by debian), I installed ubunut as i found it to be an easy introduction for a virgin user. And since it was a debian based system i figured i'd have access to all the debian packages...

however i was attemting to install grace (XMGR) and couldn't get motiff from Ubuntu..and had to move to Debian in the end (although i still have a boot option for ubuntu)...i like Ubunutu and want to stick with it..but in debian i was able to download Rasmol and Grace as packages..no fuss at all...

Why can't i do this (via synaptic) in Ubuntu...or was i screwing it all up???

The guy who helped in my attempt to work on Ubuntu has been rubbing slackware for the last 3 yrs...so i guess he knows what he's doing...[/QUOTE]

---

### Post by jimrz on 2006-04-19
Grace is in the "universe" repo, which you would need to enable in synaptic.

---

