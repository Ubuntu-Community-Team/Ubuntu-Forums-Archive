---
title: "XMMS dependencies"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-03-26
I need a mp3 player. I am not online at home, so i guess i have to use the windows box at the library to get XMMS from packages.ubuntu.com then take it home on CD. But doing it that way, i'm not warned what dependencies i need. What's the best/simplest way for me to sort this out?

---

### Post by Xian on 2006-03-26
The req'd deps are listed on the [XMMS package](http://packages.ubuntu.com/breezy/sound/xmms) Ubuntu page.
Or right-click on 'XMMS' in Synaptic goto Properties > Dependencies

You can also issue this command:
$ sudo apt-cache depends xmms

Edit: If you want the recursive dependencies then do this:
$ sudo apt-get install apt-rdepends
$ sudo apt-rdepends xmms

---

### Post by gr0kzer0 on 2006-03-27
I'm not online at home. I'd be using a windows-running pc at the library to do the download, so apt-get wont work for me... will it? Anyway, i went to the packages site and the dependencies lists for xmms and gnomp3 kinda intimidated me. I was thinking, would it be simpler to just get the files needed to make rythmbox play mp3? What are those files exactly?

---

