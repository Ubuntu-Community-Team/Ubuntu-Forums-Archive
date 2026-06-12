---
title: "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-17
Tried to install the Kubuntu desktop from the command line, and got the above error message. (Plugged it into the forum's search engine and got no hits, either.)

So, I'm running apt-get update right now, but what have I screwed up? Should I rerun apt-get install kubuntu-desktop?

---

### Post by patrick295767 on 2005-10-17
[QUOTE=editrix]Tried to install the Kubuntu desktop from the command line, and got the above error message. (Plugged it into the forum's search engine and got no hits, either.)

So, I'm running apt-get update right now, but what have I screwed up? Should I rerun apt-get install kubuntu-desktop?[/QUOTE]


My progress thread can maybe help you ... maybe [http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557)

I hope !

Pat'

---

### Post by patrick295767 on 2005-10-17
[QUOTE=editrix]Tried to install the Kubuntu desktop from the command line, and got the above error message. (Plugged it into the forum's search engine and got no hits, either.)

So, I'm running apt-get update right now, but what have I screwed up? Should I rerun apt-get install kubuntu-desktop?[/QUOTE]


u can maybe try several times: 
apt-get -f install

apt-get install 

if not working, check in my previous thread, I guess there is a copy of my 
/etc/apt/sources.list
then do : 
apt-get update

then, 
u can go on installing ... 
apt-get install my_prog_to_be_installed

---

### Post by editrix on 2005-10-18
Hi Patrick:

Wow! Your progress thread is too complicated for me. But I think I understood the apt-get -f install. The -f is for "fix"? Man pages aren't very easy to understand. Anyway, will try, thanks.

---

### Post by Murgle on 2005-10-18
one thing to check that alot of people have been ahving trouble with is that the us archives are being funky, if you use them just remove the us. in front of them in your /etc/apt/sorces.list and then reupdate

---

### Post by editrix on 2005-10-18
[QUOTE=Murgle]one thing to check that alot of people have been ahving trouble with is that the us archives are being funky, if you use them just remove the us. in front of them in your /etc/apt/sorces.list and then reupdate[/QUOTE]

Well, here I am back in Windows because something was going terribly wrong with the updates--like 900 bytes per second. I'll bet this was it. Thanks.

---

