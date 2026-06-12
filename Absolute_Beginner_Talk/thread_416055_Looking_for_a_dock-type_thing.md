---
title: "Looking for a dock-type thing"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-04-20
I liked avant window navigator, but then feisty made it stop working... Is there anything else out there like it, that is known to work in feisty?

I'm just looking for something that lets me go between windows and isn't a panel...

Thanks :)

---

### Post by spin2cool on 2007-04-20
I believe gdesklets has a dock module.  (gdesklets can be installed through automatix)

---

### Post by igknighted on 2007-04-20
> **spin2cool said:**
> I believe gdesklets has a dock module.  (gdesklets can be installed through automatix)

gdesklets is not smooth at all.  I would try wbar (it doesn't autohide, but its the smoothest I have seen) or kooldock.  If you are running beryl kibadock is an option, but it does these weird effects and is hard to make act normal.

---

### Post by Gorthus on 2007-04-20
I am using Beryl but i am in AIGLX mode...

BTW I don't know how to install tarballs.

@Spin2Cool: I know, This is only for launchers though. I want one that displays current windows as well.

---

### Post by expatCM on 2007-04-20
This may help you with tarballs

[http://berkshirelug.org/mediawiki/index.php/InstallTarball](http://berkshirelug.org/mediawiki/index.php/InstallTarball)

---

### Post by Gorthus on 2007-04-20
That didn't help. Thanks anyway.

---

### Post by markupstart on 2007-04-20
I use Avant Window Navigator just fine, what is it doing for you, that it's not working?

---

### Post by Gorthus on 2007-04-20
> **markupstart said:**
> I use Avant Window Navigator just fine, what is it doing for you, that it's not working?

Well:
[LIST=1]
[*]I'm looking for something that launches AND displays current windows
[*]I don't know how to explain it... Sometimes the icon is there, and sometimes it isn't.
[*]It makes a huge black area on the bottom half of my monitor and eats everything there
[/LIST]

---

### Post by jiminycricket on 2007-04-20
Does this help? [http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

Also, several reviews of them here: [http://osnews.com/story.php/17494/Review-Dockers-for-Linux](http://osnews.com/story.php/17494/Review-Dockers-for-Linux)

Unfortunately kxdocker doesn't work as packaged right now, so you might need to find a tar.gz for it.

---

### Post by markupstart on 2007-04-20
Well #3 is because it needs Beryl or Compiz in order to display itself properly.

> **Gorthus said:**
> Well:
[LIST=1]
[*]I'm looking for something that launches AND displays current windows
[*]I don't know how to explain it... Sometimes the icon is there, and sometimes it isn't.
[*]It makes a huge black area on the bottom half of my monitor and eats everything there
[/LIST]

---

### Post by Gorthus on 2007-04-20
Beryl doesn't work for me anymore. Another one of my long list of ubuntu problems.

---

### Post by spin2cool on 2007-04-21
Blaming Ubuntu for your beryl problems is like blaming Microsoft for your Adobe Photoshop problems.  Beryl is not supported by the official ubuntu distro, so you install it at your own risk.

---

### Post by Gorthus on 2007-04-21
> **spin2cool said:**
> Blaming Ubuntu for your beryl problems is like blaming Microsoft for your Adobe Photoshop problems.  Beryl is not supported by the official ubuntu distro, so you install it at your own risk.

By Ubuntu problems I simply mean problems within ubuntu, the operating system itself.

---

### Post by notwen on 2007-04-22
Un-install both Beryl and AWN.  I'd try installing Beryl again and once you have Beryl up & running w/o any issue, you can move on to installing AWN.  Here are some links to threads you may find useful.  Just use the appropriate links in the Beryl how-to corresponding to which version of Ubuntu you may be using.  As for AWN, if you have any issues getting ti installed, just un-install AWN and then use the deb file below.  Post back if you have any problems. Good Luck. =]

[Beryl How-To]("http://ubuntuforums.org/showthread.php?t=272104")

[AWN How-To]("http://ubuntuforums.org/showthread.php?t=385981")

[avant-window-navigator_0.1.1-1_i386.deb]("http://ubuntuforums.org/attachment.php?attachmentid=24376&d=1170430951")

---

### Post by rainwalker on 2007-04-22
I'm running Edgy right now and I'm totally lost with this whole Avant thing. I followed the instructions on the avant site, and I have Beryl installed and running, but Avant never launches (Applications -> Accessories -> Avant Window Navigator)

---

### Post by notwen on 2007-04-22
Type avant-window-navigator in a terminal and see if you get any errors.  If you're looking for a pre-loaded dock it's going to start as a empty slit of a dock that you need to drag launchers to. If you get any errors in terminal, post them back here.

---

### Post by rainwalker on 2007-04-22
> Segmentation fault

No idea what this means.

---

### Post by rebegin on 2007-05-03
> **jiminycricket said:**
> Does this help? [http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

Also, several reviews of them here: [http://osnews.com/story.php/17494/Review-Dockers-for-Linux](http://osnews.com/story.php/17494/Review-Dockers-for-Linux)

Unfortunately kxdocker doesn't work as packaged right now, so you might need to find a tar.gz for it.

installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

