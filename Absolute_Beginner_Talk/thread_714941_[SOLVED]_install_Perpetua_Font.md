---
title: "[SOLVED] install Perpetua Font"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Ohwii on 2008-03-04
Hi Guys, 

well I just looked up a whole bunch of "fond adding"-threads on this page and other blogs but it does not seem to work properly. 

Well I have the "perpetua" font, which I tried to install. However it does not work.

I went to 

```
fonts:///
```

copy and pasted it( as root) . 

did not work 

 and there were these other threads with the terminal and adding the font to "usr/*/myfonts" folder etc. 
did not work.

I would be very glad if someone could tell me what to do. So I can use the "perpetua" in OpenOffice.:)

Cheers,

Ohwii

PS: due to legal issues I am not sure whether it is allowed to post the fonts.	:confused: but if you need it will add them.

---

### Post by jordanmthomas on 2008-03-04
Here's how **I** install fonts.
1.  If you don't already have a folder in your home directory called .fonts, create it
```
mkdir ~/.fonts
```
2.  Put the fonts in this folder.  (Ctrl - H in nautilus shows hidden folders)
3.  Run this in a terminal
```
sudo fc-cache -f
```
4.  open up the program I want to use the font in and use it.

This works for me every time, whereas using fonts:/// has never worked reliably or at all for that matter.
What format is this font (.FON, .TTF, etc?) 
It's possible that it's installed but OpenOffice doesn't support its type for some reason.

---

### Post by Ohwii on 2008-03-04
First of all thanks for the quick help Mr. Thomas - I assume. 
Coming now to the question :
> **jordanmthomas said:**
> 
What format is this font (.FON, .TTF, etc?) 
very simple it is the *.TTF format 

and your final remark
> **jordanmthomas said:**
> 
It's possible that it's installed but OpenOffice doesn't support its type for some reason.

Well this is a real bummer. I might have to check the Open Office forum then. 

again thanks for the fast help. I tried it and ....

WHAM! NO WAY JOSÉ! 

It work like a charm. 

One final think can you tell me what the last command does? or why it now works? (if you have time ):)

Cheers

Oh - Wii

PS tiped the answer while testing it.

---

### Post by jordanmthomas on 2008-03-04
The last command regenerates the cache for all the fonts, effectively making them available for applications.

Basically, it scans all the directories fonts are supposed to be in (defined in /etc/X11/xorg.conf and your own .fonts directory is also included)

---

### Post by Ohwii on 2008-03-04
thanks a lot Mr. Thomas. 

but there is one final question. after that one I will stop asking ( for a little bit;) ) 

Well how do I add PFB- fonts to the fonts? 

this is the last question- for now.

thanks in advance. 

Cheers,

Oh  Wii

---

### Post by jordanmthomas on 2008-03-04
It's done the same way.  Just drop the fonts in your .fonts directory and run **sudo fc-cache -f** again.

You'll need to restart openoffice before it will know about the new fonts though.

---

