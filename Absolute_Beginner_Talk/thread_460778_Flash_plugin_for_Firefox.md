---
title: "Flash plugin for Firefox"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by phoenixankit on 2007-06-01
I wanted to install it, and I got a .rpm fie of 2.5 mb on my desktop. I didnt know how to proceed so I googled it. Then I got to know that I need to convert it to .deb (why???), for that I need to download Alien...for that I need to 
> You can install alien itself from the Ubuntu Universe repository by adding the repository to your list of sources and doing:

```
$sudo apt-get update
$sudo apt-get install alien
```

How do I add "the repository to my list of sources"
Cuz, if I try sudo apt-get update, It gets stuck on ```
99% [Connecting to in.archive.ubuntu.com (91.189.88.31)]
```

Help please........please!!!

---

### Post by kerry_s on 2007-06-01
flash is in the repos, make sure yours is all on. you can use synaptic or the terminal(sudo apt-get install flashplugin-nonfree)

---

### Post by wormser on 2007-06-01
You can install flash via apt-get.  There is no need to convert .rpms to .debs.  The repositories have most anything you need.

```
sudo apt-get install flashplugin-nonfree
```

You need to open up your repositories.  System> Administration> Software Sources.  Another method is to edit the /etc/soures.list.  Just uncomment the urls for the repositories universe and multiverse. 

```
sudo nano /etc/sources.list
```

---

### Post by phoenixankit on 2007-06-01
UPDATE: After some time of the "99% [Connecting to in.archive.ubuntu.com (91.189.88.31)]" error, of "sudo apt-get update", I get this:
```
Err http://archive.ubuntu.com feisty Release.gpg     
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]

```

---

### Post by phoenixankit on 2007-06-01
> **wormser said:**
> You can install flash via apt-get.  There is no need to convert .rpms to .debs.  The repositories have most anything you need.

```
sudo apt-get install flashplugin-nonfree
```

You need to open up your repositories.  System> Administration> Software Sources.  Another method is to edit the /etc/soures.list.  Just uncomment the urls for the repositories universe and multiverse. 

```
sudo nano /etc/sources.list
```

I tried ```
sudo apt-get install flashplugin-nonfree
``` but I get ```
E: Couldn't find package flashplugin-nonfree
```

---

### Post by wormser on 2007-06-01
> **wormser said:**
> 

You need to open up your repositories.  System> Administration> Software Sources.  

Did you try that first?

---

### Post by phoenixankit on 2007-06-01
```
sudo nano /etc/sources.list
```
gives me 
[[IMG]http://img357.imageshack.us/img357/4242/screenshotht5.th.png[/IMG]](http://img357.imageshack.us/my.php?image=screenshotht5.png)

and in

```
System> Administration> Software Sources
```
All of them are checked
[[IMG]http://img84.imageshack.us/img84/4347/screenshot1wv4.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshot1wv4.png)

---

### Post by Dougie187 on 2007-06-01
Wrong file. Its /etc/apt/sources.list

---

### Post by wormser on 2007-06-01
> **Dougie187 said:**
> Wrong file. Its /etc/apt/sources.list

Duh, my bad.  That is the right location.

---

### Post by phoenixankit on 2007-06-01
So its Sudo nano /etc/apt/sources.list ?

---

### Post by phoenixankit on 2007-06-01
So I get this:
```
deb http://ubuntu.beryl-project.org feisty main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://in.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://in.archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://in.archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://ubuntu.beryl-project.org feisty main

deb-src http://ubuntu.beryl-project.org feisty main

```

what next???(sorry, i'm a TOTAL linux newbie

---

### Post by Dougie187 on 2007-06-01
Yeah.

Here are the contents of my sources.list. If you need to you can just put this stuff in your sources.list file. Make sure you do a *sudo apt-get update* before you do *sudo apt-get install flashplugin-nonfree*.

```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
```

---

### Post by phoenixankit on 2007-06-01
> **Dougie187 said:**
> Yeah.

Here are the contents of my sources.list. If you need to you can just put this stuff in your sources.list file. Make sure you do a *sudo apt-get update* before you do *sudo apt-get install flashplugin-nonfree*.


Problem #2
On doing *sudo apt-get update*  , it gets stuck on **99% [Connecting to us.archive.ubuntu.com (91.189.88.31)]  ** and then, I get this:
```
Err http://archive.ubuntu.com feisty Release.gpg     
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]
```

---

### Post by Dougie187 on 2007-06-01
Try commenting out that repo in your sources.list. You'd get screwed if that one is the one with the flash plugin, but you can just see if it works or not.

---

### Post by Dougie187 on 2007-06-01
I guess while im waiting for you to try that one i will answer some of your other questions.

> **phoenixankit said:**
> I wanted to install it, and I got a .rpm fie of 2.5 mb on my desktop. I didnt know how to proceed so I googled it. Then I got to know that I need to convert it to .deb (why???), for that I need to download Alien
So.. rpms are install files, but not for debian based systems. So since you are on a debian based system (ubuntu is debian based) you have to convert any rpm file into a .deb. Because for debian systems .deb files are the equivalent of .rpm files. Alien is a package that allows someone to convert a .rpm file into a .deb file fairly easy.

> **phoenixankit said:**
> How do I add "the repository to my list of sources"

You add any repositories into your sources list by editing that /etc/apt/sources.list file and adding in some like with the repository address in it.

Edit:
Well im going to bed now. Just post and i will see if i can help out more tomorrow if noone gets to it tonight. Good luck.

---

### Post by phoenixankit on 2007-06-01
Now I have ##'d all the us.archives.ubuntu's, now the sudo apt-get update is "done"

---

### Post by phoenixankit on 2007-06-01
DAMN, now "sudo apt-get install flashplugin-nonfree" returns "E: Couldn't find package flashplugin-nonfree

---

### Post by phoenixankit on 2007-06-01
Help!!!

---

### Post by Rui Pais on 2007-06-01
just out of curiosity, what happens when you browse to 91.189.88.31 with firefox (or whatever your browser is)?

---

### Post by phoenixankit on 2007-06-01
Seriously, I'm not able to do ANYTHING, cant even play mp3 because of this error...help...PLEEEZE

---

### Post by phoenixankit on 2007-06-01
> **Rui Pais said:**
> just out of curiosity, what happens when you browse to 91.189.88.31 with firefox (or whatever your browser is)?
Nothing, it just says connecting to 91.189.88.31 with a blank page..

---

### Post by Rui Pais on 2007-06-01
But you can browse the web normally (i mean you can navigate to pages on the net)?
sounds to me that you having a problem with DNS servers

---

### Post by Rui Pais on 2007-06-01
what do you prefer to do, try to see if thats the problem or get instruction on how to get and manually install the package you need?

---

### Post by phoenixankit on 2007-06-01
yes i can navigate other pages. I'd like to first try and see if thats the problem, if solved,then YAY, If not then manually install

---

### Post by wormser on 2007-06-01
This method usually works for firefox.  Go to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and install the missing plugin for flash.  I do not think there is a plugin for shockwave so skip that one.

The problem you are getting from apt-get might be with that repo or a dns issue.  From your image in an earlier post it looked like you are in India.  Maybe if you go back into Software Sources and change the Download From to another location.  It is worth a try.

---

### Post by aysiu on 2007-06-01
You seem to have some weird internet configuration problem, which is its own issue.

If all you want is Flash installed, one of these methods should work (since your problem is with *apt-get* connecting to the servers), I'd recommend either the point-and-click for one user or installing from the Adobe website using the terminal:
[http://psychocats.net/ubuntu/flash](http://psychocats.net/ubuntu/flash)

---

### Post by Rui Pais on 2007-06-01
> **phoenixankit said:**
> yes i can navigate other pages. I'd like to first try and see if thats the problem, if solved,then YAY, If not then manually install

good :)

try to replace your DNS server with some good generic ones. Usually OpenDNS are the best (fast and reliable).

open you /etc/resolv.conf comment (put a # in the beginning of each line) the IPs listed there and add this too lines:```

208.67.222.222
208.67.220.220
```

try to browse again to that address or redo apt-get update.

---

### Post by phoenixankit on 2007-06-01
> **Rui Pais said:**
> good :)

try to replace your DNS server with some good generic ones. Usually OpenDNS are the best (fast and reliable).

open you /etc/resolv.conf comment (put a # in the beginning of each line) the IPs listed there and add this too lines:```

208.67.222.222
208.67.220.220
```

try to browse again to that address or redo apt-get update.
So I just edit resolve.conf, then # the existing 2 lines and add the 2 lines you gave? 
So should it look like this:
```
# nameserver 202.56.215.54
# nameserver 202.56.215.54
208.67.222.222
208.67.220.220
```
or 
```
# nameserver 202.56.215.54
# nameserver 202.56.215.54
nameserver 208.67.222.222
nameserver 208.67.220.220
```

---

### Post by Rui Pais on 2007-06-01
sorry, my mistake. you are absolutly right:
```
# nameserver 202.56.215.54
# nameserver 202.56.215.54
nameserver 208.67.222.222
nameserver 208.67.220.220
```
yes.

(i need to get a coffee, it's early here... )

---

### Post by phoenixankit on 2007-06-01
It says the file is read only & i dont have necessary permissions to save the file,,,,!!!???

---

### Post by Rui Pais on 2007-06-01
> **phoenixankit said:**
> It says the file is read only & i dont have necessary permissions to save the file,,,,!!!???

you need root powers:
on command line:
```
sudo nano /etc/resolv.conf
```
or
```
gksudo gedit /etc/resolv.conf
```

(or kedit if you have kubuntu or mousepad if you have xubuntu)

---

### Post by wormser on 2007-06-01
> **phoenixankit said:**
> It says the file is read only & i dont have necessary permissions to save the file,,,,!!!???

When ever you see that error you need to use **sudo**.  

Try going to this link and install the missing plugin for flash, the shockwave will not work.
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

---

### Post by phoenixankit on 2007-06-01
> **wormser said:**
> This method usually works for firefox.  Go to [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and install the missing plugin for flash.  I do not think there is a plugin for shockwave so skip that one.

The problem you are getting from apt-get might be with that repo or a dns issue.  From your image in an earlier post it looked like you are in India.  Maybe if you go back into Software Sources and change the Download From to another location.  It is worth a try.
Nah, It doesnt work, I changed the location to US, then this appeared
[[IMG]http://img505.imageshack.us/img505/8252/screenshotds1.th.png[/IMG]](http://img505.imageshack.us/my.php?image=screenshotds1.png)
 then,when I click on reload,
it ws stuck here:
[[IMG]http://img484.imageshack.us/img484/9382/screenshot1mw0.th.png[/IMG]](http://img484.imageshack.us/my.php?image=screenshot1mw0.png)

---

### Post by Rui Pais on 2007-06-01
> **phoenixankit said:**
> Nah, It doesnt work, I changed the location to US, then this appeared
...

sorry, don't know if  i understand quite right... it doesn't work after you move to openDNS ones? or when you try to install plugin directly from adobe?

---

### Post by phoenixankit on 2007-06-01
> **Rui Pais said:**
> sorry, don't know if  i understand quite right... it doesn't work after you move to openDNS ones? or when you try to install plugin directly from adobe?

NO, that was to wormser...

---

### Post by phoenixankit on 2007-06-01
Bump

---

### Post by wormser on 2007-06-01
Did you try this method?

Try going to this link and install the missing plugin for flash, the shockwave will not work.
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

---

### Post by Rui Pais on 2007-06-01
> **phoenixankit said:**
> NO, that was to wormser...

> **phoenixankit said:**
> Bump

ok, but in that case what happen when you set your DNS servers to openDNS? can you then browse 91.189.88.31?

---

### Post by phoenixankit on 2007-06-01
It's the same, I cant sudo apt-get update nor can I browse 91.189.88.31

---

### Post by Rui Pais on 2007-06-01
> **phoenixankit said:**
> It's the same, I cant sudo apt-get update nor can I browse 91.189.88.31

thats weird... are you beyond a firewall or connect through a proxy? 
what kind of internet connection you have (cable/router/usbmodem...)?

Or maybe your net connection just needs a restart:
```
sudo ifdown eth0 && sudo ifup eth0
```
(change eth0 for whats your case, if it's not eth0)

Or maybe your /etc/resolv.conf is overwritten automatically (it happens with certain configurations).
Check if /etc/resolv.conf still as the openDNS ones. If not they are overwritten you may try [this here]("http://www.opendns.com/start/ubuntu.php"). 

Good luck 
(keep post on failure or success)

---

### Post by phoenixankit on 2007-06-01
I have an ADSL modem, connected via Ethernet.
I'm on Windows right now, so I wont be able to try out the methods, but I will asap

---

### Post by phoenixankit on 2007-06-02
They ARE the openDNS ones. omg...this is annoying...

---

### Post by nvteighen on 2007-06-02
This thread is a bit messy. Ones are trying to solve the DNS issue and others the Flash simultaneously.

This is a method I've proven to work:

Go to [http://www.adobe.com/](http://www.adobe.com/) and click on the "Get Adobe Flash Plugin" button. This will detect your OS automatically. Ubuntu is Debian-based, so download the **.tar.gz** file NOT the **.rpm** (that's for RedHat-based systems like Mandriva, for example).

Tar files are just compressed files. Double-click it and tell the Archive Manager to extract it to your desktop (you can do it elsewhere, but it's for convenience). After that, you'll get a folder called "install_flash_player_9_linux" in your Desktop. Please, rename it to "flash" (right-click the folder)

Open a terminal and type (I assume you have followed my recommendation to extract into desktop and rename the folder to "flash"):

```
cd Desktop/flash
./flashplayer-installer

```

This will install Flash **only for you**. If you want to install it **for all users**, do:

```

cd Desktop/flash
sudo ./flashplayer-installer

```

For more information, you have also a README.txt in the extracted folder.

---

### Post by Rui Pais on 2007-06-02
> **nvteighen said:**
> This thread is a bit messy. Ones are trying to solve the DNS issue and others the Flash simultaneously.

Yes, but if you take care to read [post #24]("http://ubuntuforums.org/showpost.php?p=2759879&postcount=24") you will note that phoenixankit seems to prefer to fix the network issue first, natural when one has an internet that work but don't browse to some places or cant update some repos... watch flash movies is not what came to mind in a such a case ;)


> **phoenixankit said:**
> They ARE the openDNS ones. omg...this is annoying...

Sorry, i don't know much beyond here. It seems a DNS issue but as far as i know openDNS never failed to resolve an IP, not that one at least... 
My only suggestions by now, is you may try again, with the openDNS set to put back with India servers, using synaptic, and try to resync... not that should make great difference but a least you tried...

My best advise is to open a thread on this issue on [Networks forum]("http://ubuntuforums.org/forumdisplay.php?f=136") where you find a lot of people with advance knowledge of nets and dns issues (or others) and keep this to flash plugin, since there are now so many suggestions on that subject.

Good luck.

If you open a new thread please post the link, i'm curious to see how that would be solved.

---

### Post by nvteighen on 2007-06-02
> **Rui Pais said:**
> Yes, but if you take care to read [post #24]("http://ubuntuforums.org/showpost.php?p=2759879&postcount=24") you will note that phoenixankit seems to prefer to fix the network issue first, natural when one has an internet that work but don't browse to some places or cant update some repos... watch flash movies is not what came to mind in a such a case ;)

Oh, excuse me, I missed it! :oops:

---

### Post by Rui Pais on 2007-06-02
No need for excuses :) 
this is a public forum, one can (and should) try to help in anyway he/she knows.

Anyway that network problem it's harder then i thought at first, so maybe here (Absolute beginner) is in fact a better place to deal with flash question and open a thread on a specialized forum to get more specialized answers for the network question.

---

### Post by phoenixankit on 2007-06-03
Alright...anyways, thanks for the help...

---

