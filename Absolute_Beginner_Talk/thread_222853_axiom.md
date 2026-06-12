---
title: "axiom"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-07-25
Does anyone have any experience using axiom with texmacs, both are available directly through synaptic and I have installed them, now you are supposed to be able to use axiom within texmacs, I can technically start it in texmacs but I have no input at all, as in if I do any calculation it does nothing, just goes to the next line.

I think the problem may be to do with axiom, I say this because if I go to Run an application and type axiom, it doesn't do anything, no error but the program doesn't load up either, any ideas?

Calv

---

### Post by xhantt on 2006-07-26
Hi! I've similar problems, Axiom just hang inside Texmacs whenever I start a new session, also can't close it.

I can use Maxima inside Texmacs and work flawlessly, so it's look like problem related to the Texmacs stub that call Axiom.

To learn about Axiom you can visit [http://wiki.axiom-developer.org/FrontPage](http://wiki.axiom-developer.org/FrontPage).

---

### Post by xhantt on 2006-07-28
I've managed to get axiom working inside texmacs!! I just installed all axiom packages for breezy, and it work like a charm.

---

### Post by calvinthomas on 2006-07-29
Sorry, i'm a total noob, could you explain to me how to do that? Well done on getting it working!

Calv

---

### Post by calvinthomas on 2006-07-29
Ok, I found the packages and tried to install it but got dependency is not satisfiable libgmp3, I found that it conflicts with libgmp3c2 so I thought I could just delete that, however doing so would remove several other things including maxima, so doesn't seem I can use this method!

Calv

---

### Post by xhantt on 2006-08-02
Sorry for the delay...

I try this on Kubuntu, but this should work on Ubuntu as well

1) From packages.ubuntu.com download all axiom packages from Breezy distribution, here the url [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=axiom&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=axiom&searchon=names&subword=1&version=breezy&release=all).

2) Open a terminal, go to the folder where you downloaded axiom files and type the following command

```
sudo dpkg -i axiom_20050901-1ubuntu1_i386.deb axiom-databases_20050901-1ubuntu1_all.deb axiom-doc_20050901-1ubuntu1_all.deb axiom-graphics-data_20050901-1ubuntu1_all.deb axiom-graphics_20050901-1ubuntu1_i386.deb axiom-hypertex-data_20050901-1ubuntu1_all.deb axiom-hypertex_20050901-1ubuntu1_i386.deb axiom-tex_20050901-1ubuntu1_all.deb 
```

This should install/downgrade axiom, that's all. To test start Texmacs use Insert Session/Axiom. At the prompt -> type integrate(1/x,x) and press Enter, then axiom should respond log(x).

Note: From now on when making an upgrade you should not upgrade to axiom_20050901-4ubuntu1. If you do this accidentally you can repeat the above steps to return to breezy version.

---

