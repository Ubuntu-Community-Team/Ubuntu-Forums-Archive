---
title: "How do I Install the Newer Version of OpenOffice?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by vaago on 2007-07-01
Hello all,

There is so much documentation to rifle through and sometimes there isn't much time in the day to spend on linux, which has been my rationalizations on  staying with XP. 

I am sure that it is written down somewhere how to upgrade a package that currently exists and is installed in Ubuntu. I love to read and will read it all, but I sure would like it if you could point me to the instructions specifically to upgrade Open Office 2.0.1 to the newer 2.2.1.(which I'm guessing would be generic to all package upgrades).

Do I have to remove the 2.0.1 first?
Is it Synaptic Package Manager  key to this process or
do I use Add/Remove?
Did I even need to download the package from .org or was there an upgraded package on the Update Manager?
Am I even asking the right questions?
 
I've downloaded the new package from .org and extracted it to my home folder but I still have the tar.gz compressed file on my desktop (just in case I should have unpacked it somewhere else).

Thanks for your help:-)

---

### Post by greg_g on 2007-07-01
First of all, what version of Ubuntu are you running?

Because in Fiesty, the latest up-to-date version is 2.2.0
The best way is to use Synaptic Package Manager and search for "openoffice.org" (the latest version in the Ubuntu Repositories is "2.2.0-1ubuntu3")

It *should* have been installed by default when Ubuntu was set up, but weird things happen.  Once it is installed once, Synaptic will keep track of it for you and tell you when there are new versions available for Ubuntu.

Does that  help?

greg

---

### Post by vaago on 2007-07-01
Sorry about that; forgot to put in that I'm using 6.0.6LTS. Funny thing though, I could've s***e
that I had downloaded 7.0.4. Anyway it is Open Office 2.0 that is installed.

---

### Post by greg_g on 2007-07-01
I believe then you have to enable "backports" in your sources.list

The easy way to do this is in Synaptic.  Settings -> Repositories, then the Updates Tab, select "unsupported updates (backports)"

Or, upgrade to Fiesty.  See this page for information:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Basically, you need to upgrade to 6.10 first, then to 7.04.

But, if everything is working for you satisfactory, why bother?  Just because sometimes upgrades are not the most fun experiences, if you don't HAVE to do it, why do it?

Does that help?

greg

---

### Post by vaago on 2007-07-02
Actually it does - help that is. I have 7.04 running (live) on the other box and I like it but this one - 6.06LTS runs so well on this old Xeon, I've been hesitant to upgrade. 

I've looked for 6.10 and cannot seem to locate it. I've been fiddling with Puppy, trying to get it loaded on an old Acer Light laptop (Windows95) but I've not yet figured out how to get it to boot from CD even though I've enabled boot from cd. 

I'll try running the live 7.04 on this computer later this week and if all of the drivers are there (scsi) I'll probably do as you suggest. To tell you the truth I like the desk top colors so well (the chocolate brown of 6.06 - it's just easy on the eyes.

---

### Post by stchman on 2007-07-03
> **vaago said:**
> Hello all,

There is so much documentation to rifle through and sometimes there isn't much time in the day to spend on linux, which has been my rationalizations on  staying with XP. 

I am sure that it is written down somewhere how to upgrade a package that currently exists and is installed in Ubuntu. I love to read and will read it all, but I sure would like it if you could point me to the instructions specifically to upgrade Open Office 2.0.1 to the newer 2.2.1.(which I'm guessing would be generic to all package upgrades).

Do I have to remove the 2.0.1 first?
Is it Synaptic Package Manager  key to this process or
do I use Add/Remove?
Did I even need to download the package from .org or was there an upgraded package on the Update Manager?
Am I even asking the right questions?
 
I've downloaded the new package from .org and extracted it to my home folder but I still have the tar.gz compressed file on my desktop (just in case I should have unpacked it somewhere else).

Thanks for your help:-)

You can install the newer 2.2 by installing Feisty.  If you are running Edgy or earlier follow this:

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

If you want to install 2.2.1 you will have to follow the manual procedure and make sure to substitute 2.2.1 for 2.2.

---

### Post by vaago on 2007-07-04
stchman,

It's going to take me a little while to get my head wrapped around this, but I'm going to give it a try. It's the least I can do after you've put the effort into writing this out!

Thankyou

---

