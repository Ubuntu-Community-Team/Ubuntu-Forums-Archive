---
title: "Looking for an Ubuntu &quot;Vista looking&quot; Menu Orb"
date: 2007-07-23
forum: Art &amp; Design
---

### Post by Dev0205 on 2007-07-23
A month or so back I saw somebody post a main-menu Ubuntu icon. It was designed a lot like the new Vista Orb and I can't seem to track it down. Any help would be appreciated.

---

### Post by Paul820 on 2007-07-23
I made you one, hope you like it. If you want the .xcf let me know and i'll post it. :)

---

### Post by Dev0205 on 2007-07-23
Thanks Paul! That will work perfectly! :)

---

### Post by ryanVickers on 2007-07-24
The little logo beside "applications"; where does it get that image from (so I can change it :))?

---

### Post by cdenning on 2007-10-25
Has this Orb been posted?  Is it compatible with Gusty and Compiz?

---

### Post by smartboyathome on 2007-10-28
I made an svg of an orb in Inkscape which goes good with the human theme. It is attached.

---

### Post by Jose Catre-Vandis on 2007-10-28
> **ryanVickers said:**
> The little logo beside "applications"; where does it get that image from (so I can change it :))?

Need to know this so we can use your great icon :)

---

### Post by Crafty Kisses on 2007-10-28
> **Paul820 said:**
> I made you one, hope you like it. If you want the .xcf let me know and i'll post it. :)

That looks sick!

---

### Post by smartboyathome on 2007-10-28
> **Jose Catre-Vandis said:**
> Need to know this so we can use your great icon :)

You need to change the distributor logo in the icon theme you are using. You can find your icon themes in ~/.icons/ and /usr/share/icons/

---

### Post by Baby Boy on 2007-10-28
> **smartboyathome said:**
> You need to change the distributor logo in the icon theme you are using. You can find your icon themes in ~/.icons/ and /usr/share/icons/
Where under /usr/share/icons can you find the distributor logo (in what folder)?

---

### Post by smartboyathome on 2007-10-28
Which icon theme are you using? If you are using the default, then it would be under the folder human.

---

### Post by Baby Boy on 2007-10-29
Yeah, that's what I assumed, but there are plenty more folders under *Human* folder (*8x8*, *12x12*, *16x16*,...) each with several more inside. Can you give me some more feedback?

---

### Post by AJB2K3 on 2007-10-29
This was posted in another thread

> 
Replace this
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
using
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.old
or
sudo mv /path/to/new/icon /usr/share/icons/hicolor/48x48/apps/distributor-logo.png


---

### Post by Baby Boy on 2007-10-29
Thanks for trying to help, I appreciate it, but not even after changing the distributor-logo, gnome-main-menu, start-here and every other ubuntu logo icon that could be related to the one in the main menu in every single folder in Human, the icon still hasn't changed. I can see all the icons replaced by the one from this thread, but it's like it doesn't matter.

---

### Post by smartboyathome on 2007-10-29
> **Baby Boy said:**
> Thanks for trying to help, I appreciate it, but not even after changing the distributor-logo, gnome-main-menu, start-here and every other ubuntu logo icon that could be related to the one in the main menu in every single folder in Human, the icon still hasn't changed. I can see all the icons replaced by the one from this thread, but it's like it doesn't matter.

hm... try just doing it in the scalable section for the svg logo I made, and try resizing it to the correct size for each size folder.

---

### Post by Baby Boy on 2007-10-29
> **smartboyathome said:**
> hm... try just doing it in the scalable section for the svg logo I made, and try resizing it to the correct size for each size folder.
I've tried replacing the ones in the scalable section too, which BTW were about the same size as the one you created, but to no avail. I'll try resizing, but it will take some time. The only thing that got replaced as much as I've noticed so far is the *About Ubuntu* icon under *System*.

---

### Post by smartboyathome on 2007-10-29
> **Baby Boy said:**
> I've tried replacing the ones in the scalable section too, which BTW were about the same size as the one you created, but to no avail. I'll try resizing, but it will take some time. The only thing that got replaced as much as I've noticed so far is the *About Ubuntu* icon under *System*.

One other thing I can think of why the icon isn't changing: perhaps gnome-panel needs to be "refreshed"? To do that, use this in alt-f2:
gksudo killall gnome-panel
It should turn it off, and then the panels should come back up again.

---

### Post by #Reistlehr- on 2007-10-29
if you are using a custom theme, it will be usually.....

/home/$USER/.icons/ theme name here/48x48/places/start-here.png usually.

Edit::: 
/home/$USER/.icons/ theme name here/24x24/places/start-here.png usually.

It was the 24x24 directory, my bad. Also, you can replace it for regular themes too, /usr/share/icons/themename

---

### Post by Baby Boy on 2007-10-29
<Sigh> ...there is no solution to this... :(

I've resized the images and replaced distributor-logo, gnome-main-menu and start-here in the 24x24 and 48x48 folders under places (of course the downloaded images were resized to 24x24 and 48x48 respectably).

And no, nothing changes after restarting the panel with 

> gksudo killall gnome-panel

---

### Post by Paul820 on 2007-10-29
Try this one, [http://www.pendrivelinux.com/2007/10/19/changing-the-ubuntu-start-menu-panel-icon/]("http://www.pendrivelinux.com/2007/10/19/changing-the-ubuntu-start-menu-panel-icon/")

---

### Post by Baby Boy on 2007-10-29
Paul, I wish you'd walked into my life *before* I had to go through all that trouble...](*,) Thanks.

It was all about rebuilding the icon cache.

---

### Post by Paul820 on 2007-10-29
Glad to help :) Your screenshot is looking good :guitar:

---

### Post by Crafty Kisses on 2007-10-29
Make the Ubuntu logo a little lighter. :)

---

### Post by smartboyathome on 2007-10-30
> **Codename said:**
> Make the Ubuntu logo a little lighter. :)

j/w, was that to me?

---

### Post by (hed) p.e. on 2009-07-12
looks sick

---

### Post by SonnHalter on 2009-07-12
Here's one I made if anyone wants it. public domain I guess. 

this thread kinda wanted me to make one ^^

---

