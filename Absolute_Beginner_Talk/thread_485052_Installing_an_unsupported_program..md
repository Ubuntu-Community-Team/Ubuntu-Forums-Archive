---
title: "Installing an unsupported program."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by r3bol on 2007-06-26
I want to install this... [http://rebol.com/downloads/rebol-core-2602042.tar.gz](http://rebol.com/downloads/rebol-core-2602042.tar.gz) which I need to extract somewhere. After that it should be ready to run, but is there a preferred place to extract it? I was thinking /usr/bin/
Is that cool?

Thanks

---

### Post by Hendrixski on 2007-06-26
first check that it's not in the repo's.  
**apt-cache search ***name*****

if not then download the tarball
most programs it doesn't matter where you extract it.

just extract it then run **./configure** in the extracted directory
then run **make**
then run **make install**

That SHOULD do it (I didn't look at your particular application)

If they have an .rpm then use alien to install it
if it doesn't have a configure it may have some  .pro files, the use qmake, make, make install

---

### Post by Hendrixski on 2007-06-26
actually... technically the best practice for Debian distributions is to make your own .deb first and then install (so that you can uninstall it very easily, or upgrade it even EASIER)

all you need is dh_make and debuild -S
here check this out  [http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html) 

then to install just type "dkpk install myProgram.deb" and the same thing with updating... instead of uninstalling and reinstalling you just repackage the .deb and install it.  after you do it a few times it takes a few seconds.

---

### Post by EndPerform on 2007-06-26
The way it sounds, it may not need compiled if it is indeed ready to run.  I wouldn't unarchive it to /usr/bin, however.  /opt/rebol might be a good place, or if you're the only one that will be using it, you can put it in your home directory.  I've done this for a few things in the past (latest and greatest firefox, Doom3, UT, etc) and it works ok.

---

### Post by r3bol on 2007-06-26
It is ready to run. 
Thanks for telling me about the ./opt place. I googled it and it seems to be the place for 3rd party software. I noticed I already have Azureus there.

How do I get around: **You don't have the right permissions to extract archives in the folder "/opt"**

---

### Post by r3bol on 2007-06-27
OK i sorted the permission thing logging in as root and the program is running nicely.

---

### Post by EndPerform on 2007-06-28
> **r3bol said:**
> OK i sorted the permission thing logging in as root and the program is running nicely.

Yeah, /opt is owned by root, but once you install the program there, you should be able to run it as your regular user just fine and dandy :)

---

### Post by ubromtoo on 2007-06-30
" no acceptable C compiler found in $PATH "

   this is the error message I get after downloading "gweled-0.7.tar.gz" , then extracting

it, "cd"ing into it, and giving the command :

        ./configure


  So, what to do now ?  Have searched the forum for awhile, but no luck. Asking for help 
                                                                                                    :-k

P.S. : An earlier version (0.6) is available in Add/Delete and Synaptic, but 0.7 is the version I particularly want .

---

### Post by hyper_ch on 2007-06-30
You need to have a compiler installed:

```

sudo apt-get install build-essential

```

---

### Post by ubromtoo on 2007-06-30
hyper_ch :

   A Noobie such as myself is mystified by the following; it seemed such a simple action,

            richard@richard-desktop:~$ pwd
/home/richard
richard@richard-desktop:~$ sudo apt-get install build-essential
Password:
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

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installedor
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but it is not going to be installed
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
richard@richard-desktop:~$

      Can you make heads or tails of this ?  I'm running Dapper 6.06 , is there a 

problem with that for this application (build-essential) ?  Thank you.

---

