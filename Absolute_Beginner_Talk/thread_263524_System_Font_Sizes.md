---
title: "System Font Sizes"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by lemonsCC on 2006-09-23
Before I kill my the small things "children" that destroy all they touch can someone help me restore the original fonts and sizes system wide?  I am running XFCE Ubuntu 6.06

Here is what the system looks like:
[IMG]http://img79.imageshack.us/img79/3729/untitledzi7.png[/IMG]

There are 3 or 4 different sizes of font...ranging from 5 (maybe smaller) to looks like 12 or 14.  Please help!

Thanks

---

### Post by nts on 2006-09-23
System -> Settings -> Fonts

---

### Post by nts on 2006-09-23
[http://72.14.221.104/search?q=cache:S0WT0siyOZwJ:www.pcmech.com/show/os/943/+ubuntu+change+system+font+size&hl=en&gl=uk&ct=clnk&cd=9&client=firefox-a](http://72.14.221.104/search?q=cache:S0WT0siyOZwJ:www.pcmech.com/show/os/943/+ubuntu+change+system+font+size&hl=en&gl=uk&ct=clnk&cd=9&client=firefox-a)

see that site too for looooaaaads of info :D

---

### Post by lemonsCC on 2006-09-23
It is not a font problem it is a XFCE problem... I guess my computer was slow to get it here is the solution:

> From [http://xubuntu.wordpress.com/](http://xubuntu.wordpress.com/)

1) Edit the file ~/.config/xfce4/Xft.xrdb:

mousepad ~/.config/xfce4/Xft.xrdb

And paste in:

Xft.dpi: 96

Save and exit.

2) Edit /etc/X11/xorg.conf:

sudo mousepad /etc/X11/xorg.conf


And paste in under Section "Files" (if it&#8217;s not there alread):

FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/100dpi"

---

### Post by nts on 2006-09-23
Okey doke, good of you to post the solution for others to see :)

---

### Post by lemonsCC on 2006-09-23
i try...i searched the forums but found nothing, and by some random chance i stumbled upon the solution, I was searching for something completely unrelated.

BTW:  is it just me or is this forums search engine horrible?

---

### Post by nts on 2006-09-23
i've never tried it to be honest - i just search for stuff with Google; if i don't get a solution - i ask here.

Although when i click the button 'check to see if its already posted' (or words to that effect) - it has never found anything - so i'm either posting questions that haven't been asked or the search feature is not particularly effective.

---

