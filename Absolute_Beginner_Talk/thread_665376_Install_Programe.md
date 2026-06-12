---
title: "Install Programe"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2008-01-12
Using Ubuntu 7.10
Trying to install osmo
Everything goes as expected until I use 'make'

For instance when I use .configure I get ....(see these last few lines):

checking for style of include used by make... GNU

checking dependency style of gcc... gcc3

checking whether GTK+ version >= 2.8... no

configure: error: GTK+ not found or too old (version < 2.8)

bernard@bernard-desktop:~/Documents/osmo/osmo-0.1.2$ 


Then when I use ....' make' ...I get:

bernard@bernard-desktop:~/Documents/osmo/osmo-0.1.2$ make

make: *** No targets specified and no makefile found.  Stop.

bernard@bernard-desktop:~/Documents/osmo/osmo-0.1.2$ 


Can you see what is wrong here please ..... has it anything to do with the last 2 lines of ./configure?

Thanks


Bernard

---

### Post by amo-ej1 on 2008-01-12
Well you should correct the error configure tells you :

```

configure: error: GTK+ not found or too old (version < 2.8)

```

So you need to get the GTK+ development files (of a version >=2.8) in order to be able to successfully make it. The makefile will only be written if the configure succeeds.

---

### Post by bern1939 on 2008-01-12
Thank you ....yes I do understand that but expected that this type of dependency would be available via Synaptic!

Where do I find the missing file and what might be its precise name?


Thanks


Bernard

---

### Post by carverj on 2008-01-12
Not totally sure so googled this result: -
[http://ubuntuforums.org/showthread.php?t=91776](http://ubuntuforums.org/showthread.php?t=91776)

---

### Post by bern1939 on 2008-01-12
Thanks to all but this seems very difficult for a total newbie.

Cannot really find the GTK+ file

Ah well ..... might be included in next release!!!


Bernard

---

