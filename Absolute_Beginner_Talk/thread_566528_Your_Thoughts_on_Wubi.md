---
title: "Your Thoughts on Wubi"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by TheZorch on 2007-10-03
I have a disk for installing Ubuntu but I heard about Wubi and decided to try it.  I works fine but when I tried to install the updated Nvidia drives I got an error message that the gcc header files were missing.  My wireless adapter from Buffalo won't work under Linux so I can't get out to the web via Ubuntu until I figure out a way to connect differently (I'm located far from the router).

Would I be better off resizing my NTFS partition and installing Ubuntu natively or is Wubi will ok and once I get online I'll fine, or no?  Please reply, I'm not new to computers but I am new to Linux.

---

### Post by jordanmthomas on 2007-10-03
Wubi should detect everything exactly the same as a normal installation, and the gcc / any headers are not installed by default in Ubuntu.

```
sudo apt-get install build-essential
``` will get you gcc and some other stuff (if you had an internet connection).  If you don't have a connection, linux isn't going to be much fun for you, just a warning.
You need to install the linux-sources to get the headers for the nvidia driver I think.

One thing, though, any reason you're trying to install the driver from nvidia's website instead of from Ubuntu's repositories?  (Granted, it will still be a pain with no internet connection)

---

### Post by Irihapeti on 2007-10-03
> **jordanmthomas said:**
> Wubi should detect everything exactly the same as a normal installation, and the gcc / any headers are not installed by default in Ubuntu.

```
sudo apt-get install build-essential
``` will get you gcc and some other stuff (if you had an internet connection).  If you don't have a connection, linux isn't going to be much fun for you, just a warning.
You need to install the linux-sources to get the headers for the nvidia driver I think.

One thing, though, any reason you're trying to install the driver from nvidia's website instead of from Ubuntu's repositories?  (Granted, it will still be a pain with no internet connection)

Build-essential and gcc are on the liveCD, at least in Feisty.

---

### Post by jordanmthomas on 2007-10-03
He doesn't have the CD though because he used Wubi.

---

