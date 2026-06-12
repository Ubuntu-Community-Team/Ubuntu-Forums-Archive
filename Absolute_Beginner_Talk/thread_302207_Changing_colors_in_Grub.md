---
title: "Changing colors in Grub"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by clucas on 2006-11-18
I've been messing with the Grub menu and have created splashscreens that work great. Now my problem is that the image has a dark background and I can hardly see the highlighted line to show what to boot. How can I change the font colors as well as the highlight line color? In the menu.lst file there is a color line where I changed the colors but I see no difference. I guess I don't understand what that color line is for.

---

### Post by Tomosaur on 2006-11-18
There are specific colours which Grub allows you to use, you should be able to find which ones are allowed via google.

However, it's worth noting that if you try to use a splash image AND different colours, then you may find that the grub menu begins to look odd. It will work fine, but you may not, for example, be able to see which line is highlighted/whatever.

To get the colours working in the first place, you need to remove the # from the beginning of the prettycolours line.

The link in my sig will allow you to play with the various colours available to you, if you feel like giving it a go.

---

### Post by clucas on 2006-11-18
You're right about the highlight line. That's what I was hoping to be able to change.

I'll mess with it some more.

I just might have to use your GrubED-GUI!

Thanks.

---

