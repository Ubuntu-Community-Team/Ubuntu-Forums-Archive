---
title: "What does this mean?????"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-09-04
I was wanting to play a dvd on my ubuntu computer and I got an error message about the DVD being encrypted and that I needed libdvdcss.  I then decided to install it using apt-get and got this message:

neogreen@ubuntulinux:~$ sudo apt-get install libdvdcss
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages ( /var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i 386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package libdvdcss has no installation candidate
neogreen@ubuntulinux:~$
I then ran apt-get update but still got the same response.  What is cipherfunk?  Can some one shed some light on this.](*,)

---

### Post by Anduu on 2006-09-04
If I am not mistaken Cipherfunk is no more...the maintainer packed up and went home.

I am not sure which repos have the dvd stuff but I know Automatix can set you up.

---

### Post by NeoGreen on 2006-09-05
That figures why I can't get any updates or update to Dapper. How exactly can I update or change my repos?  :(

---

### Post by NeoGreen on 2006-09-06
I found that Automatix website, but I have question on the installing part.  Where exactly on the source list do I input the deb http//www.getautomatix.com/apt, it has several places to input it.  At the beginning or close to the end?  :confused:

---

### Post by az on 2006-09-06
> **NeoGreen said:**
> That figures why I can't get any updates or update to Dapper. How exactly can I update or change my repos?  :(

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Enable universe and multiverse:
[https://help.ubuntu.com/community/RestrictedFormats#head-c675e53915a0137a1c1e61237d136910f3966486](https://help.ubuntu.com/community/RestrictedFormats#head-c675e53915a0137a1c1e61237d136910f3966486)

---

### Post by NeoGreen on 2006-09-06
This is crazy, what I did was changed from cipherfunk to automatix on the source list.  I then decided to run automatix to see if I could get the libdvdcss.  After running it I got a message about it being illegal to download and install w32codecs, libdvdcss2 and other non-free codecs without paying a fee to the concerned authorities constitutes a CRIME in the United States. What does this mean???:confused:

---

### Post by land0 on 2006-09-06
It means that if you live within the USA **USE AT YOUR OWN RISK**. Or if you live in the USA and have an activist heart you could contact your representative. [http://lobby4linux.com/](http://lobby4linux.com/) has a good article on thier front page on how best to do this. (You may have to scroll down a bit) :)

---

### Post by Anduu on 2006-09-06
Well you learn something new every day...I wasn't aware that Automatix would not imstall libdvdcss.

I used the Restricted formats wiki myself but I thought Automatix would be easier for a newcomer.Sorry to steer you in the wrong direction :oops:

---

### Post by land0 on 2006-09-11
It's not that Auotomatix will not install libdvdcss. It is that if you live in the USA and you install it you could "potentially" get in trouble. The Automatix people by warning you of this are saying that they are not resposible. So technically you did not steer anyone in the wrong direction. ;)

---

### Post by Metacarpal on 2006-09-11
Automatix will do it, they're just warning about potential copyright and patent problems.  Realistically, you're probably not going to have any police pounding on your door if you install it.  That warning is just given to ensure that everything presented is 100% above-the-board legal.

Alternately, if you want to update your sources.list to get the non-free codecs and such, [here's a guide]("http://www.psychocats.net/ubuntu/sources") using the PLF repos instead of cipherfunk.

---

### Post by Anduu on 2006-09-11
Heh...I guess I should have clued in that it was just a disclaimer...duh.

---

### Post by NeoGreen on 2006-09-12
I went ahead and used it, I just didn't choose any updates that asked for a fee.:D

---

### Post by NeoGreen on 2006-09-12
What really gets me is that Linux is supposed to be free for everyone to use.  Why create programs that people can use on Linux and charge money.  I would have paid if someone was to ask me for a donation instead of threatening me with legal action if I download their program and not pay.

---

### Post by argie on 2006-09-12
> **NeoGreen said:**
> What really gets me is that Linux is supposed to be free for everyone to use.  Why create programs that people can use on Linux and charge money.  I would have paid if someone was to ask me for a donation instead of threatening me with legal action if I download their program and not pay.

The money's not for the people who made it possible to use, it's for the people owning the licences on the stuff that's illegal in the US.

Better them warning you about it than you doing it thinking it's all free and good.

---

