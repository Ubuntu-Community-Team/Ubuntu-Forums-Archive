---
title: "'Sudo apt-get install 'does not work....."
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-17
Hi,
I'm trying to install Adobe Reader, and I've tried typing this command:

Sudo apt-get install AdobeReader_enu-7.0.9-1.i386.tar.gz

This does not work and the terminal says E: Couldn't find package AdobeReader etc.

What am I doing wrong? I appreciate any assistance. Many Thanks, Frank

---

### Post by k33bz on 2007-05-17
have you updated your repos?

---

### Post by trent dillman on 2007-05-17
...

---

### Post by starcraft.man on 2007-05-17
Hehe, thats not how ya install via apt. To install acrobat reader you want to run this command via terminal:

```
sudo aptitude install acroread acroread-plugins
```

that will get ya reader and firefox plugin.

[Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apt.2C_Software_and_Package_Basics") is a basic guide to apt and how to install things :)

Hope that helps, have a good read about the apt command and the repos.

---

### Post by AlanD on 2007-05-17
Adobe reader is in the repositories if I remember right. Open add/remove, in the top right make sure you select all available applications, and search for Adobe Reader :)

---

### Post by wormser on 2007-05-17
To search for a file with apt use the command below.  Some times the name will be a bit different or have a version number behind it.

```
apt-cache search filename
```

Sudo is not needed because you are not installing.

Then you can install.

```
sudo apt-get install filename
```

---

### Post by gradedcheese on 2007-05-17
That's a compressed file (ie: an archive, like a .zip).  You can uncompress it:

```

tar -xvzf AdobeReader_enu-7.0.9-1.i386.tar.gz

```

And then install it.  It's probably a directory with an install script, 'cd' to it and see what it contains...

---

### Post by mattva01 on 2007-05-17
You can also use the Add/Remove Programs menu.

---

### Post by scrooge_74 on 2007-05-17
> **Brightbelt said:**
> Hi,
I'm trying to install Adobe Reader, and I've tried typing this command:

Sudo apt-get install AdobeReader_enu-7.0.9-1.i386.tar.gz

This does not work and the terminal says E: Couldn't find package AdobeReader etc.

What am I doing wrong? I appreciate any assistance. Many Thanks, Frank

To help reduce the confusion.

The file you are trying to install is a compress file, first you need to uncompress it and then follow the instructions.

apt-get  will let you install programs which are in the repositories it will download them and then do all the install for you.

For reading pdf files Ubuntu already has a reader installed (evince),  I feel that Adobe just runs to slow compare with evince

The pluggin for Firefox works also.

Automatix will either help you or break things, if you want to truly know what you are doing don't use Automatix to install things for you.

---

### Post by Brightbelt on 2007-05-17
I appreciate the suggestions,.....however, I found this for one thing:

"Automatix2

Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu. "

Also, Adobe Reader is not in Add/Remove. There are other Pdf viewing programs there and I am using KPDF (from the list) in the meantime. 

I've looked in the repository, but how do I update it? I've tried to "Add" Adobe Reader but I'm a beginner, so unless it's explained in English how to do the "complete apt line" with the url and/or repository, I probably won't guess it from luck. 

I appreciate your help... Thanks to anyone who can stick with me on this. I may have to lay this down and pick it back up tomorrow afternoon.

Thanks, Frank

---

### Post by Brightbelt on 2007-05-17
Maybe I just need to open my mind past Windows. I'm so used to Adobe, but maybe KPDF is just as good.

Which program would you say is better: Evince or KPDF?

Thanks, Frank

---

### Post by Sef on 2007-05-17
> Maybe I just need to open my mind past Windows. I'm so used to Adobe, but maybe KPDF is just as good.

Which program would you say is better: Evince or KPDF?

Try them both and see which one you like better.   As for Adobe Reader, it should be in Adept since it is in Synaptic (which is for Ubuntu.)

---

### Post by psycosmyth on 2007-05-17
[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

follow the directions given. Hey It's the real deal, you accept the agreement an your happy.

use this site for flash too and you get the better version.

I also agree with Sef, the open version are as good

---

