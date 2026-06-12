---
title: "Program install : DeVeDe"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-20
I want to install the above program and screwed up the last install so bad I want to be sure of what I'm doing before issuing commands at the terminal :) 

I have extracted the files for this program into a folder which include among others :

devede.py
devede.glade
devede.gladep

as well as :

install.sh

I presume I just type sudo ./install at the terminal in the directory I have placed this files in ( a sub-directory of my Home) and away it goes ??

If I don't like the program or it doesn't install correctly how do I remove it?

Thanks

---

### Post by taurus on 2006-04-20
Sorry but you need to use sudo to install it since it will copy it to /usr/bin and you, a regular user, don't have permission to write to it...  Open a terminal and type
```

sudo ./install.sh

```

---

### Post by cliff0108 on 2006-04-20
Thanks Taurus
Now if I wan't to subsequently "uninstall"  it what do I do?

---

### Post by taurus on 2006-04-20
As far as I know, there is no uninstall.sh so if you want to remove it, you have to do it by hand.  The binary is in /usr/bin (/usr/bin/devede.py).  Of course, you can always look in install.sh to see where everything is installed and remove each one by hand then.

```

#!/bin/bash

install devede.py /usr/bin/
chmod 755 /usr/bin/devede.py
install -d /usr/share/devede/
install -d /usr/share/doc/devede/
install -d /usr/share/locale/es/LC_MESSAGES
install -d /usr/share/locale/gl/LC_MESSAGES
install po/es.mo /usr/share/locale/es/LC_MESSAGES/devede.mo
install po/gl.mo /usr/share/locale/gl/LC_MESSAGES/devede.mo
install devede.glade /usr/share/devede/devede.glade
install devede.png /usr/share/pixmaps/
install devede.desktop /usr/share/applications/devede.desktop
install docs/* /usr/share/doc/devede/
install pixmaps/* /usr/share/devede/

```

---

