---
title: "How to get icons and GUI w/Blackbox or Enlightenment etc.."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-05-09
I decided to mess around, and check out Enlightenment the other day, but got rid of it because I didn't feel as adventurous after not having any icons or menu system with which to navigate around in. 

Today, I felt like messing about agian, so installed Blackbox through Synaptic. It's the same story pretty much, no icons, no menu's, but I obviously pulled up exterm, and just typed in firefox hoping it would open it, and obviously, it did.....

So how does one go about getting icons or shortcuts to programs, and all the rest of the things which I was used to seeing on my Gnome desktop ? 

I'm also a bit confused about the differences in how I'm supposed to view (as in comprehend) a Window Manager, compared to a desktop environment ?  Gnome AFAIK, is a DE, while Blackbox is a WM, right ? So then should Blackbox not just operate OVER Gnome ? See what I mean about being confused ?

I'd love a link to some info about this stuff, or just the knowledge which you guys posess would help me out just as well. 

I do like Gnome a lot, but sometimes I feel like I'd like faster response times, less glitz etc... Also, I'm thinking about either reinstalling Ubuntu (probably latest version, update all the way from 6.06) or perhaps trying a different distro for a bit. I must have about 10 live CD's laying around, which I've gotten from looking at distrowatch....  

It is Spring after all, and there's nothing better sometimes than a good Spring cleaning !

---

### Post by Terl on 2007-05-09
Here is a good start for you -->  [Blackbox]("http://blackboxwm.sourceforge.net/")

Enlightenment --> [Enlightenment home]("http://www.enlightenment.org/")

---

### Post by Sweet Spot on 2007-05-09
Also, why is it that when I open up Nautilus (from xterm), I halfway get the desktop back, that I was using w/Gnome ? (wallpaper, some items that I had placed there like ISO files, but no other icons than the 'computer' and trash icons)  Is this normal ? Because I don't really understand the behavior here. I just assumed that when I typed Nautilus into xterm that only Nautilus would open, leaving the plain, blue background which is standard for blackbox ?

---

### Post by Terl on 2007-05-09
You are still using GDM as a desktop manager while using Blackbox as a windows manager.  Here is a quickie link (googled desktop manager vs winows manager) [Desktop Manager vs Windows Manager]("http://community.netscape.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=127829&redirCnt=1")

---

### Post by AnRa on 2007-05-09
> **Sweet Spot said:**
> Also, why is it that when I open up Nautilus (from xterm), I halfway get the desktop back, that I was using w/Gnome ? (wallpaper, some items that I had placed there like ISO files, but no other icons than the 'computer' and trash icons)  Is this normal ? Because I don't really understand the behavior here. I just assumed that when I typed Nautilus into xterm that only Nautilus would open, leaving the plain, blue background which is standard for blackbox ?

Try this:

[FONT="Courier New"]nautilus --no-desktop[/FONT]

;)

---

### Post by Sweet Spot on 2007-05-09
Guess I'll have to do a lot more research before trying to mess with other WM's. I just don't get the concept I guess. Thanks for the quick link, I suppose I should have googled it myself but just thought there would be readily available info somewhere in the wiki etc;

---

### Post by Sweet Spot on 2007-05-09
> **AnRa said:**
> Try this:

[FONT=Courier New]nautilus --no-desktop[/FONT]

;)

I'm back in the GDM now, but thanks.  I'd still like to know the why's of it though too.

---

