---
title: "Error while installing packages from the terminal..."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by B-777 on 2007-07-07
I am trying to install some codecs to play mp3 files in Dapper following the instructions at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) .

I enter the following command per the instructions in the link above:
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

Then get the following error:
```
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-sax-expat-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The main question is, how do I get the dependent packages configured for use?

---

### Post by taurus on 2007-07-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by bigken on 2007-07-07
Ensure the relevant repositories are enabled. Click **System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories** and then click **Add**. Check the **Community maintained (Universe)** and **Non-free (Multiverse) boxes.** When you close the window, click **Reload**.

---

### Post by B-777 on 2007-07-07
> **bigken said:**
> Ensure the relevant repositories are enabled. Click **System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories** and then click **Add**. Check the **Community maintained (Universe)** and **Non-free (Multiverse) boxes.** When you close the window, click **Reload**.

Already did that.

---

### Post by B-777 on 2007-07-07
> **taurus said:**
> Can you post your /etc/apt/sources.list?
Here you go...


```
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by overdrank on 2007-07-07
> **B-777 said:**
> Here you go...


```
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse[COLOR="Red"]# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe[/COLOR]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Hi if you follow the direction on enabling repos then something did not work as you can see there still is a couple commented out

---

### Post by B-777 on 2007-07-07
> **overdrank said:**
> Hi if you follow the direction on enabling repos then something did not work as you can see there still is a couple commented out

Yes...I did follow:

> Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.

Unless I am missing a step before that.

---

### Post by overdrank on 2007-07-07
Hi, I am no way implying that you did anything wrong, It is something that just happened and I have no idea why. I would use this command in the terminal
```
gksudo gedit /etc/apt/sources.list
```
And edit the repos by uncommenting the repos by removing the # from in front of the repos, I hope this helps and when you save the file then do the 
```
sudo apt-get update
``` 
command in terminal then followed by upgrade and then dist-upgrade and hope this works.

---

### Post by forrestcupp on 2007-07-07
You did remember to click "Reload" right?

It's too bad you can't upgrade to Feisty.  It's really pretty stable, and all of this is automated in Feisty.  All you have to do is open a media file, and if you don't have the codecs, it will install it automatically if you choose.

Edit:
> **overdrank said:**
> 
command in terminal then followed by upgrade and then dist-upgrade and hope this works.
Do not enter dist-upgrade, unless you do want to upgrade to Feisty.  If you really must keep Dapper, do not type that.

---

### Post by B-777 on 2007-07-07
> **overdrank said:**
>  
command in terminal then followed by upgrade and then dist-upgrade and hope this works.

Can you give me these commands please, I am still new to ubuntu and am learning them :oops:

---

### Post by B-777 on 2007-07-07
> **forrestcupp said:**
> You did remember to click "Reload" right?

It's too bad you can't upgrade to Feisty.  It's really pretty stable, and all of this is automated in Feisty.  All you have to do is open a media file, and if you don't have the codecs, it will install it automatically if you choose.

Edit:

Do not enter dist-upgrade, unless you do want to upgrade to Feisty.  If you really must keep Dapper, do not type that.

Actually I do want to upgrade to Feisty without having to deal with the hassle of an install CD (Having a problem with the Feisty ISO I burned to disc where the live session is trying to boot from the a: drive instead of the CD, Wanted to see what Ubuntu looked like so I downloaded Dapper and installed it and now I am liking it :D).

---

### Post by overdrank on 2007-07-07
> **B-777 said:**
> Can you give me these commands please, I am still new to ubuntu and am learning them :oops:

Yes 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by B-777 on 2007-07-07
> **overdrank said:**
> Yes 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

When I type:

```
sudo apt-get upgrade
```

It still returns the error:
```
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not configured yet.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-sax-expat-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And yes I did go back and edit the file that I listed earlier and this error still coming up.

It looks like the packages above need to be configured for use, but I am not sure how to do this.

---

### Post by overdrank on 2007-07-07
Hi and there is no need for a reinstall, It has been awhile since I did the codecs with that how to. SO I am going off memory and I believe I had to also use this link provided in that how to
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
And that did the trick for me but I can't remember exactly the way I did solve the problem, If I can find out I will post back.

---

