---
title: "Automatix Problem"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Felix Jay on 2006-11-15
Hi Can anyone explain to me why I can connect to the internet fine but have absolutely no luck in updating with easyubuntu or automatix? I've printed down below my session in trying to get automatix and I'm a bit baffled. I ma of course a total learner at this and in all other regards am dead excited about ubuntu: - 

house@House:~$ gksudo gedit /etc/apt/sources.list
(gedit:6132): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
house@House:~$ sudo gedit /etc/apt/sources.list
house@House:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--21:43:35--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

21:43:35 (16.67 MB/s) - `key.gpg.asc' saved [1730/1730]

house@House:~$ gpg --import key.gpg.asc
gpg: directory `/home/house/.gnupg' created
gpg: new configuration file `/home/house/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/house/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/house/.gnupg/secring.gpg' created
gpg: keyring `/home/house/.gnupg/pubring.gpg' created
gpg: /home/house/.gnupg/trustdb.gpg: trustdb created
gpg: key 521A9C7C: public key "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
house@House:~$ gpg --export --armor 521A9C7C |sudo apt-key add -
OK
house@House:~$ sudo apt-get update
0% [Connecting to packages.freecontrib.org (1.0.0.0)]
0% [Connecting to packages.freecontrib.org (1.0.0.0)]

ANy help much appreciated. (I'm dual booted with XP)

---

### Post by raul_ on 2006-11-15
maybe those servers are down...try later

---

### Post by nickpaton on 2006-11-15
I'm not quite clear - have you actually got Automatix working, or have you simply downloaded it?

Full information on Automatix can be found on 

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

When you post again, can I politely suggest that you include which Ubuntu distro you are using, and if it's a hardware / software problem, to include your PC specs as well

And welcome to the forums, Felix

---

### Post by Felix Jay on 2006-11-15
Hi NP, Apologies i'm on version 6.06 dapper. 

Well the thing is I can't seem to download it - the closest thing I can approximate it to is that I time out! 

Again any help much appreciated!

---

### Post by nickpaton on 2006-11-15
Go for Autmatix2 which works very well.
First off lets uninstall the version of Automatix you already have and start again:

```
sudo apt-get remove automatix
```

or if it doesn't find the file, try for Automatix2:

```
sudo apt-get remove automatix2
```

Then you need to follow EXACTLY the steps for 6.06 Dapper as per the installation section of:

[http://getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29]("http://getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29")

I think that the keys will already be there, but run the commands even so to check

That should now work for you.  I think possibly you may have put the wrong deb in your sources file and it's taking you to the wrong place, but I could be wrong.

Get back with any probs.  I'm off to bed now, but will check first thing.

Good luck!

---

### Post by arnieboy on 2006-11-15
remove the freecontrib/easyubuntu repos from your sources.list and do an apt-get update

---

### Post by Felix Jay on 2006-11-16
Thanks NP I'll try that this evening and get back with any results. I thought I'd followed the steps pretty carefully for Automatix 2 but I'll give it another go! 

Arnieboy - I know this is SO stupid but how do I remove the freecontrib/easyubuntu repos from my sources.list? 

Really appreciate the help!

---

### Post by nickpaton on 2006-11-16
Felix -

Open up your Sources.list in a terminal:

```
gksudo gedit /etc/apt/sources.list
```

Scroll down to where you have freecontrib and easyubuntu and and put a comment (##) infront of them i.e:

Example of un commented repo lines (using edgy-updates):

```
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

```
After commented repo lines:

```
##deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
##deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
```

The last example will not be downloaded when a sudo apt-get update is done.

Also note that some repositories have two lines and you will need to comment both lines.

Commenting the lines means that they are available again if you want to use them again in the future.

Having modified your sources list remember to save it!

Get back with any results or problems!

---

### Post by Felix Jay on 2006-11-16
Hi Nick 

Well I've been busy - I  corrected my DNS servers (which weren't listed!) and I can now connect to  apt-get or synaptic  but it gets to 9/12 and then I get the following: 

[http://packages.freecontrib.org/plf/dists/dapper/main/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/main/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/restricted/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/universe/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/universe/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/multiverse/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/multiverse/binary-i386/Packages.gz:) 404 Not Found

[B]my sources list now reads as follows after I get the following warning: (gedit:7672): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 [/B]

eb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper main restricted universe multiverse
##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
## deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
##deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

AS EVER ANY HELP MUCH APPRECIATED AS IT ROCKS!

---

### Post by Felix Jay on 2006-11-16
Oh and I also get this! 

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

---

### Post by nickpaton on 2006-11-16
Felix

Change your sources list to:

```
##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper main restricted universe multiverse
##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
## The above lines were generated automatically by EasyUbuntu 3.02 Release
## The rest of your sources.list follows

##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper main restricted universe multiverse
##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
##Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

##deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
```

Copy and paste the above list into your sources list.

I've commented everything to do with easyubuntu

What you've done is to comment everything out, so it couldn't find any site to update from!!

Get back to me with your results etc.

---

### Post by Felix Jay on 2006-11-16
YOU ARE A GENIUS! Could now connect to apt-get and synaptic! 

MAny many many thanks for your help! 

Off now to get easyubuntu - I fear I might need it!

---

### Post by nickpaton on 2006-11-16
> **Felix Jay said:**
> Oh and I also get this! 

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

You need to subscribe to the encryption key for the freecontrib packages as follows:

```
 gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys KEYSTRING
```


KEYSTRING is F120156012B83718 in this case.

Note that in the course of running the above, it gives a smaller 8 digit number 12B83718 (<KEY>)

```
gpg --export --armor <KEY> | sudo apt-key add -
```

This process adds the encryption key and allows you to run the file.

Also, go into your sources list and uncomment (remove the ##'s against the freecontrib dapper lines.

BTW this site is often not available, so you may get no site found errors.

---

### Post by nickpaton on 2006-11-16
> **Felix Jay said:**
> YOU ARE A GENIUS! Could now connect to apt-get and synaptic! 

MAny many many thanks for your help! 

Off now to get easyubuntu - I fear I might need it!

Well done M8 - congratulations!!

Now try running the encryption key and uncommenting the freecontrib dapper repos.

---

### Post by Felix Jay on 2006-11-16
Hi Nick 

Stupid question but where do I put  gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys KEYSTRING   ??? 

Is this why having downloaded easy ubuntu, ticked what I'd like from it, it just seems to hang?

---

### Post by nickpaton on 2006-11-16
Felix - no such thing as a stupid question, so no worries!!

You open a terminal, which can be found via Applications>Accessories>Terminal

remember to substitute "keystring" with your long key number

Good luck!

---

### Post by Felix Jay on 2006-11-16
Hi Nick 

I got this - 

gpg: requesting key 12B83718 from hkp server wwwkeys.eu.pgp.net
gpg --export --armor 12B83718 | sudo apt-key add -
gksudo gedit /etc/apt/sources.listgpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
house@House:~$ gpg --export --armor 12B83718 | sudo apt-key add -
Password:gpg: WARNING: nothing exported

So best perhaps to try again later! I presume I can just go ahead anyway and try and get automatix2? 

Cheers for the advice!

---

### Post by nickpaton on 2006-11-16
Mmmm interesting....

When I put into a terminal:

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F120156012B83718

```
I get the following back:

```
gpg: requesting key 12B83718 from hkp server wwwkeys.eu.pgp.net
gpg: key 12B83718: "Lionel Le Folgoc (mr_pouit) <lionel.lefolgoc@free.fr>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

The unchanged bits are coz I've already downloaded the key, but it does seemt to work, and you can see the 8 letter key.
But hope you get the general idea!

But anyway...don't get too hung up about it.

Automatix2 is a great package, which I have used loads.

Have you actually managed to download and install it as per the previous postings?  If you have, it should now be under Applications>System Tools>Automatix with a red AX symbol.

---

### Post by Felix Jay on 2006-11-16
Ah hell Nick it's gone to pot again! Just when I thought I was flying! 

ON automatix I get this - [B]house@House:~$ sudo gedit /etc/apt/sources.list
house@House:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--23:07:09--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.1'
Resolving [www.getautomatix.com](www.getautomatix.com)... 1.0.0.0
Connecting to www.getautomatix.com|1.0.0.0|:80...
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2
failed: Connection timed out.
Retrying.

--23:10:19--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
  (try: 2) => `key.gpg.asc.1'
Connecting to www.getautomatix.com|1.0.0.[/B]0|:80

Again it looks like I'm timing out..........

My source list now reads as follows (is there anything that needs changing?) I really appreciate your help on this! 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper main restricted universe multiverse
##deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
## The above lines were generated automatically by EasyUbuntu 3.02 Release
## The rest of your sources.list follows
##Line commented out by installer because it failed to verify:
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
##deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
##deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by nickpaton on 2006-11-16
2 secs - I need to reboot..

---

### Post by Felix Jay on 2006-11-16
AH heck no worries Nick I think I'm in this for the long haul - just tried to get Thunderbird and the connection timed out which is annoying as I seem to be back to that problem!

---

### Post by nickpaton on 2006-11-16
Sorry about that!
Right - your repository list is in a right old state, so I suggest we start with a known good one from:

[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

Do a copy of the one below, and paste over your existing one.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

##deb http://packages.freecontrib.org/plf/ dapper free non-free
##deb-src http://packages.freecontrib.org/plf/ dapper free non-free

deb http://www.getautomatix.com/apt dapper main

```

I'm keeping it simple and not putting in the .gb tags to download from UK mirrors.

You will see that many of the repos are in pairs i.e. "deb http..." and "deb-src http..."
On some pairs you had one half uncommented and the other commented, so no idea what sort of download you were getting - but don't worry about that, just use the one I've posted.
You will see that I've included automatix repo, so you don't have to!

Right onto Automatix2...

Your sources list looked a tad strange with automatix uncommented on on line and then commented # (i.e. not able to download on the next).

Are you using a dial up to download?
I must admit even on bb, the site took a little time to get into tonite, so may be busy.

Leave it a couple of mins if it times out and try again.  Alternatively you may have to wait until later or tomorrow.

Try that & get back.  i will be going to bed soon!

EDIT:  I am off to bed now Felix - I'll pick this up first thing M8!

---

### Post by Felix Jay on 2006-11-17
Hi Nick 

Thanks for that! I'll copy & paste that into my sources list hopefully this evening. I have just then been pressing save which I presume is correct? 

That Psychocats website is awesome. 

I'm on BB so no idea why the source list is such a state! Do you know where I can learn more about "uncommented" and "commented" as I had no idea such as thing existed and was important! 

Once I've got the new source list how would I then get automatix? Is there a way to erm, run an update?

Once again (!) thanks for your help! Just a shame works get in the way of mucking about with linux!

---

### Post by nickpaton on 2006-11-17
> **Felix Jay said:**
> Hi Nick 

Thanks for that! I'll copy & paste that into my sources list hopefully this evening. I have just then been pressing save which I presume is correct? 

Yes you need to press save! 

> **Felix Jay said:**
> I'm on BB so no idea why the source list is such a state! Do you know where I can learn more about "uncommented" and "commented" as I had no idea such as thing existed and was important!

Off hand, Felix, I don't know any actual information about this, but as you say Psychocats's site continues to grow and grow with really good, simple information.

> **Felix Jay said:**
> Once I've got the new source list how would I then get automatix? Is there a way to erm, run an update?


Sources List and Repository (repo) are interchangeable terms.

The sources list does two main things:

1. It says what software is potentially available to you to download and use.  
So if, for instance you did not have Ubuntu Multiverse (or if it was commented out!) you might not be able to install a particular software package you want to use.

2. It specifies to the updating software which sites to use for automatically updating Ubuntu on a regular basis.

Because the Psychocats repository list does not by default contain Automatix, this is why I added it to the bottom.
It makes it potentially available to be downloaded now, and to be regularly updated in future.

The reason for having a small default repo list is to load only the basic packages to make Ubuntu run.
Therefore if you need further packages you simply add (or remove) them as they are needed.
My own one is actually quite big, coz I have quite a lot of extra packages and want them to be regularly updated.
This is one major advantage of Ubuntu over its competitors, many of whose "default" packages are over 4 and 5 CD's with just about every package on them whether you want them or not.

Sorry for the long explanation on Repositories list, but hope it makes its purpose a little clearer.

Right.. 

You have Automatix on your repo.  

Now we need to check the Automatix2 encryption key is correctly loaded on your PC.  I know that I have written this before, but it's worth repeating (apologies but hope you understand LOL!)

1. You've copied and pasted my suggested Psychocats repo with Automatix added at the end, into the sources list.

2. Save it, and close it.

We are going to put the follwing commands in turn into the Terminal, pressing the Enter key each time to let each command run before entering the next.

3. ```
wget http://www.getautomatix.com/apt/key.gpg.asc
```

Enter key!

4. ```
gpg --import key.gpg.asc
```

Enter key again!

5. ```
gpg --export --armor 521A9C7C | sudo apt-key add -
```

Enter Key (I won't repeat - think you'e got the idea LOL!!).

That should be the encryption code "registered" with your PC.  It simply means you have automatic permission to download Automatix2 - It's not some weird way of checking up on you or anything!!

6. Carry out a general update of all Dapper packages: 

```
sudo apt-get update
```

7.  Install Automatix2 package:

```
sudo apt-get install automatix2
```

If you have managed to successfully install Automatix2, you will see the icon in  Applications > System Tools.

Get back to me and Good luck again M8!:)

---

### Post by Felix Jay on 2006-11-17
Hi nick, 

That is simply superb! I will try and do it tonight (the GF thinks she's lost me to the computer!) and get back to you! Once I can get automatix working I'll be well chuffed. 

Once again thanks!

---

### Post by blood2rayne on 2006-11-17
thanks from information

---

### Post by trav5 on 2006-11-17
Hi guys. I looked at this thread last night and decided to install automatix 2 from [http://www.getautomatix.com/](http://www.getautomatix.com/) . I followed the instructions to the tee and it installed fine. I saw the ndiswapper ](*,) so I thought I would try again. I also got help from this thread [http://www.ubuntuforums.org/showthread.php?t=277037](http://www.ubuntuforums.org/showthread.php?t=277037) . I am now wireless in ubuntu:D .

---

### Post by nickpaton on 2006-11-17
> **blood2rayne said:**
> thanks from information
It's a pleasure and welcome to the forums!

---

### Post by Felix Jay on 2006-11-18
Nick, 

Just checked applications, system tools and a lovely little automatix icon is sat there. Thanks so much for your help! Awesome stuff.......

---

### Post by Felix Jay on 2006-11-18
And it's just downloaded loads of stuff! Nice!

---

### Post by nickpaton on 2006-11-18
It's a pleasure Felix - now go and enjoy the wonders of a stable virus-free OS!

Oh and my wife sympathises with your GF!!

Any other queries we're here to help any time.

---

### Post by Felix Jay on 2006-11-18
Cheers Nick again! I didn't want to involve you but any idea what is going on here?? It's got me stumped!

[http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1774926](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1774926)

---

