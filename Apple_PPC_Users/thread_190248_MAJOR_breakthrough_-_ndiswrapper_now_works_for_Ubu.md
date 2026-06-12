---
title: "MAJOR breakthrough - ndiswrapper now works for Ubuntu PPC!!"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by iamdigitalman on 2006-06-06
I was just messing around, but I found a way to make ndiswrapper work with ubuntu 6.06 PPC!!

here is what i did:

I performed a google search, and found [this](http://rpmfind.net/linux/rpm2html/search.php?query=ndiswrapper). it turns out that there are PPC versions of ndis for fedora core PPC. it's an RPM file, but I thought 'if this can work on FC, why not ubuntu?" so, I downloaded the RPM file, and ran alien to convert it to a .deb file.

then, I double clicked on it, and it said everything was OK. WOO!! now, I poped open a terminal, ran the command ndiswrapper, and got this:

> Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-a                Write module alias configuration file
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX


that's the text you get if you dont install any drivers.

next, I poped open the CD drive, and inserted the disk with the drivers on it. I installed them uising the -i command for ndis, then ran the -m command to apply an aliias. that worked.

I am so close. what do I do next to bring wlan0 up? any suggestions?

well, even though it isnt complete yet, I hope this helps.

-digital ;)

---

### Post by ssam on 2006-06-06
ndiswrapper is writen in C, so it should be possible to recompile it on powerpc and for it to run.

but it probably wont be able to load and run the drivers, as they have been compiled for x86.

---

### Post by iamdigitalman on 2006-06-06
[QUOTE=ssam]ndiswrapper is writen in C, so it should be possible to recompile it on powerpc and for it to run.

but it probably wont be able to load and run the drivers, as they have been compiled for x86.[/QUOTE]

nono, the driver is loaded and everything. a quick check of it in the terminal shows driver present, hardware present.

what is really odd is that using the wifiradar program, it can find the access point, SSID 2wire895, max signal strength, mode auto and 802.11g, and when I click connect, it says it connected OK, but I cant get online, and there still isnt an entry for wlan0 in the networking control panel.

I even tried rebooting, and I got nothing. maybe it's because I am using something ment for another distro, but it should work.

that's enough fighting with it for one night.

-digital ;)

---

### Post by iamdigitalman on 2006-06-07
well, I wrestled with this for the last day, and I cant figure it out. I tried everything I could think of, which isnt alot.

I'm open to suggestions, any help appreciated. I am *really* close, but it's like a brick wall is blocking me ](*,) 

-digital ;)

---

### Post by Audiophiliac on 2006-06-07
And I thought this was indeed a breakthrough. Oh shucks. Keep us posted.

---

### Post by ssam on 2006-06-07
have you tried conntacting the ndiswrapper developers?

---

### Post by iamdigitalman on 2006-06-07
ok, I think I found where I hit the snag.

here is a printout from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

so, even though ndiswrapper -l gives 'driver present, hardware present', it refuses to show it's face. but it is there, and it is being detected. I dunno what the problem is. I combed the wiki, forums, every scrap of ndiswrapper docs, and nothing.

I have also asked for help from them, and they are very pessimistic, claiming it is 'impossible' nothing is impossible. if that were the case, why am I holding a PPC compile of ndiswrapper in my hands?

perhaps I should contact the people who built the PPC compile, but I found the file on an RPM search page, no contact info in sight.

ah well, once again my dream has been shot down...

-digital ;)

---

### Post by benoitc on 2006-06-08
ndiswrapper can't works on ppc since it use x86 binary dll.  It could compile but dll can't be used.

---

### Post by BoneKracker on 2006-06-20
Bummer, that sounds like a MAJOR constraint.

---

### Post by slux on 2006-06-20
It's about as bad as it gets. We're talking about the reason there is a separate PPC version of anything in the first place, the processor architecture is entirely different and anything compiled into machine code for a x86 system will not run on such a cpu natively, period.

It's one of the things you really need the source code for, recompiling for a new architecture and it's one of the things you give up when you choose to use something like ndiswrapper.

---

