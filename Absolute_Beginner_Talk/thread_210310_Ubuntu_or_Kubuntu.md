---
title: "Ubuntu or Kubuntu?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Gonzo_PhD on 2006-07-06
I'm a beginner with Linux and had a few questions about Kubuntu and Ubuntu.

1) What's the difference in layman's terms (besides KDE and GNOME (because I really don't know what that is.))?

2) Which one should I go with as a beginer?

Thanks

---

### Post by shoot2kill on 2006-07-06
the best option for a beginner (like what i did)

--install ubuntu
--install kubuntu-desktop

now you will easily be able to switch between KDE and Gnome...

KDE is a bit more like windows than Gnome...

personally i prefer KDE but Gnome is not that much difference (IMO)

---

### Post by Jagot on 2006-07-06
1)  Essentially the interface differs between the two, and also the programs that are installed by default.  KDE uses a desktop environment called KDE and Ubuntu use GNOME.

Some screenshots of the two:

Kubuntu - [http://shots.osdir.com/slideshows/slideshow.php?release=662&slide=4&title=kubuntu+6.06+screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=662&slide=4&title=kubuntu+6.06+screenshots)

Ubuntu - [http://shots.osdir.com/slideshows/slideshow.php?release=659&slide=4&title=ubuntu+6.06+screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=659&slide=4&title=ubuntu+6.06+screenshots)

Videos:

Kubuntu - [http://osvids.com/files/page3-108-pop.html](http://osvids.com/files/page3-108-pop.html)

Ubuntu - [http://osvids.com/files/page3-1035-pop.html](http://osvids.com/files/page3-1035-pop.html)


2)  It really is a matter of personal preference.  I personally prefer GNOME so I use Ubuntu.  Once you have installed either of them, you can easily install the other from within the version you have installed so you can use both.

As a beginner you may also want to take a look at this video of an Ubuntu install from the Desktop (live) CD:

[http://osvids.com/files/page3-1034-pop.html](http://osvids.com/files/page3-1034-pop.html)

---

### Post by Gonzo_PhD on 2006-07-06
Thanks for the help. I think im going to install the Ubuntu DVD and then try out Kubuntu.

---

### Post by someusernoob on 2006-07-06
The only difference is the KDE and Gnome environment + programs. E.g. with Gnome you work with the gnome-terminal, in KDE with konsole, in Gnome you work with gedit (texteditor) in KDE you work with Kate (note that almost everything in KDE is writing with a K). They do the same thing, but they are different. Everything beneath is exact the same. Otherwise it would be a complete other distribution. 

As a beginner, i dont know if that makes much difference. Its more which one you like. They say KDE looks more like Windows, so its easier to work with. I dont like KDE at all. I dont know exactly why, its just like one likes his french fries with mayonaise, others dont.

Beautifull thing about this is that you just can install Ubuntu (the Gnome one) and upgrade it to KDE. You can actually choose between the two environments, and everything below is the same (e.g. your documents folder). You can also install Kubuntu (the KDE one) and upgrade it to Gnome.

To do this use:
```

sudo aptitude install ubuntu-desktop
sudo aptitude install kubuntu-desktop

```

You can swith between KDE and Gnome via the login screen (sessions).

So if you install one of the two now, and upgrade to the other, you can test and look and maybe like, and next time a new Ubuntu is released you download and install the one you most like. (It's not necessary to install it again, you can uprade it, but i myself like to start clean every now and then.)

---

### Post by bruenig on 2006-07-06
As a beginner, you should probably go with ubuntu and GNOME as more people use it and more support is available for it. When you ask a question in the forums, most people (from my experience) assume you have GNOME and give you instructions as they would in GNOME. For somebody with pretty basic knowledge it is easy to translate the instruction from GNOME to KDE (i.e. Konsole instead of Terminal) but for first time beginners it is probably easy to just go with ubuntu.

---

### Post by crystal on 2006-07-06
> The only difference is the KDE and Gnome environment + programs. E.g. with Gnome you work with the gnome-terminal, in KDE with konsole, in Gnome you work with gedit (texteditor) in KDE you work with Kate (note that almost everything in KDE is writing with a K).
I have been able to use Kate and KDevelop in Gnome, so I suppose that the lines can be blurred with the installation of appropriate libraries.

---

### Post by shoot2kill on 2006-07-06
yes, i had ubuntu (Gnome) and installed kubuntu-desktop, and you can still use ubuntu commands and programs when in KDE... thats why i like it over just one GUI desktop...

---

### Post by aysiu on 2006-07-06
Don't forget that to experience the full power of *aptitude*, you have to update first: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by Al3xanR0 on 2006-07-06
[QUOTE=Gonzo_PhD]I'm a beginner with Linux and had a few questions about Kubuntu and Ubuntu.

1) What's the difference in layman's terms (besides KDE and GNOME (because I really don't know what that is.))?

2) Which one should I go with as a beginer?

Thanks[/QUOTE]

It is all a matter of preference, I would try both then formulate your own opinion. I use both although I am a bit partial to KDE because it straightened  my learning curve during my progression to GNU/Linux from M$ Windows. In my experience, the more you tweak (aesthetically speaking of course), especially if you are anything like me the differences become very subtle. See for your self, here is [Gnome]("http://www.lynucs.org/index.php?screen_id=1354349612448d7c21403c6&p=screen") and here is [KDE]("http://www.lynucs.org/index.php?screen_id=53732162544720ecb9b54e&p=screen"). As you can see they are almost identical in appearance (aesthetically speaking of course), by and large the most noteable differences are in their mannerisms.

Ubuntu or Kubuntu? After using both you will be in a better position to answer that question yourself. Enjoy:-D

---

### Post by aysiu on 2006-07-06
[http://www.psychocats.net/ubuntu/kdegnome.html](http://www.psychocats.net/ubuntu/kdegnome.html) explains some of the differences.

---

### Post by AndyCooll on 2006-07-06
Some folk in this thread are suggesting that you try both desktop environments and I agree with this ...to a point.

IMHO it is best to start with Ubuntu (and _not_ Kubuntu). The reason I say this is because Ubuntu (and therefore the GNOME desktop) is the default installation. And if you are a noob and need plenty of assistance, most (though by no means all) of the threads in these forums provide answers for the default installation. It could be said that many of the answers work for both desktop environments, but I would suggest that you do yourself a favour and avoid any chance of confusion.

Once you have gained a level of familiarity, _then_ try Kubuntu. You might find that you prefer this, you might not.

Personally I prefer GNOME, since it is a "cleaner" desktop environment with the aim of simplicity. However, each to his own. And anyway, having said that there are many KDE apps I prefer over the GNOME ones. The beauty of these desktop environments is that you can use KDE apps on a GNOME desktop and vice-versa

:cool:

---

### Post by aysiu on 2006-07-06
I'm with AndyCooll on this one.

Start with Ubuntu--most of the support here is targeted to Gnome.

Once you're comfortable with that, you can try KDE, too.

---

### Post by gThree on 2006-07-06
Another vote for starting with Ubuntu.  I run both Kubuntu and Ubuntu in separate partitions and find Kubuntu a bit less stable.  At least on PowerPC.

KDE does come across as being more Windows-like at first, but also has some very strong programs.

After using both, I ended up liking each for different reasons and currently switch back and forth.  When you're comfortable with one, definitely try the other.  The ability to bounce around like that (at no cost but time) is one of things I really like about Linux.

Good luck ...

---

