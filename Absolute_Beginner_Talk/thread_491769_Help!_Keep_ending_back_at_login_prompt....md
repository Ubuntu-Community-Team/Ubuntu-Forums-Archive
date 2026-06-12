---
title: "Help! Keep ending back at login prompt..."
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by cknight on 2007-07-04
Well this is a bit frustrating, but when I enter my login name and password and hit enter, the screen goes black, the icon changes to the X-windows watch icon, then it changes to a pointer icon and then *poof* I'm back at the login prompt.   Any ideas on how to get past this problem?  I'm using Kubuntu edgy eft for what it's worth.

EDIT: The username and password are valid.  Entering an invalid username/password shows as such on the login screen and I'm not getting that.

---

### Post by coldstatue on 2007-07-04
was it working before? Did you just change any video settings, or install Beryl or Compiz?

EDIT - What kind of video card do you have? ATI or NVIDIA may be enough info

---

### Post by coldstatue on 2007-07-04
also, are you getting a graphical login, or just a black screen with white text?

EDIT -I guess if the cursor changes, you are starting graphically. does it kick you back to a graphical login, or just text?

---

### Post by Axed on 2007-07-04
Could be a bad session script perhaps? Try going to  Options > Select session > GNOME
And then log on.

If that doesn't work, try GNOME-failsafe. If that doesn't work, it's probably something to do with your X.org config, so kick back to console (Ctrl + Alt + F2), login, and type:```
sudo dpkg-reconfigure xserver-xorg
```
It will ask a lot of questions, if you don't know the answer just press enter.

edit: Just noticed you're using Kubuntu, so obviously you would want to use the KDE sessions.

---

### Post by njknight on 2007-07-04
Try This
As soon as you have logged in (ie. the moment you have hit return on entering your login password)
do a Ctrl + Alt + Esc and hold the keys till the desktop appears - then perhaps take a look at what's starting up in your session manager

---

### Post by SomethingCronic on 2007-07-04
This used to happen to me when my disk was full. You may need to login using recovery mode (GRUB) then navigate to

```
cd ~/.Trash
```

```
rm *.*
```

Make sure you are in the Trash folder when you run the above, I'm not accepting responsibility for you deleting your own stuff :)


reboot the PC and then try logging in.

---

### Post by cknight on 2007-07-04
Kudos to SomethingCronic for the correct solution.  My /home folder was down to 0 free bytes.  Booting to the recovery mode via GRUB and deleting some of the contents of /home folder and rebooting fixed this issue for me. 

For the record:
1) Pressing and holding Ctrl-Alt-Esc didn't do anything after attempting to log in.  Just ended up back at the login prompt
2) Trying to login using KDE and KDE failsafe made no difference to the situation
3) I started at and was getting kicked back to the graphical login screen.  I hadn't made any changes (other than filling up my /home directory!) to the video display, don't use Beryl/Compiz and have a bog standard integrated graphics card (not sure what type).

Many thanks to all who contributed, I'm still in awe at all the support this forum provides.  Its great knowing that if you encounter a showstopper problem, this forum can usually sort you our pretty quick.

---

