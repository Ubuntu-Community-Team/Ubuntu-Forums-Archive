---
title: "IBM Java 6, PPC, and Edgy"
date: 2007-02-12
forum: Apple PPC Users
---

### Post by RedRedKrovy on 2007-02-12
I have Edgy installed on my PowerBook.  I'm trying to get IBM Java 6 installed but every time I run make-jpkg I get "No matching plugin was found".  Does anyone have any ideals?

---

### Post by seebol on 2007-02-12
I believe Java is one of the big things linuxonpowerpc lacks. Other things that don't work well are Flash (I found a plugin that let me see the ads, but it wouldn't play any music or video) and some videos (realmedia, some .mkv and .avi files...)

If I'm wrong, please correct me.

---

### Post by maxamillion on 2007-02-12
> **seebol said:**
> I believe Java is one of the big things linuxonpowerpc lacks. Other things that don't work well are Flash (I found a plugin that let me see the ads, but it wouldn't play any music or video) and some videos (realmedia, some .mkv and .avi files...)

If I'm wrong, please correct me.

You're unfortunately correct, pretty much linux on ppc has gcj/gij and jike/kaffe for java and gnash for flash....

If you want ibm java ... i'm pretty sure that is just jikes, i could be wrong though.

---

### Post by phossal on 2007-02-12
I don't get it. Are you running Ubuntu? Can't you simply install the JDK directly from SUN?

---

### Post by RedRedKrovy on 2007-02-12
Sun does not make Java for the PPC arch, only for the x86.  IBM however does make Java for the PPC arch.  Sun has a Debian package for theirs how ever IBM does not.  I'm not very good at compiling from source so I try to stick with the Debian packages.  So if some one could tell me how to get the make-jpkg to work or walk me through compiling and installing it from the source.

I already have Java 5 from IBM working right now but I just downloaded a Java program that requires 6, that's why I'm trying to update.

---

### Post by phossal on 2007-02-12
What happens when you try to install the x86 JDK on your machine?

---

### Post by zakusage on 2007-02-13
Add the following line to your /etc/apt/sources.list:

```
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free 
```

Medibuntu has a deb package for the IBM Java, among other things.

Edit: Er... if you're looking for Java6 nevermind. Still, this repository may be useful to other people simply looking to install Java.

---

### Post by 3rdalbum on 2007-02-13
> **phossal said:**
> What happens when you try to install the x86 JDK on your machine?

Immediate segfault. You can't run x86 binaries on PowerPC, everybody knows that.

---

### Post by phossal on 2007-02-14
> **3rdalbum said:**
> Immediate segfault. You can't run x86 binaries on PowerPC, **everybody knows that**.
Apparently not. I didn't *assume* it would work though. I was just curious. I know nothing of the ppc arch. I didn't anticipate how poorly curiosity would go over though. Perhaps everybody *else* knows *that* too.

---

### Post by RedRedKrovy on 2007-02-18
Got on IBM's website and found a quick start guide.  IBM Java 6 does not have a plugin yet but this allows you to use it in the terminal.

You must install the SDK manually. These steps lead you through the installation process:
 1. Extract the downloaded SDK to your system. The recommended location varies by platform:
     v For Linux on Intel x86: /opt/ibm/java2-i386-60/
     v For Linux on AMD 64-bit: /opt/ibm/java2-x86_64-60/
     v For Linux on PowerPC 32-bit: /opt/ibm/java2-ppc-60/
     v For Linux on PowerPC 64-bit: /opt/ibm/java2-ppc64-60/
    To extract the SDK, use the following command at a shell prompt:
    tar -zxf ibm-java-sdk-60-linux-<arch>-<date>.tgz
    Where <arch> is your target architecture and <date> is the build date of the package.
 2. To use the SDK as your default Java SDK, configure your PATH environment variable:
    export PATH=<SDK>/bin:<SDK>/jre/bin:$PATH
    Where <SDK> is the location of the extracted SDK.
 3. Verify your configuration by checking the Java version on your system:
    java -version
    You should see output similar to the following. Exact dates and platform information will vary.
    java version "1.6.0-internal"
    Java(TM) SE Runtime Environment (build 1.6.0-internal-b99)
    IBM J9 VM (build 2.4, J2RE 1.6.0 IBM J9 2.4 AIX ppc64-64 j9vmap6424-20061020 (JIT enabled)
    J9VM - 20061020_08890_BHdSMr
    JIT - 20061019_1800_dev
    GC    - 20061018_AA)


The only thing extra I did was put the export command (step 2) in my ~/.bashrc file at the end so I wouldn't need to run the command every time I opened up a terminal.

---

### Post by Grexe on 2007-05-16
There's an old but interesting article on the subject at IBM developerWorks with tips on how to make the jdk work for non-supported platforms:
[http://www-128.ibm.com/developerworks/systems/library/es-apple.html](http://www-128.ibm.com/developerworks/systems/library/es-apple.html)

However I could not find java6-packages yet... what about OpenJdk?

---

### Post by stmiller on 2007-05-16
> **Grexe said:**
> 

However I could not find java6-packages yet... what about OpenJdk?

They have x86 Linux packages I believe, but not PowerPC yet. You could perhaps compile the sources.

BTW: This thread is obsolete. See the PowerPCFAQs (below) for how to install working java with apt-get.

---

### Post by also-rr on 2007-05-16
There is a complete guide to setting up IBM Java (including the Firefox plugin) for PPC Ubuntu here:

[http://revis.co.uk/site/?q=node/116]("http://revis.co.uk/site/?q=node/116")

If you want flash as well you can try this:

[http://revis.co.uk/site/?q=node/139]("http://revis.co.uk/site/?q=node/139")

---

