---
title: "Subpixel Font Rendering"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by doctorberen on 2007-01-18
I had been playing around with Kubuntu. In Ubuntu, there was this [_how-to_]("http://www.ubuntuforums.org/showthread.php?t=235526") on activating subpixel font rendering. This was apparently turned off in fear of patent violations.

The instructions was to type this:
```
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy experimental
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy experimental
```I was able to do this without problem in Ubuntu. In Kubuntu, when I type the first line in the terminal, I get this message:
```
bash: deb: command not found
```What's going on? How can I fix this? What's a workaround?

Or is there any other way to activate subpixel font rendering in Kubuntu? Was that how-to only for Ubuntu?

---

### Post by po0f on 2007-01-18
doctorberen,

Add those lines to /etc/apt/sources.list, they're not commands.

---

### Post by doctorberen on 2007-01-19
poOf, thanks a million! That fixed the problem.

---

