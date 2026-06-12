---
title: "Wine Trouble"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-06-24
How do I get rid of Wine completely on my computer? Like, to where there's no starting path for it under Applications?

---

### Post by shifty_powers on 2007-06-24
```
sudo dpkg -r wine
```

Should do the trick. You can always take away menu's with system>preferences>main menu....

Any particular reason you are purging wine?

---

### Post by kevCast on 2007-06-24
A change in philosophy. I was using closed software when there were suitable open source alternatives. Also, I only used it for utorrent, and I've only recently found out their deal with the bittorrent mainline. A little silly, I know, but it's not worth getting slammed with a multi-thousand dollar fine because I was seeding for others. It is a great Windows emulation tool though, it just wasn't for me I guess.

Thank you for the help shifty, I appreciate it.

:)

[I]Edit: ```
dpkg - warning: ignoring request to remove wine, only the config
 files of which are on the system.  Use --purge to remove them too.
```

Error message. =/[/I]

---

### Post by shifty_powers on 2007-06-24
well first of all try

```
sudo apt-get autoremove
```

also

```
sudo dpkg -P wine
```

I think should be the purge command...

And my pleasure ;)

If stuck

```
dpkg --help
```

is a good start ;)

---

### Post by kevCast on 2007-06-24
I think that did it. Thank you shifty, again.

^_^

---

### Post by shifty_powers on 2007-06-24
glad to be of service :D

---

