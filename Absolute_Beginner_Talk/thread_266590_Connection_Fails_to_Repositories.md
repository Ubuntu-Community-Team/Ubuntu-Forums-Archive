---
title: "Connection Fails to Repositories"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by wolfmark on 2006-09-27
](*,) 

I have tried for 3 days to use Synaptics Package Manager to download packages for my Dapper 6.06.1 install without success.  I have tried several different things found in searches on the forums here, unsuccessfully.  I am a noob with Ubuntu specifically and Linux in general, so I am sure there is something I am missing.

Here is the message I have gotten from the start of this:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.23 80]

In this particular instance, you can see I have not removed the "us." from the sources.lst file in /etc/apt but in previous instances I have, resulting in the same error (minus the "us." obviously).  Whether I run from a terminal or the GUI, I get the same error.

I can successfully navigate both my LAN and the internet with HTTP and FTP, setup Windows printers and print to them, and do everything I want except this.  I have even gone so far as to put my Ubuntu installation in the DMZ of my DSL router (a Linksys WRT54G), setting resolv.conf in /etc to my provider's DNS servers, all with no success.  I have installed both from the Ubuntu LiveCD and the alternate installation, with no success with this.  I can also ping the respository servers and navigate to them using Firefox and access the files found there.  This is very frustrating.

Do I need to add a service to my router by chance?

Please help!

---

### Post by Marsolin on 2006-09-27
Can you open the /etc/apt/sources.list file and post the contents? It is just a text file. It's possible something got messed up in it.

Can you access [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) from a web browser?

---

### Post by wolfmark on 2006-09-27
My sources.list file:

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Yes, using Firefox, I can access the repositories archive.ubuntu.com and security.ubuntu.com/.  I can ping them as well.

Thinking about what I'd said in my first post, obviously I don't need to add a service port to my router as Synaptic is using HTTP.

---

### Post by Marsolin on 2006-09-27
I have the us.archive.ubuntu.com part in mine, but other than that they are the same. And you already mentioned trying it both ways.

I'm not sure what the problem is right now. You seem to have tried the appropriate steps. If I think of anything I'll let you know.  Hopefully someone else will figure it out.

---

### Post by wolfmark on 2006-09-27
I agree, hopefully someone can come up with something.  As it is, I find Ubuntu useless to me without this process working.

One thought, could there be some sort of trust or authentication problems between me and the repositories?

Thanks Marsolin for the help.

---

### Post by wolfmark on 2006-09-27
Thought I'd post another error message, this one garnered from the software updates app that runs (which I assume uses apt in the background):

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)
  Connection failed [IP: 146.137.96.15 80]

Again, I can navigate to the url above in Firefox by IP and address.  Any thoughts on privileges/trust/authentication?

---

### Post by Marsolin on 2006-09-27
Try running the following command.

sudo apt-get --allow-unauthenticated update

That should make sure that any authentication or permissions are taken care of.

---

### Post by odinfromvalhalla on 2006-09-27
try replacing us. with en.

it happens sometimes that my local mirror is down (ro.) and changing to e. solves the problem.

---

### Post by wolfmark on 2006-09-28
Marsolin -- tried the --allow-unauthenticated option, no cigar, same error messages.

odin -- Changing us. to en. (or any xx.) seems only to make the errors occur more slowly, some more slowly than others.  Guess I could calculate network lag and congestion from it, but no packages unfortunately.

Thanks to both of you for your suggestions.  I am still looking for a solution and welcome any suggestions.

---

### Post by wolfmark on 2006-09-28
This one can be put to bed!

The install placed a line in my /etc/apt/apt.conf that said:

Acquire::http::Proxy "false";

When I looked at this days ago, I thought it was stating a proxy wasn't required, or was "false" meaning I didn't have a proxy.  Instead, it makes apt look for a proxy called "false".

I removed the line completely and viola', success!

I would think lots of people would be having this problem.  Either there are many people behind proxies where they've had to change the proxy entry in the GUI or network settings and it's written over the line above, or they just haven't realized there's a problem.

Thanks for the help guys and girls.  I found this solution in the thread [http://www.ubuntuforums.org/showthread.php?t=257988&page=2](http://www.ubuntuforums.org/showthread.php?t=257988&page=2)

---

### Post by morfy on 2006-09-28
hey how do i an where do i put this info. In terminal? if so do i say sudo first???

---

### Post by sadalmelik57 on 2006-09-28
If by "Lots of People" you are including me, you are right on target!  I was getting the same errors and found the same entry and erased it and all the repositories load now.  EXCELLENT!

---

### Post by morfy on 2006-09-28
I tried this and it still doesnt work. This is the error messages I get from Synaptic: Has anyone got more ideas???????????????????

[http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by Roobert on 2006-11-02
THANK YOU! This is *exactly * the problem I was having! :-D

---

### Post by Bartender on 2006-11-02
Good job, wolfmark.  I wonder what this setting does and why it affects some but not others?

---

