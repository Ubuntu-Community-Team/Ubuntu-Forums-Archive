---
title: "Ubuntu without the Internet"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by seyyah on 2006-06-22
Hello all,
I am plannin to install Ubuntu, but I'm a bit hesitant because it will be on a computer without Internet access. Will it be easy enough to install & maintain offline? I'll have to bring packages over on a memorystick ... is this feasible?
Thanks!

---

### Post by mips on 2006-06-22
As far as i'm concerned it is a pain in the *** to do anything without internet access on ubuntu. I would rather use debian or something of the kind where I can get all the install cd's

---

### Post by bluenova on 2006-06-22
For a basic setup it would be fine, I have setup a machine with xubuntu in a language other than English and all was ok. I think it would be quite hard to install other software though because of dependencies.

---

### Post by christhemonkey on 2006-06-22
I do this regularly.
I have 3 ubuntu machines all offline (due to untrusting parents....:p)
and when i want to installl something new, i just find it on packages.ubuntu.com and then put it on my memory stick.
Although you do have to make sure to get *all* of its dependencies!

I think it is a viable option to use ubuntu offline.  Although you dont really get the full experience imho.


Just my £0.02.

---

### Post by mips on 2006-06-22
Would be nice if Synaptic/Adept/Aptitude etc would allow you to download a package plus depencies to a location of your specification.

---

### Post by MaximB on 2006-06-22
it depends what are you going to do with ubuntu.
if you want it for multimedia and have no internet and no option to download the components (from friends) then don't install ubuntu , cuz you will have to download some codecs from the net to play mp3 and some video files

if you want it for other porpuse (I can't imagane what without internet)
then you have the option to install ubuntu from DVD
2-3 gb of installation that incloud some games and many programs - that is for users with low intenet connection or no internet at all.

---

### Post by djsroknrol on 2006-06-22
I just installed Breezy on a used T21 I got about a week and a half ago and it has no internet access (for right now..going wireless real soon on it).

Like maddark said, it would be tough without it as it depends on internet access for alot of things, but I'm happy to be outside, working on a letter or playing a preloaded game, and checking out all around functionality of the thinkpad for now....

---

### Post by nalmeth on 2006-06-22
> Would be nice if Synaptic/Adept/Aptitude etc would allow you to download a package plus depencies to a location of your specification.
sudo apt-cache clean
sudo apt-get -d install whatever

which only downloads the packages and doesn't install them?

---

### Post by seyyah on 2006-06-23
Thanks for the replies.

First of all, I'd need the multemedia codecs - would that be difficult? What about Wine?

After that, I think the basic distro has most everything I need (OpenOffice etc).

If it's too difficult to do, I might go for another Linux. Someone said Debian is easier without internet... is it much different?

---

### Post by SkyNet2029 on 2006-06-23
> sudo apt-cache clean
sudo apt-get -d install whatever

which only downloads the packages and doesn't install them?

```
$sudo apt-get -d install_whatever
```
will only download and not install.

---

