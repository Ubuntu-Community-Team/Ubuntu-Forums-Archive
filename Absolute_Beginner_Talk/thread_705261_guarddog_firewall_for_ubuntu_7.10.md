---
title: "guarddog firewall for ubuntu 7.10?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by carioca on 2008-02-23
:confused:
hi ubuntu linuxers,
guarddog firewall for ubuntu 7.10? Is that possible? the guarddog firewall is a kde software - this truth i know very well. which firewall for beginner is the most recommended to by using ubuntu 7.10? because I am used to use guarddog for a long while when I used another distro with kde. I don't like firerstarter and I don't fit well with it.. I like the guarddog best for the reason I'm very well familiarized with it. may I dowload guardog with the terminal by typing "sudo get install guarddog" ? does it really work with the gnome applications? for sure? Isn't it going to happen to no fatal errors or misconfiguration with it? do I face some problems to install it after the downloading? in that case, how do I solve it up? I'm very confused which one is more convenient to me? could you get me clear in order to reset this doubt. I'd appreciate your useful hints.god bless you! best regards.

:guitar:

---

### Post by sayakb on 2008-02-23
> **carioca said:**
> :confused:
hi ubuntu linuxers,
guarddog firewall for ubuntu 7.10? Is that possible? the guarddog firewall is a kde software - this truth i know very well. which firewall for beginner is the most recommended to by using ubuntu 7.10? because I am used to use guarddog for a long while when I used another distro with kde. I don't like firerstarter and I don't fit well with it.. I like the guarddog best for the reason I'm very well familiarized with it. may I dowload guardog with the terminal by typing "sudo get install guarddog" ? does it really work with the gnome applications? for sure? Isn't it going to happen to no fatal errors or misconfiguration with it? do I face some problems to install it after the downloading? in that case, how do I solve it up? I'm very confused which one is more convenient to me? could you get me clearin order to reset this doubt. I'd appreciate your useful hints.god bless you! best regards.

:guitar:

When you run any KDE app in gnome, a process kdeinit runs the app.. There is more chances that the app may crash, but that wouldn't harm your system.
PS: I am using dolphin KDE4 under gnome, works well, hasnt crashed a single time yet.

---

### Post by seventhc on 2008-02-23
Unless you need to configure anything differently, there is a built in firewall already. It's called iptables, firestarter and guarddog just give you a gui to work with. But if you don't need to change any settings, then there really is no need for anything else.
That being said
```

sudo apt-get install guarddog
```will install it

---

### Post by sayakb on 2008-02-23
Btw, sorry, I may be wrong with the exact concept of kdeinit and how kde apps work. I find it irrelevant in this context. But yeah, KDE apps work okay with gnome.

---

### Post by carioca on 2008-02-23
:lolflag:

thank you for your prompt reply. I got it. otherhand, if I want to use the firestarter. how do I download it and instal by using the terminal? just typing "sudo apt-get install firestarter" ? how do I configure it? best regards.

:popcorn:

---

### Post by seventhc on 2008-02-23
to install firestarter you can use apt-get, it's also in add/remove under applications.
Unless you have special needs, you don't have to configure anything. It's set up to block all incoming traffic, but allows the programs that need to connect to do so.

---

### Post by Martje_001 on 2008-02-23
> **carioca said:**
> thank you for your prompt reply. I got it. otherhand, if I want to use the firestarter. how do I download it and instal by using the terminal? just typing "sudo apt-get install firestarter" ? how do I configure it? best regards.
Correct and it will configure itself.

---

### Post by carioca on 2008-02-23
:)

thanks. as regarding to ubuntu 7.10 fresh user (home user). which is the most recommended one? guarddog or firestarter? i mean  less troubles when configuring it. best regards.

:guitar:

---

### Post by seventhc on 2008-02-23
I've never used gaurddog, so I can't say. I have used firestarter, but I never made any changes to it.
You could try both and see which you like better. Not sure if I would have both on the machine at the same time though, not sure if it's OK to do or not. But both are east to add or remove.

---

### Post by Martje_001 on 2008-02-23
I've installed both for you and compared. I would say Guarddog is far more advanced, and also a bit complicated. Firestarter is more basic, and simpler.

I would go for Firestarter because it can do, mostly (for daily use), everything Guarddog can do.

---

