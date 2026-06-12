---
title: "How do I install this file?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Marklinh89 on 2006-09-09
I downloaded a program called Openbox off of its its website, with the tar.gz file extension.  My question is, how do i go about installing this file.  theres an install-sh file in it.  but i cant seem to install it.  

Any help is greatly appreciated.  As you can tell, im an Ubuntu n00b.. >_>

---

### Post by wakaimono on 2006-09-09
I am probably as new to Linux as you, but here is what I found through other threads.

from the terminal screen:
sudo ./whateverinstall

enter your password, should go. if not post the error.

---

### Post by Marklinh89 on 2006-09-09
it says command not found?

---

### Post by Delkster on 2006-09-09
> **wakaimono said:**
> I am probably as new to Linux as you, but here is what I found through other threads.

from the terminal screen:
sudo ./whateverinstall

enter your password, should go. if not post the error.

Quite a lot of software for Linux is available in the Ubuntu repositories, and it's usually easier and better to use the packages provided there rather than fetching the original packages (often source code instead of executable binaries -- in particular, .tar.gz packages are usually source packages) from each particular project's website.

Openbox is also available in the software repositories, and unless there's a compelling reason to use something else than the Ubuntu-packaged version, you should probably just find it in the repositories. Go to Applications > Add/Remove, select the "Show unsupported software" (or whatever it exactly is in English -- I currently have my desktop set to my native language) and search for openbox. You'll find ObConf, which is actually a configuration utility for Openbox, but if you install that, it'll also pull in Openbox itself. If you haven't enabled the "universe" repository you'll be asked whether you want to do so. Enable it, as Openbox is in universe (software that is packaged and provided in Ubuntu but with no official technical support).

Since Openbox seems to be another window manager or desktop environment rather than a conventional application, you probably won't find it in the Applications menu. Instead, to use it, you'll probably need to locate it in the session selection menu in the login window. I don't really know Openbox and have never used it so I can't really help much more, though.

---

### Post by Marklinh89 on 2006-09-09
I <3 You!

---

### Post by Omnios on 2006-09-09
[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)
Here is a quick guide there are also some other links by other users that are very good

---

### Post by Omnios on 2006-09-09
```

tom@miko:~$ sh --help
GNU bash, version 3.1.17(1)-release-(i486-pc-linux-gnu)
Usage:  sh [GNU long option] [option] ...
        sh [GNU long option] [option] script-file ...
GNU long options:
        --debug
        --debugger
        --dump-po-strings
        --dump-strings
        --help
        --init-file
        --login
        --noediting
        --noprofile
        --norc
        --posix
        --protected
        --rcfile
        --restricted
        --verbose
        --version
        --wordexp
Shell options:
        -irsD or -c command or -O shopt_option          (invocation only)        -abefhkmnptuvxBCHP or -o option
Type `sh -c "help set"' for more information about shell options.
Type `sh -c help' for more information about shell builtin commands.
Use the `bashbug' command to report bugs.


```

 basicly if I remember properly you can use the sudo sh filename.sh to launch it. Sudo is to install with root which some programs requir but not 100% of them

---

