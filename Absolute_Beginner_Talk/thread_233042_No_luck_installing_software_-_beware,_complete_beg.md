---
title: "No luck installing software - beware, complete beginner"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by tom-ub on 2006-08-09
Hi All,

Got Ubuntu working fine. Struggled with slow internet on Firefox but I'm now over that. My problem is installing addition software, either by the terminal or by the packages program.

To give you some context, I want to install some of the programs which have been recommended here: 
[http://diveintomark.org/archives/2006/06/26/essentials-2006](http://diveintomark.org/archives/2006/06/26/essentials-2006)
<A HREF="http://diveintomark.org/archives/2006/06/26/essentials-2006">http://diveintomark.org/archives/2006/06/26/essentials-2006</A>
However, when i enter:

sudo apt-get install amarok

I get 

~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package amarok

As far as I know I have the correct packages available. I have also had message saying no installation candidate. I'm sure this is really simple but I just can't see what I'm doing wrong.

When I

~$ sudo gedit /etc/apt/sources.list


i get

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 


Any help would be gratefully received. I like Ubuntu so far and it seems good enough to become my main operating system.

Thanks

Tom

---

### Post by Fondor1 on 2006-08-09
type in:
```

sudo apt-get update
```

Then try installing amarok again :)

---

### Post by Kobalt on 2006-08-09
You need to run the command "sudo apt-get update" anytime you add new repositories to your sources.list, before you can install a software from that repository. 

Cheers  ! :rolleyes:

---

### Post by tom-ub on 2006-08-09
ok thanks. I'll try that now. it's usual for these things to take a while? ie/ 20 mins?

---

### Post by Engnome on 2006-08-09
> **tom-ub said:**
> ok thanks. I'll try that now. it's usual for these things to take a while? ie/ 20 mins?

nope, less than 20 seconds here. (adsl)

---

### Post by tom-ub on 2006-08-09
I am on ADSL too. 8meg. Do you know anything I can do to speed it up? It seems to be doing it at 446b/s?!

---

### Post by Brunellus on 2006-08-09
probably worth trying another apt repository mirror

---

### Post by tom-ub on 2006-08-09
do you have a link to a list?

---

### Post by tom-ub on 2006-08-09
still no luck! this is so frustrating... i don't know what i am doing wrong.




E: Some index files failed to download, they have been ignored, or old ones used instead.
~$ sudo apt-get install amarok
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package amarok

---

### Post by tom-ub on 2006-08-09
Mirror servers
The bandwidth of the main Ubuntu server is not infinite. If you have a very low transfer rate,
it is advisable for you to use a mirror. You can find a list of mirrors at
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive) (this list hasn't been reviewed for a long time and some of
these servers may be down). It was made for warty, but notice that these servers are regularly
synced with the main server, so you will find breezy packages there as well. Try to find a
server which is located somewhere in your country or somewhere close to you.
You will probably ask how to use a mirror instead of the main Ubuntu repository. It's quite
simple. First find a server suitable for you (e.g.choose one from here
[https://wiki.ubuntu.com/Archive)](https://wiki.ubuntu.com/Archive)). I will use a German mirror as an example -
[http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/).
Open up a terminal
1.
sudo gedit /etc/apt/sources.list
2.
and now modify the address of the server. if you used the default settings shown above
you will see
3.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse
restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse
restricted
just change it to
deb [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) breezy main universe multiverse
restricted
deb-src [http://debian.charite.de/ubuntu/](http://debian.charite.de/ubuntu/) breezy main universe multiverse
restricted
sudo apt-get update

---

