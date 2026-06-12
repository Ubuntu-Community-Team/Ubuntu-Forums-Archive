---
title: "java"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-23
hmm. i followed the guide to install sun java from the guide

but i get this error after typing this ...

 sudo apt-get install sun-java5-bin

Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

am i doing something wrong? i have multiverse and universe both enabled

---

### Post by Googler on 2006-05-23
you better got to [www.java.com](www.java.com) and download it from there

the link is 
[http://java.com/en/download/linux_manual.jsp]("http://java.com/en/download/linux_manual.jsp")
beside the download icon you will find the instructions for installation

---

### Post by Koech on 2006-05-23
Check this out:
  [ http://www.java.com/en/download/help/5000010500.xml#selfextracting]("http://www.java.com/en/download/help/5000010500.xml#selfextracting")
It contains instructions on how to install j2re, Ive used it successfully, however I didn't see a change when I ran showversion. Maybe someone can shed light on this.

---

### Post by KarmaKing on 2006-05-23
[QUOTE=sotonin]hmm. i followed the guide to install sun java from the guide

but i get this error after typing this ...

 sudo apt-get install sun-java5-bin

Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

am i doing something wrong? i have multiverse and universe both enabled[/QUOTE]
I am by no means a proffesional, quite the contrary, but third line from the bottom says386 for the java package.  Shouldn't the most updated version be i586?

I had days of problems with this on mine and this was the only thing I could get it to work [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)
its under Sun Java

KK

---

### Post by mlind on 2006-05-23
If you're installing java manually from .bin (like you should do),
see this [HOWTO]("https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e") from wiki.

Same instructions appy for JDK if you need development environment (that includes runtime environment too)

---

### Post by gatekeeper on 2006-05-23
Simplist method is:

sudo apt-get install j2re1.4

see: [https://wiki.ubuntu.com/RestrictedFormats#head-4c7e4207c354be7cb50a2c3c9ae6dae5e73bb6a4](https://wiki.ubuntu.com/RestrictedFormats#head-4c7e4207c354be7cb50a2c3c9ae6dae5e73bb6a4)

---

### Post by mlind on 2006-05-23
[QUOTE=gatekeeper]Simplist method is:

sudo apt-get install j2re1.4

see: [https://wiki.ubuntu.com/RestrictedFormats#head-4c7e4207c354be7cb50a2c3c9ae6dae5e73bb6a4](https://wiki.ubuntu.com/RestrictedFormats#head-4c7e4207c354be7cb50a2c3c9ae6dae5e73bb6a4)[/QUOTE]


Blackdown java is only 1.4 compatible while Sun's 1.5 offers quite bit of improvements.
I wouldn't install 1.4 anymore.

---

### Post by sotonin on 2006-05-23
hmmm ok thanks for the advice. i followed the manual instructions and get to the end....

but the recomendation doesn't solve my problem.

cafelogin@Cafe-ubuntu1:/usr/java$ DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg blah.bin
Creating temporary directory: /tmp/make-jpkg.XXXXCNv03i
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

this is all i can get out of it....

---

### Post by sotonin on 2006-05-23
has anybody else had this issue before? ... i thought i was doing good cause there was already a fix for the prob in the wiki, but it didn't solve it for me. :(

---

### Post by mlind on 2006-05-23
[QUOTE=sotonin]has anybody else had this issue before? ... i thought i was doing good cause there was already a fix for the prob in the wiki, but it didn't solve it for me. :([/QUOTE]

You're doing that fakeroot command for binary dowloaded from Sun's server right?
File is probably called jre-1_5_0_06-linux-i586.bin

You better leave that blackdown java alone, you won't need that.

---

### Post by sotonin on 2006-05-23
yes... i got the .bin from suns website ...

---

### Post by mlind on 2006-05-23
okay, have you tried without specifying DEB_BUILD_GNU_TYPE ?
doing just plain *fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin*

---

### Post by sotonin on 2006-05-23
yeah. exact same result. thats why i tried the secondary step in the first place. .. sigh

---

### Post by mlind on 2006-05-23
[QUOTE=sotonin]yeah. exact same result. thats why i tried the secondary step in the first place. .. sigh[/QUOTE]

hmm.. strange. What kernel / architechture are you running ?
output of *uname -r*

---

### Post by sotonin on 2006-05-23
2.6.15-23-386

---

### Post by mlind on 2006-05-23
what about 
*echo dpkg-architecture -qDEB_BUILD_GNU_TYPE*

I get i486-linux-gnu

---

### Post by sotonin on 2006-05-23
ohhh this is bizarre. ok. i deleted the bin and redownloaded... now it seems to be working.. how odd. it must have been corrupted the first time.

---

### Post by mlind on 2006-05-23
[QUOTE=sotonin]ohhh this is bizarre. ok. i deleted the bin and redownloaded... now it seems to be working.. how odd. it must have been corrupted the first time.[/QUOTE]

lol, good you got it sorted :mrgreen:

---

### Post by sotonin on 2006-05-23
not quite... ok this is what it's doing now...

dh_builddeb
dpkg-deb: building package `sun-j2re1.5' in `/tmp/make-jpkg.XXXXI5Zu4f/sun-j2re1.5_1.5.0+update06_i386.deb'.
    copy sun-j2re1.5_1.5.0+update06_i386.deb into directory /usr/java/
cp: cannot create regular file `/usr/java/sun-j2re1.5_1.5.0+update06_i386.deb': Permission denied

Aborted (/usr/java/).

---

### Post by sotonin on 2006-05-23
ehg. scratch that. thats what i get for following directions from sun's website... i ran it from my home folder and it created the debian file perfectly. thank for the help :) lets see if the debian step goes ok now

---

### Post by S{yndrom}e on 2006-05-23
for the record whenever you get a permissions error run the command with sudo

---

### Post by mlind on 2006-05-23
[QUOTE=sotonin]ehg. scratch that. thats what i get for following directions from sun's website... i ran it from my home folder and it created the debian file perfectly. thank for the help :) lets see if the debian step goes ok now[/QUOTE]

yeah, don't forget to do *update-alternatives --config java* and choose Sun's jvm
or you'll still be using gjc instead.

java -version
should ouput that it's Sun's jvm.

---

### Post by mlind on 2006-05-23
[QUOTE=S{yndrom}e]for the record whenever you get a permissions error run the command with sudo[/QUOTE]


In this case, it's against fakeroot principle. 
You're supposed to emulate root user privileges, not actually gain them.

---

