---
title: "how do I swtich from linux32 to linux 64 with the least amount of disruption"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by harryliddic on 2008-03-22
How do I switch from linux32 to linux64 without too much disruption. will linux64 run faster? can I still run 32-bit programs? what are the plus and minus list i would encounter?

---

### Post by bruce89 on 2008-03-22
I'm afraid the only way is to do a clean install of the AMD64 edition. There are no drawbacks unless you use non-free software (flash for instance).

It is possible to run 32 bit apps in a 64 bit environment, see *ia32-libs*.

---

### Post by defrex on 2008-03-22
I would warn against switching unless you want to use 4g of ram.

I switched to 64-bit a few months ago, and while anything from a repo will work fine, things that aren't in the repos are often trouble. Sometimes it's simply a matter of compiling rather then installing a deb, but often there are problems trying to compile. My most current frustration is not being able to get the arduino software working.

I would say don't switch unless you need to (for ram).

---

### Post by bruce89 on 2008-03-22
> **defrex said:**
> things that aren't in the repos are often trouble. Sometimes it's simply a matter of compiling rather then installing a deb, but often there are problems trying to compile. My most current frustration is not being able to get the arduino software working.

I'm afraid that this shouldn't be done at all. Using random packages from places is a sure fire way of breaking future upgrades.

I am using an AMD64 rght now, nothing wrong with it.

---

### Post by TheWizzard on 2008-03-22
> **defrex said:**
> I would warn against switching unless you want to use 4g of ram.

I switched to 64-bit a few months ago, and while anything from a repo will work fine, things that aren't in the repos are often trouble. Sometimes it's simply a matter of compiling rather then installing a deb, but often there are problems trying to compile. My most current frustration is not being able to get the arduino software working.

I would say don't switch unless you need to (for ram).

amd 64 runs smoother & faster on the amd64 kernel.

---

