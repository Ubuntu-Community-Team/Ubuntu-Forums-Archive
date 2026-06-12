---
title: "Errors when installing Yab adesklet"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by tijmz on 2007-03-21
Hi all,

I have tried to follow [this tutorial](http://doc.gwos.org/index.php/Adesklets) to install the Yab adesklet, but I can't get it running. During installation, I get the following.

```
tijmz@tijmz-desktop:~/yab-0.0.2$ ./yab.py --nautilus
Do you want to (r)egister this desklet or to (t)est it? r
Traceback (most recent call last):
  File "./yab.py", line 48, in ?
    import adesklets
  File "/usr/lib/python2.4/site-packages/adesklets/__init__.py", line 43, in ?
    raise e
adesklets.error_handler.ADESKLETSError: adesklets interpreter initialization error - can not set locale properly

Exception exceptions.AttributeError: <exceptions.AttributeError instance at 0xb7d3408c> in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0xb7c43f8c>> ignored
```

If I just run adesklets I get this:

```
    adesklets --nautilus
can not set locale properly
can not set locale properly
```

Obviously, something is wrong with my locale settings. I ran through a couple of suggested fixes (like [this one](http://codepoets.co.uk/lc_ctype_lc_messages_lc_all_locale_ubuntu)) but the errors are here to stay. 

Can anyone help me fix the locale problem/get yab to work?

Regards
tijmz

---

### Post by louis_nichols on 2007-03-21
I suggest you visit the [adesklets forum]("http://adesklets.sourceforge.net/forum/") and ask about this there. You are almost certain to obtain a solution there.

---

### Post by tijmz on 2007-03-21
Thanks, I will.

---

