---
title: "Tablet in Gimp (Wizardpen)"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Psychobiker on 2007-12-29
Hey,

I've installed the Wizardpen driver, and using the buttons on the stylus will left and right click. when i test the input of the stylus, it produces gibberish as it should.

Now, when I go to Gimp, just wondering why it's not showing up under extended devices. all that's there is the touchpad

L

---

### Post by Psychobiker on 2007-12-29
it's kinda urgent....cheers.

Works fine on my Windows machine :S.
The Mouse works A-OK, but the stylus not,

L

---

### Post by uDanimal on 2008-03-26
I had mine working just fine in Gutsy, but after I upgraded to Hardy yesterday,  I have followed the same howto in the forums to get it working, but it doesnt work with gimp now.  Anyone have any new ideas?  If I get it working I will post here and try to communicate what I did to get it.

---

### Post by uDanimal on 2008-03-27
**Bumpetty bump**

Still no luck.  I followed the same howto in the forums for enabling support, 
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
And this command:
*_ls -la /dev/tablet-event_*
outputs this line
*_lrwxrwxrwx 1 root root 12 2008-03-27 21:22 /dev/tablet-event -> input/event3_*

But it will not move the cursor, and in Gimp and inkscape the tablet no longer shows up in extended devices (although now there is a "configured mouse" that wasnt there before.

Anyone else have any suggestions?

---

### Post by Kagarrache on 2008-04-02
Same problem here after upgrading to 8.04.

Still no idea what to do? :confused:

---

### Post by andrevanzuydam on 2008-04-17
HI Everyone

If you are using the desktop effects version of X windows then GIMP doesn't detect the tablet.  

I can use my tablet properly if I disable desktop effects.  You can do this by creating this file :

 ~/.config/xserver-xgl/disable

Restart X windows and see if you can now detect your tablet.

I am working on getting GIMP to work with the tablet in desktop effects mode and I have already posted a thread on installing GIMP with xinput support which I hope someone can help us with.

The key here is the xinput support in the GTK+.

---

