---
title: "Apple International English Keyboard"
date: 2009-03-10
forum: Apple Hardware Users
---

### Post by Pedro Borges on 2009-03-10
Hi,

Which Keyboard layout do I use with an Intl EN Keyboard?


Thanks!

---

### Post by dennda on 2009-09-03
*bump*

Does anybody know the answer?
I have the same keyboard now and I do wonder what keyboard layout I should choose...

The keyboard looks like this: [http://tinyurl.com/n8k4w4](http://tinyurl.com/n8k4w4)

Thanks in advance.

---

### Post by luigi.viggiano on 2009-09-03
Hi. I use "USA Macintosh" but I have ±§ and ~` swapped on my keyboard, so I added this script to Session Startup of Gnome:

```

#!/bin/bash

# fix keyboard layout switching §± and `~
xmodmap -e "keycode 49 = section plusminus section plusminus section plusminus"
xmodmap -e "keycode 94 = grave asciitilde grave asciitilde dead_grave dead_horn"

```

HTH.

Posted here, to have an easy (for me) reference for future :)
[http://en.newinstance.it/2009/09/03/macbook-international-keyboard-and-linux/](http://en.newinstance.it/2009/09/03/macbook-international-keyboard-and-linux/)

---

