---
title: "Change GRUB appearance"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-19
If I understand correctly, you can add a picture to the background of the GRUB bootloader. If so, in Feisty, how would I go about doing this.... ?

---

### Post by oilchangeguy on 2007-06-19
> **ts51 said:**
> If I understand correctly, you can add a picture to the background of the GRUB bootloader. If so, in Feisty, how would I go about doing this.... ?

why would this possibly matter? grub is only seen for a few seconds. if you can't look at it for that long, turn your head.

---

### Post by Gwasanaethau on 2007-06-19
There's a fairly simple way of doing it. First of all, you need to get a suitable picture. It must be 640 × 480 with only 14 colours (you can use the GIMP to change a picture you already have if that's the case). As you're saving it, you need to save it in '.xpm' format. Then, you need to compress it with 'Gzip' (this you can do by right clicking on your image, and then going to 'Create Archive' and then clicking on '.gz' from the pull-down menu. Now your image is ready.

From the terminal, enter:
```
cd /boot/grub
sudo ln -s [YOURIMAGE] splash.xpm.gz
sudo update-grub
```

You can also change the colour of the text and selection bar, but unfortunately I don't know how to do that.

Hope that helps!

---

### Post by KIAaze on 2007-06-19
This might also interest you:
[Howto : GfxBoot ( Grub like suse )]("http://ubuntuforums.org/showthread.php?t=208855")

---

### Post by ts51 on 2007-06-19
> **Gwasanaethau said:**
> There's a fairly simple way of doing it. First of all, you need to get a suitable picture. It must be 640 × 480 with only 14 colours (you can use the GIMP to change a picture you already have if that's the case). As you're saving it, you need to save it in '.xpm' format. Then, you need to compress it with 'Gzip' (this you can do by right clicking on your image, and then going to 'Create Archive' and then clicking on '.gz' from the pull-down menu. Now your image is ready.

From the terminal, enter:
```
cd /boot/grub
sudo ln -s [YOURIMAGE] splash.xpm.gz
sudo update-grub
```You can also change the colour of the text and selection bar, but unfortunately I don't know how to do that.

Hope that helps!

OK... I will try this... 

BTW: I totally agree that it's not important, but, I guess I just like to tinker! :mrgreen:

---

### Post by coffeecat on 2007-06-19
> **oilchangeguy said:**
> why would this possibly matter? grub is only seen for a few seconds. if you can't look at it for that long, turn your head.

Why make such an unhelpful post? The OP wants a nice grub splash screen and I'm glad the two subsequent posters were able to help him with constructive advice.

**Edit: ts51**, [This link](http://ruslug.rutgers.edu/~mcgrof/grub-images/) is old but still useful and has links in it to a few ready-made grub images. If I come across any more I'll post them.

---

### Post by ts51 on 2007-06-19
> **KIAaze said:**
> This might also interest you:
[Howto : GfxBoot ( Grub like suse )]("http://ubuntuforums.org/showthread.php?t=208855")

How would I boot if this went terribly wrong? Just curious... Wouldn't want to totally kill my system over a theme, you know?

---

### Post by KIAaze on 2007-06-19
Mmh, simply back up the MBR and the menu.lst file? ;)

Here's how ("hdx" being the partition where your MBR is):
_1)Back up:_
```
sudo cp /etc/boot/menu.lst /etc/boot/menu.lst.bkp
dd if=/dev/hdx of=MBR-backup bs=512 count=1

```
_2)Restore:_
```
dd if=MBR-backup of=/dev/hdx bs=512 count=1
sudo cp /etc/boot/menu.lst.bkp /etc/boot/menu.lst

```
(You might need to use the Ubuntu LiveCD for this of course.)

[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/")
[http://en.wikipedia.org/wiki/Mbr#Unix-like_systems]("http://en.wikipedia.org/wiki/Mbr#Unix-like_systems")

**Note: I have never tried it personally, but I think it should be enough to be able to go back in case of problems. ^^'**

---

