---
title: "The look of Gnome"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Qarnak on 2007-08-22
Greetings,

I just bought a new Dell with Ubuntu 7.0.4. I love it. It is so much better than Winders. I am not an absolute newb, having tried Ubuntu, Kubuntu, Xubuntu, Debian, Mandriva, Fedora, and Puppy Linux before, but I have always used distros with KDE or Xfce. I even purchased Xandros Home 3, Linspire 5.0 and ran an Ubuntu server for a while. However, I find now, since it came this way, that Gnome is better than KDE. Gnomebaker is superior to K3b, and the whole thing seems faster. 
The one thing that I cannot get used to is the "look" of Gnome. Having my menu on the top of the screen is irritating. I know I can move the panel, but that just puts my trash at the top or gives me a double menu on the bottom. Is there a skin, or something like that, to make Gnome look more like KDE ??? Also, is there a way to make Gnome use double clicks of the mouse, like KDE gives the option to do ???

Thank you,

Bob

---

### Post by prince_niceguy on 2007-08-22
Yes you can remove the panel on the top by right click --> delete this panel. Whatever was on the top panel can be added on the bottom by right click on bottom panel and clicking add to panel. You can increase the panel size by right click again on bottom panel and properties.

Not sure if this is the solution you are expecting. You can search for themes/skins on gnome-look.org

I too temporarily switched to gnome because i got irritated with kde crashes and its incompatibility with compiz fusion. I am waiting for KDE 4 though and will try that out.

I some how find KDE more friendlier to me. Give a shot at kubuntu if you want to play around with KDE.

---

### Post by mcduck on 2007-08-22
You are not limited to moving the panel, you can move all the panel applets where ever you want. Just drag them around with middle mouse button or right-click and select "Move" (If they won't move, right-click the applet and make sure "Lock to Panel" is not enabled).

This way you can change your desktop to work the way you like, and even arrange it into one-panel layout like KDE has.

If you right-click in any empty space in the panel you get a menu where you can add and remove panels and change the way they look and behave. There are are also some additional applets you can add to your panels if you select "Add to Panel" from the right-click menu.

---

### Post by Qarnak on 2007-08-22
Wow !!! What a quick reply !!! Thank you. :)

I think this solution will work fine. I was unaware that I could add to panels or delete panels. In the past I simply changed the property of the panel to change where it showed up. I am sorry that you are having probs with KDE. I have never had a crash or problem with Linux, except for with Linspire, which was my fault(I used unsupported repositories and apt, instead of their CNR)
Of course I do not really do all that much with Linux. I mainly surf the web and play a few games, burn a couple CDs and use bit torrent clients. The web server I ran was very simplistic and only had a few users. It was mostly a file server.

Peace,

Bob

---

### Post by stchman on 2007-08-22
> **Qarnak said:**
> Greetings,

I just bought a new Dell with Ubuntu 7.0.4. I love it. It is so much better than Winders. I am not an absolute newb, having tried Ubuntu, Kubuntu, Xubuntu, Debian, Mandriva, Fedora, and Puppy Linux before, but I have always used distros with KDE or Xfce. I even purchased Xandros Home 3, Linspire 5.0 and ran an Ubuntu server for a while. However, I find now, since it came this way, that Gnome is better than KDE. Gnomebaker is superior to K3b, and the whole thing seems faster. 
The one thing that I cannot get used to is the "look" of Gnome. Having my menu on the top of the screen is irritating. I know I can move the panel, but that just puts my trash at the top or gives me a double menu on the bottom. Is there a skin, or something like that, to make Gnome look more like KDE ??? Also, is there a way to make Gnome use double clicks of the mouse, like KDE gives the option to do ???

Thank you,

Bob

I will agree that Gnome might be a better GUI than KDE, but K3B is far better than Gnomebaker for CD/DVD burning purpose.

---

### Post by Qarnak on 2007-08-22
I really like K3b, but I cannot get it to work with mp3. I installed libmad0, but it still says it is missing a plugin. I cannot find said plugin with the add and remove app.

Peace,

Bob

---

### Post by stchman on 2007-08-23
> **Qarnak said:**
> I really like K3b, but I cannot get it to work with mp3. I installed libmad0, but it still says it is missing a plugin. I cannot find said plugin with the add and remove app.

Peace,

Bob

You need the mp3 plugin for k3b.  Do the following:

```
sudo apt-get install libk3b2-mp3
```

That will fix the problem.

---

### Post by myke on 2007-08-28
I've had clean installs on my dual boot system (have to use WinXP for work stuff some times) of both Kubuntu and Ubuntu over the past few months so that I could really see the difference between KDE and Gnome.   I've decided, that for me ... Gnome is the better of the desktop environments for general folder and file management.  I think KDE is way to dependent on Konquerer for everything which always seemed to slow the system down.   However, program/package wise ... QT/KDE based apps seem much more polished than their GTK/Gnome counterparts.    I don't think there's any comparison between a program like K3b and Gnomebaker.  K3b is far superior.   The apps are really more QT vs GTK than KDE vs. Gnome.   That's the real argument if there is one.   To me, the desktop environment is flexible according to what is best for you.  Gnome works better for me.  It's simple, clean, and pretty quick.  But the QT based apps are generally much better.    This may sound picky but one thing I really HATE about GTK based apps are the inability to customize the menus.   I like to pick and choose my toolbar buttons and such and QT apps like K3b, Kaffeine, and Amarok allow this whereas Gnomebaker, Totem, and Banshee do not.  Also, those 3 QT programs generally look just a hell of a lot better than their GTK counterparts which are rather ugly.

So ... for me ... and it IS all about CHOICE here ... so no flames please ... I keep Gnome as my desktop/file & window manager but generally prefer QT/KDE based apps/packages (with the notable exceptions of Synaptic over Adept and Gaim/Pidgin over Kopete -- which itself is rather ugly).

---

### Post by hyper_ch on 2007-08-29
if you don't like gnome, why don't you just simply install Xfce or KDE then?

```

sudo aptitude install xubuntu-desktop

```
or
```

sudo aptitude install kubuntu-desktop

```

---

