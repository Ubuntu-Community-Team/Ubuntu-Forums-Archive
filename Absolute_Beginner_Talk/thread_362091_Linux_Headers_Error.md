---
title: "Linux Headers Error"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-15
Hmmm well what to say, i tried to install Linux Headers and here is what i got:

```

shoaibi@saber-rider:~$ sudo apt-get install linux-headers- `uname -r`
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package 2.6.17-10-generic

```

also please tell me that what this command actually do, i understand the wget part but what's after the pipe sign and -o means extra option to wget with? isn't it?
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```

---

### Post by halfvolle melk on 2007-02-15
There's a space between headers- and `uname -r`. Also, what does your /etc/apt/sources.list look like?

---

### Post by igknighted on 2007-02-15
Can't help you with the first part, perhaps try grabbing the package through synaptic instead.  As for the second part, what you are doing is importing the security key of that repository.  The key validates the packages inside, like a signature, so you know that only the packages with that signature are valid.  If a non-legitimate package were to end up in the repo it wouldn't have the proper signature, hence why you import it so Ubuntu knows what to check for.

---

### Post by highneko on 2007-02-15
You have some whitespace in there. Copy and paste this:
sudo apt-get install linux-headers-$(uname -r)

---

### Post by shoaibi on 2007-02-15
@half volle melk:
there was space in what i typed :(, 
and here is the Source.list:

```

shoaibi@saber-rider:~$ cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```


@igknighted:
Thanks buddy.

@highneko:
Thanks, and what about:
sudo apt-get install linux-headers-`uname -r`

won't it be the same?

---

### Post by halfvolle melk on 2007-02-15
> **shoaibi said:**
> @half volle melk:
there was space in what i typed :(, 
Yes, and it shouldn't be there.

---

### Post by anchor on 2007-02-15
> **highneko said:**
> You have some whitespace in there. Copy and paste this:
sudo apt-get install linux-headers-$(uname -r)

Was having the same problem, this fixed it right up.  

Thank you so much! :)

---

