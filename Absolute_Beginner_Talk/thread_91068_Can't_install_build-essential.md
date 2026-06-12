---
title: "Can't install build-essential"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2005-11-16
When i try, I get the following errors:
```

doc@Caliban:~$ sudo apt-get install build-essential
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
  build-essential: Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages

```

If I try to install the dependencies, I just get more and more dependency errors.

-Doc

---

### Post by Kyral on 2005-11-16
Can I see your sources.list?

---

### Post by Doc.Caliban on 2005-11-16
[QUOTE=Kyral]Can I see your sources.list?[/QUOTE]

Ubunto universe did not help, and backports resulted in a ton of 404's when I updated, so both are now disabled.  (But I tried them)

```

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

#deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
#deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

```

Thanks,

-Doc

---

### Post by Kyral on 2005-11-16
One thing Ubuntu Universe IS enabled, but Build-Essential is in Main.

Hmm, can you try 
```
sudo apt-get -f install
```

And I'll get back to you after class :D

---

### Post by Doc.Caliban on 2005-11-16
[QUOTE=Kyral]One thing Ubuntu Universe IS enabled, but Build-Essential is in Main.

Hmm, can you try 
```
sudo apt-get -f install
```

And I'll get back to you after class :D[/QUOTE]

Sorry, I meant breezy universe.

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

-Doc

---

### Post by jeffreyvergara.NET on 2005-11-16
i only used the default sources.list (cd rom source) and it worked fine. I recommend it when you have slow internet connection

---

### Post by Doc.Caliban on 2005-11-16
[QUOTE=jeffreyvergara.NET]i only used the default sources.list (cd rom source) and it worked fine. I recommend it when you have slow internet connection[/QUOTE]

I have a good connection, but I appreciate the input.  I think there's something more sinister going on....

-Doc

---

### Post by Doc.Caliban on 2005-11-16
BTW, Tried this and still get the same error:

 apt-get check 

 apt-get update 

 apt-get clean 

 apt-get -f install

-Doc

---

### Post by Kyral on 2005-11-16
Hmm, the us archive seems to be acting up as of late. Try dropping the "us." from the mirrors, update, and try again. This is VERY disturbing

---

### Post by Doc.Caliban on 2005-11-16
[QUOTE=Kyral]Hmm, the us archive seems to be acting up as of late. Try dropping the "us." from the mirrors, update, and try again. This is VERY disturbing[/QUOTE]

Removed "us." from the begining of the URL's, updated, and tried to install again.  Same dependency errors.  :-(   Rats.

-Doc

---

### Post by Kyral on 2005-11-16
Hmm, this is VERY VERY disturbing indeed....

Wait, can you try to install g++ and gcc and show me why they won't be installed?

---

### Post by Doc.Caliban on 2005-11-16
[QUOTE=Kyral]Hmm, this is VERY VERY disturbing indeed....

Wait, can you try to install g++ and gcc and show me why they won't be installed?[/QUOTE]

gcc

```

doc@Caliban:~/Incoming/truecrypt-4.0$ sudo apt-get install gcc
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
  gcc: Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages

```

g++

```

doc@Caliban:~/Incoming/truecrypt-4.0$ sudo apt-get install g++
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
  g++: Depends: gcc (>= 4:4.0.1-3) but it is not going to be installed
       Depends: g++-4.0 (>= 4.0.1-2) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages

```

---

### Post by Kyral on 2005-11-16
How did...how did dependacy hell break out....what are those PLF repos there for. Its the only thing I might think of..

Okay, it make take a while but I'll get you sorted out. This ISN'T Normal BTW ;P

Okay, both are complaining about gcc-4.0...try installing that (The package versions are right)

Eventually we will find one package that is cause this entire mess

Oh just to make sure I'm not overlooking something humor me and try a ```
sudo apt-get dist-upgrade
```

---

### Post by Doc.Caliban on 2005-11-16
[QUOTE=Kyral]How did...how did dependacy hell break out....what are those PLF repos there for. Its the only thing I might think of..

Okay, it make take a while but I'll get you sorted out. This ISN'T Normal BTW ;P[/QUOTE]


Cool, thanks.  I'll be offline unitl Friday night I think.  This is the first thread I'll look at!

-Doc

---

### Post by Kyral on 2005-11-16
I'll ask in the Devel channels to see if they know anything

---

### Post by Doc.Caliban on 2005-11-16
BTW, should I leave the us. off the url's in my sources.list?  I'm in Brazil if that makes any difference.

-Doc

---

### Post by Kyral on 2005-11-16
Yah you should put "br." in front of archive. It should be faster.

I even got bored and generated a Sources.list for Brazil using the new Source-o-matic

```
[FONT=monospace]
[/FONT]# Automatically generated sources.list[FONT=monospace]
[/FONT]# http://www.ubuntulinux.nl/source-o-matic
# Ubuntu supported packages (packages)
deb http://br.archive.ubuntu.com/ubuntu breezy main restricted
deb http://br.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources)
deb-src http://br.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://br.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages)
deb http://br.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://br.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources)
deb-src http://br.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu backports project (packages)
deb http://br.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources)
deb-src http://br.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

### Post by Doc.Caliban on 2005-11-18
Wow, cool.  I appreciate that.

The bad news is that I'm going back to Windows.  :-(   I've used Windows for 16 years and I really wanted to get rid of it.  This was my first try at Linux and I've just found too many limitations for the things I do on my computer.  I am definitly going to give it another shot when the next version of Ubuntu comes out though!

Thanks for all the help,

-Doc

---

### Post by Kyral on 2005-11-18
Yah I have no idea what happened but I talked to some dev types and they said basically the PLF repo might have messed it up and you'd have to dive into the realm of Apt-Pinning, which is tricky stuff. The Dapper Drake should really be awesome. I'm glad that you are gonna try again in 6 months though. The Forums will always be here to help

---

### Post by Doc.Caliban on 2005-11-18
I'm looking forward to the next round.  This time there were just a few too many instances of having to do B to get A to work, but having to do C to get B to work, D & E to get C to work, etc.  :-)  

You'll see me here again!

-Doc

---

### Post by khai on 2005-11-19
I'm having the same problem also. I'm a long time ubuntu user, but this is a new installation. I'm guessing the problem stems from having a bunch of system components upgraded. 

It looks like downgrading gcc-base from 4.0.2-3ubuntu to 4.0.1-4ubuntu9 would solve the dependency problem, but I would end up having over 300 packages removed that depend on it (from apt to xpdf).

I think this started after I ran automatrix and then tried to install build-esstential. I believe automatrix adds PLF repos to sources.list.

---

