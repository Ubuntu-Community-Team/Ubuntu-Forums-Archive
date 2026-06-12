---
title: "Google Earth Install Trouble"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by dreamersword on 2007-04-23
I downloaded the GoogleEarthLinux.bin program from google and installed it by running 

sudo ./GoogleEarthLinux.bin 

I get the follow message 
```

Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.2735.0..................................................................

(setup.gtk2:15850): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(setup.gtk2:15850): Gdk-WARNING **: locale not supported by C library
Installing mimetypes...
Running /usr/bin/update-mime-database /home/dreamersword/.local/share/mime

Note that '/home/dreamersword/.local/share' is not in the search path
set by the XDG_DATA_HOME and XDG_DATA_DIRS
environment variables, so applications may not
be able to find it until you set them. The
directories currently searched are:


- /root/.local/share
- /usr/local/share/
- /usr/share/

Installing desktop menu entries....

- /root/.local/share
- /usr/local/share/
- /usr/share/

Installing desktop menu entries...

```

It says it installs ok but when i got to run it. It comes up with a little box the says going earth and on the tool bar it says initializing and it never does anything after that. It just stays there until i force it to close. 

Any suggestions?

---

### Post by john38242 on 2007-04-23
what I did was right click the bin file then I put a check mark where it says allow executing of this program. then open it up  it run with terminal 

that worked for me

---

### Post by john38242 on 2007-04-23
sorry just click run  not run with terminal

---

### Post by dreamersword on 2007-04-23
but if you run it that way you don't install it as root. Would that get you into trouble if you want to use multiply users? 

I went ahead and tried it anyways and i got the same thing. The error message seems to indicate that i a missing something with gtk. I tried installing some of the libraries. I also tried adding the /home/dreamersword/.local/share to the PATH to see if that helped put no luck.


Any thoughts?

---

