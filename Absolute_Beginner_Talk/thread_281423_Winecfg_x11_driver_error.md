---
title: "Winecfg x11 driver error"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by esma on 2006-10-21
I've recently installed Dapper Drake Ubuntu and wine, however when I try getting into the winecfg I get the following error

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

I've been looking for a solution all day but nothing I've done has worked.  Any help I could get with this would be appreciated.

---

### Post by bolt212 on 2006-10-23
I'me haveing the exact same problem.  been searching for 2 or 3 days and nothing as worked to fix it.

---

### Post by sumo on 2006-10-24
there is a rather simple solution just copy/pasta this into you konsole

sudo cp /usr/lib/wine/winex11.drv.so /usr/local/lib/wine/

and it all works out.

Much love from the n00b-5qu4d!

---

### Post by SendDerek on 2006-10-29
I've been getting this same error message. 

I tried what sumo had to say, but I couldn't find winex11.drv.so in the directory he specified.  I actually found it in a picassa directory:
"sudo cp /opt/picasa/wine/lib/wine/winex11.drv.so /usr/local/lib /wine/"

Well, I tried this method and ran winecfg (BTW: I'm working with wine version 0.9.24) and I recieved a different error message:

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).

```

Does anybody know what might be happening?

I don't know much about how wine works, but is it possibly the wrong winex11.drv.so file for the wine version?

If we need to, lets step back to the original problem with:
```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
err:imagelist:ImageList_ReplaceIcon no color!

```

---

### Post by SendDerek on 2006-10-29
Also, this same issue is being discussed at a more active thread here:

[http://ubuntuforums.org/showthread.php?t=245356](http://ubuntuforums.org/showthread.php?t=245356)

---

### Post by s_pradeep on 2007-11-13
You must be running the XServer as some user and u might be trying to run the application as root!

---

