---
title: "Mac Hd reformatted to fat32 problem"
date: 2010-07-06
forum: Apple Hardware Users
---

### Post by Colonel Dragoon on 2010-07-06
Hey community,

I'll try to explain my problem as best as I could. but if you're not interested in the history, you can skip through to after the horizontal line.

**The History** :

I installed Ubuntu on my intel-based 5,5 macbook pro 13'', with rEFIt installed on the mac hd, everything worked fine and I've been using Ubuntu for a while now, as in a month or more, but you see I only partitioned my 150GB mac hd to 7gb to install ubuntu on, but after downloading all the software and media, of course that space is starting to look a little bit small, anyway I didn't notice that until actually Ubuntu started to act up, as in it's being too slow and unresponsive , well that's what I should expect when I'm severely running out of space right.
anyway the space I had left was only a few megabytes, so what I thought would solve this, is actually using the Mac HD, since I have 50gb or 90gb of free space, but actually I can't write on my mac hd, so after research I found out that Ubuntu can only read hfs+ but can't write unless it's fat32 or linuxswap or other formats, so to my unexperienced decision, I happily decided to simply reformat my mac HD from hfs+ to fat32 using Gparted, BIG MISTAKE, once I did it, which happened in 4 seconds mind you, I restarted my macbook, and to my unpredicted surprise, where rEFIt should load, nothing did, not even my MAC OS, just a blue screen was there...of course I panicked, I mean nothing loaded, how am I going to be able to even fix this if nothing as in not even Bios is there...but after a while Ubuntu or Grub just loaded, so I thought good, at least I have an OS to post my problem using, I tried deleting some media to free up space so I could at lease open a web page.
_______________________________________________________________________
[B]
The Problem :[/B]

so my problem is, is there a way to return my Mac HD after reformatting it to fat32, I tried to format it back to hfs+ but for some reason Gparted can't do that, and now  I can't access anything on my Mac, I find it hard to believe that around 100gb of data could be deleted in a mere 4 seconds, but if it did, at least I want my mac and OS back.

**The Thanks :**

thanks in advance.

---

### Post by linuxopjemac on 2010-07-06
You should always be able to boot from an OSX installation CD and format your drive back to HFS+. Hold option or "c" during boot with the OSX CD.

---

### Post by Colonel Dragoon on 2010-07-06
I see, thanks
and would my data still be there after I reformat it  hfs+ or should I kiss it goodbye?

---

### Post by linuxopjemac on 2010-07-06
If you format it it is gone....

---

### Post by Colonel Dragoon on 2010-07-06
oh well...thanks for your guidance,
I'll silently cry under the moon for my beloved data...

---

### Post by kmsalex on 2010-07-06
[http://www.piriform.com/recuva](http://www.piriform.com/recuva)
Is there a similar application for Linux? 
I've use this several time in windows when i accidentally delete something.

Edit: I've got it running under wine but im not sour how well it will work for a formated partition. It won't convert it back to hfs+ but it might get some of your pic's and doc's back, give it a try in wine.

---

### Post by Colonel Dragoon on 2010-07-06
> **kmsalex said:**
> [http://www.piriform.com/recuva](http://www.piriform.com/recuva)
Is there a similar application for Linux? 
I've use this several time in windows when i accidentally delete something.

Edit: I've got it running under wine but im not sour how well it will work for a formated partition. It won't convert it back to hfs+ but it might get some of your pic's and doc's back, give it a try in wine.
I'd love to try and actually get my data back but if what gparted says is true then maybe the data is truly lost, I wonder how is that possible in 4 seconds though.
I've included an attachment for reference.

---

### Post by dtfinch on 2010-07-06
If you have an extra hard drive lying around, you might be able recover a small handful of common file types.

[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image) (I haven't needed to try any of these)

---

