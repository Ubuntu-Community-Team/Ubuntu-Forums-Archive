---
title: "music-applet 0.9.2 i want 2.1.0. for Exaile .tar.gz"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-03-23
hi, music-applet is available in the repositories, but it's a very early version with no support for Exaile, my player of choice. i have downloaded the source from:
```
http://www.kuliniewicz.org/music-applet/
```
and it is a tar.gz file
> music-applet-2.1.0.tar.gz
i extract it and then open terminal and type:
```
cd Desktop/music-applet-2.1.0
sudo ./configure

```
at this point it came with an error python headers, i installed python 2.4 dev
once configure is finished i go:
```
sudo make
sudo make install
```
then i expect the new pannel applet to be there, but it isn't

what am i doing wrong?

---

### Post by zvacet on 2007-03-23
Wrongcommand is :sudo make .It should be make .Just last one goes with sudo :
sudo make install

---

### Post by bortx on 2007-05-13
Facing the same problem.

I've compiled it successfully, but when trying to perform 'make' I get this error

```

file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[2]: *** [de.gmo] Error 127

```

It seems that variable GMSGFMT is null, because 'make' is trying to ferform this action

```

file=`echo $* | sed 's,.*/,,'`.gmo \
	  && rm -f $$file && $(GMSGFMT) -o $$file $<

```

Any help? Thanks a lot

---

### Post by bortx on 2007-05-15
> **bortx said:**
> Any help? Thanks a lot

I answer myself:

Installed library libgettext-ruby-util and compile sucessfully. Now enjoying music applet for exaile in feisty 

:)

---

### Post by ernz on 2007-05-28
[COLOR="White"]keywords: add to panel, exaile, music, applet, music-applet, missing, problem, 2.1.0[/COLOR]
If you are having trouble with the applet not showing in the Add to Panel menu with version 2.1.0 my post here might help:

[http://ubuntuforums.org/showpost.php?p=2734258&postcount=5]("http://ubuntuforums.org/showpost.php?p=2734258&postcount=5")

---

