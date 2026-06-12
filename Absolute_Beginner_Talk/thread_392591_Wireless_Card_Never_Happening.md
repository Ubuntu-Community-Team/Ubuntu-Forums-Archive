---
title: "Wireless Card Never Happening?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-24
I have a Gigabyte W101GT mini- PCI E Wireless card. Whenever I boot Ubuntu, the text at the beginning before the OS loads says something about my WiFi card not supported. Is there anything I can do to make my wireless card work in Ubuntu? Ive searched google for drivers, but the device manager doesnt even seem to show my wireless card. I wouldnt think having a driver would do any good...

Suggestions?

Thanks...

---

### Post by luke411 on 2007-03-24
did you try ndiswrapper and the windows driver?

---

### Post by GSF1200S on 2007-03-24
> **luke411 said:**
> did you try ndiswrapper and the windows driver?
Hey, thanks for the fast response...

Allow me to clarify a point. I am an absolute NOOB when it comes to Linux. Ive come to Linux (specifically GNOME and Xfce) to have a more stable operating system with a more customizable setup, and I think Ive found that.

I was honestly amazed by all the stuff Ubuntu automatically supported. Media readers, USB stuff, I mean dang, Linux isnt mainstream at all and it does quite well. 

Getting back to the topic, the only 2 hardware items not supported by Ubuntu is my video card (Nvidia GForce 7600 Go 256MB PCI-express) and my wireless card (my biggest pain).

No, I havent even been able to find the windows drivers... I guess Ill have to do more research.. Im not trying to come to this forum for all my answers. What is Ndiswrapper and can I get it through the Synaptic Package Manager?

Thanks for your help...

---

### Post by luke411 on 2007-03-24
ndiswrapper is a package that can make some windows wireless cards work and think they are on a windows based machine. In some cases, you can even get more support for your device going this route, rather than using some scaled down linux driver. "ndisgtk" is an optional GUI to use with ndiswrapper that will make it a little easier to use. Both can be downloaded from the package manager.

---

### Post by luke411 on 2007-03-24
oh, once you install everything, you will find the ndisgtk in your system-administration menu and it will say "Windows wireless drivers". Then you will only need to get  a copy of your windows driver and follow the prompts.

---

### Post by GSF1200S on 2007-03-26
> **luke411 said:**
> oh, once you install everything, you will find the ndisgtk in your system-administration menu and it will say "Windows wireless drivers". Then you will only need to get  a copy of your windows driver and follow the prompts.

Hmmm.. Well I managed to install ndiswrapper, ndisgtk just fine, but still no joy. Ndisgtk clearly shows drivers installed, but it says "Hardware Present: No" under the driver name. I dont know whats going on. Ive got like 7 tabs open in Firefox trying to figure this out... Any ideas on how to get my "hardware present: yes"? I would guess after my hardware is present under Ubuntu, I would use iwconfig to find a wireless network?

And hey, if anyone knows any linux drivers for a Gigabyte W101GT mini-pci, that would be all the better. Thanks...

---

### Post by GSF1200S on 2007-03-26
> **GSF1200S said:**
> Hmmm.. Well I managed to install ndiswrapper, ndisgtk just fine, but still no joy. Ndisgtk clearly shows drivers installed, but it says "Hardware Present: No" under the driver name. I dont know whats going on. Ive got like 7 tabs open in Firefox trying to figure this out... Any ideas on how to get my "hardware present: yes"? I would guess after my hardware is present under Ubuntu, I would use iwconfig to find a wireless network?

And hey, if anyone knows any linux drivers for a Gigabyte W101GT mini-pci, that would be all the better. Thanks...

Addon: My wireless card works 5.0 in windows. Also, before I installed Ubuntu (Installed yesterday) while loading live cd it would say something about wifi card not supported. Does this mean its just impossible for this card to work with Linux? If so, im quite dissapointed at the monopoly of Windows only cards...

---

### Post by GSF1200S on 2007-03-26
bump? I think im close here...

---

