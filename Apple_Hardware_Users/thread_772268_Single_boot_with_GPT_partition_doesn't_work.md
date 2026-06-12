---
title: "Single boot with GPT partition doesn't work"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by cesarse on 2008-04-28
Hi.

I've been using a single boot installation of Ubuntu 7.10 (Gutsy) on my macbook with a MBR partition for a while and everything works fine (though 20 secs delay at boot time).

I've made the same with Ubuntu 8.04 (Hardy) and it worked like a charm.

Then i've installed it in a GPT formated disk, but now a folder with a question mark inside appears and nothing else happens.

I thought Ubuntu 8.04 (gparted + grub + kernel) could handle GPT partitions as well as MBR ones.

Am I missing something?

Thanks in advance
César

(sorry for my bad english, ask me if something is not clear :-))

---

### Post by cyberdork33 on 2008-04-28
> **cesarse said:**
> Hi.

I've been using a single boot installation of Ubuntu 7.10 (Gutsy) on my macbook with a MBR partition for a while and everything works fine (though 20 secs delay at boot time).

I've made the same with Ubuntu 8.04 (Hardy) and it worked like a charm.

Then i've installed it in a GPT formated disk, but now a folder with a question mark inside appears and nothing else happens.

I thought Ubuntu 8.04 (gparted + grub + kernel) could handle GPT partitions as well as MBR ones.

Am I missing something?

Thanks in advance
César

(sorry for my bad english, ask me if something is not clear :-))grub still relies on MBR for booting. Technically, I lwould that what you have done would still work, but I would guess that you may have changed where the gpt boot flag is located which it doesn't like for some reason.

---

### Post by cesarse on 2008-04-29
Initially, there was no flag at all, then I used gparted do set boot flag in /dev/sda1, finally, I ran the following commands in grub console: "(hd0, 0)" and "setup (hd0)".

I think I have to wait till Ubuntu 8.10 and grub2. :-(

---

### Post by cyberdork33 on 2008-04-29
> **cesarse said:**
> Initially, there was no flag at all, then I used gparted do set boot flag in /dev/sda1, finally, I ran the following commands in grub console: "(hd0, 0)" and "setup (hd0)".

I think I have to wait till Ubuntu 8.10 and grub2. :-(
for some reason the Mac doesn't like it unless the EFI partition is set as bootable only in the GPT (and your normal bootable partition in the MBR).

you will probably have to wait a lot longer than that for grub2 / booting from EFI.

---

