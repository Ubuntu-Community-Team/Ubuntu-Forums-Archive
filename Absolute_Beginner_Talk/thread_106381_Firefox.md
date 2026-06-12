---
title: "Firefox"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Ted D. on 2005-12-20
I have lost the ability to Launch FF. Tried to install Ver 1.5 with no luck so i removed it. tried to go back to the package version. tried reinstalling but can't launch it from icons or application menu. lost the link or have the incorrect link  to menu icon. how do i correct this? i the see the firefox directory and all the firefox files, i think. trouble is i don't know the right file to point to - being new to linux.
assistance please. and thanks in advance.
Ted D.

---

### Post by bscbrit on 2005-12-20
One possible cause is that a part of firefox is still running.

On a command line try the following

killall firefox-bin

You might also try it with sudo e.g.

sudo killall firefox-bin

Firefox sometimes does not shutdown cleanly.  It leaves a  lock of some description which prevents another copy of firefox from starting.

---

### Post by bscbrit on 2005-12-20
Having given this a bit more thought - it is unlikely that you still have a part of firefox running but not impossible.  But do not expect too much from my previous advice.

How did you install version 1.5?

It may have changed the structure of the data stored below .mozilla in your home directory (This is a guess - not a statement of fact).

What do you see when you try to install the original package.  Are you using synaptic or apt-get?  Are there any error messages?

---

### Post by Ted D. on 2005-12-20
Hi,
I tried to install FF 1.5 as per instructions in Wiki. thought i had followed it to the letter but apparently i didn't. then i followed the instructions to remove it, again, as per the wiki inst.
i tried to install original pkg via synaptic. everything seem to ok (no error messages that i can recall)
The path from the application menu must incorrect.
Ted D.

---

### Post by jrib on 2005-12-20
see if firefox will run with the absolute path

```
/usr/lib/mozilla-firefox/firefox
```

If it does, post back here and we'll see if we can get to the source of the problem.

---

### Post by Ted D. on 2005-12-20
tried all of the above but no luck

---

### Post by ecto on 2005-12-20
I used to have the same problem. The thing is when you get firefox from the official mozilla site you dont exactly compile it more or less its already compiled and ready to be used (unless you used the CVS). What I had to do was to, move that directory into a directory called /opt and symlink it. Afterward even, though i symlinked it the icon on my desktop (as well as my panel launcher) kept on launching the old version. The only thing i could do was make a whole new icon and launcher. Im not sure if you compiled it or not but try making a symlink. Sorry i cant be more specific but im not as experienced as many others but I had to put my two cents in

---

### Post by Ted D. on 2005-12-20
have not tried ecto's suggestion but i will.  i thought i would see what would happen if i installed the mozilla browser. the same thing happened. no browser. this is very baffling.

---

### Post by jrib on 2005-12-20
see what the following say:

```

apt-cache policy firefox | grep Installed
dpkg -L firefox | grep bin

```

---

### Post by Ted D. on 2005-12-21
[QUOTE=_jason]see what the following say:

```

apt-cache policy firefox | grep Installed
dpkg -L firefox | grep bin

```[/QUOTE]
The folowing was the resonse to the input
apt-cache policy firefox | grep Installed
Installed: 1.0.7-0ubuntu20

dpkg -L firefox | grep bin
/usr/lib/mozilla-firefox/libgtkxtbin.so
/usr/lib/mozilla-firefox/res/html/gopher-binary.gif
/usr/lib/mozilla-firefox/firefox-bin
/usr/sbin
/usr/sbin/update-mozilla-firefox-chrome
/usr/bin
/usr/bin/firefox
/usr/bin/mozilla-firefox

Hope this can lead us somewhere. As a newcomer to linux it doesn't mean much to me at the moment except that Firefox is there.

---

### Post by Ted D. on 2005-12-22
Decided after trying various appraoches, to reinstall Ubuntu. Works now but there has to be a simpler way.

---

