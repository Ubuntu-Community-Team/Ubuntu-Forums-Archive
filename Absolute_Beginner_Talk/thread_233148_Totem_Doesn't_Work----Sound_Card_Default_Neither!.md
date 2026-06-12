---
title: "Totem Doesn't Work----Sound Card Default Neither!"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Ambimom on 2006-08-09
Everything loaded into Totem tells me that I need more plugins....but when I go to "help" on the net, there's nothing there, not that I'd know what to do anyway....It should play Divx and Xvid, but it doesn't.  The only thing it does play is Ogg.  

I've installed Videolan VLC which seems to play everything, audio and video.

Which brings me to my perpetual sound card issues.  I've noticed that when Ubuntu loads, every so often, the wrong sound card is defaulted.  The default is Intel ICH5, but sometimes when I boot up, it defaults to a USB Device that I don't have.

I have begun rebooting to fix the sound card default, but there must be a way to fix this.  I've already been through the reinstallation of the ALSA driver thingy.

Any answers?  I really want to understand and use Linux.

---

### Post by matthewv on 2006-08-09
The correct codecs will need to be installed to get totem to work.
See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for more help on that. I'm not certain as to what's up with your soundcard issues

---

### Post by Ambimom on 2006-08-10
Thank you!!!!!!!  Totem works!!!!! Yipppeeeee!!!

Now if I can only figure out why the sound card defaults to usb....when I don't have USB sound card....

Audacity only works when the Intel card is the default....

Thanks again!

---

### Post by davebgimp on 2006-08-10
Check your system BIOS and try disabling all inboard sound (leaving only your sound card).

---

### Post by Ambimom on 2006-08-10
My sound preferences show the usb and the Intel sound card but I can't switch the default.  If I switch to Intel manually in the preferences, it will immediately revert....

I'm just not going to use Audacity for Linux...that's the only thing that seems to be affected by the sound card default issue. 

I'm afraid to mess with my Bios.  I don't know enough to start monkeying around with it.  I'm not that adventurous.  Installing Linux on a second hard drive is about as adventurous as I am.  LOL

---

