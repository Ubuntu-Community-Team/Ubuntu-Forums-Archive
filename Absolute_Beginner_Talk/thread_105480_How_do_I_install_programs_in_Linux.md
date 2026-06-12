---
title: "How do I install programs in Linux?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Robert Leithe on 2005-12-18
Hi,

How on earth do you install new programs in Linux? I've been working with DOS/Windows the last 15 years, but have absolutely no experience with Linux (any distributions).

I downloaded firefox-1.5.tar.gz from [www.mozilla.com](www.mozilla.com) and tried to follow the installation described at this address [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion), but to no avail. When I try to start Firefox now (from the "Start menu") what happens is this:

1) I get a message on the line at the bottom of my screen saying "Starting Mozilla Firefox"
2) The mouse pointer changes indicating activity
3) After a short while the "Starting Mozilla Firefox" message disappears and the mouse pointer returns to normal. That's it.

---

### Post by kaamos on 2005-12-18
What happens when you run it from a terminal by typing "firefox" ?

About installing programs in general, look here: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
Very easy :)

---

### Post by aysiu on 2005-12-18
[quote=Robert Leithe]How on earth do you install new programs in Linux? I've been working with DOS/Windows the last 15 years, but have absolutely no experience with Linux (any distributions).[/quote]Programs in general? See the second link in my sig.

The most up-to-date versions of programs... well, you're in for hurting if you don't like the command-line.

That said, all the instructions for Firefox 1.5 are at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

If you're fine with Firefox 1.0.7 (that's what I use), do nothing. I would advise, since you're new to Linux, that you start by doing the simple stuff first--get comfortable. Then, move on to getting cutting edge versions of software.

---

### Post by Robert Leithe on 2005-12-18
kaamos: When I type "firefox" in the terminal window I get this message:
/opt/firefox/firefox-bin: error whilw loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

aysiu: I have no problems with command line ;)

Robert

---

### Post by aysiu on 2005-12-18
Can we assume you've already done this? ```
sudo apt-get install libstdc++5
```

---

### Post by Robert Leithe on 2005-12-18
No, you can't... ;)

But after I did so, Firefox 1.5 works like a charm!

Thanks for your help and for your links to further reading.

If you have the time:
What exactly is the "sudo" command? I've seen it several places tonight, both in various documentation I've browsed through, and now in your posting here...

---

### Post by aysiu on 2005-12-18
You can read all about it here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

