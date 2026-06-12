---
title: "Problems installing gcc"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by moofdaddy on 2006-09-08
Greetings,
I'm trying to install gcc through a variety of sources and I keep hitting a wall. Every method I try prompts me to insert the draper-drake-amd64 cd (which I thought I got in the mail but when I put it in the disk isn't recognized).  This happends when I download the package file from the ubuntu package site and also when I use apt-get.  

There are other things I would like to install but I can't build them from source till I get this done.  Any idea why it keeps asking for a CD and won't just find the parts it needs online?

---

### Post by davmac on 2006-09-08
I think this might be a problem with your apt sources list.

Could you open up a terminal and type "cat /etc/apt/sources.list" and paste the results back into a response.

Alternatively if you can see a line in this file that refers to the CD try editing it ("sudo gedit /etc/apt/sources.list") and commenting out the offending line by prefixing it with "#".

Hope this helps,

Dave Mac

---

### Post by davmac on 2006-09-08
Forgot to mention, once you do get this problem resolved, the easiest way of installing all you want is "sudo apt-get install build-essential" of using synaptic to install build-essential.

Dave Mac

---

### Post by moofdaddy on 2006-09-08
Here is my sources list:

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

So I should comment out the line looking at the CD?

---

### Post by moofdaddy on 2006-09-08
I commented out the CD line and things seem to be working now.  Thanks!

---

### Post by davmac on 2006-09-08
Yes. I'd comment out the first line. For my sources.list, I have also uncommented all of the other lines that start "deb...", giving  access to a much wider repository of software.

Once you've saved it, type "sudo apt-get update" followed by "sudo apt-get upgrade" and it'll get everything up to date. Follow that with sudo apt-get install build-essential" and you should have everything you need to compile from source.

Hope this helps,

Dave Mac

---

