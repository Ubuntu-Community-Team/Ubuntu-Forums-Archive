---
title: "[SOLVED] Why are certain Options in the update manager grayed out??"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-24
Hi I do not understand this picture:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-UpdateManager.png[/IMG]

Is this bad? Can I change that? Am I missing something? Why can I not get ffpeg etc... ?

explicatate me :P :),
sv

---

### Post by p_quarles on 2007-09-24
Generally that's because those packages conflict with something you already have installed on the system. To find out exactly what is conflicting, you can open Synaptic (in the System >> Admin menu) and run a search for those packages. If you try to mark them for installation, it will tell you would have to remove before doing so.

---

### Post by ThrobbingBrain66 on 2007-09-24
To add to p_quarles advice.  Don't just do what Synaptic suggests (removing packages, etc) because sometimes it can be a little over-zealous.  The greyed-out packages can also mean that some dependencies to those packages haven't reached your mirror yet.  Fixing that is as simple as giving the updates a few hours to a day to propagate throughout all the mirrors.

EDIT: Do you have any 3rd-party repositories that could be pushing those updates through?  If so, your problem probably is as p_quarles suggested.

---

### Post by p_quarles on 2007-09-24
> **ThrobbingBrain66 said:**
> To add to p_quarles advice.  Don't just do what Synaptic suggests (removing packages, etc) because sometimes it can be a little over-zealous.  The greyed-out packages can also mean that some dependencies to those packages haven't reached your mirror yet.  Fixing that is as simple as giving the updates a few hours to a day to propagate throughout all the mirrors.

EDIT: Do you have any 3rd-party repositories that could be pushing those updates through?  If so, your problem probably is as p_quarles suggested.
Yeah, thanks for clarifying that. I didn't mean to suggest that those packages should actually be uninstalled, just to use Synaptic to find out what they were. 

If you specifically need those packages for some reason, then you can experiment, but the simple fact that they are greyed out is not reason for concern.

---

### Post by staticvoid on 2007-09-25
Ok,
thanks guys. I might need them, and if I do I'll use synaptic, a couple of times synaptic has said "cannot install, the following packages will not be installed" or something along those lines. probably because of confliction :P. 

About the extra repositories: I've been messing with my sources a ton and that might be the mess up. here is my source list:

```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted multiverse universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) feisty thunderbird
# pidgin repos START


deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main
```

I do not need half that stuff. e.g. I do not have scrrenlets ;).  Wow, off topic on my own thread but: What do you guys recomend for sources to add? I do not even need trennos... I removed compiz :P.

thanks again... I'll try looking things up in synaptic

---

### Post by ThrobbingBrain66 on 2007-09-25
I've done some research, and this is what I've come up with.  Those updates are being pushed through by the debian-multimedia.org repo.  Basically what's happening is that the version numbers of those packages don't match up with the dependencies' version numbers, therefore update-manager won't let the updates through.

Remove any and and all repos you don't use.
-screenlets repo
-debian multimedia repo
-you can keep the thunderbird repo if you need it.
-you may as well get rid of the leftover comments from the pidgin and automatix repo as well.

After you do that, and then 'sudo apt-get update && sudo apt-get upgrade' those troublesome updates will go away.  If you don't need any third-party repos, don't use them.  The one I would suggest however is Seveas' repos.  He has lots of multimedia related packages.  Take a look here:
[http://seveas.theplayboymansion.net/seveas/dists/feisty-seveas/all/](http://seveas.theplayboymansion.net/seveas/dists/feisty-seveas/all/)

---

### Post by staticvoid on 2007-09-25
Thank you for doing that research! :D I will remove the packages I do not need. I need to do some house cleaning anyway :P....

sv

EDIT: Yay :D it worked. I do not have grayed out options. But I could not get Seveas repos to work, could not get the dpg key or something/.. I'll try it again...

ok... it says this:

> W: GPG error: [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) feisty-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

:( so what should I do? I looked through his list and Lives looked perty cool... I'm looking for a video editor for vlogging. something like windows movie maker (splicing, effects, video layers would be nice :D)


ok.... SORRY now for the THIRD edit :P I did this:

wget [http://seveas.theplayboymansion.net/seveas/1135D466.gpg](http://seveas.theplayboymansion.net/seveas/1135D466.gpg) -O- | sudo apt-key add -

and it worked... silly me..............

---

### Post by ThrobbingBrain66 on 2007-09-25
Glad you got it all sorted out.

---

### Post by staticvoid on 2007-09-25
I hope it's not only beneficial for me :)

---

### Post by mysticmatrix on 2007-09-25
> **staticvoid said:**
> I hope it's not only beneficial for me :)

Mark thread as solves so that others might benefit too. :)

---

### Post by staticvoid on 2007-09-25
Thanks for reminding me :D.

done

---

### Post by mattismyname on 2008-01-17
Thanks

---

