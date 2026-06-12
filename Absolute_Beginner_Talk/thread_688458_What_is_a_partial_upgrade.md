---
title: "What is a partial upgrade?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2008-02-05
I've searched the forums, but can't find the answer (one post said it could be caused by Automatix, which has never been installed...)

Today I came home and the Upgrades available icon wan on in the upper-right hand corner of my screen, so I clicked it. I was told that I could only do a partial upgrade (there were quite a few files, and it took about 20 minutes...  Also came with a new Kernel.)

The upgrade went fine, but now I'm wondering, why was it a partial upgrade?
I'm not testing a new release, and I am running UbuntuStudio 7.10

Has this happened to anyone else?
What caused it?

---

### Post by neurostu on 2008-02-05
This just happened to me as well.

It means that some of the packages you already have installed cannot be upgraded for a couple of reasons.

These reasons could include, they are proprietary packages not supported by ubuntu, they are packages that are no longer supported by ubuntu, etc...

If you system is working. I wouldn't worry about it.

---

### Post by justin whitaker on 2008-02-05
> **jondecker76 said:**
> I've searched the forums, but can't find the answer (one post said it could be caused by Automatix, which has never been installed...)

Today I came home and the Upgrades available icon wan on in the upper-right hand corner of my screen, so I clicked it. I was told that I could only do a partial upgrade (there were quite a few files, and it took about 20 minutes...  Also came with a new Kernel.)

The upgrade went fine, but now I'm wondering, why was it a partial upgrade?
I'm not testing a new release, and I am running UbuntuStudio 7.10

Has this happened to anyone else?
What caused it?

Partial upgrades mean that either one or more of the dependencies for the upgrades have not been committed to the repository yet, or that one of the repositories' public access key has changed or is unrecognized by Update manager. 

Update manager basically overlooks the dependencies and installs what it sees as safe to upgrade.

---

