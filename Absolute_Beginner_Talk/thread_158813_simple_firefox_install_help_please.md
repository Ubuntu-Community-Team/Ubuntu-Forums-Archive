---
title: "simple firefox install help please"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-04-11
These are early days with Ubuntu for me so excuse the low level of knowledge.
I'm trying to follow the instructions in wiki
([https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29))
 to upgrade to Firefox 1.5 to hopefully get speedier browser.  I've downloaded the tar file to desktop and now instructions say:

Install it to /opt/firefox:

 # extract tar into /opt (you should make sure /opt already exists)
 sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
 # remove the package if you no longer require it
 rm firefox-1.5.0.1.tar.gz

but I get the following:

tar: firefox-1.5.0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

So how do I proceed?  I think I need to tell it the file is on the desktop or place the tar in another file.  Thanks.

---

### Post by nalmeth on 2006-04-11
> simple firefox install help please
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)
See if automatix will work for you. You may find other valuable goodies in this excellent app.
Only reason it shouldn't work is if you are a amd64/ppc user.
If you installed the regular breezy, then this should work.

---

### Post by aysiu on 2006-04-11
You probably aren't in the same directory as the .tar.gz.
The terminal assumes you're in your /home/username directory. People typically download files to /home/username/Desktop.

By the way, [this script](http://www.psychocats.net/ubuntu/firefox) automates the Wiki instructions.

**Edit**: What nalmeth's suggests is a wonderful tool if you want to install not only Firefox but a ton of other popular applications and multimedia codecs. The script I'm linking to is for Firefox only and is a little less intrusive (Automatix installs a program called Automatix, and it changes your sources.list).

---

### Post by flyingsolo on 2006-04-11
Well, I already had Automatix but haven't used it much and yes it installs Firefox 1.5 very easily but doesn't keep the bookmarks I had intact...not too much of a problem since most of them were imported from Firefox on WinXP.
Still, my first impressions are that Firefox is much slower on Ubuntu than WinXP.

---

### Post by nalmeth on 2006-04-11
I have heard mixed stories about this, you shouldn't be lead too easily either way.
I think breezy firefox startup vs windows firefox startup is slower by about half a second in so called "controlled" conditions.
This is not considering prelinking firefox for quick startup, also all the speed boosts in Dapper.

---

### Post by flyingsolo on 2006-04-11
The speed problem I see isn't so much at startup but just simple browsing page to page--very slow loading of new pages under Ubuntu whereas Win was nearly instantaneous (router, DSL access)

---

### Post by aysiu on 2006-04-11
I use Firefox regularly on about (physically) four computers (essentially five, since one is a dual boot), and I can honestly say it's no faster or slower on OS X, Windows XP, Windows 2000, or Ubuntu Breezy.

---

### Post by Stranger678 on 2006-04-11
I have four comps and ubuntu is my third OS, Firefox acts the same in all of them, maybe a hair faster in my primary windows box, but it has three times the RAM, so I let that one slide.

---

### Post by flyingsolo on 2006-04-11
Because of the last 2 posts above, I'm still trying to figure what needs to be tweaked to fix my perception of speed difference.  I should have said I'm using Firefox 1.5 under Win XP and Ub.B.B on the same machine (dual boot) so they both have same hardware setup.

---

### Post by aysiu on 2006-04-11
I'm not sure what tweaks you'd need, as I haven't had to tweak it at all.

Firefox does start a bit more slowly in Ubuntu, but you said in your earlier post that it wasn't about starting times but loading from page to page.

---

