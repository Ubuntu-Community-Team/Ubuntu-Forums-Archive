---
title: "Tilda not working on macbook pro 2015 [16.04]"
date: 2016-08-12
forum: Apple Hardware Users
---

### Post by emotion2 on 2016-08-12
Just installed ubuntu on my mac book pro and the tilda key doesn't work it gives me '>' or some + under = symbol. Help?

---

### Post by howefield on 2016-08-12
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by awjrichards on 2016-08-20
> **emotion2 said:**
> Just installed ubuntu on my mac book pro and the tilda key doesn't work it gives me '>' or some + under = symbol. Help?

I was having the same problem with 16.04 on my MacBook Air 6,2. The following fix worked for me:

```

$ echo options hid_apple iso_layout=0 | sudo tee -a /etc/modprobe.d/hid_apple.conf
$ sudo update-initramfs -u -k all
$ sudo reboot

```

I got this fix from [Apple Keyboard help page]("https://help.ubuntu.com/community/AppleKeyboard#Correcting_swapped_keys_and_wrong_keymaps_for_international_.28non-US.29_keyboards").

---

