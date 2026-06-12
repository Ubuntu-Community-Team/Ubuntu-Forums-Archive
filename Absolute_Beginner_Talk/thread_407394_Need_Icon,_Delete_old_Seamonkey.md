---
title: "Need Icon, Delete old Seamonkey?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-04-12
SUCCESS - KINDA...
I finally got Seamonkey installed, but now I don't have the correct icon, it didn't show up after install.  I made a launcher, but can't get the right icon, it doesn't show up in Seamonkey Icons directory when I search for it.

So now:

1) How do I get correct Icon?
2) Can I just delete the first installation (1.1) in Roger-Seamonkey directory? Or will that kill all my bookmarks? I can't find an "uninstall" file, maybe it's not necessary?

Thanks!!!

---

### Post by mac.ryan on 2007-04-12
Not sure I got what the problem is... why not to [download the icon]("http://ctho.ath.cx/tmp/seamonkey-logo-original.png") and make a launcher using that?

---

### Post by pistcivet on 2007-04-12
The SeaMonkey icon should be in:
/usr/local/seamonkey/chrome/icons/default/

Your mail and bookmarks should be in:
/home/<user>/.mozilla/default/<random text>.slt/

To uninstall SeaMonkey, simply delete /usr/local/seamonkey

To install SeaMonkey:
```
sudo su
./seamonkey-installer
/usr/local/seamonkey/seamonkey     (this runs Seamonkey as root, as soon as it starts, quit SeaMonkey)
exit
```

They say to run SeaMonkey once as root before you start using it
(to set up the profile I believe.)

Hope this helps.  :)

---

### Post by RogerDavis on 2007-04-13
When I get to the "Icons" directory, there is no default directory.

Any further ideas?

Thanks!

---

### Post by RogerDavis on 2007-04-13
Well, found the "default" directory, I missed it the first time because when creating the launcher, the icon browse doesn't see any of the icons (if that's what they are with .xpm and .png ?

---

### Post by mac.ryan on 2007-04-13
> **RogerDavis said:**
> Well, found the "default" directory, I missed it the first time because when creating the launcher, the icon browse doesn't see any of the icons (if that's what they are with .xpm and .png ?

Anything that you will see in the icon browser (.png, .svg, etc...) will also show up on the desktop/panel. Icons are just images.

As for finding the icons I understand you now managed, but just in case: once you saved the icon you want to use somewhere on your file system, you press on "no icon" form the launcher creator dialogue, and than "browse"...

Have fun! :)

---

### Post by pistcivet on 2007-04-13
Now that you mention it, I had a little difficulty setting the icon myself.
Of course the one you want is "seamonkey.png", the biggest icon.
I should have mentioned it, but its been so long I completely forgot. :roll: 

BTW, when you update to a new version you'll want to uninstall the old one first.
I just do this:```
cd /usr/local/
sudo rm -dr seamonkey
```
Then reinstall as before.

Be careful with "rm -dr", it recursively deletes directories and files with no warning.
Hope you like SeaMonkey, I just love it! :)
I think its slightly faster and more stable than Firefox. (In my experience)

---

