---
title: "Finder freezes when deleting files across a OS X/Linux network"
date: 2011-04-16
forum: Apple Hardware Users
---

### Post by pedrogent on 2011-04-16
I have my MacBook 5,2 hooked up to an Ubuntu 10.10 'server' via ethernet.

I've installed netatalk and avahi-daemon on the server. I've disallowed Spotlight (OS X's search utility) from indexing the networked drives.

Everything works as it should, however, from time to time when I delete files that reside on the Ubuntu server from my MacBook, Finder (OS X's file manager) will freeze. I can kill the Finder process. I then try to restart it from the Terminal from the command line but I get the following error message printed:

```
LSOpenURLsWithRole() failed with error -10810 for the file /System/Library/CoreServices/Finder.app.
```

The only solution I know of at present is to reboot the MacBook.

So I guess I need to know what my options are here. Is it better for me to use SMB? Or is there a config file I can alter? I have a feeling this bug may be linked to certain disallowed characters in file or pathnames as it doesn't happen all the time, although this is just a hunch.

Has anyone else experienced this bug?

I asked the same thing [here]("http://askubuntu.com/questions/34368/finder-freezes-when-deleting-files-across-a-os-x-linux-network"). But as yet I've had no luck.

---

### Post by pedrogent on 2011-04-19
*bump*

---

