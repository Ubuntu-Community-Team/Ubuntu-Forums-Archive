---
title: "how to enable alt-plus. for example alt + 0128 = euro sign?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by joris1977 on 2006-06-10
I've been using these codes (alt + combination of numbers on the num lock path) for special characters since word perfect 5.1 and for me it's the fastest way for typing. I know these codes could work in Openoffice, because i used Openoffice with windows 2000 and then it was working by default. How do I enable this for Ubuntu?

Any help would be appreciated, becuase i couldn't find anything in the forums

---

### Post by mostwanted on 2006-06-10
System -> Preferences -> Keyboard

The third tab.

I have some problems with it myself, but that's because I use Compiz which isn't exactly stable yet.

---

### Post by Gustav on 2006-06-10
You can use ctrl+shift+number to get special caracters.

The number should be in hexadecimal form though. (so now it's ctrl+shift+80 for &#8364; (128 in decimal form is 80 in hex))

(strange... it doesn't look as my regular euro-symbol that I get by typing my &#8364;-key (ctrl-shift-80: &#8364;, AltGr-e: &#8364;))

edit: in the result they look the same, but when I edited the text the ctrl-shift-80 version were much thinner and uglier

---

### Post by dvarsam on 2006-06-10
To print the "€" sign, type:
> Ctrl+Shift+20ac

Have Fun!

---

### Post by joris1977 on 2006-06-10
Thanks for all the fast help, didn't expect it to come so fast. However it didn't work. 

Mostwanted: what do i need to enable in the third tab: there's so many options and it tried several but didn't seem to workout by now... I'm not too smart yet with ubuntu, that's why i posted it in the beginners forum.

When I try ctrl + shift + 80 in openoffice nothing happens in open office it just beeps....

quote from Gustav: The number should be in hexadecimal form though. (so now it's ctrl+shift+80 for € (128 in decimal form is 80 in hex))

and sorry i'm a real noob ,but hexadecimal  goes far beyond my technical/intellectual skills... i'll try to google it when crtl + shift + 80 works..  (Ubuntu is a very easy distro, so that attracks simple users like me :D)

---

### Post by CronoDekar on 2006-06-10
Depending on which ones you want to use, it's possible to set up certain "shortcuts" in System > Keyboard.  In Layout Options there's an "Adding the EuroSign to certain keys options", which when you're holding down a "third level chooser" (a key which you decide on in the same tab) along with E, 5, or 2, you get a &#8364;

Also in the tab there's a "Compose key" option, which makes it so when you hold down the Compose key lets you can "combine" certain keypresses to get special characters.  Like when I hold down my compose key (which I set up as Right Win) and press e and then ', I get é, and è from e + `.  There's a list of them in /usr/X11R6/lib/X11/locale/, then choose the one appropriate for your keyboard, and open the file Compose.  Now I don't know WHICH one it is, but I find that most of them that I try in the en_US and iso8859-1 ones work for me, though not all of them.

(Now that I try it though it doesn't seem Compose works within in Opera, though they should work in other aps.)

Though of course if you want other special characters besides these... then you'll probably have to use the hex method :)

---

### Post by joris1977 on 2006-06-23
The crtl + shift + 80 still doesn't work for me. Maybe someone can explain what settings i need to make to get this working, because i'm getting nowhere. 

In this thread [http://www.oooforum.org/forum/viewtopic.phtml?t=34775&highlight=compose+keys](http://www.oooforum.org/forum/viewtopic.phtml?t=34775&highlight=compose+keys) 

from the open office forum if found out there is no alt + key support for openoffice under linux. But there is something mentioned which is called altkeyhandler. 

Although it seems to be discouraged in the forum post. Is there anyone who has experience with this. I am not he only one interested or having this alt keys enabled: see this post: 

[http://www.ubuntuforums.org/showthread.php?t=159499&highlight=AltKeyHandler](http://www.ubuntuforums.org/showthread.php?t=159499&highlight=AltKeyHandler)

with no asnwer... maybe now?

---

