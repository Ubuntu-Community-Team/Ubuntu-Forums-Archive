---
title: "Intialization lost after updating ... Why?"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by pmilin@ptt.yu on 2006-03-06
Hi,
Although I am not a complete newbie, I thought that it would be the best to put my question here, for other people sake. In very brief, few days ago I did updating (when I got a chance to have solid connection, not dial-up), and did linux-headers upgrading from 2.6.12-9 to 2.6.12-10. First, I lost possibility to load either Ubuntu or Win XP, and after some hokes-pokes and sniffing around, I realized that, by divine will, my grub's menu.lst changed path to linux from hda2 to hda5 (swap is here!) and erased Win XP from a list. I fixed that, and everything is loading fine, except that those nicely made initialization sequences, in Ubuntu's brownish colors have been lost, and now I have console-like black-and-white sequence of:
something                           [ok]
something else                    [ok]
another thing                       [ok]
Why is that nicely designed colored thing gone? I would like to have that back, for the pleasure of my eyes only, since functionality is ok.

Sincerely,
[email]pmilin@ptt.yu[/email]

---

### Post by Moebius on 2006-03-06
You may need to edit your /boot/grub/menu.lst and add "splash" (without quotes) to your "kernel" option.

I'll give you a example of how I've set up mine (splash highlighted)

```
title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda3 ro quiet **splash** vga=795
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot
```

---

