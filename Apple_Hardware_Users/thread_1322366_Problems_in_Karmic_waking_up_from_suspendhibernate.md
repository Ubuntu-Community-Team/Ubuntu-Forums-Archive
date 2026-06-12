---
title: "Problems in Karmic waking up from suspend/hibernate"
date: 2009-11-10
forum: Apple Hardware Users
---

### Post by rpras on 2009-11-10
So my iBook G3 successfully suspends itself when I close the lid.  However, upon opening the lid, the display gets completely messed up.  I can see the login screen and the password prompt -- even be able to type my password in but it never fixes its display.

Have you been able to successfully wake up from a suspend/hibernate?  Did you have to do anything special to get it to work?

---

### Post by linuxopjemac on 2009-11-11
I recommend compiling pbbuttonsd.

[http://pbbuttons.berlios.de/](http://pbbuttons.berlios.de/)

---

### Post by rpras on 2009-11-11
> **linuxopjemac said:**
> I recommend compiling pbbuttonsd.

[http://pbbuttons.berlios.de/](http://pbbuttons.berlios.de/)

Thanks for the pointer!  I just checked -- pbbuttonsd 0.7.9-2ubuntu4 installed on my iBook.  I'll give the latest version -- 0.8.1a -- a try.

---

### Post by linuxopjemac on 2009-11-12
Is it in the Ubuntu repository ? I don't think so...

---

### Post by rpras on 2009-11-14
> **linuxopjemac said:**
> Is it in the Ubuntu repository ? I don't think so...

0.7.9-2ubuntu4 is but not 0.8.1a.  You have to compile it yourself.  It compiled fine for me -- still testing.

---

### Post by ant2ne on 2010-02-05
> **rpras said:**
> 0.7.9-2ubuntu4 is but not 0.8.1a.  You have to compile it yourself.  It compiled fine for me -- still testing.hows the testing going? Hows about a little tut on how you compiled installed and set it up. I'm a few steps behind you on every thread. LOL

---

### Post by ant2ne on 2010-02-06
```
ant2ne@bad-apple:~/bin/pbuttonsdinstall/pbbuttonsd-0.8.1a$ sudo make install
{bunch of stuff}
**Compiling ibam_stub.cpp:                                              [ERROR] ** 
  g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../intl -I../libpbbipc -I/usr/include/glib
  -2.0 -I/usr/lib/glib-2.0/include -c -o ibam_stub.o ibam_stub.cpp
  g++: No such file or directory
make[1]: *** [ibam_stub.o] Error 99
make: *** [install-recursive] Error 1
ant2ne@bad-apple:~/bin/pbuttonsdinstall/pbbuttonsd-0.8.1a$ 
```:(


I can't find ibam_stub.cpp in synaptec. ](*,)

---

### Post by alexmurray on 2010-02-06
ibam_stub.cpp is part of the source - you should try running:

```
./configure
make
sudo make install
```

Instead of just 'sudo make install' - ie. configure and compile it as a user, then just install using sudo.

---

### Post by mvz on 2010-03-14
I have suspend and resume working properly on my iBook with the standard Karmic kernel. I had to do two things to get this to work:

First, the wireless modules (airport and orinoco) need to be unloaded on suspend and reloaded on resume. I did this by adding a file **/etc/pm/config.d/local-sleep-modules**, containing the line:

```
SUSPEND_MODULES="ohci_hcd airport orinoco"
```

(Note: I already had the module ohci_hcd there before. I'm not sure unloading it is needed anymore.)

Second, the display needs to switch to a text terminal before suspending. I did this by adding a file **/etc/pm/sleep.d/00-local-chvt**, containing the following lines (adapted from **/usr/lib/pm-utils/sleep.d/99video**):

```

#!/bin/sh

. "${PM_FUNCTIONS}"

maybe_chvt()
{
    fgconsole |savestate console
    chvt 63
}

maybe_deallocvt()
{
    state_exists console || return
    chvt $(restorestate console)
    deallocvt 63
}

case "$1" in
        suspend) maybe_chvt ;;
        hibernate) maybe_chvt ;;
        resume) maybe_deallocvt;;
        thaw) maybe_deallocvt ;;
        help) help ;;
esac
```

This switching would happen automatically if the iBook's display driver did not have the 'no-chvt' quirk set (not sure why it's a quirk not to need to change the terminal).

---

### Post by ant2ne on 2010-03-15
What about screen dimming on the same iBook G3 model? WPA, reliable hibernate and suspend, and screen dimming are the things that are keeping from ubuntu right now. (yeah I know I want it all) and for the most part I get it all with slackintosh. [http://www.ant2ne.com/?p=173]("http://www.ant2ne.com/?p=173") I'd prefer ubuntu though.

---

### Post by mvz on 2010-03-17
> **Chauncellor said:**
> The LCD died on me and it's not worth getting another.


Is that the infamous [iBook backlight problem]("http://schwarztech.us/articles/ibookcable")? If you're comfortable opening up laptops, you may be able to fix it. Let me know if you need details.

---

### Post by ant2ne on 2010-04-12
I spent some time and I got ubuntu working on my 800Mhz iBook G3 to my satisfaction.

My requirements
1 Functional Linux OS with GUI
2 Ethernet, and wifi with WPA
3 Power management including screen dimming and quick and reliable suspend and hibernation.
4 Ability to easily install applications with apt-get

[You can read all about it here]("http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/").

---

