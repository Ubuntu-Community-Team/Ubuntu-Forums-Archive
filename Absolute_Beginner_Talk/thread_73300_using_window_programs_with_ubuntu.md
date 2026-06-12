---
title: "using window programs with ubuntu?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by macgip on 2005-10-08
hello guys I'm new to ubuntu and i'm willing to crossover to ubunto, but i have several prgrams that i use with my current windows xp. My main question is what windows based programs can i use with ubunto if there is any.:)

---

### Post by loupy on 2005-10-08
You can install Wine to run some Windows programs.  There is also a non-free version of Wine called CrossOver Office which will makes it easier to install Win programs.  I've removed windows entirely from my main machine and run only ubuntu with CrossOver Office and it works fine for me (Lotus Notes and Quicken 2005).

check out the trial at [www.codeweavers.com](www.codeweavers.com)

---

### Post by zerhacke on 2005-10-08
Untill you install some special packages, you can't use any Windows programs with Ubuntu.  None.

However, there's several suites designed to let you run Windows programs under Ubuntu/Linux.  One is called WINE.  To install it, I believe you insert

```
sudo apt-get install wine
```

in a command prompt such as Xterm.  It'll connect to the internet and download the WINE suite of programs and libraries.  Once it's done that, you launch your Windows programs by typing into a command prompt such as Xterm

```
wine /path/to/program/name-of-program.exe
```

You'll either get lucky and the program you're trying to run will start, or you'll get unlucky and the program you're trying to start isn't supported by WINE.

There's also a configuration program for WINE that sets up a lot of info WINE needs, like where the base of the system should be.  I'll get you the name of the program in a jiffy, as soon as I install WINE myself.

Also, there's more Windows compatiblity software out there than just WINE.  It just happens to be the only one I know anything about.  Someone else is bound to come along and tell you the name of another program that will do what you want as well.  You may want to listen to their advice over mine, because I'm not as Linux knowledgable as many of the other folks at this site.

---

### Post by macgip on 2005-10-08
thanks i will give it a try when i install ubuntu. i still have to get thrue the dual boot part. but thanks it gave me an idea of what to expect.

---

### Post by macgip on 2005-10-08
thanks for the replay i will give it a try as soon as get thrue the dual boot part of the install. i still don't want to loose windows just yet.

---

### Post by Azrael on 2005-10-08
Don't forget though, where Wine fails, Qemu often comes to the rescue.

Check [this thread]("http://ubuntuforums.org/showthread.php?t=39513") out.

---

### Post by Nasso on 2005-10-08
There are probably replacements for the windowsapps you use. Post here what you are looking for and we will be glad to tell you what the replacements are :)

Some examples,
photoshop can be replaced by gimp,
msn by gaim,
mirc by xchat,
winamp by xmms or beep-media-player, 

and so on...

---

### Post by macgip on 2005-10-08
one of them is dvd burning software and cd. like nero or roxio. can you give me some replacement on these.

---

### Post by Wolki on 2005-10-08
GnomeBaker and K3B are the most popular choices. There's also Graveman, Xcdroast and NeroLinux, among others. You can burn data CDs/DVDs and disk images with standard gnome, and audio CDs with serpentine which will be installed by default in Breezy.

---

### Post by TraderEyal on 2005-10-08
Hi, I tried the apt-get install wine and got a message that Package wine is not available, but is referred to by another package.
E: Package Wine has no installation candidate.

Any idea why this happened?

Thanks
Eyal


[QUOTE=zerhacke]Untill you install some special packages, you can't use any Windows programs with Ubuntu.  None.

However, there's several suites designed to let you run Windows programs under Ubuntu/Linux.  One is called WINE.  To install it, I believe you insert

```
sudo apt-get install wine
```

in a command prompt such as Xterm.  It'll connect to the internet and download the WINE suite of programs and libraries.  Once it's done that, you launch your Windows programs by typing into a command prompt such as Xterm

```
wine /path/to/program/name-of-program.exe
```

You'll either get lucky and the program you're trying to run will start, or you'll get unlucky and the program you're trying to start isn't supported by WINE.

There's also a configuration program for WINE that sets up a lot of info WINE needs, like where the base of the system should be.  I'll get you the name of the program in a jiffy, as soon as I install WINE myself.

Also, there's more Windows compatiblity software out there than just WINE.  It just happens to be the only one I know anything about.  Someone else is bound to come along and tell you the name of another program that will do what you want as well.  You may want to listen to their advice over mine, because I'm not as Linux knowledgable as many of the other folks at this site.[/QUOTE]

---

### Post by aysiu on 2005-10-08
Have you [enabled extra repositories](http://www.psychocats.net/sources.html)?

---

### Post by TraderEyal on 2005-10-08
[QUOTE=aysiu]Have you [enabled extra repositories](http://www.psychocats.net/sources.html)?[/QUOTE]

I tried that. It gave me an error:

Error: /var/tmp/kdecache-myusername is owned by uid 1000 instead of uid 0
links points to /var/tmp/kdecache-root

I tried the same as root and got this:

xlib: connection to :0.0 refused by server
xlib: no protocol specified
kwrite: cannot connect to x server :0.0

I'm lost.. :???:

---

### Post by macgip on 2005-10-11
ok you said wine or the other program, but where could i download these programs??:)

---

### Post by Protostar on 2005-10-12
Alright, I got wine but for some reason the terminal won't let me switch to the Program Files folder. It keeps saying it can't find it when it's right there! Very confusing.:???:

---

