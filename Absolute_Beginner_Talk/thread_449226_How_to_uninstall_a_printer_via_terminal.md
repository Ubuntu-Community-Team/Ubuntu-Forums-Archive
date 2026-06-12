---
title: "How to uninstall a printer via terminal"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by jabbapam on 2007-05-20
i just had some great help from RichGuk and my first post "trouble with Samba"

Now I can't open the printers window. It starts then just stops.

I think it may have happened after I set-up a printer.

I think if I can delete the printers via the terminal then I should be OK.

I've removed and reinstalled Samba and Cups with no improvement.

Any help would be greatfull

---

### Post by ajmorris on 2007-05-20
> **jabbapam said:**
> i just had some great help from RichGuk and my first post "trouble with Samba"

Now I can't open the printers window. It starts then just stops.

I think it may have happened after I set-up a printer.

I think if I can delete the printers via the terminal then I should be OK.

I've removed and reinstalled Samba and Cups with no improvement.

Any help would be greatfull

You could remove the printer via cups..... go into firefox (or the web browser you use) and in the URL bar type: 
[http://127.0.0.1:631](http://127.0.0.1:631)

Navigate to the printers tab and remove the printer.

---

### Post by jabbapam on 2007-05-20
Thank you,

I'm now not sure what's going on i can't print from my ubuntu pc to the connected printer, I can't even start print preview.

I can see my xp laptop but now can't see my ubuntu pc from the laptop.

I've uninstalled and reinstalled cups and samba with no luck.

I can't open 'printing' via system>administration.

When i try to print or open 'printing' nothing happens then about 5mins later I get a window that states 'CUPS server could not be contacted'

I really need some help!

---

### Post by ajmorris on 2007-05-20
> **jabbapam said:**
> Thank you,

I'm now not sure what's going on i can't print from my ubuntu pc to the connected printer, I can't even start print preview.

I can see my xp laptop but now can't see my ubuntu pc from the laptop.

I've uninstalled and reinstalled cups and samba with no luck.

I can't open 'printing' via system>administration.

When i try to print or open 'printing' nothing happens then about 5mins later I get a window that states 'CUPS server could not be contacted'

I really need some help!

What happens if you type this into a terminal?:
```
gnome-cups-manager
```

---

### Post by jabbapam on 2007-05-20
It took some time but this finally came up...

joe@joe-desktop:~$ gnome-cups-manager

** (gnome-printer-view:13766): WARNING **: IPP request failed with status 1280
joe@joe-desktop:~$ 

Then the previous window of 'CUPS server could not be contacted' came up.

---

### Post by jabbapam on 2007-05-21
Fixed It!

Somehow I had put 'ServerName 192.168.0.1' into /etc/cups/client.conf

Have removed and its working again.

Thanks for your help ajmorris

---

