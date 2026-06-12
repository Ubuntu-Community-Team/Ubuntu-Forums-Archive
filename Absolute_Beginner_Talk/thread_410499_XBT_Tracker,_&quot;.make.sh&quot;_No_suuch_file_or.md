---
title: "XBT Tracker, &quot;./make.sh&quot; No suuch file or directory"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-04-15
Hi, I am trying to install the XBT tracker, And i am having a few problems... I think what i need to do is compile the files, but it dose not seem to be working, i am fallow the instructions on this page [http://xbtt.sourceforge.net/tracker/ ]("http://xbtt.sourceforge.net/tracker/") and i am up to where it asks you to type in "./make.sh" and i just get a message back saying "
-bash: ./make.sh: No such file or director

Please help :)

---

### Post by jfinkels on 2007-04-16
> **LoicNyssen said:**
> Hi, I am trying to install the XBT tracker, And i am having a few problems... I think what i need to do is compile the files, but it dose not seem to be working, i am fallow the instructions on this page [http://xbtt.sourceforge.net/tracker/ ]("http://xbtt.sourceforge.net/tracker/") and i am up to where it asks you to type in "./make.sh" and i just get a message back saying "
-bash: ./make.sh: No such file or director

Please help :)
The reason you get that message is...well, the file doesn't exist!

You'll need to checkout a copy of the code, I think, from SVN. If you need help doing this, please post back here and we'll see what we can do :)

In short, install SVN if it is not already, then
```

svn co https://xbtt.svn.sourceforge.net/svnroot/xbtt/trunk/xbt/Tracker xbtt

```
then ```
cd xbtt
``` then ```
./make.sh
```

But it seems like this is a Windows program...there are many excellent bittorrent clients around for Linux...try Deluge, Transmission, BitTornado, etc.

---

### Post by LoicNyssen on 2007-04-18
Yeah, But im not looking for a client... looking for a tracker... 

and the only one anyone can suggest to me is xbt, Anyone know of any others?

---

### Post by jfinkels on 2007-04-19
> **LoicNyssen said:**
> Yeah, But im not looking for a client... looking for a tracker... 

and the only one anyone can suggest to me is xbt, Anyone know of any others?

Oh, I see...well, I don't really know that much about torrents, but this site ([http://www.bittorrentportal.net/](http://www.bittorrentportal.net/)) lists two other trackers you might want to give a try if that one doesn't work out for you :D Did you get the make script working?

---

### Post by Hakker on 2007-11-17
well I do get it but somehow compiling it is a whole different story... I don't think it's written to handle ubuntu which kinda suck since the tracker itself is good.

whenever I try ./make.sh I get prompted with the following:

./make.sh: line 2: mysql_config: command not found
./make.sh: line 2: g++: command not found

---

### Post by u1oo on 2008-04-29
Reading the instructions on the site that you linked to might help.

Pay special attention to the "Installing under Linux" section that begins "The following commands can be used to install the dependencies on Debian."

You are missing some dependencies. Install them first, then install XBT.

---

