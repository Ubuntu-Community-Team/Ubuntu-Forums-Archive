---
title: "System Setup password problem, MAKE problem"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by fallintosanity on 2007-09-11
I recently installed Ubuntu Dapper Drake, and have had nothing but problems since. I'm using an HP laptop, AMD Athlon for XP, with a wired Internet connection. 

First: 

My MAKE command is missing. I tried to install Build-Essential, and got a series of dependency errors:
________________
root# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but it is not installable
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed                   Depends: make but it is not installable
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages
________________

I get similar errors when I try to install MAKE on its own. Attempting to install any variation of libc results in Synaptic freezing. I tried directing my apt-get to an Ubuntu install CD, but that didn't work, either (same dependencies result). The result of all this is that I can't install programs, can't update properly, can't upgrade, and basically can't do much of anything. 

So I tried to reinstall Ubuntu, Feisty Fawn edition this time. Now, I have one of the annoying HP laptops that won't boot to CD, so I have to use a convoluted USB-floppy workaround. But to do this, I need to be able to get into my System Setup at startup -- and a password has mysteriously appeared on my System Startup. It's not my user password, not my root password, not "default," "admin," "password," or any other obvious default passwords (yes, I tried upper- and lower-case variants). I can't for the life of me figure out how this password got on there, what it is, or how to get rid of it so that I can fix my system. 

Please help! I'm beginning to hate Ubuntu, and I don't want to hate it solely on the basis of a terrible, unfixable installation.

---

### Post by lisati on 2007-09-11
Do you get similar results when you use aptitude instead of apt-get?

---

### Post by zipperback on 2007-09-11
> **fallintosanity said:**
> But to do this, I need to be able to get into my System Setup at startup -- and a password has mysteriously appeared on my System Startup. It's not my user password, not my root password, not "default," "admin," "password," or any other obvious default passwords (yes, I tried upper- and lower-case variants). I can't for the life of me figure out how this password got on there, what it is, or how to get rid of it so that I can fix my system. 

Please help! I'm beginning to hate Ubuntu, and I don't want to hate it solely on the basis of a terrible, unfixable installation.


You should be able to reset your root password providing of course that you have a user account in the SUDOERS access informatgion.

Just enter: sudo passwd root

Then changed your password.

However, if you think it just magically changed and things on your system are acting different than normal, I would suggest that you download the current version of ubuntu and then do a clean install with it.

- zipperback
:guitar:

---

### Post by fallintosanity on 2007-09-11
I'm not actually sure what happens when I use aptitude instead of apt-get. It doesn't give me the dependency errors, but it doesn't appear to actually install anything, either:
____________

root# sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
The following NEW packages will be automatically installed:
  binutils gcc272 linux-libc-dev
The following NEW packages will be installed:
  binutils gcc272 linux-libc-dev
0 packages upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2057kB/10.1MB of archives. After unpacking 42.5MB will be used.
The following packages have unmet dependencies:
  g++-4.1: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) which is a virtual package.
           Depends: gcc-4.1 (= 4.1.2-0ubuntu4) which is a virtual package.
           Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed.
  g++: Depends: cpp (>= 4:4.1.2-1ubuntu1) which is a virtual package.
       Depends: gcc (>= 4:4.1.2-1ubuntu1) which is a virtual package.
       Depends: gcc-4.1 (>= 4.1.2) which is a virtual package.
  libstdc++6-4.1-dev: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) which is a virtual package.
                      Depends: libstdc++6 (>= 4.1.2-0ubuntu4) but 4.0.3-1ubuntu5 is installed.
  dpkg-dev: Depends: dpkg (>= 1.13.20) but 1.13.11ubuntu7 is installed.
            Depends: make which is a virtual package.
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.3.6-0ubuntu20.5 is installed.
  build-essential: Depends: gcc (>= 4:4.1.1) which is a virtual package.
                   Depends: make which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
build-essential [Not Installed]
dpkg-dev [Not Installed]
g++ [Not Installed]
g++-4.1 [Not Installed]
gcc272 [Not Installed]
libc6-dev [Not Installed]
libstdc++6-4.1-dev [Not Installed]

Score is 55

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
_____________

After doing this, I checked through Synaptic to see if anything was actually installed, and nothing was -- I still don't have Build Essential. I don't know how to tell the installer to meet those unresolved dependencies automatically, or how to work around them, or install them manually, or whatever.

---

### Post by fallintosanity on 2007-09-11
> **zipperback said:**
> You should be able to reset your root password providing of course that you have a user account in the SUDOERS access informatgion.

Just enter: sudo passwd root

Then changed your password.

However, if you think it just magically changed and things on your system are acting different than normal, I would suggest that you download the current version of ubuntu and then do a clean install with it.

- zipperback
:guitar:

That worked -- thanks! I am trying to get a current version of Ubuntu to install properly, but like I said, my laptop refuses to boot to CD and the workaround I used to install Ubuntu in the first place isn't working any more. (Sometimes I really hate computers...)

---

