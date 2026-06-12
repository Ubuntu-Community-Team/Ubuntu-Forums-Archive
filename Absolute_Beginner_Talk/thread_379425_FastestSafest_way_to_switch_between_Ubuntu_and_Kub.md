---
title: "Fastest/Safest way to switch between Ubuntu and Kubuntu"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-03-08
I'm interested in testing the KDE environment and its programs. What's the best way to go about switching to KDE and the KDE package temporarily?

---

### Post by benfindlay on 2007-03-08
you can install kde into ubuntu with this command:

```
sudo aptitude install kubuntu-desktop
```

This will install the kde environment and the various programs that come with it

And by using aptitude instead of apt-get it is much easier to remove (sudo aptitude remove kubuntu-desktop)

Hope this helps!

---

### Post by Starks on 2007-03-08
> **benfindlay said:**
> you can install kde into ubuntu with this command:

```
sudo aptitude install kubuntu-desktop
```

This will install the kde environment and the various programs that come with it

And by using aptitude instead of apt-get it is much easier to remove (sudo aptitude remove kubuntu-desktop)

Hope this helps!

Does that overwrite Gnome? Or can I toggle between the two?

---

### Post by Bachstelze on 2007-03-08
It will install some KDE apps plus all the Kubuntu extras in parallel to Gnome/Ubuntu. You can choose at the login screen whether you want to start KDE or Gnome.

You have another option, though, which is to install a very minimal KDE, with only a few essential apps like Konqueror and Konsole for ex. and without all the Kubuntu artworks - which I personnally don't like at all. If you want to do so, put *kde-core* instead of *kubuntu-desktop*. Of course, it will also let you start KDE or Gnome when you login.

---

### Post by chavo on 2007-03-08
No it doesn't overwrite anything. It's very easy to switch between the 2. Just log out of your Gnome desktop, and then on the Login screen menu select Session -> KDE and then login. Voila you are now in your nice new KDE desktop. To go back to Gnome, just log out again. You can even run both at the same time if you're crazy enough. Heck you can run one in a window inside the other if your absolutely nutty!

---

### Post by aysiu on 2007-03-08
You can toggle. More details here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by bodhi.zazen on 2007-03-08
Another "trick" is to use your virtual terminals.

See this : [http://www.ubuntuforums.org/showthread.php?t=271674](http://www.ubuntuforums.org/showthread.php?t=271674)

---

### Post by Starks on 2007-03-08
While we are on the subject...

What about Xfce? Can I have a menage a trois of all three environments?

---

### Post by Bachstelze on 2007-03-08
Of course, just install *xubuntu-desktop* and the XFCE option will be added to the Sessions menu in gdm.

---

