---
title: "Getting extra buttons on logitech keyboard to work..."
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by diggs on 2006-01-14
[http://www.logitech.com/index.cfm/downloads/software/CA/EN,CRID=1796,contentid=6997](http://www.logitech.com/index.cfm/downloads/software/CA/EN,CRID=1796,contentid=6997)

That's the mouse and keyboard there, works fine. But I want to use all them fancy buttons! ANyone? Thanks :)

---

### Post by JimmyJazz on 2006-01-14
System>Preference>Keyboard Shortcuts

try them out there and see what happens

---

### Post by Madpilot on 2006-01-14
[https://wiki.ubuntu.com/MultimediaKeys](https://wiki.ubuntu.com/MultimediaKeys) as well.

---

### Post by bscbrit on 2006-01-14
If the advice given so far does not meet your needs (it should!) then you could also try the following:

If you enter 'xev' at the command line, you can see masses of information regarding each key that you press.  Included is the keycode of the key.

You can create a file in your home directory (e.g. ~/.Xmodmap) and edit it to contain the key mappings that you would like (e.g. keycode 161=F13).  Running xmodmap ~/.Xmodmap) will set the key mappings.

Acknowledgment:  Many thanks to LinuxFormat LXF76 Feb 2006, for providing the succinct description that I have plagiarised above.  I'll probably have my subscription cancelled because of copyright issues! /Acknowledgment.

---

### Post by rizzyc on 2006-01-14
I just installed Keytouch and installed my correct keyboard, everything is running great except I want my a,b,c,d buttons to coincide with Desktop1,2,3,4 and I installed the special plugin that allows that to happen... but for some reason when i press those buttons nothing happens

I have a logitech media keyboard, i have the function button on so (F1 etc. get disable and the special options load) hmm, ok interestingly enough my copy/paste buttons do work in the F mode,  and so does the print/save functions. The word/powerpoitn/excel buttons dont open the appropriate programs.. so in short my word (f2) excel (f3) powerpoint (f4) and a,b,c,d buttons are not doing anything

---

### Post by bscbrit on 2006-01-14
I'd love to try and help - but what is 'Keytouch'?  I cannot find it in my repositories.  And how can the 'Word' , 'Excel' and 'Powerpoint' buttons do anything in Linux?  Do you want them to point to linux equivalents, perhaps the similar elements of OpenOffice?

---

### Post by rizzyc on 2006-01-15
When i'm using openoffice and i hit the undo button on my logitech, it undo's the action like its supposed to
when i hit the print button, the print dialog option opens up 
when i hit the save button, it saves the documents

ok a few posts back, one of the poster refers to a website with the link for keytouch, dl the .deb file and then use the command sudo dpkg -i ___.deb to install it. it will show up in your System -> Administration -> keytouch 
just play around with it and read the documentation section on the keytouch website, theres a link on it over there

i cant get my other buttons to do anythign yet tough like changing desktops :(

---

