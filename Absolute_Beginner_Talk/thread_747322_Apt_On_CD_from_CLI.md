---
title: "Apt On CD from CLI"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by DBrocks on 2008-04-06
Hey guys. I figured this would be a good place for my question to be answered, so here goes: I have a working ubuntu CLI server (internet, everything). I have another computer that I need ndiswrapper for (the drivers for the ethernet card don't work, so  no internet.) That computer is also CLI. So my question: How can I get ndiswrapper, and all it's dependencies burned to a cd from my Ubuntu CLI working server, so I can install ndiswrapper on the other computer? I've heard of apt-on-cd, but I've never used it. Can I use apt-on-cd from CLI? If not, is there another solution? Thanks in advance!

~Dan

---

### Post by mikeyphi on 2008-04-06
From: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Quote: APTonCD is on Ubuntu Feisty, Gutsy, Debian Unstable and Testing's repository now! So just install the aptoncd package.

$ sudo apt-get install aptoncd   Quote

[http://garr.dl.sourceforge.net/sourceforge/aptoncd/aptoncd_0.1-1_all.deb](http://garr.dl.sourceforge.net/sourceforge/aptoncd/aptoncd_0.1-1_all.deb)

Hope that helps.

---

### Post by DBrocks on 2008-04-06
Thanks, but thats not quite what I need. I need a way to use aptoncd from CLI to burn a cd containing ndiswrapper, and all the dependencies. I don't know how to use aptoncd from CLI. Sorry if I wasn't clear enough :lolflag:

---

