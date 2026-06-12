---
title: "Installation of any software/updation always gives netbeans error"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ayesha kalra on 2007-06-12
Hi Ubuntuers (is that a word?)

Every time I install something or update my system I get this error message

```

Setting up netbeans5.5 (5.5-0.59) ...
This package is an installer package, it does not actually contain the NetBeans IDE. You will need to go download the IDE from:
Feom the NetBeans IDE 5.5 Dowload page: 
http://www.netbeans.info/downloads/all.php?b_id=2323

Select the English(en) tgz Download Archive Distribution 82.8 MB
http://www.netbeans.info/download/start.php?f_id=13710&lang_id=1

and place the file in /tmp (with root.root ownership) now.

[Press RETURN to try again, 'no' _RETURN  to abort]

```. Every time I updat emy system I have to type 'no' + press RETURN and then the updation continues. Finally is gives the following message.

```

E: netbeans5.5: subprocess post-installation script returned error exit status 1

```

All this started when I was trying to get NetBeans. I must have tried to install it from command line. I do not remember exactly how. But is there anyway I can correct it so that this message does not show up. The message itself tells me to put the file in /tmp ... I do not fully understand it. Any help here will be very much appreciated.

Thanks
Ayesha

---

### Post by zvacet on 2007-06-13
```
sudo apt-get --purge remove netbeans5.5
```

---

