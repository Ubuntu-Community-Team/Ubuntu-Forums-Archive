---
title: "Need more space for upgrade"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-02-11
I'm trying to upgrade to Edgy on my home compootor, but it keeps aborting, saying that there isn't enough space. I thought I had prepared for this, but evidently not. What must I do?

---

### Post by RomeReactor on 2007-02-11
The only thing i can think of at the moment is to purge the unnecessary installers Apt might have left in your HD. So

```
sudo apt-get autoclean
```

to clean up on those .deb files left just wasting space. See if that makes any difference. Also, clean the Firefox cache (though it's unlikely you'll get more than 100 MB back from it)...

---

### Post by kerry_s on 2007-02-11
You can also delete the doc and man files to gain alot of space.

/usr/share/doc
/usr/share/man

---

### Post by ricardisimo on 2007-02-11
There's something I just don't understand, though: when I originally installed Dapper, I wanted it to have access to the entire drive. Is there any way for me to reclaim those "Unallocated" 6.42 Gigs? complete reinstall the only option? Thanks.

---

### Post by ricardisimo on 2007-02-13
So here's the story: master drive is Win XP Pro, the slave is Ubuntu Dapper (pictured above). I want to try out Feisty, and completely overwrite Dapper, but the installation disk only seems to give me sizing options on the master, not on the slave. Is it going to work around the Dapper partition or overwrite it? Will it leave the master drive completely alone so that my wife won't divorce me? Thanks.

---

### Post by RomeReactor on 2007-02-13
Hi. Try disabling your Master HD (the one with win xp) from the motherboard's BIOS. As far as i know, Ubuntu won't touch it that way. Not sure if this is what you're looking for, though.

---

### Post by ricardisimo on 2007-02-13
It might be exactly what I'm looking for, especially if I can re-attach it later. Do you have a good "How-to" towards which you can point me? Thanks.

---

### Post by RomeReactor on 2007-02-13
Well, specific methods for accessing BIOS in motherboards vary from brand to brand, but usually it's done by pressing **DEL** (the delete button that's near "end", "page down", "insert", etc.) when, after turning on the computer, a message appears saying something along the lines of **Press DEL to access settings** or something similar, and the key to press may be **ESC** instead, or maybe another one (though it's usually one of those two), or the message may not even appear. Please refer to your motherboard manual for more accurate instructions, or visit the website of your motherboard's manufacturer (if you know which one it is), or ask a friend if they know how to access the BIOS in your particular motherboard. Sorry i can't be more specific, but it really is about knowing what motherboard you have and how to to access it's settings.

When in doubt, you can try with the above mentioned methods and maybe one will work. And, as far as i know, disabling a HD in BIOS poses no problem to your system and you can easily re-enable it entering BIOS again. And as far as how to disable it once you're inside the BIOS settings, it shouldn't be too difficult to do, as most modern motherboards' usage is pretty much self-explanatory (**just be careful not to move any other settings while you're there**).

---

