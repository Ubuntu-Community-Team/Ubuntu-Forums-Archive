---
title: "[SOLVED] Getting a Korn shell"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Mr.Ganja on 2007-07-15
total newbie here

got ubuntu feisty maybe 2 weeks ago

i have this book on UNIX that i found useful but there is a part in it that describes the Korn shell
and it's use. I want to learn about it

I need help with getting a korn shell to run in a terminal. 

Absolutely no idea how to do it?

please help

---

### Post by kevinlyfellow on 2007-07-15
```
sudo apt-get install ksh
ksh
```

You can login by default using the korn shell if you like (but be sure you will remember how to change it back!!!)
```
sudo usermod -s ksh <username>
```

But bash is great (actually, better than great), and there are a lot of similarities.  Have fun with korn, but be sure to learn bash since just about everyone uses it nowadays in their distros.

---

### Post by jtraub on 2007-07-15
```

sudo aptitude install ksh

```

Then every time you need to use Korn shell you should open terminal and type 
```
ksh
```

I recommend you not to setup ksh as you default shell for the first time

---

### Post by jtraub on 2007-07-15
> **kevinlyfellow said:**
> ```
sudo apt-get install korn
korn
```

You can login by default using the korn shell if you like
```
sudo usermod -s korn <username>
```


Hm..
```

mikv@hawk:~$ sudo aptitude show korn
&#1055;&#1072;&#1082;&#1077;&#1090;: korn
&#1057;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077;: &#1085;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
&#1042;&#1077;&#1088;&#1089;&#1080;&#1103;: 4:3.5.6-0ubuntu6
&#1055;&#1088;&#1080;&#1086;&#1088;&#1080;&#1090;&#1077;&#1090;: &#1085;&#1077;&#1086;&#1073;&#1103;&#1079;&#1072;&#1090;&#1077;&#1083;&#1100;&#1085;&#1099;&#1081;
&#1056;&#1072;&#1079;&#1076;&#1077;&#1083;: universe/kde
&#1057;&#1086;&#1087;&#1088;&#1086;&#1074;&#1086;&#1078;&#1076;&#1072;&#1102;&#1097;&#1080;&#1081;: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1074; &#1088;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1072;&#1085;&#1085;&#1086;&#1084; &#1074;&#1080;&#1076;&#1077;: 635k
&#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;: kdelibs4c2a (>= 4:3.5.5-1), libc6 (>= 2.5-0ubuntu1), libgcc1 (>=
                        1:4.1.2), libice6 (>= 1:1.0.0), libpng12-0 (>=
                        1.2.13-4), libqt3-mt (>= 3:3.3.8really3.3.7), libsm6,
                        libstdc++6 (>= 4.1.2), libx11-6, libxext6, zlib1g (>=
                        1:1.2.1), kdepim-kio-plugins | kdebase-kio-plugins
&#1054;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: KDE mail checker
 Korn is a KDE mail checker that can display a small summary in the Kicker tray.
 It supports checking mbox, pop3, imap4, and nntp sources. 
 
 Once mail is received you can have Korn run a third party program or change the
 color/icon of the Kicker display.  In addition to this you can have Korn run a
 program once you click on the docked icon in Kicker. 
 
 This package is part of the official KDE pim module.

```

---

### Post by kevinlyfellow on 2007-07-15
> **jtraub said:**
> Hm..
```

mikv@hawk:~$ sudo aptitude show korn
&#1055;&#1072;&#1082;&#1077;&#1090;: korn
&#1057;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077;: &#1085;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
&#1042;&#1077;&#1088;&#1089;&#1080;&#1103;: 4:3.5.6-0ubuntu6
&#1055;&#1088;&#1080;&#1086;&#1088;&#1080;&#1090;&#1077;&#1090;: &#1085;&#1077;&#1086;&#1073;&#1103;&#1079;&#1072;&#1090;&#1077;&#1083;&#1100;&#1085;&#1099;&#1081;
&#1056;&#1072;&#1079;&#1076;&#1077;&#1083;: universe/kde
&#1057;&#1086;&#1087;&#1088;&#1086;&#1074;&#1086;&#1078;&#1076;&#1072;&#1102;&#1097;&#1080;&#1081;: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1074; &#1088;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1072;&#1085;&#1085;&#1086;&#1084; &#1074;&#1080;&#1076;&#1077;: 635k
&#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;: kdelibs4c2a (>= 4:3.5.5-1), libc6 (>= 2.5-0ubuntu1), libgcc1 (>=
                        1:4.1.2), libice6 (>= 1:1.0.0), libpng12-0 (>=
                        1.2.13-4), libqt3-mt (>= 3:3.3.8really3.3.7), libsm6,
                        libstdc++6 (>= 4.1.2), libx11-6, libxext6, zlib1g (>=
                        1:1.2.1), kdepim-kio-plugins | kdebase-kio-plugins
&#1054;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: KDE mail checker
 Korn is a KDE mail checker that can display a small summary in the Kicker tray.
 It supports checking mbox, pop3, imap4, and nntp sources. 
 
 Once mail is received you can have Korn run a third party program or change the
 color/icon of the Kicker display.  In addition to this you can have Korn run a
 program once you click on the docked icon in Kicker. 
 
 This package is part of the official KDE pim module.

```

Oops, I forgot, the program is ksh, I'll edit above to fix that.  Thanks

Edit:  Looks like you did it for me :-)

---

### Post by Mr.Ganja on 2007-07-15
works great thanks:)

---

