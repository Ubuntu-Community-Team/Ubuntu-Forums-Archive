---
title: "bz2 module not available?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Ikith on 2008-04-08
So I'm really bored and I am using jhbuild to compile gnome 2.22 for 7.10. I've had a few problems that I have solved along the way but this one I cannot find an answer too nor figure out:

```
*** Installing waf *** [13/14]
make   install
./waf-light install --strip --prefix=/opt/gnome2
------> Executing code from the top-level wscript <-----
-> preparing waf
Traceback (most recent call last):
  File "./waf-light", line 139, in ?
    Scripting.prepare()
  File "/home/mearle/checkout/gnome2/waf-1.3.2/wafadmin/Scripting.py", line 292, in prepare
    if fun: fun()
  File "/home/mearle/checkout/gnome2/waf-1.3.2/wscript", line 285, in init
    create_waf()
  File "/home/mearle/checkout/gnome2/waf-1.3.2/wscript", line 118, in create_waf
    tar = tarfile.open('%s.tar.%s' % (mw, zipType), "w:%s" % zipType)
  File "/opt/gnome2/lib/python2.4/tarfile.py", line 901, in open
    return func(name, filemode, fileobj)
  File "/opt/gnome2/lib/python2.4/tarfile.py", line 990, in bz2open
    raise CompressionError, "bz2 module is not available"
tarfile.CompressionError: bz2 module is not available
make: *** [install] Error 1
*** error during stage install of waf: ########## Error running make   install *** [13/14]

  [1] rerun stage install
  [2] ignore error and continue to done
  [3] give up on module
  [4] start shell
choice:
```

Can anyone help me out? Thanks.

---

### Post by sdennie on 2008-04-08
I think you can fix this by doing the following:

```

sudo apt-get install php5-cli

```

That will install, among other things the python bz2 module.

---

