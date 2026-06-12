---
title: "Flash Help Ubuntu 7.10"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2008-01-30
I installed flash, and still it wont work any ideas, still says i need to install it? Thanks

---

### Post by ycason on 2008-01-30
This happened to my roommate because he installed both flash and gnash.  Firefox got confused and didn't know what to do.  Solution was to delete the .mozilla folder in the home directory (it's a hidden folder).  Uninstall gnash, flashplugin-nonfree and all dependencies.  Then the next time you start firefox go to youtube or some other site with flash and install flash again when it asks.

Hope this helps you,
:popcorn:

---

### Post by jaytek13 on 2008-01-30
Did you install it in firefox? Like, when you go to a page that uses flash, firefox says it requires plugins, and allows you to install it from there? There is a known bug with doing this.

If this is what you did, go to a terminal and type

sudo apt-get remove flashplugin-nonfree

Then, instead of using the web browser to install it, type

sudo apt-get install flashplugin-nonfree


and then it should work...

---

### Post by jan quark on 2008-01-30
rhis method worked for me
namely installing it from the official adobe page
[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by oedha on 2008-01-30
or dowload from
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
and install it......

~E~

---

### Post by Motorhead Kaze on 2008-01-31
I second that.  I did all the various methods of installing, removing, reinstalling from here, there, other there and all I needed to do was get rid of gnash.

There are oodles of flashplayer threads in the forums now.  I read several VERY long threads and it was this one simple thread that fixed me up.   Thanks guys.

---

