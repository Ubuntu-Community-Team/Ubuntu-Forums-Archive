---
title: "fn key doesn&#359; work"
date: 2011-07-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Veren on 2011-07-18
Hello there,
I have an ASUS G73 and Natty 11.04. Ever since I installed it, the "fn" key on the left doesn't seem to work, just as don't work all the combinations with it.
I have there is an easy workaround I haven't found yet,
thank you for any advice.

---

### Post by toor58 on 2011-07-19
Can you be more specific? What keys are not working? Some? None? There may be something that can be done for certain keys.

---

### Post by klxy on 2011-07-21
can it work under windows?

---

### Post by toor58 on 2011-07-22
If you have your original windows flavor or some windows to go on it then yes all your keys should work.

---

### Post by testalucida on 2011-07-23
i have the same problem, too. NONE of the function keys combined with 'fn' key is working.
In concrete terms i would like to disable the touchpad. Someone knows a workaround? Thanks for your help

testalucida

---

### Post by testalucida on 2011-07-24
as for my asus x73s, the touchpad is recognized as PS/2 Logitech Mouse (id=13):

```

testalucida@ubuntu:~$ **xinput list**
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.00    id=11    [slave  pointer  (2)]
&#9116;   &#8627;* PS/2 Logitech Wheel Mouse                   id=13*    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; ASUS USB2.0 WebCam                          id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```...so I entered
```

testalucida@ubuntu:~$ **xinput set-prop 13 "Device Enabled" 0**

```

that makes the touchpad stop working.
Perhaps one could do that within a boot script.

Once deactivated, you have to reboot to activate it anew.

---

### Post by pupil on 2011-07-28
i am usingnest asus K43U, the "fn" button that works is: zz, wi-fi, brighnest, screen off
the "fn" button that doesn't work is: split display, off touchpad, volume

please give me advise to fix it.

---

### Post by Chromos on 2011-08-12
same problem here. asus k43sv. touchpad isnt recognized correctly and fn key doesnt work proper.

---

### Post by toor58 on 2011-08-13
Jupiter will help with touchpad, super engine, etc.

[http://www.webupd8.org/2011/04/jupiter-0050-released-fixes-restore.html]("http://www.webupd8.org/2011/04/jupiter-0050-released-fixes-restore.html")

Should help. Good luck.

PS: install the ppa for updates!

---

