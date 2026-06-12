---
title: "Problems installing Java Runtime"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-16
Here's the link to Sun's instructions on installing Java Runtime Environment for Linux:

[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

I only get past step one in the instructions however.  I can open up the terminal fine, I type in "su" (without quotes) and then hit enter.  Then it prompts me for the password, I start typing in my password but the letters don't make it to the page if that makes sense.  Basically no matter what I type, nothing shows up, and if I press enter it says "Authorization Required". :confused:

---

### Post by aysiu on 2006-07-16
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by GuitarHero on 2006-07-16
I think automatix and easy ubuntu also both have java in them.  Search the forum for them, they are auto-install scripts.

---

### Post by fatsheep on 2006-07-16
> **aysiu said:**
> [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I have enabled all multiverse repositories.  Now sun java 1.5 shows up but it gives me this error message when I try to install it in add/remove programs:

> 'sun-java5-bin' is not available in any software channel

The application might not support your system architecture.

> **GuitarHero said:**
> I think automatix and easy ubuntu also both have java in them.  Search the forum for them, they are auto-install scripts.

Thanks, I'm taking a look at easy ubuntu right now, I'll check it out.

---

### Post by fatsheep on 2006-07-16
I don't see what's so automatic or easy about these scripts, you have to install them in terminal and it didn't even work for me (the easy ubuntu one anyway).  :confused:

---

### Post by aysiu on 2006-07-16
> **fatsheep said:**
> I have enabled all multiverse repositories.  Now sun java 1.5 shows up but it gives me this error message when I try to install it in add/remove programs What's your system's architecture? PowerPC? AMD64?

---

### Post by fatsheep on 2006-07-16
Amd 64

---

### Post by aysiu on 2006-07-16
That's weird. According to this page, there is an AMD64 build of that package:
[http://packages.ubuntu.com/dapper/libs/sun-java5-bin](http://packages.ubuntu.com/dapper/libs/sun-java5-bin)

Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by fatsheep on 2006-07-16
Yep, here's the output:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


By the way, I downloaded sun-java5-bin_1.5.0-06-1_amd64.deb from the link in your post and when I tried to run it, it gave me this message:

> Error: Wrong architecture 'amd64'

That's really strange. :-k

---

### Post by aysiu on 2006-07-16
The only multiverse I see in there is for the backports, not the regular repositories.

Try getting a fresh sources.list and trying again:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by fatsheep on 2006-07-16
> **aysiu said:**
> The only multiverse I see in there is for the backports, not the regular repositories.

Try getting a fresh sources.list and trying again:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Done but it's still giving me this message from the add/remove:

> 'sun-java5-bin' is not available in any software channel

The application might not support your system architecture.

---

### Post by aysiu on 2006-07-16
You're using Add/Remove.

Can you try installing from the command-line and see if that makes a difference? I'm not sure Add/Remove has a **Reload** button. I know Synaptic Package Manager does. You can try that, too. ```
sudo aptitude update
sudo aptitude install sun-java5-bin
```

---

### Post by fatsheep on 2006-07-16
Here's my results on the manual install 

> root@fatsheep-desktop:/home/fatsheep# sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [42.8kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [24.9kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [36.8kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4558B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [9118B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6951B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [902B]
Fetched 209kB in 2s (78.5kB/s)
Reading package lists... Done
root@fatsheep-desktop:/home/fatsheep# sudo aptitude install sun-java5-bin
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
[B]Couldn't find any package whose name or description matched "sun-java5-bin"
No packages will be installed, upgraded, or removed.[/B]
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


I tried both the add/remove and manual install a second time after reloading from the synaptic package manager with identical results.

---

### Post by tuxcantfly on 2006-07-16
have you added the multiverse repository?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by fatsheep on 2006-07-16
Yes I have added all of the respositories in software properties.

EDIT: 

Hmm I just went into the synaptic manager and re-enabled the multiverse repository and it works now.  :p

Thanks guys, I'm installing Java now.

---

### Post by aysiu on 2006-07-16
There's no way to tell Add/Remove that you have new repositories enabled. It's too simple an interface.

You have to do that through Synaptic Package Manager or the command-line.

Every time you add or remove repositories, you have to "reload" or "update" your repositories list so that the package manager knows where to look for stuff.

Well, glad it worked out.

---

### Post by fatsheep on 2006-07-16
> There's no way to tell Add/Remove that you have new repositories enabled. It's too simple an interface.

You have to do that through Synaptic Package Manager or the command-line.

Every time you add or remove repositories, you have to "reload" or "update" your repositories list so that the package manager knows where to look for stuff.

Thanks I will remember that in the future.  Don't wanna spend 2 hours installating Java again haha. 

> Well, glad it worked out.

Me too. ;)

---

### Post by sherlock-holmes on 2006-07-21
i installed java using sudo aptitude install sun-java5-jre

it says java 1.5 is installed... but when i try java --version on the command line i get 1.4.2... 
is there anything wrong? how to remove 1.4.2 from my system?

thanks

---

