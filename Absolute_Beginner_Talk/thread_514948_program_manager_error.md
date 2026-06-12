---
title: "program manager error"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by reecedeg on 2007-08-01
I get this error message when I try to run Package manager. I need help to solve this problem. Thanks Reece

E:Malformed line 44 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read

---

### Post by afterwego on 2007-08-01
It sounds like line 44 in your sources files is not correct, so it is stopping the whole show with that error. Could you post your /etc/apt/sources.lit file, so we can see what you have there?

---

### Post by reecedeg on 2007-08-01
don't know how to find this file, thanks for your help

---

### Post by forestpixie on 2007-08-01
open a terminal - accessories terminal

when it opens type

```
 gedit /etc/apt/sources.list
```

a text editor will open, copy the text and post it in your thread

Edit - to get it in a code box - make sure you use "post reply" , rather than quick reply and after highlighting text you want in code box click the # icon just above where you enter text

---

### Post by reecedeg on 2007-08-01
I feel really lost now. Have I got this right? Thanks for the help.


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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

---

### Post by forestpixie on 2007-08-02
It seemes to be the lat two google lines. I've looked at the google pages for their repos and I can't get them to update either.

It could be that someone else has had the same problem - I would suggest searching the forum for a more specific 'google' problem.

In the meantime we can remove the lines so you can use apt-get.

In terminal

```
sudo cp /etc/apt/sources.list /etc/apt/sources.bak.0208
```

then 

```
gksudo gedit /etc/apt/sources.list
```

which will open in a text editor, go to the last two lines and put # in fron of them.

Then to update your sources

```
sudo apt-get update
```

Edit - what is it that you're trying to install - why do you need the repos?

---

### Post by RomeReactor on 2007-08-02
Hi. The error comes from having an error in the penultimate entry in the source.list file:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
**deb [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-free**
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

Notice that the last line is correct according to [Picasa's FAQ page]("http://picasa.google.com/linux/faq.html#5b"); just comment that line, so it looks like this:
```
#deb http://dl.google.com/linux/deb/stable non-free
```
or delete it, as you only need the last one (the previous one is a malformed duplicate. Save the file, close Gedit, and press the **Reload ** in Synaptic, or update the repositories from the command line, as **forestpixie** said.

---

### Post by forestpixie on 2007-08-02
I knew it was line 44 - but I've only just crawled out of bed and can't see the wood for the tress - thanks RomeReactor:)

---

### Post by RomeReactor on 2007-08-02
No problem. You're the one that told him how to fix it; I just added a few comments ;)

---

### Post by reecedeg on 2007-08-02
Thanks to you all very much. My program manager and everything else is working fine. I  would never have made w/o the wonderful step by step instructions. That was great. I love working w/ this I just need a lot of help. It is so easy to get that w/ people like you. Thanks!--Reece

---

