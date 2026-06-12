---
title: "Installing a game &quot;dirname: missing operand&quot;"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Crazychicken on 2007-06-17
I installed Dockingstation for Linux, following the guidelines, but when I try to run it  it says
```
anna@anna-desktop:~/dockingstation_195_64$ dockingstation --help
dirname: missing operand
Try `dirname --help' for more information.

```

I'm a 17 years old girl who installed Ubuntu yesterday on a whim, so I didn't expect to make anything out of it, but my dad can't understand either. Help?


(and   *waves* hi!:D)

---

### Post by schorsch on 2007-06-17
If you are in the directory, where the dockingstation binary exists, you have to type:

```
./dockingstation --help
```

The leading "./" stands for the actual directory.

---

### Post by Crazychicken on 2007-06-17
It gives me the same error.

---

### Post by schorsch on 2007-06-17
Where did you get the software from and where are those guidelines you mentioned?

---

### Post by Crazychicken on 2007-06-17
[http://www.gamewaredevelopment.co.uk/downloads_more.php?id=448_0_8_0_M13](http://www.gamewaredevelopment.co.uk/downloads_more.php?id=448_0_8_0_M13)
here.
oh, but the file was here
[http://creatures.treesprite.com/Notice.html](http://creatures.treesprite.com/Notice.html)

---

### Post by schorsch on 2007-06-17
EDIT: If your game is installed the right way, please try the following command first:

```
bash dockingstation nocheck
```


O.K., i tried the installation by myself and there are some obstacles due to the fact that this game is a little bit older :p

The first thing:

If you want to use the default install, please change the following line in the instruction:

```
Type cd dockingstation_195_64 and [COLOR="Red"]sudo[/COLOR] ./dstation-install to start installation
```

I tried a custom install as mentioned by the installer, but this did not work, too .....:(

Second:

To start the game now, use the following line:

```
bash dockingstation nocheck
```

without the parameter "nocheck" the game searches for updates on a webserver, which does not exist any longer, as it seems .... it's a quite old game, remember? ;)

After that I got a graphical windows, but also an error message, that I have no sound ... but that will be another question. Perhaps it's just my laptop ...

---

### Post by Crazychicken on 2007-06-17
I get still the same message. I'll try to reinstall the game but... How do I uninstall it?  :biggrin:
Thank you for all the help!

---

### Post by schorsch on 2007-06-17
Deinstallation of the game is nearly the same as the installation:

```
Type "cd dockingstation_195_64" and "[COLOR="Red"]sudo[/COLOR] ./dstation-install [COLOR="Red"]uninstall[/COLOR]" to start deinstallation
```

---

### Post by Crazychicken on 2007-06-17
I reinstalled it and it seems just the same. but I can get it to do something more from that directory there v

yet apparently```
/usr/local/games/dockingstation/langpick: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
``` it says the same when it tries to use "imageconvert". That "libgtk-1.2.so.0:" is also mentioned in the Gameware page. I suppose I have to find it somewhere?

---

### Post by schorsch on 2007-06-18
```
apt-get install libgtk1.2
```

---

