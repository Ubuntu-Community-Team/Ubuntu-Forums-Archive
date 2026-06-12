---
title: "[SOLVED] compile problems, unresolvable dependencies.."
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-09-29
well ive tried to install g++ however!

it says that i cannot install g++ because 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++: Depends: g++-4.1 (>= 4.1.2) but it is not going to be installed
E: Broken packages

so i tried g++-4.1.. and i got this:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++-4.1: Depends: libstdc++6-4.1-dev (= 4.1.2-0ubuntu4) but it is not going to be installed
E: Broken packages

ok, no problem right? so ill just install libstdc++6-4.1-dev! but i get this:

The following packages have unmet dependencies:
  libstdc++6-4.1-dev: Depends: libc6-dev (>= 2.3.6-7) but it is not going to be installed

ok ok, cool cool, ill just dl libc6-dev right? WRONG, i get this:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.6.1-1ubuntu7 is to be installed
E: Broken packages

... ok i try libc6 now.... and i get this:

Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

WTF?

someone please help this is not fun anymore :S

ive tried to install both by way of synaptic and the cli, but getting same results :S

im using fiesty with kernel 2.6.22, fully updated.. apparently lol
and heres my sources list too:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties

---

### Post by dynamethod on 2007-09-29
please help me :S

---

### Post by Steveway on 2007-09-29
Don't bumb your thread every few minutes!
sudo apt-get install build-essentials

---

### Post by dynamethod on 2007-09-29
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

---

### Post by Steveway on 2007-09-29
Oh, now I see what's wrong.
Your missing some entrys in your sources.list.
I can't give you the missing ones cause I use Gutsy and not Feisty but I'm sure someone here will give you his.

---

### Post by Perfect Storm on 2007-09-29
```
cat /etc/apt/sources.list
```

Please, post the output.

---

### Post by dynamethod on 2007-09-29
i just used sudo aptitude install build-essential

turns out linux-headers-2.6.22-12-generic does not go down too well lol

just downgrading now,

btw the my sources list are at the bottom of my first post

---

