---
title: "Fonts"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by kiwidipstick on 2006-12-02
I wish to install some fonts. I have searched the forums which gave me some good answers. But, my problem seems to be that I don't have permission to copy the fonts to the font folder. How do I go in as root?
When I installed Etchy Etch 6.10, I gave a username and p/w but, I do not remember being asked to give a root p/w.
Appreciate your assistance please. Btw, etchy etch is very good.
Cheers, kiwidipstick.](*,)

---

### Post by taurus on 2006-12-02
If you need to move or copy something outside of your $HOME directory, use the sudo command...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by fritz_monroe on 2006-12-02
Ubuntu does not set up a root user by default.  You make use of sudo to do the work.  The sudo password is the password for the first account set up.  So, you could do a

```
sudo cp fontfile /etc/fonts

```

Give it the password and it will copy over.

---

### Post by kiwidipstick on 2006-12-02
Hi fritz_monroe, thanks for your reply.
Quote; Ubuntu does not set up a root user by default. You make use of sudo to do the work. The sudo password is the password for the first account set up. So, you could do a sudo cp fontfile /etc/fonts

As my name suggests I am a slow learner. Appreciate help here.
I have the fonts I want in a font folder in my home directory and, obviously need to copy them to either etc/fonts or usr/share/fonts. I do not know which is the correct folder. What is the exact command?
Incidentally, using other Ubuntu distros, I could drag and drop. Not now though under Etchy Etch, it seems?
Cheers.

---

### Post by taurus on 2006-12-02
If you want to drag 'n drop, then use nautilus...

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by kiwidipstick on 2006-12-02
Hi Taurus, tried your suggested command with this response
james@james-desktop:~$ gksudo nautilus
(nautilus:8914): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:8914): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Alas, I do not know what to do next. Thanks.

---

### Post by taurus on 2006-12-02
Then just do it the old fashion way, by a terminal!!!

```
sudo cp <path to your font> <where you want to move to>
```

---

### Post by jlapier on 2006-12-09
FYI - you don't need to sudo for this. The Edgy Help files (Click on System, Help, System Documentation) say:

> If you prefer to download individual fonts by hand, you can install them simply and easily by opening a file manager, and typing fonts:/// into the location bar (see the file manager manual for how to use the location bar). Then you can simply drag the font you downloaded into the group of existing fonts.

This actually copies the font into a to a folder in your home directory (called .fonts). It seems like the font doesn't show up in the fonts folder when you drag it in, but if you open up an application you should see the font in the font list.

- Jason

P.S. If you want to install a font system-wide (not necessary for the casual user), you will need to copy it and then rebuild the font-cache:
```
sudo cp some_cool_font.ttf /usr/share/fonts/truetype/
sudo fc-cache -f -v
```

---

### Post by Hyuuga on 2006-12-09
this thread solved my problem. so i thought i'd just ask my follow-up problem here.

take a look at the attachment, and look at the top bar. It doesn't use the font i installed (elder futhark runes). it uses any other (like purisa) but not this one... why?
oh and, in applications like amarok it doesn't show in the fonts list... why?

ah, nevermind. A reboot fixed it.
Hmm, anyone else noticed that ubuntu has the highest reboot rate of all linux distros?

---

