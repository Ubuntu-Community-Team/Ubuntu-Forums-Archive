---
title: "Ubuntu Packages (deb files)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Snitz on 2008-04-02
Where can I download ubuntu packages other than the synaptic?
Is there a website or something?

---

### Post by hyper_ch on 2008-04-02
[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by kellemes on 2008-04-02
[http://www.getdeb.net/]("http://www.getdeb.net/")

---

### Post by Rocket2DMn on 2008-04-02
packages.ubuntu.com is the Ubuntu repository location, but if you're going to download packages, make sure you get any dependencies with it.  getdeb.net has some packages as well, some of which aren't available in the repositories, and although they usually work well, there is no guarantee.
Some programs offer .deb packages from their own websites as well, rather than just the source code (they may also offer rpm's for RHEL based distros like Fedora and CentOS, as well as installers for windows, or even *BSD systems).  However, you just want the .deb packages - got a little sidetracked there :)

---

### Post by kellemes on 2008-04-02
> **Rocket2DMn said:**
> packages.ubuntu.com is the Ubuntu repository location, but if you're going to download packages, make sure you get any dependencies with it.  getdeb.net has some packages as well, some of which aren't available in the repositories, and although they usually work well, there is no guarantee.
Some programs offer .deb packages from their own websites as well, rather than just the source code (they may also offer rpm's for RHEL based distros like Fedora and CentOS, as well as installers for windows, or even *BSD systems).  However, you just want the .deb packages - got a little sidetracked there :)

Nothing wrong with providing a little understanding ;-)

---

### Post by sayakb on 2008-04-02
getdeb provides newer versions of packages to those available in the repos. Just make sure that you have the correct architecture. Do not try to install any package using force architecture unless unless necessary.

---

### Post by MasterSushi on 2008-04-02
This may be a bit of a newbie question but:

Why don't groups that create the applications create .deb files so that their application can be easily installed? I know there would need to be a 32 bit version and a 64 bit version. I am just confused as to why this is left to the user to figure out instead of being handled by the application maker.

---

### Post by mrsudo on 2008-04-02
> Why don't groups that create the applications create .deb files

i was wondering this myself....

---

### Post by kellemes on 2008-04-02
> **MasterSushi said:**
> This may be a bit of a newbie question but:

Why don't groups that create the applications create .deb files so that their application can be easily installed? I know there would need to be a 32 bit version and a 64 bit version. I am just confused as to why this is left to the user to figure out instead of being handled by the application maker.

For the user there isn't too much figure out, as long as know what OS you're using you know what .deb you need.. It's the same with Windows, you may have a couple of different .exe file available for the Windows versions supported.

Developers of software need to create a lot of .deb's
There are about 120+ distributions making use of deb's.
Debian Stable
Debian Testing
Debian Unstable
Ubuntu Dapper
Ubuntu Feisty
Ubuntu Gutsy
Ubuntu Hardy
Mint?
Knoppix?
etc..
etc..

And what about RPM's??
There are a lot of distributions out there making use of RPM but need an RPM for there specific distribution version, this RPM will be different from the one used by RH or Fedora.

It's best for distributions themselfs to do this..

---

### Post by sayakb on 2008-04-02
> **MasterSushi said:**
> This may be a bit of a newbie question but:

Why don't groups that create the applications create .deb files so that their application can be easily installed? I know there would need to be a 32 bit version and a 64 bit version. I am just confused as to why this is left to the user to figure out instead of being handled by the application maker.

 Debian packages are infact the best we have among all. Plus, we also have different setups for different architectures under Windows. Also, when you try to install any package belonging to a wrong architecture, the package manager would notify you (For example, it says "Wrong architecture i386") and the installation will not be continued. So there is nothing much to worry about :)

---

### Post by Rocket2DMn on 2008-04-02
I think developers just find it's a hassle compile all kinds of different packages and test them adequately, esp. for smaller projects with limited resources.  It is true they would have to compile for 32 bit, 64 bit for x86 and x86_64 processors, but there are other processor architectures as well.  In the FOSS world, it is generally understood that you can just take the code and compile it yourself (and even edit it first), package management is just an easier way to stay organized, but it is not universally accepted between distributions.  Also, just because a .deb works under Debian and Ubuntu does not necessarily mean it will always work under other distros that use .debs (though they should), same goes for rpm's.

Compiling the code yourself also allows the executables to be tweaked to your processor/kernel so long as your compiler (gcc/g++) is also for that architecture.  Ex: tweaked for 686 instead of 386.

---

### Post by MasterSushi on 2008-04-02
I guess I should learn how to compile a program, then I won't be dependent on the repositories or someone making a working .deb file for Ubuntu.

I used Linux about 7 years ago and remember compiling was always a nightmare with missing dependencies and errors like crazy. Has the process for compiling gotten better or easier?

---

### Post by Rocket2DMn on 2008-04-02
The process is still the same, typically using
```
./configure
make
make install
```
(might need sudo in the last command, I don't recall).  However, there are SO MANY programs in the repositories, you rarely ever need to do this.  Enable the universe and multiverse repositories, then the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos and you will have access to thousands of packages.

---

