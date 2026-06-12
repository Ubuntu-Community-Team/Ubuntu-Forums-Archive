---
title: "CITRIX, links and ldd resolutions"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by eplkln on 2007-12-02
hi,- 

I have installed the amd64-version of 7.10 ubuntu, and am quite satisfied. 

It did however take me a while to get CITRIX up&running, and the problem seems to point back to some unresolved (?) dependencies, that ldd showed when run for the wfica or wfcmgr of CITRIX. 

What seemed to resolve it was removing gnash (for firefox) and installing flash (likewise for firefox), and lo-and-behold, the CITRIX ldd-dependencies were resolved, and now CITRIX works like a charm
(like all the other stuff, but the CITRIX was a major obstacle ..) 

Question: Some good pointers to sources of information on how the lib-path (if that is the naming in this OS) or similar resolutions are defined and handled) - ? 

regards klaus

---

### Post by ilrudie on 2007-12-02
As a side note this is not because of a gnash problem it is because flash is 32bit and installs the 32bit dependencies that Citrix requires.

---

### Post by eplkln on 2007-12-02
Your right on that - the flash install listed quite a few lib<something>32 in the install, but I'm trying to understand (or find the sources of documentation ...) how the dependencies are built / handled, and how I can resolve them in the "next case" when I want to install <whatever-application> ? 

Any good pointers to information / docu will be apprecieated 

regards klaus

---

