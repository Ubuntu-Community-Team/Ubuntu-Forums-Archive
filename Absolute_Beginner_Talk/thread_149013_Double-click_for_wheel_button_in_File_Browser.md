---
title: "Double-click for wheel button in File Browser"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Ancalagon on 2006-03-23
I've been trying to get the wheel button on my USB Intellimouse to function as a double-left-mouse-click in the File Browser and can't seem to get it.

I followed steps 1 through 4-1 here (btw- I installed imwheel_1.0.0pre12-2_i386.deb) :

[https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons](https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons)

but in Step 3 I entered:

".*"
None, Button2, Button1, 2

This didn't work, so I found:

[http://dotnet.org.za/matt/articles/39097.aspx](http://dotnet.org.za/matt/articles/39097.aspx)

I didn't create a .imwheelrc in my /home/username dir b/c it already existed in my /etc/X11/imwheel dir.

I did set IMWHEEL_START=1 in my /etc/X11/imwheel/startup.conf file.

This didn't change anything.

I'm sure some of you experts can figure this out in a sec, but I can't.  

Thanks much

---

### Post by Ancalagon on 2006-03-24
Well, I'm pretty convinced now that the wheel button cannot be assigned to anything other than Button1 in File Browser or ctrl_L | Button1 in firefox.

I ended up putting in my xorg.conf:

"Buttons" 	"9"
"ZAxisMapping"	"6 7 8 9"

and putting in my 57xmodmap:

"pointer = 1 2 3 8 9 4 5 6 7"

Then I settled for Thumb1 as 'go back one page' and Thumb2 as double-click with:

".*"
,Thumb2,Button1,2
,Thumb1, Alt_L|KP_Left

I'd like to be proven wrong, but this seems like the next best solution to the wheel button as a double-click.

---

### Post by trent dillman on 2006-03-24
Um, the wheel click is used (usually) for pasting text.

Highlight some text in Firefox (copy), then click your wheel in gedit (paste).

Of course, if your mouse has 9 buttons... :-P

---

