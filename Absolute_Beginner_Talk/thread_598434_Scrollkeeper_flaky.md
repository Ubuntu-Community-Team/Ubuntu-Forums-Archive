---
title: "Scrollkeeper flaky"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by sloe on 2007-10-31
Hi all,  I'm fairly new to the Ubuntu distro, but I am not a newbie by any means.  Being as how this is my first real experience with a Linux GUI, though,  I thought I would toss the question in here since it appears to be Gnome related.

Anyhow, I got Gusty installed as a VM to play with it and evaluate for replacing XP on my Dell C840.  So far, I'm liking it, but every time I do something with the Synaptic Package Manager, the output log shows a LOT of these errors:

```
/var/lib/scrollkeeper/es/scrollkeeper_cl.xml:792: parser error : Extra content at the end of the document
ntentsList>
^

```

It throws out so many errors that I can't read the log in the supplied terminal window.  

My question is this:  Is this normal behavior, or do I have a broken file somewhere that I can fix?

thanks!
-sloe

---

### Post by sloe on 2007-11-01
bump....

Ok, let me try this again.  Does anyone else see this error, or is it just me?

---

### Post by montezumax on 2007-11-02
Yep, same issue here.  I just finished installing Gutsy and then tried to uninstall the Ekiga software package and I started seeing scrollkeeper errors.  Also, I opened a console and ran top and noticed that scrollkeeper-up was using 80%+ of the CPU.

I googled this item and several people mention it but I haven't seen any workarounds or solutions.

---

### Post by feigenbaum on 2007-11-02
I've had the same problem and solved it as follows:

I opened a console and became root to have the required permissions...
```

sudo su

```
(You have to enter your accounts password)

..., then I moved the broken file in my roots home directory.
```

mv /var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml /root

```
(It is in your case another directory but I assume you can adapt it to your needs)

After that I build a new scrollkeeper_extended_cl.xml by:
```

dpkg-reconfigure scrollkeeper

```

It took a while and after that I got the errors no more.

I hope I could help you with that.

---

### Post by mverrilli on 2007-12-06
I've gotten this error on a few package installs... do I need to go back and figure out which installs I did that showed this error and reinstall them?  Will I have trouble one day if I don't?

What problems does this error really cause?

Thanks

---

### Post by forestpixie on 2007-12-06
I had the same barrel of laughs - used the fix above and it went away and haven't had a problem since then with it - 

no idea what it's all about to be honest - didn't find much when I started searching for the error

---

### Post by Hendrixski on 2007-12-11
yep, had the same error
that dpkg-reconfigure command is a lifesaver, eh?

---

### Post by piratesmack on 2008-03-16
Thanks, this helped me out a lot. 

I've been getting this error for who knows how long, but I've just been ignoring it

I can delete the old scrollkeeper_extended_cl.xml right? you just moved it to your root directory for backup purposes right?

---

### Post by CPesyna on 2008-04-25
This didn't quite do it for me. I did everything up to 

$ sudo dpkg-reconfigure scrollkeeper

which didn't solve the problem. Instead, I tried

$ sudo scrollkeeper-rebuilddb

which did the trick.

---

### Post by neurostu on 2008-05-29
So I got the same error, I ran both:
dpkg-reconfigure scrollkeeper
&
scrollkeeper-rebiulddb and I get the same weird error.
```

root@stockton-mini:/home/slayton# dpkg-reconfigure scrollkeeper
Rebuilding the database. This may take some time.
///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity '&#914;&#959;&#942;&#952;&#949;&#953;&#945;' not defined
                  <para><guimenuitem>&#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;&&#914;&#959;&#942;&#952;&#949;&#953;&#945;;</gui
                                                                           ^


root@stockton-mini:/home/slayton# scrollkeeper-rebuilddb 
scrollkeeper-update: warning: /usr/share/omf/workspace-switcher/workspace-switcher-de.omf overrides /usr/share/omf/gnome-panel/workspace-switcher-de.omf
scrollkeeper-update: warning: /usr/share/omf/window-list/window-list-de.omf overrides /usr/share/omf/gnome-panel/window-list-de.omf
///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity '&#914;&#959;&#942;&#952;&#949;&#953;&#945;' not defined

```

---

### Post by neurostu on 2008-05-29
For some reason it was a problem with my blackjack.xml help file. I ran:
sudo apt-get remove gnome-games gnome-games-data 

then 
sudo scrollkeeper-rebuilddb worked!

---

### Post by austin1030 on 2008-05-30
> **neurostu said:**
> For some reason it was a problem with my blackjack.xml help file. I ran:
sudo apt-get remove gnome-games gnome-games-data 

then 
sudo scrollkeeper-rebuilddb worked!

neurostu, doesn't that get rip off games? try this.

I've search to fix this problem myself since Ubuntu hardy came out. 

Today, I found it. 

Go download scrollkeeper package from below link and install. 
This will eliminate any problem you might have with scrollkeeper.

[http://debian.tula.net/ubuntu/pool/main/s/scrollkeeper/]("http://debian.tula.net/ubuntu/pool/main/s/scrollkeeper/")

Hope this save from a nightmare...: )

Austin

---

### Post by neurostu on 2008-05-30
Yes that did uninstall the games, I just ran:
```

sudo apt-get install gnome-games gnome-games-data

```
and it reinstalled them, everything is working great now.

---

