---
title: "intalling automatix"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-28
Ok well basically i followed the install guide over at getautomatix.com thinking that it was for 7.4 (because im a complete moron) but it was actually for 7.10 so i uninstalled it after realising and tried to install the 7.4 version but now it will only install the gutsy version?

Please help.....im using kubuntu 7.4

o yer whats the deal with there website because i can only access it after like 9 at night otherwise i get a timed out notice:confused:

---

### Post by Daveth on 2007-10-28
probably worth reading this first....

[https://help.ubuntu.com/community/Automatix](https://help.ubuntu.com/community/Automatix)

---

### Post by carusoswi on 2007-10-28
> **kamitsukai said:**
> Ok well basically i followed the install guide over at getautomatix.com thinking that it was for 7.4 (because im a complete moron) but it was actually for 7.10 so i uninstalled it after realising and tried to install the 7.4 version but now it will only install the gutsy version?

Please help.....im using kubuntu 7.4

o yer whats the deal with there website because i can only access it after like 9 at night otherwise i get a timed out notice:confused:

You will probably not get much help here in the community.  There seems to have been almost a revolt against Automatx here.  It's not supported . . . plenty claim it's of no benefit, many claim it will break things.

Go to the Automatx site and search or post in the forums there.  You should get the help you need.

FWIW, it appears that an effort is being made by the Automatx team to address the critics here and heal the wounds that caused the riff.  I hope the healing goes both ways.

I don't really care what I need to do to get my machine working.  If I find that I can live without Automatx when I upgrade to 7.10, then so be it.  I do feel that most of the chorus rant against it was unsubstantiated with plenty of piling on.

I'd be curious if you tried to add Automatx because you were having problems or because you have always approached Ubuntu with Automatx in mind.

For certain, Automatx for 7.04 is not compatible with Ubuntu 7.10.  You cannot upgrade from 7.04 to 7.10 if your 7.04 install includes anything installed by Automatx for 7.10.

Good luck.

. . . and happy computing.

Caruso

---

### Post by Kosimo on 2007-10-28
Why do you need to use Automatix?

---

### Post by gn2 on 2007-10-28
> **carusoswi said:**
> You cannot upgrade from 7.04 to 7.10 if your 7.04 install includes anything installed by Automatx for 7.10.

My desktop PC which has Automatix upgraded from 7.04 to 7.10 no problems at all.
My laptop which doesn't have Automatix would not run properly after same upgrade.

Generally speaking I have had fewer problems with the Automatix PC than the non-Automatix laptop.

Others however may have had different experiences......

---

### Post by shadowtroopers on 2007-10-28
just now i try to install automatix, seem to be my system clashed after that. Below are the details:

mm@mm-desktop:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
--19:37:21--  [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
           => `automatix2.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 208.67.219.132

Connecting to www.getautomatix.com|208.67.219.132|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://guide.opendns.com/?url=www.getautomatix.com%2Fkeys%2Fautomatix2.key&servfail](http://guide.opendns.com/?url=www.getautomatix.com%2Fkeys%2Fautomatix2.key&servfail) [following]
--19:38:01--  [http://guide.opendns.com/?url=www.getautomatix.com%2Fkeys%2Fautomatix2.key&servfail](http://guide.opendns.com/?url=www.getautomatix.com%2Fkeys%2Fautomatix2.key&servfail)
           => `index.html?url=www.getautomatix.com%2Fkeys%2Fautomatix2.key&servfail.2'
Resolving guide.opendns.com... 208.67.219.131
Connecting to guide.opendns.com|208.67.219.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 1,929         --.--K/s             

19:38:05 (777.81 KB/s) - `index.html?url=www.getautomatix.com%2Fkeys%2Fautomatix2.key&servfail.2' saved [1929]

mm@mm-desktop:~$ gpg --import automatix2.key
gpg: can't open `automatix2.key': No such file or directory
gpg: Total number processed: 0

then i stopped there, then this is what i get after the process:

mm@mm-desktop:~$ sudo apt-get update
E: Type '&#8220;deb' is not known on line 38 in source list /etc/apt/sources.list

right now i can't even use "add/ remove programme" there's an error stated that:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

and this is the error message that i got when open the synaptic:
E: Type '&#8220;deb' is not known on line 38 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i follow the instruction but still getting the same problem. can anyone help me out, i'm running ubuntu 7.10.

---

### Post by n3tfury on 2007-10-28
i have to add my .02 and say that automatix is mostly rubbish.  bit hard to troubleshoot issues from installing it.

---

### Post by kamitsukai on 2007-10-28
thanx everyone and im in total agreement with carusoswi about doing anything to get a machine working :P

---

### Post by por100pre1 on 2007-10-28
No need to use Automatix, read [this]("http://ubuntuforums.org/showthread.php?t=413625") carefully. Let us know if you need anything else. :)

---

### Post by shadowtroopers on 2007-10-28
right now i can't even use my synaptic and "add and remove" programme. It's conflict somewhere. Is there any method on how to revert this?

---

### Post by Incense on 2007-10-28
> **shadowtroopers said:**
> 

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

and this is the error message that i got when open the synaptic:
E: Type '“deb' is not known on line 38 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i follow the instruction but still getting the same problem. can anyone help me out, i'm running ubuntu 7.10.

Looks like you messed up the repos a bit. Run from the term

```
gksu gedit /etc/apt/sources.list
```

Find line 38 and fix the entry so you don't have the " in front of the deb. You need to comment it out with a # or have it open with nothing in front of it. Then save and run.

```
sudo apt-get update && sudo apt-get install -f
```

hope that helps.

---

