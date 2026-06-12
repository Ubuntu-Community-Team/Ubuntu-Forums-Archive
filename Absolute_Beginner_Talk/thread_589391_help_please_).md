---
title: "help please :)"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-10-24
ok i need to know how to do this to fix gppp....i kinda understand it but dont know how to compile a .tar file. please help me with step by step commands on how to do this. thatks.

"What we are doing is recompiling Gnome-PPP with a diff in detection due to the different way wvdial now has output. Grab a .tar of Gnome-PPP & after expanding it, sub the patched gnome-ppp-wvdial.c with the one in the stock app & then compile. I compiled with ./configure --prefix=/usr, so it replaced the unpatched version--if you are not comfortable with this just ./configure & call it from your /usr/local."

:)

---

### Post by realvz on 2007-10-24
why dont u use the community version
sudo apt-get install gnome-ppp

---

### Post by natehatewindows on 2007-10-24
because it has a bug and im trying to recompile it to fix the bug. gppp in gusty wont connect all the way due to a difference in wvdial in gusty. Because it wont connect all the way i cant use apt0get or anything like that.
thanks :)

---

### Post by realvz on 2007-10-24
where is this tutorial that you are reading...

---

### Post by natehatewindows on 2007-10-24
[https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487)

---

### Post by realvz on 2007-10-24
so you have the cvs archive of gnomeppp...
extract it but right clicking on it and then select extract here...
in your extracted folder  copy the patched file from the launchpad page...

do this and then we move forward

---

### Post by natehatewindows on 2007-10-24
when i do ./configure it gives me this error: "checking for C compiler default output file name... configure: error: C compiler cannot create executables"

any way around this?

---

### Post by realvz on 2007-10-24
Type "sudo apt-get install build-essentials" in a terminal
and try ./configure again

---

### Post by natehatewindows on 2007-10-24
> **natehatewindows said:**
> because it has a bug and im trying to recompile it to fix the bug. gppp in gusty wont connect all the way due to a difference in wvdial in gusty. Because it wont connect all the way i cant use apt0get or anything like that.
thanks :)



wont work.

---

### Post by realvz on 2007-10-24
goto synaptics
search for glibc
and install all u see

---

### Post by hyper_ch on 2007-10-24
it's not essential**s** but:

```

sudo apt-get build-essential

```

---

### Post by realvz on 2007-10-24
he already has build-essentials

---

### Post by Maestro23 on 2007-10-24
> **realvz said:**
> he already has build-essentials

It's** build-essential**

---

### Post by hyper_ch on 2007-10-24
;)

And next time please use an appropriate thread title. You know, about 99% of the threads started in this forum are about a problem and asking for help ;)

---

### Post by natehatewindows on 2007-10-24
yeah sorry about the title...i just was not sure how to put it because i was sure it would go into more topics than what i started with. I need to either compile this gppp with thi new file i add to it after its extracted or figure out a way to install kppp. When i download kppp from packages.ubuntu.com to my desktop and try to install i get and error something like "Error: Dependencies not satisfiable" ...what does that mean and is there a way to fix it? I only have a dail up connection here in Ukraine and when i connect via wvdial or gppp it does not connect all the way (part of the bug i gave a link to) so i cant use apt-get, or add/remove apps, do updates or upgrades, get plugins. basically ubuntu does not know i have a connection. So if anyone has a way i can install/or compile one of these program i would be very thankful. :) im quiet new at some of these things and dont really know what im doing.

have a great day!

---

### Post by hyper_ch on 2007-10-24
unlike windows the packages contain only the essential stuff relating to the according package but they may need to include also other stuff from other packages. Hence the dependencies. If you try to install the .deb file while having an internet connection, it will automatically download the dependencies.

As for the gppp --> did you install now build-essential?

---

### Post by Maestro23 on 2007-10-24
> **natehatewindows said:**
> yeah sorry about the title...i just was not sure how to put it because i was sure it would go into more topics than what i started with. I need to either compile this gppp with thi new file i add to it after its extracted or figure out a way to install kppp. When i download kppp from packages.ubuntu.com to my desktop and try to install i get and error something like "Error: Dependencies not satisfiable" ...what does that mean and is there a way to fix it? I only have a dail up connection here in Ukraine and when i connect via wvdial or gppp it does not connect all the way (part of the bug i gave a link to) so i cant use apt-get, or add/remove apps, do updates or upgrades, get plugins. basically ubuntu does not know i have a connection. So if anyone has a way i can install/or compile one of these program i would be very thankful. :) im quiet new at some of these things and dont really know what im doing.

have a great day!

While over at Ubuntu packages, you need to download the dependencies as well for kppp.  It should tell you on the page for it everything that it requires.

*It's a pain doing it this way, I know.

---

### Post by natehatewindows on 2007-10-24
can i download build essentials as a package without apt-get? 

and you mean at [http://packages.ubuntu.com/gutsy/net/kppp](http://packages.ubuntu.com/gutsy/net/kppp) i need to not only download kppp but everything listed under "other packages related to kppp"????


thanks guys! your saving my a** here.....im so lost but your really helping me :)

---

### Post by hyper_ch on 2007-10-24
build-essential should also be there on the packages site... and you have to download all the other packages listed on the site that have teh red circle (if you read the legend it will say that those are the dependencies).

---

### Post by natehatewindows on 2007-10-24
ok great....ill try it in a while....im making the wife mad right now ;) wont get off here she says :)

---

