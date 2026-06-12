---
title: "how do i update grub for a new OS?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-29
^^^^^

---

### Post by Turgon on 2006-08-29
You could try with:

sudo update-grub

But it didn't find vista for me.

Most likely, you will ahve to edit menu.list manualy:

sudo gedit /boot/grub/menu.lst

---

### Post by L_o_N_e_R on 2006-08-29
ill try that thnx :)

btw what part do i edit in menu.lst?

---

### Post by L_o_N_e_R on 2006-08-29
i tried to use the command... didnt work -.-


im tring to add mepis on GRUB 

andy help on editing the menu.lst?

---

### Post by L_o_N_e_R on 2006-08-29
bump

---

### Post by Tomosaur on 2006-08-29
That depends on what OS you're installing, and where you're installing it to.

---

### Post by L_o_N_e_R on 2006-08-29
i said mepis <_<

just installed btw

---

### Post by Tomosaur on 2006-08-29
Try running 'sudo update-grub' (from within Ubuntu) and it should add Mepis automatically.

---

### Post by confused57 on 2006-08-29
If you know the partition Mepis is on, here's my entry I had to add to Dapper menu.lst:
```
title             MEPIS at hda3, kernel 2.6.15-25-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 nomce quiet vga=791
boot
```

You'll have to edit it for your system, also you might be running the 2.6.15-26-386 kernel.

Just add something like the above to the very bottom of the /boot/grub/menu.lst file.

---

### Post by L_o_N_e_R on 2006-08-29
ill try


whats the kernel that came from the cd?

---

### Post by confused57 on 2006-08-29
> **L_o_N_e_R said:**
> ill try


whats the kernel that came from the cd?

I had installed the Mepis6.0-rc3, but I think the final release Mepis6.0 probably came with the 2.6.15-26-386 kernel.

Also, if you opted to install the Mepis grub to the Mepis root partition, you can boot Mepis from your Dapper grub using the following entry:
```
title          Mepis
root           (hd0,2)
chainloader +1
```

Of course, adjust entry to your partition Mepis is on.

---

