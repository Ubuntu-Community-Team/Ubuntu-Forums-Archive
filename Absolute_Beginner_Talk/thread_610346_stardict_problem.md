---
title: "stardict problem"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-11-11
I have installed Ubuntu 7.10 Gutsy and then tried to use stardict as I did in Feisty. But having installed the program from repositories when I opened it up, the floating definition window seemed to be weirdly behaving. Whenever I double-click a word and the definition pops up, it suddenly flees towards the upper left corner of the desktop and disappears.

I tried to remove and install a newer version [http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb](http://downloads.sourceforge.net/stardict/stardict_3.0.1-1_i386.deb)

But when I try to install it, it gives the error "failed to install package..." [IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=49950&stc=1&d=1194837376[/IMG]

I tried to install that package again and again, but in didn't succeed.

I now plan to install an older version. Could you help me, please?

---

### Post by SpiritIsReality on 2007-11-11
howdy
this page talks about apt errors.
[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)
what you might try is 
sudo updatedb
slocate stardictoldpackagename
and see if it shows up anywhere. If it does you could try
sudo aptitude remove --purge stardictoldpackagename
then try to install. If it doesn't work then you could run
ls /var/lib/dpkg/info | grep stardictoldpackagename
and then remove any of them.
and try to install again. YouAreInTheSaddle
trails

---

### Post by sauravbhaumik on 2007-11-11
> **SpiritIsReality said:**
> ....
sudo aptitude remove --purge stardictoldpackagename
then try to install.... 

Thank you very much! It worked.

But please explain what is the significance of the term "stardictoldpackagename". How does the computer understand that it means "the old package names of stardict"?

---

### Post by SpiritIsReality on 2007-11-11
howdy
ok you're right. I should have said
sudo aptitude remove --purge "the old package names of stardict"
that's two - in from of the word purge.
You're kidding me right? 
sudo aptitude remove --purge stardict_3.0.1-1_i386.deb
only replace the 3.0.1-1_i386.deb with the old name...
You just ran the sudo aptitude remove --purge "the old package names of stardict" 
and then you could install?
trails

---

### Post by sauravbhaumik on 2007-11-11
> **SpiritIsReality said:**
> howdy
ok you're right. I should have said
sudo aptitude remove --purge "the old package names of stardict"

Of course I didn't hint that you should.

> 
that's two - in from of the word purge.
You're kidding me right? 
sudo aptitude remove --purge stardict_3.0.1-1_i386.deb
only replace the 3.0.1-1_i386.deb with the old name...
You just ran the sudo aptitude remove --purge "the old package names of stardict" 
and then you could install?
trails

No I was a bit serious indeed.
I meant to ask how the computer understand the suffix "oldpackagename" . That is, whether it is a standard suffix (ie, whether I can use terms like "vlcoldpackagename", "xmmsoldpackagename" etc) or else this is for stardict only.

---

### Post by SpiritIsReality on 2007-11-12
howdy
all is well, except my spelling needs work. haha!
I do not know how a command
sudo aptitude remove --purge stardictoldpackagename
would work, unless aptitude recognized the word stardict
and ignored the rest of the line.
at a terminal you can type
sudo aptitude
and you can read about it here [https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)
if you type ctrl-T you can use the menu at the top of the window, with the mouse.
if you run the aptitude without the sudo, then there is no worries of messing up, because you don't have root privileges.So
aptitude
at the command line and then there is a help manual which I've tried to stumble thru a couple of times. just like trying to use vi or emacs, haha!
you type q to quit.
[http://people.debian.org/~dburrows/aptitude-doc/en/index.html](http://people.debian.org/~dburrows/aptitude-doc/en/index.html)
trails
[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+aptitude&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+aptitude&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=aptitude+manual&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=aptitude+manual&btnG=Google+Search&meta=)
links
[http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
[http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
[http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)

---

