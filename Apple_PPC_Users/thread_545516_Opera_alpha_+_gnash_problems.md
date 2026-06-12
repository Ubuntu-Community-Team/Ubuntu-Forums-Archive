---
title: "Opera alpha + gnash problems"
date: 2007-09-07
forum: Apple PPC Users
---

### Post by stmiller on 2007-09-07
I'm trying the new Opera 9.5 alpha in PPC from [here]("http://my.opera.com/desktopteam/blog/2007/09/04/go-and-get-opera-9-5-alpha-3"), and Gnash 0.8.1 does not seem to work. Gnash does not even start, it seems. (Gnash *does* work fine in Firefox.) 
Opera recognizes gnash as a plugin, though when trying a flash page I get this in the terminal of opera's output:

```

opera: Plug-in 9910 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plugins.

```

Anyone have any ideas? Or maybe it's just an Opera alpha release sort of issue with plugins?

---

### Post by jnorthr on 2007-09-07
my version of opera is 9.23 no gnash though. I have 11 tabs open and it flies compared to firefox.

---

### Post by trash on 2007-09-18
> **stmiller said:**
> I'm trying the new Opera 9.5 alpha in PPC from [here]("http://my.opera.com/desktopteam/blog/2007/09/04/go-and-get-opera-9-5-alpha-3"), and Gnash 0.8.1 does not seem to work. Gnash does not even start, it seems. (Gnash *does* work fine in Firefox.) 
Opera recognizes gnash as a plugin, though when trying a flash page I get this in the terminal of opera's output:

```

opera: Plug-in 9910 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plugins.

```

Anyone have any ideas? Or maybe it's just an Opera alpha release sort of issue with plugins?

9.22 here and it doesn't even recognize the plugin! How did you do it?

---

### Post by kakao on 2007-10-03
> **stmiller said:**
> 
```

opera: Plug-in 9910 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plugins.

```

confirmed with opera 9.23. When I type
```
about:plugins
```
(or opera:..) I get
```
Shockwave Flashapplication/x-shockwave-flash	swf
/usr/lib/opera/plugins/libgnashplugin.so
```
And when opening some flash page like youtube.com I also get
```
opera: Plug-in 13087 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.

```
It even shows the familiar "Click to activate and control" stuff in the status bar but wouldn't do it when I click it. Bummer! I hope someone can convince it to work with opera. It does work with firefox and opera worked with flashplugin-nonfree like a charm... When I find the time I might file a bug on launchpad since it seams to be gnash (it is alpha after all). A pitty opera is not open source an hence not supported by Ubuntu...

@trash:
As stated by [kayrune]("http://ubuntuforums.org/showthread.php?t=551463") I made a symlink by
```
$ cd /usr/lib/opera/plugins/
$ sudo ln /usr/lib/gnash/libgnashplugin.so
```
after I installed the gnash plugin package with
```
$ sudo aptitude install mozilla-plugin-gnash 
```
Good luck!

---

