---
title: "Possible Debian convert!"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Nosf3ratu on 2006-04-25
Hi there!  After years of hearing how terrific Ubuntu is, I cannot ignore it anymore.  I've been running Debian sid for the past four years, and while I love it, there are times that I wish it was easier to maintain (especially since I'm running amd64, and I have to use a chroot to run some 32bit programs, etc. It's a real pain).

Obviously, I'm not new to any of this, so I've got my box partitioned nicely and the transition, I'm sure, will be painless.

Couple of questions:
1) Can I just dist-upgrade to Ubuntu after changing my sources.list?
2) Ubuntu's amd64 support is truly multi-arch, correct?  No need for 32bit chroots and all that mess?
3) Licensing.  Can I actually apt-get install nonfree packages such as Sun's JRE?  Debian's licensing restrictions are just annoying.
4) [The big one] Just because Ubuntu is user-friendly, has it been nerfed in any way for experienced users like myself?  [I'd appreciate it any other Debian-converts could answer this one]

Thanks! :D

---

### Post by Perfect Storm on 2006-04-25
1) Yes. 
3) Check: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
and setup for w32codecs, java etc. etc.
4) The good thing is that even experience users can use/enjoy Ubuntu. One of the big diffrence between Debian and Ubuntu is that it's made easy to install.

---

### Post by Jason_25 on 2006-04-25
2.  The goal Dapper +1, "Edgy" is stated to have true multi-arch support as a goal.  I've found that I can run alot of stuff already in Dapper without a chroot though.  Sometimes I'll need to copy a library or two to /usr/lib, but many 32-bit programs work without a hitch.  No WMV or browser-integrated flash without a chroot of course.

---

### Post by Nosf3ratu on 2006-04-25
Wow, the source-o-matic is a lovely tool.  

So without kubuntu sources, which apparently only support Breezy (which is Ubuntu's "debian stable" as I understand it, right?) I don't have any KDE at all, or what?

Do I need to use Breezy to have KDE & Amarok?

---

### Post by Nosf3ratu on 2006-04-25
[QUOTE=Jason_25]2.  The goal Dapper +1, "Edgy" is stated to have true multi-arch support as a goal.  I've found that I can run alot of stuff already in Dapper without a chroot though.  Sometimes I'll need to copy a library or two to /usr/lib, but many 32-bit programs work without a hitch.  No WMV or browser-integrated flash without a chroot of course.[/QUOTE]

Ah, that's the same as debian-amd64.

---

### Post by Rinzwind on 2006-04-25
[QUOTE=Nosf3ratu]Wow, the source-o-matic is a lovely tool.  

So without kubuntu sources, which apparently only support Breezy (which is Ubuntu's "debian stable" as I understand it, right?) I don't have any KDE at all, or what?

Do I need to use Breezy to have KDE & Amarok?[/QUOTE]

Ubuntu = gnome+totem
Kubuntu =  kde+amarok

So Breezy does not explain the windowmanager you use ;)

But ubuntu with kde is 2 apt-gets away (remove gdm and install kde) ;)

---

### Post by Jason_25 on 2006-04-25
Kubuntu Dapper is being developed too.  

You can and should install Kubuntu with a separate ISO.

You can run KDE based apps from within gnome, on breezy or dapper.

As the poster above said, you can apt-get kubuntu-desktop to have both DEs if you want, but I wouldn't recommend it.

---

### Post by Perfect Storm on 2006-04-25
I may hastly answered number one. Do you mean from Debian to ubuntu or like breezy to dapper? I never heard annyone dist upgrade from debian to ubuntu, anyone?

Anyway, Ubuntu contains only one disc. If you want KDE, go for Kubuntu. If you downloaded/installed Ubuntu (default with gnome), just
```
sudo apt-get install kubuntu-desktop
```

or XFCE

```
sudo apt-get install xubuntu-desktop
```

---

### Post by Rinzwind on 2006-04-25
[QUOTE=Artificial Intelligence]I may hastly answered number one. Do you mean from Debian to ubuntu or like breezy to dapper? I never heard annyone dist upgrade from debian to ubuntu, anyone?[/QUOTE]

Yes I read a post a few minutes ago about a debian -> woarty -> breezy -upgrade-. 

But the general idea is to make a backup of things that need saving (documents/music etc) and just install breezy.

---

### Post by Perfect Storm on 2006-04-25
[QUOTE=Rinzwind]Yes I read a post a few minutes ago about a debian -> woarty -> breezy -upgrade-. 

But the general idea is to make a backup of things that need saving (documents/music etc) and just install breezy.[/QUOTE]

Sounds to me more like it's time consuming and the risk of breaking stuff with all the upgrades.

---

### Post by Nosf3ratu on 2006-04-25
[QUOTE=Artificial Intelligence]I may hastly answered number one. Do you mean from Debian to ubuntu or like breezy to dapper? I never heard annyone dist upgrade from debian to ubuntu, anyone?[/QUOTE]

Yeah, I meant Debian->Ubuntu.

The rest of the stuff is just like regular Debian, no big deal.  I guess I'm just trying to figure out if I should switch at all . . . seems that the amd64 stuff isn't true multiarch yet, so I'm not sure what Ubuntu would afford me besides a prettier install and a bigger userbase.

---

### Post by Perfect Storm on 2006-04-25
[QUOTE=Nosf3ratu]Yeah, I meant Debian->Ubuntu.

The rest of the stuff is just like regular Debian, no big deal.  I guess I'm just trying to figure out if I should switch at all . . . seems that the amd64 stuff isn't true multiarch yet, so I'm not sure what Ubuntu would afford me besides a prettier install and a bigger userbase.[/QUOTE]

Well, we also do group-hug :mrgreen:  j/k

If you're KDE fan/user you may check out [http://kubuntu.org/](http://kubuntu.org/)

---

### Post by Nosf3ratu on 2006-04-25
[QUOTE=Rinzwind]Yes I read a post a few minutes ago about a debian -> woarty -> breezy -upgrade-. 

But the general idea is to make a backup of things that need saving (documents/music etc) and just install breezy.[/QUOTE]

No need to back up anything if you've used a proper partitioning schema.

---

### Post by Nosf3ratu on 2006-04-25
[QUOTE=Artificial Intelligence]Well, we also do group-hug :mrgreen:  j/k

If you're KDE fan/user you may check out [http://kubuntu.org/](http://kubuntu.org/)[/QUOTE]

I'm more of a KDE *application* fan/user.  I don't use the desktop environment itself at all.  Just amarok & konqueror within fluxbox.

---

