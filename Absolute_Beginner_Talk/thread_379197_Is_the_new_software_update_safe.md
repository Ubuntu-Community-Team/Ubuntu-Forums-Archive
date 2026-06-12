---
title: "Is the new software update safe?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-03-08
When I clicked on the new software update i got this. 

[IMG]http://i18.tinypic.com/2m6o6lt.png[/IMG]

---

### Post by STREETURCHINE on 2007-03-08
i think you will find they are ok,

---

### Post by Paul41 on 2007-03-08
I get this message when I have WINE updates. I have never worried about it and have never had any problems.

---

### Post by Repent on 2007-03-08
Ok, so I installed the new update and now I no longer have sound. I checked all my sound setting and they all look ok, now what?

---

### Post by oldone on 2007-03-08
Now you REPENT!

---

### Post by dannyboy79 on 2007-03-08
follow the comprehensive sound guide thread within this forum. it will help you troubleshoot the issue OR you could try to undo your updates?

---

### Post by Repent on 2007-03-09
Now I try to print and my printers not working this is not good, I use TurboPrint what can I do now?

---

### Post by Repent on 2007-03-09
Come on guys, no one can help me?

---

### Post by Paul41 on 2007-03-09
> **Repent said:**
> Come on guys, no one can help me?

You could try to do what dannyboy79 and undo your updates.

---

### Post by PriceChild on 2007-03-09
You have added 3rd party unsupported repositories. You do not have the key to authenticate their downloads.

This is why its telling you they're unauthenticated.

Pricey

---

### Post by doubtful wisdom on 2007-03-09
The sound problem is probably in configuration.  After an update at least one of my channels was turned off (can't remember whether more were or not), but turning the channel on restored sound.  It is the PCM control that must be on.  Right click on speaker symbol, open volume control then take care of problem.

The printer problem is another update issue.  My Epson USB connected CX6600 no longer is recognized.  I found that a bug report has been filed and verified.  Don't know when it will be fixed, nor how to apply the work around that was posted.

---

### Post by Repent on 2007-03-09
So PriceChild should I not have downloaded the update, And if not why was 3rd party unsupported repositories in a update?

---

### Post by PriceChild on 2007-03-09
> **Repent said:**
> So PriceChild should I not have downloaded the update, And if not why was 3rd party unsupported repositories in a update?The 3rd party repository YOU added put updates on its repository. This isn't ubuntu's fault.

---

### Post by Cariboo1938 on 2007-03-09
> **PriceChild said:**
> The 3rd party repository YOU added put updates on its repository. This isn't ubuntu's fault.
**So it is a question of a 'safe' sources.list, right?**

---

### Post by undertakingyou on 2007-03-09
I am having the same turboprint problems.  My only question is how does one undo the updates?  Also, doubtful wisdom, what is the bug report number. I'd really like to look at that.  Thanks.

---

### Post by Repent on 2007-03-09
I see..how can I remove them, and thanks for your help I do truly appreciate it.

---

### Post by doubtful wisdom on 2007-03-09
The USB printer bug report (high)  Bug #90724:.  There is a new workaround that I will try in a moment.  I may have to re-install my printer.  Still believe that problems experienced by initiator of the thread were caused by the updates with the sound issue rather benign, but the printer is another thing altogether.

---

### Post by picpak on 2007-03-09
> **Repent said:**
> I see..how can I remove them, and thanks for your help I do truly appreciate it.

Can you please post the contents of your /etc/apt/sources.list?

---

### Post by Repent on 2007-03-09
Is this what you needed? 


joe203@joe203-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:5389): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
joe203@joe203-desktop:~$ 




## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by Repent on 2007-03-09
> The USB printer bug report (high) Bug #90724:. There is a new workaround that I will try in a moment.

Where is the workaround?

---

### Post by picpak on 2007-03-10
> **Repent said:**
> Is this what you needed? 


joe203@joe203-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:5389): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
joe203@joe203-desktop:~$ 




## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

That's weird, besides Automatix and the Google repo there are no third-party repos to speak of. Which programs did you update?

---

### Post by Repent on 2007-03-10
You know I'm not sure, I should have taken a snapshot of it but I wasn't thinking at the time. But from the response I got here I thought it would be OK.

---

### Post by PriceChild on 2007-03-10
> **picpak said:**
> That's weird, besides Automatix and the Google repo there are no third-party repos to speak of. Which programs did you update?You never know... those might be the 3rd party repos?

---

### Post by picpak on 2007-03-10
> **PriceChild said:**
> You never know... those might be the 3rd party repos?

I went to the Google repo and it says...not found?

I know automatix updated today but, how would that break his sound and his printers?

If you don't know which programs you upgraded, open Synaptic, go to File > History, and go to the day you upgraded. It should list the upgraded packages.

---

### Post by Repent on 2007-03-10
OK thanks this is what I downloaded on the 8th the day I made this post, the printer problem is a usb problem.

Commit Log for Thu Mar  8 08:18:03 2007


Upgraded the following packages:
gnupg (1.4.3-2ubuntu3.2) to 1.4.3-2ubuntu3.3
k9copy (1.1.0~beta1-0ubuntu2) to 1.1.0~beta2-0ubuntu1~edgy1
libapache2-mod-php5 (5.1.6-1ubuntu2.2) to 5.1.6-1ubuntu2.3
libgphoto2-2 (2.2.1-2ubuntu4) to 2.3.0-0ubuntu3~edgy1
libgphoto2-2-dev (2.2.1-2ubuntu4) to 2.3.0-0ubuntu3~edgy1
libgphoto2-port0 (2.2.1-2ubuntu4) to 2.3.0-0ubuntu3~edgy1
php5-common (5.1.6-1ubuntu2.2) to 5.1.6-1ubuntu2.3
tzdata (2006p-0ubuntu6.10) to 2007b-0ubuntu0.6.10

Installed the following packages:
libusb-dev (2:0.1.12-2)

---

### Post by Repent on 2007-03-10
Bump.

---

### Post by Repent on 2007-03-10
I'm going to Bump this until I get this problem fixed, sorry if this upsets you! :popcorn:

---

### Post by Repent on 2007-03-10
> The USB printer bug report (high) Bug #90724:. There is a new workaround that I will try in a moment.


Where is the workaround?


this is what I downloaded on the 8th the day I made this post, the printer problem is a usb problem.


Commit Log for Thu Mar 8 08:18:03 2007


Upgraded the following packages:
gnupg (1.4.3-2ubuntu3.2) to 1.4.3-2ubuntu3.3
k9copy (1.1.0~beta1-0ubuntu2) to 1.1.0~beta2-0ubuntu1~edgy1
libapache2-mod-php5 (5.1.6-1ubuntu2.2) to 5.1.6-1ubuntu2.3
libgphoto2-2 (2.2.1-2ubuntu4) to 2.3.0-0ubuntu3~edgy1
libgphoto2-2-dev (2.2.1-2ubuntu4) to 2.3.0-0ubuntu3~edgy1
libgphoto2-port0 (2.2.1-2ubuntu4) to 2.3.0-0ubuntu3~edgy1
php5-common (5.1.6-1ubuntu2.2) to 5.1.6-1ubuntu2.3
tzdata (2006p-0ubuntu6.10) to 2007b-0ubuntu0.6.10

Installed the following packages:
libusb-dev (2:0.1.12-2)

Someone please help I need my printer.

---

### Post by Repent on 2007-03-10
Bump.

---

### Post by Repent on 2007-03-10
Come on guys!

---

### Post by undertakingyou on 2007-03-11
Repent,

The problem seems to be in the libgphoto package.  This isn't anything to do with your having 3rd party repos.  There is an updated libgphoto package, your should run update again, install that, and everything should work.

For future information, bug reports are found on [www.launchpad.net](www.launchpad.net).  A quick search there can lead you straight to already reported bugs, and you can submit bugs if they haven't already been done.

---

