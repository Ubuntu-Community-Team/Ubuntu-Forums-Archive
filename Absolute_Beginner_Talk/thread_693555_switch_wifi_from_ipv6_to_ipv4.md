---
title: "switch wifi from ipv6 to ipv4"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by PJVT on 2008-02-11
After I changed my aliases my wired network works fine but whe I switch to wireless my network still trying to use ipv6 and I cant reach the internet.

any help will be greately appreciated

by the way the laptop is a dell inspiron 1420 with an integrated wireless
802.11bgn card

thanks

---

### Post by jan quark on 2008-02-11
so you want to disable ipv6?

you can do this by blacklisting it

run this
```

gksudo gedit /etc/modprobe.d/blacklist
```

and add this line at the end

```
blacklist ipv6 
```

and safe

reboot

if your PC explodes after the reboot :)
you can undo this by simply doing the steps as mentioned above and removing the added line

---

### Post by sailor2001 on 2008-02-11
in your browser address line:  'about:config'  and in the filter search: 'ipv6'   .....double click on the ipv6 line to change false to true

---

