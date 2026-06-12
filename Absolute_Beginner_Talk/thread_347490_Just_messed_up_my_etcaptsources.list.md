---
title: "Just messed up my /etc/apt/sources.list"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-01-27
Trying to load automatix and I now get the error message when I select applications > add/remove

[COLOR="Blue"]Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.[/COLOR]

This is my file now.

[COLOR="Blue"]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2



deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main[/COLOR]

Can anyone help me from my 2 left feet please ??:cry:

---

### Post by Tomosaur on 2007-01-27
Snip these lines out of the file:
```

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

```

Then run:
```

sudo aptitude install -f
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by jvc26 on 2007-01-27
Remove the lines:
```

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

```
Then type:
```

sudo aptitude install -f
sudo aptitude update
sudo aptitude upgrade

```
If it complains about the automatix repo, run each of these lines one by one:
```

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update

```
That should sort you out,
Il


EDIT:: Sorry tomosaur, took me ages to reply and hadnt seen your post!

---

### Post by Tomosaur on 2007-01-27
> **Illuvator said:**
> 
EDIT:: Sorry tomosaur, took me ages to reply and hadnt seen your post!

Two heads are better than one :D

---

### Post by bugster on 2007-01-27
Thanks both - I really don't deserve help after being so  dumb.  :oops:

---

### Post by bugster on 2007-01-27
Thanks again both - it now works fine again - sighs of relief :D .

As the dust settles I'm wondering does this mean I now have automatix?

---

### Post by taurus on 2007-01-27
> **bugster said:**
> 
As the dust settles I'm wondering does this mean I now have automatix?

Look in Applications -> System Tools.

---

### Post by bugster on 2007-01-27
Thanks Taurus - seems not - so I'll try again.  I have kept a back up of sources.list this time  :-\"

---

### Post by taurus on 2007-01-27
Did you do

```
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by bugster on 2007-01-27
> **taurus said:**
> Did you do

```
sudo aptitude update
sudo aptitude install automatix2
```

No but I have now and all seems perfect.  Thanks again for your help and patience.):P

---

### Post by boulderjosh on 2007-02-27
I just migrated from Windows and just had the same problem.  I don't know how to "snip" the bad code out.  Any help??

---

### Post by taurus on 2007-02-27
> **boulderjosh said:**
> I just migrated from Windows and just had the same problem.  I don't know how to "snip" the bad code out.  Any help??

Applications -> Accessories -> Terminal
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```

---

### Post by boulderjosh on 2007-02-27
Thank you Taurus/ 
What exactly did I just do, though?

---

