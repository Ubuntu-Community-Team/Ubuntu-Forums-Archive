---
title: "Can't install cinelerra"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Pttyboy 92 on 2007-08-25
i can't install cinelerra although i did everything i was supposed to do, install the 64-bit FEISTY repositories and enabled the restricted, universe, and multiverse repositories. did the apt-get update right after adding the repositories , and then i did the last step and...E: Couldn't find package cinelerra
WTF:confused:
and here's the website:[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by Majorix on 2007-08-25
Search synaptic for cinelerra. I don't think the package is called exactly "cinelerra".

---

### Post by pizzutz on 2007-08-25
what does your /etc/apt/sources.list look like ?

---

### Post by Pttyboy 92 on 2007-08-25
> **pizzutz said:**
> what does your /etc/apt/sources.list look like ?
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
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

---

### Post by Majorix on 2007-08-25
Your sources.list has the repo listed. Did you try my reply?

---

### Post by Pttyboy 92 on 2007-08-25
> **Majorix said:**
> Your sources.list has the repo listed. Did you try my reply?
couldn't find anything

---

### Post by jordanmthomas on 2007-08-25
I searched for cinelerra ubuntu and this came up.  Maybe give it a quick try?

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

**edit** woops, you already have it

Have you tried a ```
sudo apt-get update
``` and then an
```
apt-cache search cinelerra
```?

**edit2** the packages is called cinelerra

---

### Post by Pttyboy 92 on 2007-08-25
> **jordanmthomas said:**
> I searched for cinelerra ubuntu and this came up.  Maybe give it a quick try?

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)
lol that's the one i did pretty much

---

### Post by pizzutz on 2007-08-25
hmm.. I did it with no problem. your sources list looks right. As long as you did the sudo apt-get update  and sudo apt-get install cinelerra you should be good to go.  I'm missing something.....

does 

```

sudo apt-get update | grep kiberpipa

```

give you output?

---

### Post by jordanmthomas on 2007-08-25
but the question remains...have you done a
```
sudo apt-get update
```

---

### Post by Pttyboy 92 on 2007-08-25
> **jordanmthomas said:**
> I searched for cinelerra ubuntu and this came up.  Maybe give it a quick try?

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

**edit** woops, you already have it

Have you tried a ```
sudo apt-get update
``` and then an
```
apt-cache search cinelerra
```?

**edit2** the packages is called cinelerra
nothing happened

---

### Post by Pttyboy 92 on 2007-08-25
i've tried everything on here, there must be something wrong

---

### Post by Pttyboy 92 on 2007-08-25
> **pizzutz said:**
> hmm.. I did it with no problem. your sources list looks right. As long as you did the sudo apt-get update  and sudo apt-get install cinerella you should be good to go.  I'm missing something.....

does 

```

sudo apt-get update | grep kiberpipa

```

give you output?
it got ouput, but still no cinelerra, what does that command do anyway

---

### Post by pizzutz on 2007-08-25
It tells me whether or not apt-get update is hitting that repo. if you got 4-5 lines of output saying that it hit that repo, then we know it did.  if it gave no output, then we would have the problem narrowed down to the update ( | grep <search term> just filters the output from whatever command you give it.. in this case I was only interested in the lines of output refering to the kiberpipa repo)

I'm sorry for this, but I have to ask; I am running out of ideas. You aren't capatilizing  the c in cinelerra are you? Cinelerra and cinelerra would be 2 different packages.

edit: package is cinelerra

---

### Post by Pttyboy 92 on 2007-08-25
> **pizzutz said:**
> It tells me whether or not apt-get update is hitting that repo. if you got 4-5 lines of output saying that it hit that repo, then we know it did.  if it gave no output, then we would have the problem narrowed down to the update ( | grep <search term> just filters the output from whatever command you give it.. in this case I was only interested in the lines of output refering to the kiberpipa repo)

I'm sorry for this, but I have to ask; I am running out of ideas. You aren't capatilizing  the c in cinerella are you? Cinerella and cinerella would be 2 different packages.
no, im not

---

### Post by pizzutz on 2007-08-25
Then I have no idea.  I added the repo, and 

sudo apt-get install -s cinelerra 

worked fine for me to simulate the download. it would have installed it if I took out the -s.  It had no problems finding it.  Something else must be wrong on your end, but I have no idea what it could be.

---

### Post by bac on 2007-09-26
I also did apt-cache search cinelerra
the only message is 
xmovie - a nice video player for uncompressed Quicktime, MPEG streams and more

---

### Post by Amazona aestiva on 2007-09-26
See the third link in my signature.

---

### Post by diskotek on 2007-10-31
i had the exactly same problem with "bac"..
but amazona aestiva's mini tutorial worked great. thanks...

---

