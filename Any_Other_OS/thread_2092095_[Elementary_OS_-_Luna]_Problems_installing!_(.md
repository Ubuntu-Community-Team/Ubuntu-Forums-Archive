---
title: "[Elementary OS - Luna] Problems installing! :("
date: 2012-12-06
forum: Any Other OS
---

### Post by DS McGuire on 2012-12-06
Hey, right I have made a live USB stick of Elementary OS because I want to try it out, when I try to run it live I get the option screen asking me weather I want install it, use without installing, boot from first hard disk, check for errors etc... Whatever I select nothing happens, I little cursor thing blinks in the bottom left but nothing happens.

I tried this on a Linux Min 13 desktop, that is all it runs. 

I also have a HP laptop that is a year old running windows 7, I try it on that (the same live USB stick) and it works fine, it gets past that screen and boots the OS.


Any reason why I can't get it on my first (desktop) PC?

---

### Post by Chdslv on 2012-12-06
Check md5sum!

---

### Post by DS McGuire on 2012-12-06
> **Chdslv said:**
> Check md5sum!


What the hell is that? I have googled it... Still no idea.

---

### Post by BlinkinCat on 2012-12-06
Hi, -

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Cheers.

---

### Post by BlinkinCat on 2012-12-06
Don't know if this helps - :P

[https://launchpad.net/elementaryos/+milestone/luna-wallpapers](https://launchpad.net/elementaryos/+milestone/luna-wallpapers)

Cheers,

---

### Post by Chdslv on 2012-12-06
> **DS McGuire said:**
> What the hell is that? I have googled it... Still no idea.

With the "what the hell" business, I shouldn't reply to you, but as there maybe lot of new guys around here, and for their sake, I am replying.

Once, you download a iso, you must check whether you've got everything correct, so you have to check the md5sum. That is given in any self-respecting developer in his/her web site. If the md5sum of the downloaded iso doesn't match, you can't boot it. Period!

You navigate to the folder, where your iso is and in the Terminal write > md5sum the-file-of-the-downloaded-isoand check it with the one given in the download page.

md5: 10fb147bb93ec13ff4b683a24bcf43b0 for the 32 bit
md5: 9a15eb16a7dc66b35726fc4c94b78a2f  for the 64 bit

*snip*

---

### Post by NormanFLinux on 2012-12-07
A bad download can lead to installation errors.

If you have an already existing eos installation, daily updates will bring it to the beta version.

Hope this helps.

---

