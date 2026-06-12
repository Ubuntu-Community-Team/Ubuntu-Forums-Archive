---
title: "Instlaling acer IPN2220 Wlan + changing wrong architecture"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by persofi on 2007-05-02
Hey folks,
I'm totally new to Ubuntu and Linux, and would very much appreciate your help. This is probably a rather basic question:

I'm running Ubuntu Feisty Fawn i386 on an Aspire 1520 (Aspire 1524 WLMI) notebook. Important: It has an AMD 64 processor. (which means I have the wrong version of Ubuntu?) The first problem I want to solve is, that the wirelass card (acer IPN2220 Wireless Lan Card) is not detected by Ubuntu. I tried to do everything exactly like in this tutorial: [http://users.skynet.be/ostaquet/aceraspire1360/](http://users.skynet.be/ostaquet/aceraspire1360/)

The problem here, that without my wireless card, I cant access the internet and thus the synaptic manager etc... is not that useful :) My only way to access the internet is in the university library, the machines there are running Windows XP and I can transport files with my USB stick. So I got:

1) The drivers like the tutorial said from acer
2) from the packages.ubuntu.com under the feisty fawn section:
a) ndiswrapper-common_1.38-1ubuntu1_all.deb
b) ndiswrapper-source_1.38-1ubuntu1_all.deb
c) ndiswrapper-utils-1.9_1.38-1ubuntu1_amd64.deb  --> this I got from the ndiswrapper sourcefourge page I think.

In a brute force trial+error attempt, these were the results: 
a) The "ndiswrapper-common" package seems to have installed just fine.
b) The "ndiswrapper-source" file says "Error: Dependency is not satisfiable: module-assistant".
c) The "ndiswrapper-utils" says "Error: wrong architecture, 'amd64'"

I only have a vague idea what these messages mean. And I dont have any idea what to do next and why. Seems like a good situation to ask for help ;)

Oh and here is something strange: I uninstalled all the preinstalled Ubuntu games. When I tried to reinstall them I got the error "Wrong architecture"... It seems I have to switch from the i386 version I installed to the AMD64 version, but how do I do that?

---

### Post by persofi on 2007-05-02
Now I downloaded the AMD64.iso, but how do I uninstall the previous version of Ubuntu?

---

### Post by mikeyphi on 2007-05-02
> **persofi said:**
> Now I downloaded the AMD64.iso, but how do I uninstall the previous version of Ubuntu?

Run the Live Cd -overwrite the previous installation of Ubuntu

---

