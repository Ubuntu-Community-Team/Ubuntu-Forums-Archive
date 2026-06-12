---
title: "MacOnLinux problems... can't use &quot;make&quot; command?"
date: 2006-07-19
forum: Apple PPC Users
---

### Post by Ryan Marcus on 2006-07-19
I've got MoL working with Mac OS X, but it is un-usable slow, so I tried to follow the adivce in the wiki.

> 
1) Download the latest kernel source. You can user uname -r to determine your version. Mine was 2.6.12-9-powerpc. You can also use the synaptic package manager or Adept to do this.

So I run uname -r and I get 2.6.15-23-powerpc. I open up Synaptic and search for 2.6.15, I get several results, but they are all installed already.

> 
2) Follow the instructions on this Wiki for building the kernel found at [WWW] [https://wiki.ubuntu.com/KernelBuildPPCHowTo](https://wiki.ubuntu.com/KernelBuildPPCHowTo).

The page does not exist... I assume that because it is already installed I don't need to build it.

> 
3) Download the patched MOL that Joe Jezak has kindly provided. [WWW] [http://dev.gentoo.org/~josejx/](http://dev.gentoo.org/~josejx/) Look for the latest mol version he has lprovided.

I downloaded [ the most recent MoL]("http://dev.gentoo.org/~josejx/mol-0.9.71_pre8.tar.bz2").

> 
4) Extract it using tar -jxvf

I get loads of scrolling text... then it stops.

> 
5) Build it using make.

If you ask me, this is where the instructions need to be a bit more specific...

I tried sudo make, make, and make (path to tarball) and all I got was:
bash: make: command not found


Now what? :(

---

### Post by mlind on 2006-07-19
```

sudo aptitude install build-essential

```

---

