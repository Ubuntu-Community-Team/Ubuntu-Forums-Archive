---
title: "Help on compiling new software?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Cpt.Flint on 2007-02-27
Hello,

So I have a problem installing 1 program. I want to install "Galleon" web-browser. 
I downloaded it from gnomefiles.org and unpacked it. Entered the folder from the terminal and made the "./configure" and here's what happened:

velio@frontdesk:~/Desktop/galeon-2.0.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


I checked the "config.log" file but didn't understand anything...

So any suggestions on what should I do?

---

### Post by Bachstelze on 2007-02-27
```
sudo apt-get install build-essential
```

---

### Post by Cpt.Flint on 2007-02-27
> **HymnToLife said:**
> ```
sudo apt-get install build-essential
```

velio@frontdesk:~$ sudo apt-get install build-essential
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
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
velio@frontdesk:~$

:(

---

### Post by Bachstelze on 2007-02-27
PLease paste your /etc/apt/sources.list - I think we'll find something wrong in there.

---

### Post by Cpt.Flint on 2007-02-27
## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

#AUTOMATIX REPOS START

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by Bachstelze on 2007-02-27
add that line to your sources.list :

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

then apt-get update and apt-get install build-essential. Certainly you should ask yourself - or the geniuses behind Automatix - why it was removed in the first place...

---

### Post by Cpt.Flint on 2007-02-27
ok - so I changed my repositories according to this site:
[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

then added

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted      at the bottom of the file.

sudo apt-get update   - and the system checked something

and then this:

velio@frontdesk:~$ sudo apt-get install build-essential
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
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
velio@frontdesk:~$


and nothing... I guess I screwed the system, installing "Automatix" but I wanted the "easy way to Ubuntu" and guess I messed it up...

---

### Post by Rui Pais on 2007-02-27
you didn't forget to do a **sudo apt-get update**, after you change  sources.list, didn't  you?

---

### Post by Cpt.Flint on 2007-02-27
I did the  sudo apt-get update  command, but still I can't install the build-essential.
Even restarted the pc (old windows habbit :) ) but still the same...

---

### Post by Cpt.Flint on 2007-02-27
ok, so when I run 

sudo apt-get install build-essential

here's what happens:

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
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages


I'm running on Ubuntu 6.06...

When I try to install the build-essential via Synaptic Package Manager, i get this:
build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed

---

### Post by Rui Pais on 2007-02-27
you got something related with libc broken, something that it's terrible bad.

Either some broke while you install something or you end up with some wrong/incompatible version of libc from a non-ubuntu repo from an Automatix server.

Try to fix any broken packages with synaptic, going to 'Custom FIlters' (bottom left buttons) and then on the upper list choose 'Broken'. Double click on any package that appear with a red color mark.

If that didn't fix comment out the lines from automatix (put a sign # on the beginning of each line) redo a sudo apt-get update and try install build-essential (try sudo aptitude install instead of  apt-get since it deals better with dependencies) and/or retry the broken fix above.

Good luck (with broken libc you may really need it :()

---

### Post by Cpt.Flint on 2007-02-27
It apperas that nothing is broken...
I guess reinstall is my only option

DON'T USE AUTOMATIX!
It may save you some time and efforts in the beginning but it will most likely screw you up after that.

---

### Post by Bachstelze on 2007-02-27
Before you reinstall, could you paste your new sources.list ? Also, is there something unusual whan you run apt-get update ?

---

### Post by sarwatj on 2007-02-27
i got the same problem i was using package manager to install downloaded package build-essential had 2 dependencies

package g++ and package stdc-6.4-dev

now these both packages are dependent on each other and neither will install before the other so none of the three install 
sounds like a riddle :)  
so i am facing the same problem

---

### Post by Bachstelze on 2007-02-27
That's not the problem, or else you wouldn't be able to install pretty much anything since those "cross-dependencies" are very common. What's the error you get when installing build-essential ?

---

### Post by sarwatj on 2007-02-27
sorry mis named the second pkg its libstdc++-6.4-dev

---

### Post by Cpt.Flint on 2007-02-27
my sources.list

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by Bachstelze on 2007-02-27
And what happens if you try to install them one at a time, for example

```
sudo apt-get install g++
```

---

### Post by Cpt.Flint on 2007-02-27
> **HymnToLife said:**
> And what happens if you try to install them one at a time, for example

```
sudo apt-get install g++
```

velio@frontdesk:~$ sudo apt-get install g++
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
  g++: Depends: g++-4.0 (>= 4.0.3) but it is not going to be installed
E: Broken packages


nothing I guess :confused:

---

### Post by Cpt.Flint on 2007-02-28
So yesterday I reinstalled Ubuntu, installed [SIZE="4"]build-essential[/SIZE] and tried to ./configure Galeon... AND IT STILL WON'T INSTALL :(  This time I didn't put Automatix in the system, and I have extra repositories enabled. Here's what ./configure displays after a while:

No package 'gtk+-2.0' found
No package 'libgnomeui-2.0' found
No package 'libbonoboui-2.0' found
No package 'libglade-2.0' found
No package 'gdk-pixbuf-2.0' found
No package 'gdk-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GALEON_DEPENDENCY_CFLAGS
and GALEON_DEPENDENCY_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by Bachstelze on 2007-02-28
This is a totally different problem : you miss some of the libraries required to build Galeon. Try to install the packages it suggests.

---

### Post by Maestro23 on 2007-02-28
Why don't you make it easy on yourself and install the galeon 2.0.2.2 from the Repositories?

> sudo aptitude update

sudo aptitude install galeon

Unless you just want the latest version.

---

### Post by Cpt.Flint on 2007-02-28
> **Maestro23 said:**
> Why don't you make it easy on yourself and install the galeon 2.0.2.2 from the Repositories?



Unless you just want the latest version.

It's not that I want the latest version, or that I'm so keen on Galeon AT ALL. It's just that yesterday I tried to build it, and since I still can't do it pisses me off :)  I just want to get it done. At least this way I'll learn a little bit more about Linux.

Other than that - I'm using Ubuntu for just a couple of days now. It's my first Linux so far and I have to say that I'm prerry satisfied for now. The Comunity and howtos are great, so THANKS alot to everybody who tried to help me out :KS 

Anyway, back to the Galeon stuff :mad:

---

### Post by Maestro23 on 2007-02-28
> **Cpt.Flint said:**
> It's not that I want the latest version, or that I'm so keen on Galeon AT ALL. It's just that yesterday I tried to build it, and since I still can't do it pisses me off :)  I just want to get it done. At least this way I'll learn a little bit more about Linux.

Other than that - I'm using Ubuntu for just a couple of days now. It's my first Linux so far and I have to say that I'm prerry satisfied for now. The Comunity and howtos are great, so THANKS alot to everybody who tried to help me out :KS 

Anyway, back to the Galeon stuff :mad:

Ok man.  You want trial by fire.:) 

As you can see, compiling from source can be a pain. Get those dependecies taking care of first then.

---

### Post by Rui Pais on 2007-02-28
> **Cpt.Flint said:**
> It's not that I want the latest version, or that I'm so keen on Galeon AT ALL. It's just that yesterday I tried to build it, and since I still can't do it pisses me off :)  I just want to get it done. At least this way I'll learn a little bit more about Linux.

Other than that - I'm using Ubuntu for just a couple of days now. It's my first Linux so far and I have to say that I'm prerry satisfied for now. The Comunity and howtos are great, so THANKS alot to everybody who tried to help me out :KS 

Anyway, back to the Galeon stuff :mad:

sounds a little the old gentoo myth... 
compiling stuff will not teach anything (besides basic make commands)...
but will not brake your back either :lol:

you need to search for each of those dependencies and search, using synaptic is usually the way, the equivalent packages with a "-dev" at the end of the name.

good luck :)

---

### Post by konst88 on 2007-02-28
sudo apt-get build-dep galeon

---

