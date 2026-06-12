---
title: "Enable Multiverse Repositories"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by GLSmyth on 2007-07-01
Quote:
Originally Posted by p_quarles View Post
cogadh's solution will definitely work.

If you want to install JRE (and much more!) from synaptic, though, you need to go to System >> Administration >> Software Sources and enable the multiverse repositories.
When I go there I do not see an option titled, "Enable Multiverse Repositories." Is it labeled something different or should I be looking elsewhere?

Cheers -

george

---

### Post by wolfen69 on 2007-07-01
open:   synaptic/settings/repositories

---

### Post by xpod on 2007-07-01
[ATTACH]37036[/ATTACH]

It should be there right above the "source code";)

---

### Post by Bothered on 2007-07-01
It's the fourth checkbox down

---

### Post by GLSmyth on 2007-07-04
> **xpod said:**
> [ATTACH]37036[/ATTACH]

It should be there right above the "source code";)

Above "Source Code" I have "Proprietary devices for devices (restricted)," which is the fourth option.  I am using Ubuntu 6.10.

Cheers -

george

---

### Post by lbelloq on 2007-07-04
If you're using Feisty *universe* and *multiverse* are enabled by default. IIRC.

---

### Post by GLSmyth on 2007-07-04
> **lbelloq said:**
> If you're using Feisty *universe* and *multiverse* are enabled by default. IIRC.

I am told that the package I need to find to install Java is j2re1.4.  I don't see that when I enter "Java" in Synaptic.  If this is not an issue where I need to enable another repository then would you know if it's called something different (or if I should be seeing a different option)?

Cheers -

george

---

### Post by Nythain on 2007-07-04
not sure if j2re is the same as java2-runtime, but it sounds like it... try searching for/installing that instead

---

### Post by GLSmyth on 2007-07-04
> **Nythain said:**
> not sure if j2re is the same as java2-runtime, but it sounds like it... try searching for/installing that instead

In searching for "java2-runtime" the only thing found is openoffice.org, which is installed.

Cheers -

george

---

### Post by Nythain on 2007-07-04
paste the contents of your /etc/apt/sources.list file and we'll see whats goin on

---

### Post by GLSmyth on 2007-07-04
> **Nythain said:**
> paste the contents of your /etc/apt/sources.list file and we'll see whats goin on

Here is the contents of that file:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Cheers -

george

---

### Post by lbelloq on 2007-07-04
Might be a better option to use Automatix. I used it to install Java+Azureus and worked flawlessly.

---

### Post by GLSmyth on 2007-07-04
> **lbelloq said:**
> Might be a better option to use Automatix. I used it to install Java+Azureus and worked flawlessly.

Someone else recommended that so I installed Automatix.  When I select it nothing happens, so I'm not sure what I am supposed to do.

Cheers -

george

---

### Post by Bothered on 2007-07-04
I recommend that you edit your /etc/apt/sources.list to (make a backup first, "sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak"):

[I]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse[/I]

That will enable universe and multiverse for all updates except backports and proposed. Then launch synaptic and reload.

I think the package you're looking for is sun-java6-jre. Automatix shouldn't be needed to install the java runtime or azureus.

EDIT: You probably also want sun-java6-plugin.

---

