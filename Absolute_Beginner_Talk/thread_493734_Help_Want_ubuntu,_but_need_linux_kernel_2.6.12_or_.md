---
title: "Help? Want ubuntu, but need linux kernel 2.6.12 or lower"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Ethernull on 2007-07-06
Hello,

I installed breezy but found out that all the apt-get files are no longer around :(

I would like to use ubuntu, but need to run a kernel version of 2.6.12 or lower.

Is there a way to do this?

I just dumped Mandriva because too many base libraries (openssl, tcpdpump, libpcap etc.) were putting thier library header files in non-default locations and I couldn't build anything without modifying CFLAGS in all the source. So I figured I should go to a debian based distro.

I am hoping it will be ubuntu.

Any advice is appreciated.

---

### Post by jrusso2 on 2007-07-06
Why do you need to run such an old kernel?

---

### Post by Ethernull on 2007-07-06
The tcp stack was changed drastically in 2.6.13 and a lot of wireless security apps wont run on the newer kernels. Need to run madwifi drivers for Atheros cards with LORCON and 802.11mercenary tools, kismet, airjack etc.

---

### Post by Ethernull on 2007-07-06
I should correct myself.. I meant the pcmcia code, not the tcp.

---

### Post by kerry_s on 2007-07-06
> **Ethernull said:**
> The tcp stack was changed drastically in 2.6.13 and a lot of wireless security apps wont run on the newer kernels. Need to run madwifi drivers for Atheros cards with LORCON and 802.11mercenary tools, kismet, airjack etc.

who told you that "mandriva"? those applications are updated to work with the new kernels. i've used all those you named and and trust me i wasn't using 2.6.12.
i see those apps in synaptic, i'm using debian lenny/sid, but those apps should be available in dapper to gutsy.

also the repos have some 20000+ applications you can just apt-get or use the gui, only if you want somthing special will you need to compile.

---

