---
title: "How do I install anjuta?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by wwuster on 2006-01-11
I can't find this in the synaptic list, but I read references to people running it in Ubuntu. How do you install this?

thanks,
William

---

### Post by mustang on 2006-01-11
Did you try 

```
sudo apt-get install anjuta
```

?

If that doesn't work, search around on the forums how to modify your sources.list to add the other repositories. Be sure to apt-get update afterwards.

---

### Post by wwuster on 2006-01-11
I didn't even know that you could do it that way. I tried it but I get

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package anjuta

---

### Post by Buffalo Soldier on 2006-01-11
First you have to enable the Universe repository
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

here's a link to the user documentation site [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by wwuster on 2006-01-11
I looked at the howto but I just don't see any "community maintained" universe items here. I must be doing something wrong, but not sure what. I did check the "display hidden items" (or whatever it is called). Is this howto up to date?

William

---

### Post by Buffalo Soldier on 2006-01-11
What's the content of your **/etc/apt/sources.list** file? Paste it here and me or someone in here can show you what to change to that file to enable your universe repository.

---

### Post by Sef on 2006-01-12
> I looked at the how to but I just don't see any "community maintained" universe items here.

To get to Universe and Multiverse, follow these directions.

System ----> Administration ----> Synaptic Package Manager ----> Password      ----> Settings ----> Repositories -----> Add ----> Check Community Maintained (Universe) and Non-free (Multiverse) -----> Click on ok ----> Click on ok again       ----> Click on Yes ----> When it finishes up grading they will be added.

---

### Post by wwuster on 2006-01-12
Here is sources.list. I didn't know about it (I've been told that synaptic is the official package manager). I see the comments about uncommenting universe and multiverse. Which ones should I uncomment? Is there anything wrong with uncommenting everything?


deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by wwuster on 2006-01-12
[QUOTE=Sef]To get to Universe and Multiverse, follow these directions.

System ----> Administration ----> Synaptic Package Manager ----> Password      ----> Settings ----> Repositories -----> Add ----> Check Community Maintained (Universe) and Non-free (Multiverse) -----> Click on ok ----> Click on ok again       ----> Click on Yes ----> When it finishes up grading they will be added.[/QUOTE]

Thanks. That worked. The other instructions that I read didn't work.

---

