---
title: "My keyboard is messed u_!"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by saxofoner on 2006-11-30
Is there some easy way to default the keyboard shortcuts?  I was assinin music controller keys, and now my key, and my  key don't work.  OH WAIT, that's not very helful.  Let me indicate which keys it is...
KICK KICK _UNCH _UNCH
That's not lunch, it's unch.
And this one.
NOT STRAI_HT, NOT BI, NOT _AY.  Often indicated by letter 6 in 1337 seak.  

I kind of need my keys back, because cut and astin the letters takes a reat while. Like this.  G p   I cut and asted those off of this ae. Can someone tell me how to fix this?  

See, I assined those keys to "dummy shortcuts" while I chaned some of the other ones, and it ermanently disabled them in normal use!  IT'S A BU@!!! aHHH!!!

---

### Post by LLRNR on 2006-11-30
Saxofoner, I'm really sorry, I don't understand anything else from your post except that you have a **really** big problem with your keyboard; and that you can copy and paste too.

So try this in a terminal, it should take care of your keyboard issues, as far as I know:

```
sudo dpkg-reconfigure xserver-xorg
```

By default, this does a copy (a backup) of your /etc/X11/xorg.conf file. In case anything goes wrong (i.e. worse than it already is) you can revert to that original file:
```
[b]cd /etc/X11
ls -l [/b]*[ you'll see the contens of this dir, with the date when the files were created, too ]*
**sudo mv xorg.conf.backup xorg.conf** *[ assuming that xorg.conf.backup is your backup file ]*
```

Good luck !

LLRNR

---

### Post by CatKiller on 2006-11-30
You should be able to remove the keyboard shortcuts with System -> Preferences -> Keyboard Shortcuts

Or, failing that, maybe with **gconf-editor** (Alt-F2 and paste from this page) in the /apps/metacity section, or possibly in /apps/gnome_settings_deamon/keybindings.

EDIT: LLRNR, he's set up some keybindings that don't work as expected (possibly because they involve the Windows key?) and now he can't use his P or G keys.

---

### Post by saxofoner on 2006-11-30
Sorry, what I was tryin to say was, my keys are messed u= and I want to default them. I'll try what you said.

CatKiller:  That's the roblem!  I removed these keys from all shortcuts, it's like Ubuntu kees them from bein used, anyway!

---

### Post by saxofoner on 2006-11-30
No, sorry, neither of those thin6s worked.  I don't know how to fix the keys in confi6 edit, and my xor6 backu8 didn't hel8.  6osh, I ho8e I can fix this soon.  I re6ret messin6 with my keyboard shortcuts.

---

### Post by CatKiller on 2006-11-30
> **saxofoner said:**
> I re6ret messin6 with my keyboard shortcuts.

How did you set those shortcuts u8? (sorry, up? :) )

To change the configuration with gconf-editor, you only really need to find and remove the shortcut. So say you set "Show Desktop" to <Super>G, you'd find /apps/metacity/global_keybindings/show_desktop, double-click on it, and then delete the value.

I think all of the keybindings are kept in gconf, although it's possible that they would be in a different part to the ones I mentioned. If they are, I don't know where that would be.

Unless you used a different method to change the keybindings, with xmodmap or something. I have no idea how other methods would work, or where they keep their configuration settings, since I've never tried them.

EDIT: for the time being, you can use the Character Map at Applications -> Accessories -> Character Map (it might not be enabled by default - right-click on the menu and select Edit Menus if it isn't there, and then put a tick in the box next to the application you want on the menu) to drag-and-drop Gs & Ps to facilitate communication. You'll want to use the Latin script.

---

### Post by saxofoner on 2006-11-30
Ohhh, okay, it's in Metacity.  Thanks.   

I used the System > 8references > Keyboard Shortcuts tool.  It's almost like it's broken or somethin6.  Your 8lan, should, I think, work.  Thanks.

Edit:  That didn't work either.  There were no settins in Metacity for the "8ause, 8lay, start music 8layer" etc. I don't know where those are ke8t.

---

