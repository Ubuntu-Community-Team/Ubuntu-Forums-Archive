---
title: "Grub didnt install with android x86? how can I install manually?"
date: 2016-10-30
forum: Any Other OS
---

### Post by psnworks123 on 2016-10-30
hey guys, sorry if this has been posted before but I am a little stuck here, I am not new to linux of any kind but aside from the usual installs/boot-repairs/ following guides online, im basically new,

SO, I have attempted to duel boot my samsung series 7 slate with android x86 (android 6.0) the install went fine and I was able to set up and boot, but grub loader for whatever reason, never installs through the android installer and because of that, I have no way of booting into android, I have attempted to load up ubuntu live cd and install boot repair, I get through all the necessary stuff in terminal but it gave me a "couldnt locate package boot-repair" error so I attempted to boot the boot repair iso , tried recommended
 settings ans got yet another error, I would imagine this is due to the fact that grub isnt installed at all and therefore has nothing to repair,

so to get to the point, how can I go about installing grub2 or another loader that will allow me to load up android as well as keep windows as a second duel boot option?


any help is very appreciated

thanks!!

---

### Post by Neill_R on 2016-10-30
boot into Ubuntu(dual boot)  and run sudo update-grub this should discover the other operating system

---

### Post by howefield on 2016-10-30
Thread moved to the "*Any Other OS*" forum.

---

### Post by psnworks123 on 2016-10-31
ok so I have wiped my hard drive clean, re installed windows, then installed ubuntu on a seperate partition to hopefully give me grub loader to then install android, getting "unrecognized path, grub rescue" on boot now, attempted to install boot repair through live cd and again got "cant locate package boot repair" bout to try the boot repair disc iso, if still nothing I think im going to give up cus honestly this is bull ****, but if you have any ideas please shoot

---

