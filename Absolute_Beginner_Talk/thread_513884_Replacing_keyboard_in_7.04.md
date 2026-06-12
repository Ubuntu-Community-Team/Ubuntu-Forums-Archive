---
title: "Replacing keyboard in 7.04"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by zuolan on 2007-07-31
I had to replace my keyboard from one connected through rs232 to that through ps/2. Now after ubuntu boots up, it does not respond to the keyboard that I cannot login. However, the keyboard works for the bios setup, Windows 2000 and grub still works. Any one can help? Thanks.

---

### Post by be4truth on 2007-07-31
reboot in rescue mode
you should be able to use your keyboard then. Then type 

```
dpkg-reconfigure xserver-xorg
```

Go with the defaults (just press enter) until you come to the keyboard section.

---

### Post by zuolan on 2007-08-01
Thank for the suggestion. When I boot up in safe mode, the keyboard stopped working. What should I do?

---

### Post by be4truth on 2007-08-02
Do you have a second computer handy? Home network?

---

### Post by zuolan on 2007-08-02
I do have access to other computers. Also, I still have the old keyboard(minus the right arrow). So I can still logon to ubuntu with that keyboard. Does this help?

---

### Post by be4truth on 2007-08-02
You could try to connect the old keyboard, boot into Ubuntu, open a shell and type in:

```
dpkg-reconfigure xserver-xorg
```

Stay with the default except when the keyboard part comes. There you choose PS2 after you went through with the configuration your old key board may fail. Then switch you computer off. Attach the new keyboard and reboot.
Hope that works. I don't have an old keyboard to try.

---

