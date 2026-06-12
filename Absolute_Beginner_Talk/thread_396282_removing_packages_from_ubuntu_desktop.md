---
title: "removing packages from ubuntu desktop"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by marmalade on 2007-03-29
I've been using Ubuntu on and off since Warty Warthog, but on some questions (eg how the ubuntu philosophy translates into actual distro decisions), I'm still a total beginner in terms of understanding.

It's great that everything you might need can be included at install without the need to search for it, but why can't I remove the things I don't want?
To be more specific - I *want* to remove evolution - it has no use for me. However, 'ubuntu-desktop' depends on it, and that's something I feel wary about removing. Is that like *the whole desktop*? Surely not, but I can't find online what functionality I'll lose by removing this package, and until I know, I'm inclined to guess the worst! 

(And if it is important, somehow, why has it been made to depend on this entire groupware entire suite? Not all machines have 45Mb to spare on something which is never used..:confused: )

---

### Post by milton1 on 2007-03-29
ubuntu-desktop is a metapackage that installs lots of desktop applications. If you uninstall specific programs, it will uninstall the metapackage. This will not damage your system (assuming the other apps you removed are not essential).

---

### Post by david_kt on 2007-03-29
> **marmalade said:**
> I
To be more specific - I *want* to remove evolution - it has no use for me. However, 'ubuntu-desktop' depends on it, and that's something I feel wary about removing. Is that like *the whole desktop*? Surely not, but I can't find online what functionality I'll lose by removing this package, and until I know, I'm inclined to guess the worst! 

(And if it is important, somehow, why has it been made to depend on this entire groupware entire suite? Not all machines have 45Mb to spare on something which is never used..:confused: )

Just go ahead, it will only remove the ubuntu-desktop meta package, not the entire desktop. Unless it inform you that it will remove the whole bunch of packages, it is safe to remove ubuntu-desktop.

DK

---

### Post by compmodder26 on 2007-03-29
Just a note, if/when you wish to upgrade to next ubuntu release, you'll need to reinstall ubuntu-desktop.

---

### Post by dstew on 2007-03-29
The reason that ubuntu-desktop "depends" on different applications is mainly for updating. That is, when you update ubuntu-desktop, the system will automatically update the packages that it "depends" on, including evolution. It doesn't really mean that your desktop needs evolution to function, and it doesn't mean your desktop will disappear if you remove ubuntu-desktop.

---

### Post by Drakkor on 2007-03-29
I would be very careful with this, I had the same idea to get rid of evolution, since I use Thunderbird mail, anyway I went and removed everything "evolution" and it would boot , but no desktop whatsoever, had to restore an image of that partition that I had backed up !! :)

---

### Post by marmalade on 2007-03-29
Ta, everyone.

As I mentioned, some things are still mysterious to me. This included metapackages....

---

### Post by david_kt on 2007-03-29
> **Drakkor said:**
> I would be very careful with this, I had the same idea to get rid of evolution, since I use Thunderbird mail, anyway I went and removed everything "evolution" and it would boot , but no desktop whatsoever, had to restore an image of that partition that I had backed up !! :)

That is why I said before:
[INDENT]**Unless it inform you that it will remove the whole bunch of packages...**[/INDENT]

You should only see two packages to be removed:
[INDENT]
evoltuion ubuntu-desktop[/INDENT]

then you are safe.

DK

---

### Post by marmalade on 2007-03-30
Ta for the warning.

In fact, I think that was why I was so wary of removing ubuntu-desktop, having upgraded to Edgy two months ago due to a similar problem.
I was tinkering a lot, installing and removing packages, so I don't know exactly which operation actually sent my previous system (Dapper, maybe) over the edge, but I remeber needing to upgrade some thousands of packages at some point just to get K3b working & backup before reinstalling.
I pleaded with my live-in tech support to get K3b running, but unfortunately gave him too general a brief - I didn't mention that I would like to keep other things (eg the desktop) running as well.

The last I saw of that system was what sounds like the same problem you had- X but no gnome. 
Quite likely it was due to some everything-depends-on-evolution bug.
I was very confused by the whole thing and I'm glad not to have to think about it any more!

---

