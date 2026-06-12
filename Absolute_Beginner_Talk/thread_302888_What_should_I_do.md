---
title: "What should I do?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Axis on 2006-11-19
Well I am completely new to Linux entirely. I was wondering if everyone had to suggest 5 programs to install that don't come standardly installed and maybe some articles to read; what would they be?

Thanks
Axis

---

### Post by bulldog on 2006-11-19
Well install what **you** need,not what anyone else needs.

And there are lots of information sites on the net,just search for it.

---

### Post by turbojugend_gr on 2006-11-19
This should answer most of your questions, and create some new as well, and answer them too.. ;) It's the official Desktop Guide, I suggest bookmarking it.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

---

### Post by Axis on 2006-11-19
Bulldog I just meant programs that everyone find useful, there are generally programs that most people agreed should be with windows so I assumed the thing would be the same for Ubuntu.

Thank you turbo I will be sure to read that.

---

### Post by LLRNR on 2006-11-19
Just a quick tip in case you're a nostalgic Paint fan like me... ;) Try Kolourpaint, it's awesome !!

```
sudo aptitude install kolourpaint
```

Cheers,

LLRNR

---

### Post by turbojugend_gr on 2006-11-19
Just in case you still have some tasks that you don't have an app that satisfies you for, here's what I use:

iTunes (indexing-lyrics-album covers-library-visualizations-ipod integration-podcasts and even more like artist wikipedia article, radio and others) like music player --> Listen (it's in the repos, actually it's the previous version, so if you need the latest version there's a deb in their site)

torrents (&#956;torrent like app, with even more capabilites, social ones) torrent swapper (I have a how-to [here]("http://www.ubuntuforums.org/showthread.php?t=278093"))

videos --> mplayer (it's in the repos)

web browsing --> firefox, photoshop like (again better) --> gimp, msn/aim/icq/jabber and stuff -->gaim, office --> openofice // you have those. 

Proggramming (IDE) --> anjuta IDE (it's in the repos too)

...Oh forget it they are too many ;). Just say what you need and we 'll hit back with an app.

---

### Post by ReaderRat on 2006-11-19
I suggest these to many newbies. They are done by a moderator named **[COLOR="Red"]aysiu[/COLOR]** , and they will save you a lot of time and frustration:

  [**[color=blue]Psychocats Tutorials[/color]**](http://www.psychocats.net/ubuntu/index)

---

### Post by Axis on 2006-11-19
Well possibly a free antivirus? I am big on security and tools that will optimize my computers performance. 

Also I seem to be having problems installing a few simple games I downloaded. I noticed it's nothing like windows when it comes to that stuff.

---

### Post by turbojugend_gr on 2006-11-20
As for the Anti-virus, if you are not a cluster administrator, or  massively forwarding mails, or anything that would involve windoz security, then you won't need one for sure (if what's you mean is to scan your Linux system for viruses). Linux is built in such a way that viruses have a very hard time in affecting it (in my experience, it's an _extremely_ seldom event), also not being popular takes the target of it's back too. If you add the open source factor, which means weeknesses are dynamically solved, you will receive a vast amount of security updates over time, it would be silly to care about an anti-virus. It would be like using a mousetrap to protect a safe -> the ones that the trap catches can't open the safe and actually they don't care about it after all, while if one would be able to open the safe the trap wouldn't bother him at all. Silly example I know, but I couldn't think of a better one ;).

Now Linux has 3 differrent ways of installing software in general, here is a quick synopsis:

1. FROM SOURCE: You obtain a tarball (files usually ending likw *.tar.gz or *.tbz2) which contains the source code of the app, you extract the contents somewhere, you entere this folder via terminal, and issue the following commands 1."./configure" 2."make 3."sudo make install" what those commands do exactly it's not the time to explain. Anyway the most likely thing is that you will miss some libraries that are needed to compile the tarball, so it is not an easy ride. Though if you get this working then the app is qorking like a grace and usually much better than when it comes in other forms (executables,binaries,packages etc.)

2. FROM A PACKAGE: Usual types of packages are *.deb and *.rpm, the first one is for debian base distros, while rpm is for others like SuSE, Red Hat/Fedora and others. Ubuntu being based on Debian, uses debs. This one is a pre-compiled package, so it is easier to install, and informs you if you need a library too. You install via debs, via terminal by issuing "sudo dpkg -i PACKAGE_NAME (note not package fiulename, just it's name), or better by double clicking the package in nautilus (you need gdebi installer for this one-it's in the repo's). Actually most repo's contain deb packages, so when you install via synaptic you are actually installing debs most of the times,btw the repository is used so you will get automaticaly updated)

3. Via binaries, this ones are like the windows installers, you just start 'em (if they have a gui double clikcing 'em will do it, but if they are command line installers, you need to type sth like "./BINARY_FILE_NAME.bin" and simply follow the instructions.

If you ask me, the easiest way to install is via deb's, you just double-click 'em, the better results you get when compiling your self, and binaries are mostly used from closed source projects, though open source projects also use 'em some times cause it is not Distro specific.

Finally if you are not familiar yet, there's an appplication application in your System/Admin menu called Syanptic, this one is a life savior. You open it, you make a search for what you need (name, name and description etc) you select what you wish to install, it downloads the deb for you through the repo's and installs it for you. It is a front-end for the command line tool apt-get.

I would **strongly** suggest to go **thourgh** the guide I suggested in post #3, it has many of this things categorized, follow it and you will get familiar with most common things in ubuntu. If you are done take a look at [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") one too, it the ubuntuguide.org.

I hope I helped you, best regards,TJ.

---

### Post by housam on 2006-11-20
You can go for [www.getautomatix.com](www.getautomatix.com) and install automatix2 .it is an GUI installing program . you will find many interresting programs to install through it.

---

### Post by HareBall on 2006-11-20
> **LLRNR said:**
> Just a quick tip in case you're a nostalgic Paint fan like me... ;) Try Kolourpaint, it's awesome !!

```
sudo aptitude install kouloupaint
```

Cheers,

LLRNR

I believe this should have been:
```
sudo aptitude install kolourpaint
```
There was a typo in the name.

---

### Post by ladoga on 2006-11-20
> **Axis said:**
> Well I am completely new to Linux entirely. I was wondering if everyone had to suggest 5 programs to install that don't come standardly installed and maybe some articles to read; what would they be?

Thanks
Axis
[Audacity](http://audacity.sourceforge.net/)
[GQview](http://gqview.sourceforge.net/view-shot.html)
[MPlayer](http://www.mplayerhq.hu/design7/news.html) (best when configured to your liking and built from source)
[GIMP](http://www.gimp.org/)
[Prelink](http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink)

And for reading:
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by rsambuca on 2006-11-20
Check out the following page. I don't know how up-to-date it is, but there is a lot of info for windows-linux equivalent programs.  In any event, it is a good starting point to find what you are looking for.  You can then search the forums for reviews and help.

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

---

### Post by LLRNR on 2006-11-20
> **HareBall said:**
> I believe this should have been:
```
sudo aptitude install kolourpaint
```
There was a typo in the name.

Yup, HareBall, I'm sorry I made a typo indeed, ... I was thrilled at the thought of Kolourpaint and made a typo :rolleyes: I'm sorry, I'll correct it; thanks for noticing.

---

### Post by HareBall on 2006-11-23
> **LLRNR said:**
> Yup, HareBall, I'm sorry I made a typo indeed, ... I was thrilled at the thought of Kolourpaint and made a typo :rolleyes: I'm sorry, I'll correct it; thanks for noticing.
I only noticed because I tried to install it and it couldn't find it. So, I checked and noticed the typo. Worked as designed after that;)

---

### Post by Axis on 2006-11-23
Thanks everyone for all of the useful information. I have read some of the guides suggested and feel a bit better and more comfortable with linux. Thanks again, axis

---

### Post by PrinceArithon on 2006-11-23
This is a great place here to go [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

I used this place when I first started.  Sometimes things might not work like they are supposed to and you'll have to come back here.  That only happened to me twice.

Now as for anti-virus you can get anti-virus from your synaptic manager.

Go to system > administration> synaptic package manager

somewhere in that HUGE list of alphabetically ordered programs you should look for something called avg71flm..or something like that.

It's a really good program to use.

---

