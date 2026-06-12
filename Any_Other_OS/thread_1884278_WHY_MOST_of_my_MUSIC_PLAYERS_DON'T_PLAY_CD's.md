---
title: "WHY MOST of my MUSIC PLAYERS DON'T PLAY CD's????"
date: 2011-11-21
forum: Any Other OS
---

### Post by daniel227 on 2011-11-21
Hello,
I'd like to settle on ONE player for all my music.
During my search i noticed that there seems to be some problem with  Linux and Audio CD's - sometimes they show up in my file browser  (thunar), sometimes not. when they show clicking on it says: Could not  mount Audio CD: Location is not mountable.

I understand that they can't be read as a file system by linux.

However, most music players don't recognize them either, namely Rhythmbox, Gmusicbrowser, Clementine, Guayadaque...

VLC and Gnome-mplayer have a menu entry "open disc"  and do play audio cd's
(however in VLC the field is filled with garbage and everytime i have to enter /dev/cdrom or /dev/sr0 again).

To me it seems something is not working properly here - something that is not about any particular media player.

something about mounting? fstab? i'm such a semi-noob. also still fairly new to linux so please bear with me.

daniel

                                                                                                                                    *                                              [ps: i had to post this as a new thread otherwise it won't be seen]("http://ubuntuforums.org/posthistory.php?p=11471257")*

---

### Post by Sonsum on 2011-11-21
I'm much more familiar with Gnome than XFCE, but when I insert a CD (Bon Jovi! :guitar:), the system asks me what player I want to open it in. I open it up and I'm Livin' on a Prayer.

Do you have ubuntu-restricted-extras installed? Perhaps there is a driver you're missing,

---

### Post by Bucky Ball on 2011-11-21
This might get you somewhere, though not a permanent fix:

[http://linux.about.com/od/xubuntu_doc/a/xubudg28t04.htm](http://linux.about.com/od/xubuntu_doc/a/xubudg28t04.htm)

Are you using Xfce or Gnome (thunar will run in either, Sonsum)? If you have a particular preference for Thunar (and if you're using Gnome this is likely), great. If not, Nautilus will run in either and if you edit preferences there is a 'Media' tag there.

* UPDATE: If using Xfce, it is Apps>Settings>Removable Drives and Media. That *should* fix things.

** FURTHER UPDATE: I have no entry for the CD in fstab, that is not your issue ... or at least, shouldn't be. And:

> In Xfce  4 Settings Manager>Desktop Tab Icons check the box for  Removable Devices and insert a CD, then see if you can open it from the  desktop.

... from here:

[http://ubuntuforums.org/showthread.php?t=1533121](http://ubuntuforums.org/showthread.php?t=1533121)

---

### Post by Sonsum on 2011-11-21
> **Bucky Ball said:**
> (thunar will run in either, Sonsum)

I am aware of this, but I have a feeling that this is XFCE. Don't ask me why.

Perhaps some clarification on the OP's part could help sort this out?

---

### Post by daniel227 on 2011-11-21
sonsum, right feeling! i'm using linux mint fluxbox which uses elements of both lxde and xfce - definitely not gnome. distro's based on ubuntu lucid LTS. I thought LTS is a good idea but maybe it isn't...

bucky ball, this thread [http://ubuntuforums.org/showthread.php?t=1533121](http://ubuntuforums.org/showthread.php?t=1533121)
seems to answer it all.

the first link (mount -o or sth) did not help. always complains that /dev/sr0 is not in fstab, neither in mtab. i had tried that before.

my  interpretation of the situation is that some music players depend on  the file manager to see and play audio cd's, others don't. and thunar  can't mount audio cd's. right or wrong?
btw i can tell thunar-volman to open cd's with an application, that works.

so the question is:
is this just the way it is with mint fluxbox, lxde, xfce and thunar?
can i install something to make it so that those particular music players can see and play cd's?

asks daniel.

ps: by the way i checked burned cd's and originals, both don't work. dvd's and data cd's are recognized and browsable in thunar.

pps: it seems i have most of the functionality of xfce but not the menu structure, so instead of saying "go to menu->system->someapp", could you give the command instead? thanx.

---

### Post by Elfy on 2011-11-21
Thread moved to Other OS/Distro Talk.

---

### Post by Bucky Ball on 2011-11-23
??? Everyone on the forum can still see your post! What is your problem here exactly? forestpixie hasn't censored you at all, simply moved your post into the appropriate forum, still in full view of the entire community.

Nothing was wrong before. Your abusive comments in the last post could cause a problem, though ...

---

### Post by Elfy on 2011-11-24
Posts jailed - thread closed.

---

