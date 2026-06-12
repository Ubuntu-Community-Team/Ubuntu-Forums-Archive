---
title: "Dual boot- Ubuntu and Mint"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by crzytoxicant on 2008-02-02
3 Questions:
1)Where can I find the linux mint alternate CD
2) How would I dual boot Linux mint if I'm already running Xubuntu?
3)would I be able to run mint with my current setup (check signature)
Thanks for the help I get.

---

### Post by JoshuaRL on 2008-02-02
1).  I don't think that Linux Mint has an Alternate CD.  They have a Light version, but I think it's a Live CD too.
2).  The installer should have an option to have them guide you through a partitioned installation.  I would go with that.
3).  Should be okay, but you might try the XFCE CE if you want it to run faster.

---

### Post by wolfen69 on 2008-02-02
> Running a 1.0 Ghz processor with 128mb ram, GeForce 2 MX/400 and a 40 GB HD...lol (old compy)

mint will not run on 128ram. you would need at least 384 to run it effectively.
try crunchbang linux(ubuntu based) [http://crunchbang.org/archives/2008/01/22/crunchbang-linux-7-dot-10-dot-01-release-notes/](http://crunchbang.org/archives/2008/01/22/crunchbang-linux-7-dot-10-dot-01-release-notes/)  i just tried it in virtualbox and it was pretty good. it should run on 128ram.

---

### Post by crzytoxicant on 2008-02-02
I've honestly never heard of cruchbang linux.is it just as good as ubuntu, or is it a lil watered down?

---

### Post by JoshuaRL on 2008-02-02
I have no idea about that.  But if you really wanted to try Mint you could always burn an XFCE or Fluxbox version off of their site.  It may not work, but they're easier on resources, especially on the Live CD.  So it might just work.  But I don't know for sure.

---

### Post by crzytoxicant on 2008-02-02
I see. the only problem is I couldn't run the live installer on any of the other distros I tried, that's even with some of the light weight ones too.

---

### Post by JoshuaRL on 2008-02-02
Yeah, I know what you mean.  I have an HP Omnibook that was the same way.  Almost the same specs too.  From what I've seen on my test install of Mint, they aren't nearly as well-developed as Ubuntu.  There isn't a packages.mint.org site, it has problems installing some packages from Ubuntu, and has very few programs to install from their Mint Installer app.

It's pretty and makes it easy to use restricted codecs, but it does have problems.  Not the same as Ubuntu, even though it might be based on it.

---

### Post by jan quark on 2008-02-02
don't make mint bad:(

I am using it and it works well for me
it is based on gutsy, package manager is there so... I am not missing anything so far...
and do not having any problems, but perhaps I am the exception to the rule

---

### Post by JoshuaRL on 2008-02-02
No, it's great for the right person.  I just like Ubuntu better and was outlining the reasons why.

My main gripe is this:
In Ubuntu you can get another, or all, of the desktops by a variety of:
```

sudo apt-get install ubuntu-desktops

```
There is no such version on Mint.  I tried doing the above command on Mint to see if I could get Gnome and got a crapload of dependencies.  And then I did something really stupid and now APT doesn't work.  Not really their fault, but I just had problems.  The user experience was excellent, and again, it is really pretty.  But like all distros it has it's problems too.

---

### Post by crzytoxicant on 2008-02-02
Hmmm I see. wit, what does the 
Code:

sudo apt-get install ubuntu-desktops

do? I know it gets you the different desktops, but where do you find the option of changing the one you use?

---

### Post by sandysandy on 2008-02-02
u can add the mint repositories to ubuntu  as mint is based on ubuntu.

regards

---

### Post by JoshuaRL on 2008-02-02
Yeah, but there's no way to add the desktop from Mint.  Ubuntu has the following three metapackages:
```

ubuntu-desktop
kubuntu-desktop
xubuntu-desktop

```
and they install everything you need to run those DE just as if you installed them separately.  But you can't do that in Mint, from what I've seen.

---

### Post by crzytoxicant on 2008-02-02
hmmm. alright thanks a bunch people. I appreciate all the help. =D

---

### Post by sandysandy on 2008-02-03
> **JoshuaRL said:**
> Yeah, but there's no way to add the desktop from Mint.  Ubuntu has the following three metapackages:
```

ubuntu-desktop
kubuntu-desktop
xubuntu-desktop

```
and they install everything you need to run those DE just as if you installed them separately.  But you can't do that in Mint, from what I've seen.

hi

 i converted Edubuntu 7.10 to Mint. This is the link to the thread.

[http://ubuntuforums.org/showthread.php?t=624064&page=3](http://ubuntuforums.org/showthread.php?t=624064&page=3)

regards

---

### Post by JoshuaRL on 2008-02-03
That's crazy cool.  I was on the Mint Forums trying to see if you could do exactly that and the mod Husse told me that I couldn't.  So sorry for the missinformation, I was uninformed.  I just posted this over there!

[http://linuxmint.com/forum/viewtopic.php?f=54&t=8783&p=57121#p57121](http://linuxmint.com/forum/viewtopic.php?f=54&t=8783&p=57121#p57121)

---

### Post by sandysandy on 2008-02-03
> **JoshuaRL said:**
> That's crazy cool.  I was on the Mint Forums trying to see if you could do exactly that and the mod Husse told me that I couldn't.  So sorry for the missinformation, I was uninformed.  I just posted this over there!

[http://linuxmint.com/forum/viewtopic.php?f=54&t=8783&p=57121#p57121](http://linuxmint.com/forum/viewtopic.php?f=54&t=8783&p=57121#p57121)

you are welcome.

regards

---

### Post by cotcot on 2008-02-03
> **JoshuaRL said:**
> 1).  I don't think that Linux Mint has an Alternate CD.  They have a Light version, but I think it's a Live CD too.
2).  The installer should have an option to have them guide you through a partitioned installation.  I would go with that.
3).  Should be okay, but you might try the XFCE CE if you want it to run faster.

Confirm : no alternate CD
Light edition is the main edition without restricted drivers and other proprietary software.
If you want a lighter edition you could try XFCE edition (beta)

---

### Post by crzytoxicant on 2008-02-03
I see. well i just ended up using crunchbang linux and it worked like a charm but I partitioned it wrong. haha but w/e it's all good. =D

---

