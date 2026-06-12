---
title: "symlink problem"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by jipke on 2006-04-02
I've downloaded swiftfox (getswiftfox.com) and copied it into /opt/.
When I want to start the program from terminal I have to create a symlink in /usr/bin/ right?

So entered the following code:
```
cd /usr/bin/

sudo ln -s /opt/swiftfox/firefox /usr/bin/swiftfox
```

Unfortunately entering swiftfox in a terminal will give the following error:
```
jipke@ubuntu:~$ swiftfox

run-mozilla.sh: Cannot execute /opt/swiftfox/swiftfox-bin.
```

What is it i'm doing wrong? Thanks in advance!

---

### Post by jipke on 2006-04-02
[QUOTE=jipke]run-mozilla.sh: Cannot execute /opt/swiftfox/swiftfox-bin.[/QUOTE]

I've misread the line, it's says swiftfox-bin (instead of firefox-bin), which indeed doesn't exist. Why does it searches for swiftfox-bin, because I named the symlink swiftfox? Must a symlink have the same name as the executable?
 
I want to use swiftfox next to firefox, the executables are the same (firefox) and both are installed in /opt/ (/opt/firefox and /opt/swiftfox). How do I make the symlink swiftfox for /opt/swiftfox/firefox that doesn't override the firefox symlink in /usr/bin? 

Apperantly 

```
sudo ln -s /opt/swiftfox/firefox /usr/bin/swiftfox
```

doesn't work.

Thanks.

---

### Post by Stirling on 2006-04-03
There are two ways to fix this.  The first way is to rename firefox and firefox-bin in the swiftfox directory to swiftfox and swiftfox-bin.  Then symlink to the renamed swiftfox file.  The second way to fix this is to use a startup script in the /usr/bin directory instead of a symlink.

```
#!/bin/sh

export MOZILLA_FIVE_HOME=/opt/swiftfox
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$MOZILLA_FIVE_HOME

# get URL to load
url=$1; [ -z $url ] && url=about:blank

# try xremote first
$MOZILLA_FIVE_HOME/mozilla-xremote-client openURL\($url,new-tab\) && exit 0

# if xremote failed, then launch the browser
exec $MOZILLA_FIVE_HOME/firefox $url
```

This would obtain the same results.  The first method would be the better method though in my opinion.  I really don't understand why the symlink tries to call swiftfox-bin though when the symlink just points to the firefox script.  The ultimate solution will be to have Swiftfox ship with the files already renamed I guess.

---

### Post by nu11point3r on 2006-12-09
Hi I used that script and it made it work :) 

BUT I installed swiftfox only because of flash and this crap is closing every time I try to load a flash page.

I'm on a AMD64 with ubuntu64 edgy .. anyone else having the same problem? ](*,)

---

### Post by slicker on 2006-12-09
> **nu11point3r said:**
> Hi I used that script and it made it work :) 

BUT I installed swiftfox only because of flash and this crap is closing every time I try to load a flash page.

I'm on a AMD64 with ubuntu64 edgy .. anyone else having the same problem? ](*,)

Get rid of Swiftfox. It isnt free software. Go to the [64bit section]("http://ubuntuforums.org/forumdisplay.php?f=134") of the forum and read the [sticky thread]("http://ubuntuforums.org/showthread.php?t=191205") It has howto's for all the applications that give 64bit users problems. The title of the Sticky says Dapper, but they all work in Edgy.

---

