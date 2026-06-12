---
title: "Updating Gaim"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-17
The newest version of gaim is 2.0b6 - ubuntu 6.10 edgy came with 2.0b3 installed.  Is it possible to update gaim to 2.0b6 and if so, how would I do it?

On a similar note - I use gaim for irc.  Is it possible to make gaim autojoin #ubuntu when it opens?

---

### Post by nsn3 on 2007-03-17
Enter synaptic (System>Admin>Snynaptic) and find Gaim.

Then left-click on it and check if "Mark for Upgrade" is available.

---

### Post by meborc on 2007-03-17
that is not going to help, as the beta6 is only in feisty repos at the moment... to get the 2beta6 for edgy, there is a quick way on [www.debuntu.org](www.debuntu.org) :) (instructions here - [http://repository.debuntu.org/](http://repository.debuntu.org/))

---

### Post by wheezer on 2007-12-22
I would liike to upgrade to 2.3, but it's not in synaptic, and I don't feel like spending an hour learning how do to build it,  Is there one of those handy links or commands that will just do it for me without forcing me to spend my work time learning yet one more upgrade methodology? Pidgin seems to give you one big tar, and assumes you know all about compiling things in linux.  I don't

Any pointers here?

---

### Post by nowshining on 2007-12-22
go to my website, i just put today a howtwo get the newest pidgin, gaim and gimp at least for gutsy, just change gutsy to feisty and maybe itta work on other versions of ubuntu too, i don't know tho. :) site is in sig.

---

### Post by wheezer on 2007-12-22
> **nowshining said:**
> go to my website, i just put today a howtwo get the newest pidgin, gaim and gimp at least for gutsy, just change gutsy to feisty and maybe itta work on other versions of ubuntu too, i don't know tho. :) site is in sig.

Thanks, but i cant' find any such thing on your site. A lot of random stuff, and some pidgin link that doesnt' seem to be about updating.

---

### Post by nowshining on 2007-12-22
pidgin is gaim, renamed, new and improved. :)

a lot are tips, fixes and howtwos, and yes it does update it to the newest version. I found it off another site - compiling pidgin didn't work for me - 2.3.1 and so such found that link searching on ixquick.com

[http://www.thinkdigit.com/forum/showthread.php?t=74267](http://www.thinkdigit.com/forum/showthread.php?t=74267)

---

### Post by wheezer on 2007-12-22
> **nowshining said:**
> pidgin is gaim, renamed, new and improved. :)

a lot are tips, fixes and howtwos, and yes it does update it to the newest version. I found it off another site - compiling pidgin didn't work for me - 2.3.1 and so such found that link searching on ixquick.com

[http://www.thinkdigit.com/forum/showthread.php?t=74267](http://www.thinkdigit.com/forum/showthread.php?t=74267)

Shinging,

Now you give me a link to another forum, with about 3 dozen posts, each differing on how to do something, and not remotely clear as to whether it works or not.  I do appreciate your effort to reply, but this kind of response is not really that helpful.  You direct me to things you yourself dont' really know for sure work, and your replies make others think my question is answered.  If you actually want to help, why not post a concise, tested response with exactly the right command.  It seems more like you are posting mostly to promote your site. If you can answer me clearly and concisely., I am sure many will appreciate it. Thanks

---

### Post by nowshining on 2007-12-22
sorry but

"Did you do sudo apt-get build-dep pidgin ?

Also just add this repo: "deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) gutsy main" to you /etc/apt/sources.list

And import the key: "wget [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg) -O- | sudo apt-key add -"

This repo contains latest versions of Rhythmbox and Pidgin.. It should have Pidgin 2.3 in a day or two..
__________________
The best way to accelerate a computer running Windows is at 9.81 m/s²
"


that's the post  - 2nd one i got on how to update pidgin to the newest version for gutsy

If u go into the link tho they posted there is another named feisty for the feisty series. 

by the way the how to updated was at the very bottom - last one tip #45. I made it as easy as possible.


or

u can compile it urself, the compile did not work out for me so that's the way i got 2.3.1.

---

### Post by wheezer on 2007-12-23
Thanks

As I am still using feisty (too afraid to update that while doing real work), I think i am going to assume that this version is just not stable enough for someone to update synaptic.  Who makes those decisions. Do you know? When can i expect pidgin 2.3 to be available that way?

---

### Post by nowshining on 2007-12-23
sorry wheezer u don't get updated version of programs thru ubuntu, only security updates, and maybe a bug fix here and there, but not new features, sorry :( u'l have to update to the latest version of ubuntu to get the latest.

Altho there is backports that can be enabled thru the sources gui via a check mark. It is unknown whether a new version is going to get backported or not.  :(

---

