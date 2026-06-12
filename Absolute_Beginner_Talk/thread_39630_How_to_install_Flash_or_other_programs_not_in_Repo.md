---
title: "How to install Flash or other programs not in Repository?"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by meat on 2005-06-05
First, I read this link [how to install flash](http://ubuntuguide.org/#flash-mozilla) 

And I got a message saying can't find package.  I then used this link[How to install other repositories](http://ubuntuguide.org/#extrarepositories) 

But it still didn't work.  What did I do wrong and what do I do if other packages aren't found?

---

### Post by pdk001 on 2005-06-05
read here [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
it will be help you out

---

### Post by meat on 2005-06-05
I did that and I said I did that in my original post and it did not work  :)

---

### Post by Gtaylor on 2005-06-05
Can you please be more descriptive with the "did not work" part? Please copy and paste exactly what you're typing and exactly what's coming back out.

---

### Post by meat on 2005-06-05
```
root@ubuntu:/home/eric # sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
``` 

I also looked in the package manager and flashplayer-mozilla is not there.  I took out the remarks on my source file, so that I could get more repositories.

---

### Post by meat on 2005-06-05
Here is my sources.list file

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src ftp://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by Gtaylor on 2005-06-05
Do a:

sudo apt-get update

Before you do:

sudo apt-get install flashplayer-mozilla

It looks like you have the right repositories.

---

### Post by meat on 2005-06-05
Hmmm, Yeah I did that also, but still no luck.

---

### Post by Gtaylor on 2005-06-05
I'm not sure but you shouldn't be sudo'ing if you're logged in as root. I doubt that'll fix it but maybe try that.

---

### Post by jjross on 2005-06-06
I use the Synaptic package manager, system/administration/synaptic package manager, i checked mine and it is listed there and i have the same repositories that you do,it was listed as flashplayer-mozilla,
                      good luck

---

### Post by meat on 2005-06-06
Thanks for your help guys.  I did everything correctly, but for some reason my package manager will not display flashplayer-mozilla.

---

### Post by poofyhairguy on 2005-06-06
[QUOTE=meat]Thanks for your help guys.  I did everything correctly, but for some reason my package manager will not display flashplayer-mozilla.[/QUOTE]

I know whats up. you need the multiverse. Add this line:

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by meat on 2005-06-06
You were right that worked.  Thanks Poofy!

---

