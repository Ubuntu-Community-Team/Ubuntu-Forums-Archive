---
title: "PowerMac G4 Sawtooth AGP woe. Nothing works!"
date: 2009-02-14
forum: Apple Hardware Users
---

### Post by Roger Thornhill on 2009-02-14
I have been trying in vain to get Xubuntu to load into my PowerMac. I am an Ubuntu noob, btw.

Machine has a CDRW, 768MB RAM, 400Mhz, Airport, Ethernet. 2 HDD (80GB, 60GB) and AGP graphics connected via the old VGA style connector to a SONY Trinitron display capable of up to 1600x1280, though I tend to keep it on 1280x1024@75Hz. 

I have tried live CDs, alternates. Pretty much everything from 6.06 to 9.10 daily that would fit onto a CD. Many are over 650MB and so beyond my RW media so I am a little cautious about burning another drinks coaster until I find out what I am doing wrong.

The best I managed to get after various modprobe jiggery was, after much beating and pounding, 8.04LTS "video=ofonly", as even my multisync CRT could not handle the display - which I find bizarre, btw - and then it switched to C64 esque resolution 800x600 and took 30secs to register if I had touched a drop down menu, i.e. it ran like the proverbial 2 legged dog pulling a fully laden sled across a gravel drive. The menus did not permit any other resolutions. Odd.

BTW as per general health, Tiger runs fine but Leopard is a bit erratic and I know Snow Leopard will ignore this machine, hence the move to Xubuntu.

Something is wrong. II am clearly doing something wrong.

BTW I did try one of the methods that involved editing xconf, but the VI editior, apart from being a PoS I have managed to avoid most of my life (EDT, now that was a rational editor), did not appear to be able to synchronise what text was on the screen and what it thought was on the screen. FAIL.

Any ideas? I'd really like to get this up and running and then see if I can get Erlang on it!

---

### Post by louvann on 2009-02-14
I have a similar machine PPC-450-dual-agp.

I struggled to get anything to go until I realized that the black screen was a failure on X.  Try to go to a virtual terminal cmd-opt-F1 to get to a terminal. to return cmd-opt-F7. If this is your issue then follow the xorg.conf problem line. Your stock machine has an ATI card and this was problematic for me. I had previously installed 6.06 without much problem but 8.xx has been a challenge. 
Currently, my ppc-450 machine is only running in low res graphics. (?16? color) but everything else is basically functional. I am waiting for an ATI fix since this is across PPC and intel?

best of luck

---

