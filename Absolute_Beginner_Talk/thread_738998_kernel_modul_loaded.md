---
title: "kernel modul loaded?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by benste on 2008-03-29
I want to use my Vaio and I've got one question, how can I see wheahter a modul is loaded?

these2:

> To enable these features in Linux you may need some additional drivers:

    * sony-laptop (CONFIG_SONY_LAPTOP and CONFIG_SONYPI_COMPAT)
    * sonypi (CONFIG_SONYPI) 

[http://www.linux.it/~malattia/wiki/index.php/Sony_drivers]("http://www.linux.it/~malattia/wiki/index.php/Sony_drivers")

---

### Post by c-ron on 2008-03-29
From the terminal or console:
```
lsmod | less
```

Note that the "|" is not an "l" (lower case L). "|" is usually located on the same key as the "\" character.
"lsmod" displays your loaded kernel modules, while piping the output (the "|") to the "less" screen pager will only display one screen of info at a time.

If you want to only see modules related to "sony":
```
lsmod | grep sony
```

"lsmod" will pipe ("|")  the output to the "grep" pattern matcher to find "sony".

If you want to load a certain module:
```
modprobe thenameofthemodule
```

---

### Post by benste on 2008-03-29
Thank you
> benste@VAIOFe31m:~$ lsmod | grep sony
sonypi                 23192  0 
sony_acpi               6540  0 
sony_laptop            35292  0 


PS: on a german keyboard the | is located top of the FN key (near STRG and AlT)
it normally contains < and >

---

