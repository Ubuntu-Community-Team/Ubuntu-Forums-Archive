---
title: "Firefox and Help trouble"
date: 2005-05-21
forum: Absolute Beginner Talk
---

### Post by agger on 2005-05-21
I tried to download some extensions in Firefox, and FF told me to upgrade to the most recent version (1.04) to do that.

That's fine and I installed my plugins, but now the Help facility doesn't work - it terminates whenever I try to start it.

Starting yelp from at terminal (yelp is the actual Help program) I get the following:
--------

yelp: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory

------

So my upgrade of Firefox seems to have broken some GTK/mozilla libraries - anybody knows how to fix this.

Thanks in advance,
Carsten Agger

UPDATE: I tried to install the Mozilla browser instead of Firefox since installing Mozilla might take this library with it - seems it did not, however.

---

### Post by poofyhairguy on 2005-05-21
[QUOTE=agger]I tried to download some extensions in Firefox, and FF told me to upgrade to the most recent version (1.04) to do that.
[/QUOTE]

What Firefox are you using? The backport Firefox works well for me.

Look at this:

[http://ubuntuforums.org/showthread.php?t=34099](http://ubuntuforums.org/showthread.php?t=34099)

---

### Post by agger on 2005-05-22
[QUOTE=poofyhairguy]What Firefox are you using? The backport Firefox works well for me.

Look at this:

[http://ubuntuforums.org/showthread.php?t=34099](http://ubuntuforums.org/showthread.php?t=34099)[/QUOTE]


Thanks - but i still don't really know how to solve the yelp problem.

I'm running the most recent Firefox from Mozilla (as referred to in the post above) and installed it on top of Hoary's 1.02 Firefox.
Then, i was allowed to install extensions, but yelp still doesn't work; would it be safe to uninstall and reinstall it from the repositories? Because in that case it ought to get the dependencies right.

Thanks
Carsten

---

### Post by zenlord on 2005-05-22
[QUOTE=agger]Thanks - but i still don't really know how to solve the yelp problem.

I'm running the most recent Firefox from Mozilla (as referred to in the post above) and installed it on top of Hoary's 1.02 Firefox.
Then, i was allowed to install extensions, but yelp still doesn't work; would it be safe to uninstall and reinstall it from the repositories? Because in that case it ought to get the dependencies right.

Thanks
Carsten[/QUOTE]
 I have  done the same, and my help is broken too...

Don't know hw to fix it tho...

Zl.

---

### Post by Moses Palmér on 2005-05-26
I have the same problem. First, I tried simply downloading Mozilla again using Synaptic Package Manager, and this solved the yelp problem, but I was unable to download any extensions for Mozilla.

Once again I downloaded the newest version of Mozilla, and then used Synaptic Package Manager to just download the Ubuntu version of mozilla and then unpack libgtkembedmoz.so to /usr/lib/mozilla-firefox. This time yelp actually started, but complained: I/O warning : failed to load external entity "/home/moses/.gnome2/yelp-bookmarks.xbel". After that the program crashed.

---

### Post by Whistler on 2005-05-27
I'm not sure if Debian .deb files will work, but you can probably try that.

I know Debian's Firefox build is different from the official build

---

### Post by ChinaCatJones on 2005-05-29
I had the the same issue.  I order to resolve it do the following.

1.  Launch the browser.
2. Type "about:config" in the address bar and hit enter.
3. Look for the entry there marked "extensions.lastAppVersion" and change the value to 1.0.4
4. Restart your browser and you should be good to go.

Chris

---

