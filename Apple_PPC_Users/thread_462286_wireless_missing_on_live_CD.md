---
title: "wireless missing on live CD"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by stephen k on 2007-06-02
hI

I bought a ubuntu 6.06 cd for mac/ppc from "the linux shop".

I'm running it now on a iBook G3 (900Mhz 640Mb ram) while i'm typing this post.

When I go to system>admin>networking it shows Ethernet connection "enabled" and Modem connection "not configured" But alas, no sign of the Wireless connection. (airport works fine in os x).

I typed "sudo lshw" in terminal and there was no info output of the airport card, just the Ethernet info was shown.

Its as if the software is not seeing the Airport wireless connection

I'd like to resolve this problem before i install 

Any advice or assistance would be appreciated

Regards steve

---

### Post by Auria on 2007-06-02
look at the PPC FAQ (its a sticky) it contains all steps to get wireless working - i'm not sure you can do it from the liveCD as you need to install stuff

BTW 6.06 is a little old, 7.04 is reported often much better on PPC for stability

---

### Post by stephen k on 2007-06-02
Hi Auria
Thanks for the reply.

I think the sticky you mention is mainly for extreme, my airport (802.11b) is quoted to "work straight out of the box".

I went for the 6.06 because it has long term support.
Regards Steve

---

### Post by Auria on 2007-06-02
It's quoted to work out of the box in 7.04 - I have no idea about 6.06 however.

hopefully someone else can help you =) there some very knowledgable users here, don't give up.

However, don't be surprised if people ask you to try 7.04 - you say you want 6.06 for long-term support. however you're not using the support anyway, you're using the forums ;)

---

### Post by stmiller on 2007-06-02
The 'Long Term Support' doesn't quite work with PPC Linux. Feisty has huge fixes for PPC hardware, esp for G5 machines. Previous releases of Ubuntu had issues with wireless, X, sound, everything. Bleh.

Also LTS is more for companies and such using Ubuntu on critical servers who need a stable machine backed by Canonical [paid] technical support.
Not only that, but Canonical has dropped tech support for PPC. So there is no LTS for PPC.


Anyways, get Feisty. :)

---

### Post by stephen k on 2007-06-03
Hi stmiller
thanks for the reply

Both you and Auria seem to send the same message - Feisty

I think I.ll go with that but i would have liked to find a fix for wireless in Dapper

My brother suggested "Configure network card" in Add/remove apps>system tools, any thoughts?
Regards Steve

---

### Post by stmiller on 2007-06-03
Hey yeah you can try that thing your brother suggested. The big thing in Feisty is the gnome network manager. Or actually the fact that the gnome network manager actually works! ;)
It did not work that well at all in previous ubuntu releases. Just click on the applet, choose your network, and it connects.

---

