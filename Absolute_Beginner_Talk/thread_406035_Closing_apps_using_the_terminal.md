---
title: "Closing apps using the terminal"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-04-10
Does anybody know how to stop Beryl via the terminal.  I have been unable to boot into my computer for three days since an Ubuntu update.  The only thing I can boot into is Faisafe Terminal mode.

Help!!!

---

### Post by chakkaradeep on 2007-04-10
> **Norfolk 'n' Good said:**
> Does anybody know how to stop Beryl via the terminal. 

Try,

```
sudo killall beryl
```

---

### Post by caffienefree on 2007-04-10
killall beryl
killall beryl-manager

---

### Post by Kasper42 on 2007-04-15
I guess because you can't login at startup you want to stop beryl booting at startup?

Login a failsafe terminal in GRUB.

```
rm ~/.config/autostart/beryl-manager.desktop
```

then
```

rm ~/.config/autostart/beryl.desktop
```

I had exactly the same problem as you where I couldn't login to ubuntu for more than 20 secs without being logged out due to beryl. This also happened after I installed a software update.

---

