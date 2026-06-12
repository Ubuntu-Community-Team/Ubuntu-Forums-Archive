---
title: "gedit not working"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by impuwat on 2006-08-08
I just installed Xubuntu.  I'm trying to get a netgear usb wireless adapter working.  In one guide I read I needed to blacklist native linux drivers for the netgear adapter.  My problem is when I try:

"sudo gedit /etc/modeprobe.d/blacklist" in the terminal, I get "sudo: gedit: command not found".

I used the file manager (Thunar) to manually navigate to "blacklist" and then tried editing the file with a text editor.  When saving the changes I get the response, "Can't open file to write".
 
I know it has to be something simple I'm overlooking but I can't find it.  What am I missing?

---

### Post by skale on 2006-08-08
Most likely, you chucked gedit along with ubuntu, and don't have it. XFCE comes with it's own editor, "mousepad", or you can choose between two others, "vi" and "nano". Vi is a toughie, but the other two are pretty straightforward. Later, when your internet works, do a: 
```
sudo aptitude update && sudo aptitude install gedit
```
and you can use gedit again, if you want.

---

### Post by impuwat on 2006-08-08
That explains why gedit is not working.  But I'm using Mousepad to try to edit the file "blacklist".  I tried AbiWord, which is installed with Xubuntu and got another error message.  Any other ideas?

I'll look for the other two you mentioned and try them.  Thanks for the assistance.

---

### Post by impuwat on 2006-08-09
Hooked up my Xubuntu box to a hardwired/ethernet and followed your advice regarding installing gedit.  It installed flawlessly and I was able to use it to edit "Blacklist".  

Still not sure why mousepad would not do it.  Must be a bug there somewhere.  Similar to how I lost my Applications menu right off the bat.  Found enough help files to solve that problem after some initial consternation.  Despite these complications I'm really liking what I see with Xubuntu.  Nice and fast on my older test machine.

Thanks again for the help.

---

### Post by A2A on 2006-08-09
Hi impuwat.
I had the same issues as you.  I needed to edit a file and thats when I found out that Xubuntu does not have gedit installed by default.  Rather it uses mousepad and nano as editors.
I added gedit via synaptec, and it installed with a few warnings, but no serious errors.  A dev here advised me it was OK to use despite the warnings.  
On another note, my Applications menu has vanished as well.  You mentioned you had the same issue but managed to revive it,  could you please post some feedback on the steps you took to get the menu back?

Thanks,

A2A

---

