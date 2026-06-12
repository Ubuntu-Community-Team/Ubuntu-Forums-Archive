---
title: "Automatix says it for 6.10, but I used the correct file"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by dacookiemonn on 2007-06-02
I installed the [COLOR="SeaGreen"]automatix2_1.1-4.5-7.04feisty_i386.deb[/COLOR] file and got it to work.  After rebooting, i run it and it says " This version of Automatix is for ubuntu 6.10 only.
Like I said though, its the right package and was working before I rebooted.
Any suggestions.
Thanks in advance

---

### Post by blue_shift on 2007-06-02
Where did you get the file from? Official source?

How did you install feisty? Plain install/upgrade?

---

### Post by dacookiemonn on 2007-06-02
ya, i got it right from the source and did a full install of feisty.  I goes to the splash and i see it shows at the bottom of the automatx spash "Found 7.04",then the message comes up.
How do i uninstall it, ill just re-install it

---

### Post by blue_shift on 2007-06-02
```
sudo apt-get remove package
```

Assuming you installed:
```
sudo apt-get install package
```

---

### Post by STREETURCHINE on 2007-06-02
please post the out put from 

```
cat /etc/apt/sources.list
```

and we will check what is happening..

---

### Post by dacookiemonn on 2007-06-02
ok, sorry, i got it this way [COLOR="Blue"]wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)[/COLOR]
Dont know how to undo it

---

### Post by dacookiemonn on 2007-06-02
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
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by STREETURCHINE on 2007-06-02
> **dacookiemonn said:**
> ok, sorry, i got it this way [COLOR="Blue"]wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)[/COLOR]
Dont know how to undo it


First Step:

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list

Second Step:

 wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

Third Step:

 gpg --import automatix2.key

Fourth Step:

gpg --export --armor E23C5FC3 | sudo apt-key add -

Fifth Step:

 sudo apt-get update

---

### Post by dacookiemonn on 2007-06-02
Thanks, i did notice that it was the other version, not the feisty after looking through the text.
I did all your steps and the 6.10 error still comes in

---

### Post by STREETURCHINE on 2007-06-02
yep ok go to the automatix site ,there is a link in my signature and ask arnieboy he will sort it out in a jiffy for you.

but i think you may just have to make it look like this.

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

so i would just put the hash in front and try again.

---

### Post by dacookiemonn on 2007-06-02
thanks, i think i figured it out though.
i did install the edgy version on accident, and had to uninstall it first then I ran your steps to get it working, waiting on it right now

---

### Post by arnieboy on 2007-06-02
> **dacookiemonn said:**
> thanks, i think i figured it out though.
i did install the edgy version on accident, and had to uninstall it first then I ran your steps to get it working, waiting on it right now

you need to delete the following line from your /etc/apt/sources.list
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

and then save and close the file and do a :
```
sudo apt-get update
```
unless you do that, you will keep getting edgy updates.. and yes, please post in the automatix forums in future for quicker and more correct responses.

---

