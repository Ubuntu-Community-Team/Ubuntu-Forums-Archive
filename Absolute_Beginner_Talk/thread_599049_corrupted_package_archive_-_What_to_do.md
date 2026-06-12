---
title: "corrupted package archive - What to do?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by the_rajah on 2007-10-31
I've got the little icon showing that indicates that I've got updates available. The only update that shows up when I click on it is for libpng. When I try to do the update I get an error message that says: "E: /var/cache/apt/archives/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb: corrupted filesystem tarfile - corrupted package archive"

I've tried everything I could think of as a relative newbie and I'm stuck. 

I went into su mode in the command line and tried to delete the file as was suggested in another thread here, but permission is denied. What's next? I've tried searching here and don't get any useful answers other than to delete the archive, which doesn't work, so It's time to ask after fighting this for several days.

I figure that if I just re-install, I won't learn anything about what to do the next time it happens. Help!! :confused:

Thanks!

---

### Post by overdrank on 2007-10-31
> **the_rajah said:**
> I've got the little icon showing that indicates that I've got updates available. The only update that shows up when I click on it is for libpng. When I try to do the update I get an error message that says: "E: /var/cache/apt/archives/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb: corrupted filesystem tarfile - corrupted package archive"

I've tried everything I could think of as a relative newbie and I'm stuck. 

I went into su mode in the command line and tried to delete the file as was suggested in another thread here, but permission is denied. What's next? I've tried searching here and don't get any useful answers other than to delete the archive, which doesn't work, so It's time to ask after fighting this for several days.

I figure that if I just re-install, I won't learn anything about what to do the next time it happens. Help!! :confused:

Thanks!
Hi could you post the output of these commands in the terminal
```
sudo apt-get upgrade
cat /etc/apt/sources.list
 
```

---

### Post by the_rajah on 2007-10-31
I get:

[sudo] password for roger:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libpng12-0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/188kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 95701 files and directories currently installed.)
Preparing to replace libpng12-0 1.2.15~beta5-2build1 (using .../libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb) ...
Ignoring nonregistered document libpng12
Unpacking replacement libpng12-0 ...
dpkg: error processing /var/cache/apt/archives/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 /var/cache/apt/archives/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
roger@roger-ubuntu:/var/cache/apt/archives$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main
roger@roger-ubuntu:/var/cache/apt/archives$ 


Thanks for the quick reply.. :-)

---

### Post by overdrank on 2007-10-31
Ok you may and try to get a fresh source.list
[http://www.psychocats.net/ubuntu/sources#editfile](http://www.psychocats.net/ubuntu/sources#editfile)
and then try and update again. Hope this helps good luck!

---

### Post by the_rajah on 2007-10-31
I updated the list per the instructions. When I started the update, I got:

[INDENT]"http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz: 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz:) 404 Not Found"[/INDENT]

and then got the original corrupted package message when I attempted to apply the updates. 

I'm still stumped.. :(   BTW, I'm running Gutsy inside VIrtualBox on Windows XP at work and it did this update just fine there today.  The machine I'm having trouble with is a Dell E520N that I bought with 7.04 pre-installed. I was already running 7.04 on another PIII machine here, but wanted to vote with my wallet for preinstalled consumer Linux. :-)  Besides, I got this nice core2 duo machine.

Thanks again for your help.

---

### Post by overdrank on 2007-11-01
Try and remove that libpng12 with the command 
```
sudo apt-get remove --purge libpng12

```
And comment out the medibuntu in your source.list with a # and this command will get you to edit it
```
gksudo gedit /etc/apt/sources.list
```
Then update and upgrade again
```
sudo apt-get update && sudo apt-get upgrade
```
Hope this helps. Good luck!

---

### Post by the_rajah on 2007-11-01
Running the first command gives the result:

[INDENT]roger@roger-ubuntu:/var/cache/apt/archives$ sudo apt-get remove --purge libpng12
[sudo] password for roger:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libpng12[/INDENT]

So it didn't work.

Speaking of not working.. I have to get up at 6:30 to go to work in the morning and it's after 11 here. I'll check back tomorrow.

Thanks so much for the help. It's people like you that make OSS tick.

---

### Post by overdrank on 2007-11-01
> **the_rajah said:**
> Running the first command gives the result:

[INDENT]roger@roger-ubuntu:/var/cache/apt/archives$ sudo apt-get remove --purge libpng12
[sudo] password for roger:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libpng12[/INDENT]

So it didn't work.

Speaking of not working.. I have to get up at 6:30 to go to work in the morning and it's after 11 here. I'll check back tomorrow.

Thanks so much for the help. It's people like you that make OSS tick.

I understand same time here, I am glad I put the wrong command in the quotes because I just ran it on my Feisty system and that would uninstall a bunch of stuff. SO DO NOT USE THAT COMMAND This is over my head so maybe someone else will pop in tomorrow. Good luck!

---

### Post by Jaco Du Toit on 2007-11-01
EDIT: OK I see you did try this. Wonder why you get permission denied though...

It looks like it isn't even trying to download the new package because it already thinks that it has it... Anyways, have you tried removing the corrupted package from the command line? (My apologies if you did and I just didn't see it)

From the command line type:

> cd /var/cache/apt/archives

Then type:

> sudo rm libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb

Then try the whole sudo apt-get update and sudo apt-get upgrade thing again

---

### Post by the_rajah on 2007-11-02
Thanks! That worked. It was just a matter of deleting the corrupted archive which I tried before, but did something wrong since it wouldn't let me. Oh, well. Perisitence pays. :)

I'd mark this [SOLVED], but i'm not sure how to do that.

---

### Post by overdrank on 2007-11-02
> **the_rajah said:**
> Thanks! That worked. It was just a matter of deleting the corrupted archive which I tried before, but did something wrong since it wouldn't let me. Oh, well. Perisitence pays. :)

I'd mark this [SOLVED], but i'm not sure how to do that.

Great glad to hear and you can mark it solved under thread tools. Good luck!

---

