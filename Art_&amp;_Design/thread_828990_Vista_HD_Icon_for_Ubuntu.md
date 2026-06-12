---
title: "Vista HD Icon for Ubuntu?"
date: 2008-06-14
forum: Art &amp; Design
---

### Post by Seablue on 2008-06-14
Hi all,

I have been looking at My Computer, where I have noticed that there are these nice icons. Vista has a very nice one, while the rest don't. (Note: If you don't know what I'm talking about, look at the icons [here](http://img216.imageshack.us/my.php?image=desk3py5.jpg).
Now, does anyone know where i can get a Vista Icon that has a Linux Penguin instead of the Vista icon, or can anyone make one?

---

### Post by Anzan on 2008-06-14
Why don't you try the icon sets on gnome-look or kde-look and so on? There are a great many excellent sets availablr.

---

### Post by Seablue on 2008-06-14
That's for Linux, not Windows.

---

### Post by BreakDecks on 2008-06-16
1. Create a custom icon using Photoshop or The GIMP.
2. Save the icon as a .ico file
3. Place the file into the root of your Ubuntu ext3 IFS drive with the filename "autorun.ico".
4. Create a file "autorun.inf" in the root of your Ubuntu ext3 IFS drive containing the following:

```

[autorun]
icon=autorun.ico

```

Your drive should now display your custom icon in place of the default hard drive icon.

I do not know where you could get a pre-made ubuntu icon designed to match the Windows Vista default device icons, so you will likely have to make one yourself.

Also, I cannot guarantee that adding files to the root of your ext3 IFS drive will not do damage to your Ubuntu installation.

---

### Post by MadsRH on 2008-06-16
Something like this would be great :)

[ATTACH]74282[/ATTACH]

---

### Post by Seablue on 2008-06-16
> **MadsRH said:**
> Something like this would be great :)

[ATTACH]74282[/ATTACH]

Thats nice. However, im looking for an icon to be displayed on Windows.

---

### Post by steveneddy on 2008-06-16
> **Seablue said:**
> Thats nice. However, im looking for an icon to be displayed on Windows.

Have you tried, um, a Windows forum?

I wonder what Google has for you?

Tried a search yet?

---

### Post by steveneddy on 2008-06-16
Maybe this?

---

### Post by steveneddy on 2008-06-16
or this...

[IMG]http://farm2.static.flickr.com/1054/668166403_4e26fee5b1.jpg?v=0[/IMG]

---

### Post by Seablue on 2008-06-16
> **steveneddy said:**
> Have you tried, um, a Windows forum?

I wonder what Google has for you?

Tried a search yet?
Yes to everything but Windows forum. Asked here because i'm looking for a Ubuntu icon, and i hate when Windows says "Ubuntu?" Considering i'm a huge computer fan, it may be time to join a vista forum....

> **steveneddy said:**
> Maybe this?
No Ubuntu icon, im afraid.

---

### Post by steveneddy on 2008-06-16
gnome-look.org then

---

### Post by John.Michael.Kane on 2008-06-16
Have you tried here.
[hd icons]("http://search.deviantart.com/?section=browse&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5&q=hd+icons")

[BD, HD DVD,Icons]("http://generalbrazil69.deviantart.com/art/BD-HD-DVD-RTM-Calendar-Icons-42778630")

[Icons]("http://webtrance.deviantart.com/art/Q-s-Vista-RC1-Bin-Icons-39174557")

Note: You may have to modify the icons to work on Ubuntu.

---

