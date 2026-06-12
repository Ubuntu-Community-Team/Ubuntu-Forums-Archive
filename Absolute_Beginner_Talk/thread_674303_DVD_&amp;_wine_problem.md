---
title: "DVD &amp; wine problem"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by onana on 2008-01-21
My DVD burner doesn't show up in wine. How do I solve this problem without having to rewrite the kernal like all the other forums suggest I do. I'm not comfortable with this since I am a COMPLETE beginner. Trying to use DVD Decrypter.

My version of Ubuntu is 7.10 and I think it's Gutsy but I'm not sure

---

### Post by jken146 on 2008-01-22
Are you sure you need DVD Decoder?  Have you tried DVD::Rip, AcidRip or Thoggen?  They are all native Linux applications and are in the Ubuntu repositories.  You can install them through Applications -> Add/Remove...

---

### Post by TeaSwigger on 2008-01-22
Hello, have you been helped with this issue yet? If not, let's see...

First, please only backup titles you own according to laws of your country etc and so forth.

Now, to be clear, does this DVD drive show up okay in ubuntu? You can play a DVD and everything in ubuntu right? Because WINE won't see it if ubuntu doesn't. If not, I can't help on that, in fact I'm trying to get help on that myself right now :p

If so, great! Open WINE's configuration dialog, you can open that from a terminal just by entering 

```
winecfg
```

Note the drives tab. Click that. Here's where you can set the drives etc as you want WINE to see them. If your DVD drive isn't there, click the autodetect button. If it's still not there, you can add a new "drive" letter and just point it at your DVD drive ( at /dev/dvd or maybe /dev/scd0 or /media/cdrom, wherever it is ). Hit "show advanced" and with the DVD drive selected, specify in the "type" drop down box that it's a cdrom. That should be that, apply & exit.

Now, do you have DVD Decrypter installed? If so, in winecfg again, under Applications tab, you might want to "add application" adding DVD Decrypter's .exe, and specify Windows NT 4 version. Sometimes people have had better luck using that setting. Open DVD Decrypter now. In its options, besides making sure it's not checking for updates, under the I/O tab, choose "SPTI - Microsoft" interface. You should now be good to go.

Mind I agree with the above advice, that you explore native Linux alternatives; for one thing it avoids the complicated WINE situation and another DVD Decrypter can't handle some new titles and won't be updated. k9copy has a lot of happy users for one example.

Luck, and remember, if you have questions, ask, search, ask, search, ask and search, and you'll get it :)

---

