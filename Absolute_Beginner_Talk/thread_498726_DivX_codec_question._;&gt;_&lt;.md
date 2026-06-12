---
title: "DivX codec question. ;&gt;_&lt;"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-11
I feel like I should know how to do this, and so feel VERY awkward asking this, but:

I've recently downloaded and supposedly installed that Divx 6.1.1 codec. Everything looks fine, and the codec appears to be there (libdivx.so **is**  the right thing, right? ;>_>)...but .avi files, etc. still won't play in xine, so my question is this:

Is there anything I need to do in terms of getting the codec to activate or something? If not, am I installing something totally different? And which files does this DivX codec affect? Do I need any other codecs to play .avi files, and if so, what are they?

And lastly, although this has nothing to do with DivX codecs, how the heck am I supposed to update my sources.list in Knoppix 3.8 (Kubuntu? ;?_?)??? When I try sudo kate /etc/apt/sources.list, it gives me this:

> "root@box:/# sudo kate /etc/apt/sources.list
mkdir: Owner of /tmp/.ICE-unix should be set to root
QPixmap: Cannot create a QPixmap when no GUI is being used
QPixmap: Cannot create a QPixmap when no GUI is being used
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-10671' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-10658' to 'kate'
kate: ERROR: Communication problem with kate, it probably crashed.
root@box:/# Mutex destroy failure: Device or resource busy
"

And when I try sudo kwrite /etc/apt/sources.list I get this:
> 
"Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwrite: cannot connect to X server :0.0


When I had Breezy, I just did "sudo gedit /etc/apt/sources.list"...is the same principal applied here? (Yes, I'm really new at this, if you hadn't guessed.)

---

### Post by taurus on 2007-07-11
For Gnome,
```
gksudo gedit /etc/apt/sources.list
```

For KDE,
```
kdesu kate /etc/apt/sources.list
```

Or
```
sudo nano -Bw /etc/apt/sources.list
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ARandomKid on 2007-07-11
> root@box:/# kdesu kate /etc/apt/sources.list

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0

root@box:/# sudo nano -Bw /etc/apt/sources.list

sudo: nano: command not found
 

Myeh.:( Can't wait 'til that Feisty CD gets here. Things sound much easier with that...

---

### Post by Drakkor on 2007-07-11
Try vlc for avi play, I believe it's in the repos :)

---

### Post by ARandomKid on 2007-07-11
Bah. Can't install vlc. Or MPlayer, for that matter...

...I'll just wait until the feisty CD I ordered gets here, this isn't THAT major.

---

