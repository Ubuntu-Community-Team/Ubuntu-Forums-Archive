---
title: "Slacker Radio Player with wine help!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by 4KvRMU7Nnv on 2007-12-11
Hi, I tried to install the slacker radio player ([www.slacker.com](www.slacker.com)) on ubuntu with wine 9.50 and it says that everything is installed correctly, but when I run it, it gives my hex code.  and an error.  here is the output from the terminal:
```
john@gaia:~$ wine '/home/john/.wine/drive_c/Program Files/Slacker/Software Player/slacker.jukebox.exe' 
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x34f958): Stub!
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x34fb10): Stub!
Could not find value for key log4j.appender.diag2
Could not instantiate appender named "diag2".
File option not set for appender [slacker3].
Are you using FileAppender instead of ConsoleAppender?
File option not set for appender [slacker1].
Are you using FileAppender instead of ConsoleAppender?
File option not set for appender [slacker2].
Are you using FileAppender instead of ConsoleAppender?
File option not set for appender [slacker4].
Are you using FileAppender instead of ConsoleAppender?
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x34f8d8): Stub!
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x34f870): Stub!
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x34f778): Stub!
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x34f778): Stub!
err:seh:setup_exception stack overflow 340 bytes in thread 0040 eip 7b84498a esp 7c5d3eac stack 0x7c5d4000-0x7c6e4000

```

If anyone knows what is wrong, please help me!

---

### Post by stego_s_aurus on 2007-12-11
First off, have you tried running wineconf and seeing if it will work when the default is set to win98 or win2000 or winxp? It may not work under one setting but will work on another.

If not, and if thats your only win program that you installed under wine, you might need to get IE6 installed first: There are plenty of instructions out there for installing IE6 and the core fonts, get that installed frst and then try again.

---

### Post by smoaky on 2008-03-31
If all else fails try this out.
 [http://www.pandora.com/](http://www.pandora.com/)
Works great with Linux and Wine is not needed.\\:D/
Peace

---

