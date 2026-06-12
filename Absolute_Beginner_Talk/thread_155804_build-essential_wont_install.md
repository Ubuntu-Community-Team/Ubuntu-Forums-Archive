---
title: "build-essential wont install"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-04-05
I've tried sudo apt-get install build-essential and it says

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev


So I researched the forums and tried:

sudo apt-get install libc6 libc6-dev build-essential

which says:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.5-1ubuntu12.5.10.1 is to be installed

](*,) 

I even tried su root to bypass sudo but same errors.

I like to think I know what I am doing and am no longer a beginner but I am stumped.  Any help? Thanks in advance!

---

### Post by dcstar on 2006-04-05
[QUOTE=GaFFy]I've tried sudo apt-get install build-essential and it says

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev


So I researched the forums and tried:

sudo apt-get install libc6 libc6-dev build-essential

which says:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.5-1ubuntu12.5.10.1 is to be installed

](*,) 

I even tried su root to bypass sudo but same errors.

I like to think I know what I am doing and am no longer a beginner but I am stumped.  Any help? Thanks in advance![/QUOTE]
Most likely you have mis-matched repositories in your system.

Post your /etc/apt/sources.list contents here and one of the gurus may be able to spot the problem.

---

### Post by GaFFy on 2006-04-05
here is my sources.list:

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by GaFFy on 2006-04-05
Duh reading my own post gave me the answer, hoary got into my sources.list.
That pesky hoary!  I must have copy/pasted a hoary list.

Thanks for the help its all set now, I knew I was missing something simple!

;)

---

### Post by dcstar on 2006-04-06
[QUOTE=GaFFy]Duh reading my own post gave me the answer, hoary got into my sources.list.
That pesky hoary!  I must have copy/pasted a hoary list.

Thanks for the help its all set now, I knew I was missing something simple!

;)[/QUOTE]
See, I told you a guru would spot the problem......                    8)

---

