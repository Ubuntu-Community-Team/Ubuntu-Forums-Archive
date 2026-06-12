---
title: "[SOLVED] disappeared - wiki - &amp;amp;amp;quot;how to install anything&amp;amp;amp;quot;"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-12-08
I had used a wiki page someone wrote about how to install anything in Ubuntu. It was awesome, but now, I cannot find it. 

I'm trying to install Bible Desktop. My java is right, but it won't work. My searches yield several threads where other people aren't able to get this installed. I had it installed before, so I know it works in Ubuntu.

If anybody might have a link or suggestion, I would appreciate the help.

---

### Post by arochester on 2007-12-08
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by aysiu on 2007-12-08
I didn't know that was a Wiki page. I thought it was just a page. You can also find it here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

For Bible Desktop, maybe try pasting these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://www.crosswire.org/ftpmirror/pub/jsword/release/bibledesktop-1.0.7-bin.tar.gz
tar -xvzf bibledesktop-1.0.7-bin.tar.gz
cd jsword-1.0.7/
chmod +x BibleDesktop.sh
./BibleDesktop.sh
```

---

### Post by Papa-san on 2007-12-08
Thank you!

---

### Post by Papa-san on 2007-12-08
I guess I'm not understanding where things are supposed to go.

aysiu,
I tried the commands you gave me, but I keep getting errors.
I got this OK, I guess:```
john@john-laptop:~$ wget -c http://www.crosswire.org/ftpmirror/pub/jsword/release/bibledesktop-1.0.7-bin.tar.gz
--12:56:25--  http://www.crosswire.org/ftpmirror/pub/jsword/release/bibledesktop-1.0.7-bin.tar.gz
           => `bibledesktop-1.0.7-bin.tar.gz'
Resolving www.crosswire.org... 64.140.154.250
Connecting to www.crosswire.org|64.140.154.250|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.
john@john-laptop:~$
```
Then:```
john@john-laptop:~$ tar -xvzf bibledesktop-1.0.7-bin.tar.gz.tgz
tar: bibledesktop-1.0.7-bin.tar.gz.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@john-laptop:~$

```
then```
ohn@john-laptop:~$ cd jsword-1.0.7/
bash: cd: jsword-1.0.7/: No such file or directory
john@john-laptop:~$

``` ```
john@john-laptop:~$ chmod +x BibleDesktop.sh
chmod: cannot access `BibleDesktop.sh': No such file or directory
john@john-laptop:~$

``````
john@john-laptop:~$ ./BibleDesktop.sh
bash: ./BibleDesktop.sh: No such file or directory
john@john-laptop:~$

``` Yet again, Papa-san hasn't quite got it down... I was going to do the how-to, but I've never found your suggestions to not go flawlessly... Any thoughts/suggestions?

---

### Post by aysiu on 2007-12-08
Sorry. There was an extra *tgz* in the command I gave you. I've edited my original post to correct that problem.

---

### Post by Papa-san on 2007-12-08
AWESOME!  (I'm so excited!) LOL Yes, it works, and I'm downloading my other bibles... Thank you!

Now, will I need to build a shortcut to be able to open it next time or something? Or will a command prompt work better?

---

