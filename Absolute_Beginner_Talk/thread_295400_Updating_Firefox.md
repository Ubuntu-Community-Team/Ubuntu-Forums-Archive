---
title: "Updating Firefox"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Orwell on 2006-11-08
Being new to Ubuntu and Linux in general, im not sure how to go about updating my Firefox browser from 1.5.0.7 to version 2. Have tried clicking 'Help', 'Check For Updates' but 'check for updates' is grey, not available to be clicked.

Any ideas?

---

### Post by bodhi.zazen on 2006-11-08
Go here [Download firefox](http://www.mozilla.com/en-US/firefox/)

Extract the archive.

Firefox 2 is a binary, no install required.

---

### Post by bache on 2006-11-08
You can also read this [tutorial]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by bodhi.zazen on 2006-11-08
That tutorial, while good, will not update to firefox 2.

---

### Post by helphope on 2006-11-08
> **bodhi.zazen said:**
> Go here [Download firefox](http://www.mozilla.com/en-US/firefox/)

Extract the archive.

Firefox 2 is a binary, no install required.

What do you mean, that if I install FF 2.0 it will run together with FF 1.5?

---

### Post by scheuri on 2006-11-08
> **Orwell said:**
> [...]Any ideas?
Actually...yes...:)

Ubuntu (and most other distributions as well) come in releases.
Meaning that after a certain time of development a new release such as 6.06, 6.10 and in 2007 surely 7.04 comes out.

The software packed in those releases have a certain version (eg firefox 1.5, apache 2.0, KDE 3.5.5 and so on) which was tested and cleared for the release.
When adding a new version of a software things would need more testing if that new version is working with all other related software which is included.

Therefore only* security updates are provided for releases of distributiones. 

*However, there are of course "backports" which provide newer software for certain releases. But you should use them with a grain of salt as they MAY break things (they do not need to necessarily).

greetings
scheuri

---

### Post by Orwell on 2006-11-08
> **bodhi.zazen said:**
> Go here [Download firefox](http://www.mozilla.com/en-US/firefox/)

Extract the archive.

Firefox 2 is a binary, no install required.

What do you mean by 'extract the archive'? I downloaded Firefox from the site u listed.....now...?

---

### Post by Orwell on 2006-11-08
> **scheuri said:**
> Actually...yes...:)

Ubuntu (and most other distributions as well) come in releases.
Meaning that after a certain time of development a new release such as 6.06, 6.10 and in 2007 surely 7.04 comes out.

The software packed in those releases have a certain version (eg firefox 1.5, apache 2.0, KDE 3.5.5 and so on) which was tested and cleared for the release.
When adding a new version of a software things would need more testing if that new version is working with all other related software which is included.

Therefore only* security updates are provided for releases of distributiones. 

*However, there are of course "backports" which provide newer software for certain releases. But you should use them with a grain of salt as they MAY break things (they do not need to necessarily).

greetings
scheuri


Thanks scheuri, good points, i'll stick with the version that came with my ubuntu release for now.:)

---

### Post by bodhi.zazen on 2006-11-08
> **Orwell said:**
> What do you mean by 'extract the archive'? I downloaded Firefox from the site u listed.....now...?

Here is how I would do it.

Assuming you downloaded **firefox-2.0.tar.gz** to your desktop:
In a terminal:
```
mkdir ~/src
mv ~/Desktop/firefox-2.0.tar.gz ~/src
cd ~/src
tar xzf firefox-2.0.tar.gz
sudo ln -s ~/src/firefox-2.0/firefox /usr/bin/firefox2
```

_Note_: That sudo link may be sudo ln -s ~/src/firefox-2.0/firefox/firefox /usr/bin/firefox2

You can now launch firefox 2 from a terminal:
```
firefox2
```

You can create a desktop icon or launcher with the command:> /usr/bin/firefox2


PS: Firefox 2 will not break anything.

---

### Post by Bachstelze on 2006-11-08
> **bodhi.zazen said:**
> That tutorial, while good, will not update to firefox 2.

Yes, it will...

---

### Post by TheRingmaster on 2006-11-08
the easiest way to upgrade your system is > sudo aptitude update

sudo aptitude dist-upgrade

---

### Post by Bachstelze on 2006-11-08
And that will surely install FF 2 if you're running Dapper ;)

---

### Post by bodhi.zazen on 2006-11-08
> **HymnToLife said:**
> Yes, it will...

I was not aware fierfox 2 was in the repositories yet. Thank you.

---

### Post by fakie_flip on 2006-11-08
That's not the recommended way of going from Dapper to Edgy. My friend tried it before reading this, and it caused so many problems for him that it probably would have been easier just to download and install from a cd. Read here.

[https://wiki.ubuntu.com/EdgyUpgrades](https://wiki.ubuntu.com/EdgyUpgrades)

---

### Post by glotz on 2006-11-08
When you have a question, first you search
1) the wiki [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
2) the forums [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)
and only then you ask if your question wasn't already answered. [-X

If you'd followed that drill, you'd seen this [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by aysiu on 2006-11-08
> **bodhi.zazen said:**
> That tutorial, while good, will not update to firefox 2.
Um, bulls**t?

Yes, it will.

---

### Post by bodhi.zazen on 2006-11-08
> **aysiu said:**
> Um, bulls**t?

Yes, it will.

aysiu: No need to swear !!

I am confused, if the repositories are now up to date, please just say so.

Otherwise, why the install scripts [here](https://help.ubuntu.com/community/FirefoxNewVersion) and here[www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Are you saying the drapper repositories are now up to date? Then perhpas the above sites should be updated as well.

---

### Post by aysiu on 2006-11-08
The script doesn't install the repositories 2.0. It installs the Mozilla build of Firefox 2.0.

Firefox in the Dapper repositories is still 1.5.

---

### Post by glotz on 2006-11-08
And to further confuse (us) poor newbies, the Firefox version in the Edgy repos is 2.0. :mrgreen:

---

### Post by fakie_flip on 2006-11-08
I grabbed a deb of Swiftfox2 from its website because it is a deb. The dependencies are already met on my Dapper system. It's the same thing as Firefox 2 but optimized for my cpu, with the removal of a few uneeded things too all for speed.

---

### Post by sddfdds on 2006-11-08
It's too bad there isn't a more official backporting for things like this so that dapper users could easily update their firefox with synaptic/apt.  FF 2.0 is a pretty crucial piece of software to not be available in Dapper.

---

### Post by bodhi.zazen on 2006-11-09
> **bodhi.zazen said:**
> That tutorial, while good, will not update to firefox 2.

Hmmm ....

In looking at the tutorial (after some sleep perhpas :lol: )it seems I did not read past:
> Methods for Installing Firefox
Firefox comes standard as the default browser on Ubuntu and Xubuntu. If you're using Kubuntu, you can install Firefox using Add/Remove Programs, Adept, or this terminal command:```

sudo aptitude update && sudo aptitude install firefox
```

:redface:

The second part of the tutorial:> If you want the newest Firefox, you have several options: ..... Will work.

Sorry for my error, still the discourse should remain civil. When mistakes are made in the forums, it should be taken as an opportunity for correction/education :p not swearing [-X . That should hold double for forum moderators.

---

### Post by aysiu on 2006-11-09
We all make mistakes. I didn't insult you. I just called what you said *bulls**t*, which it was.

---

