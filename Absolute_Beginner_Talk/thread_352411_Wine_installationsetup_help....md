---
title: "Wine installation/setup help..."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by drky on 2007-02-03
Hey, i'm currently trying to get wine installed and setup so i can have a go at running photoshop cs2 in ubuntu.

I've got wine installed however every time i run

'sudo wine /*' 

in the terminal to create the directory structure i get an error:

'wine: could not load L"Z:\\ATI_LICENSE.TXT": Bad EXE format for'

Can anyone recommend anything?

I have the ATI drivers installed according to 'fglrxinfo' and the ATI_LICENSE.txt file is in my filesystem directory.

Any help greatly appreciated

---

### Post by pseudonym on 2007-02-03
You shouldn't be running wine as sudo. If you have wine installed via apt-get or Synaptic, what you need to do is type 'winecfg' in the terminal, as regular user. A wine configuration GUI will come up with some settings for you. Once you're done your ~/.wine directory gets created.

You should also browse the documentation at winehq.com if you haven't already. There's plenty of useful stuff, including an apps database and a wiki.

HTH

---

### Post by drky on 2007-02-03
Wicked thanks for that, i'll give it a go and see what happens

---

