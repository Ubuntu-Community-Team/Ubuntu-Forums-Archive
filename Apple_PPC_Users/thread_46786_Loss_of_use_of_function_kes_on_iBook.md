---
title: "Loss of use of function kes on iBook"
date: 2005-07-06
forum: Apple PPC Users
---

### Post by Duo Maxwell on 2005-07-06
Well my Ubuntu CDs arived today, wanted to test on my [iBook 600 Late 2001](http://www.apple-history.com/frames/ibook_late_2001.html) so I tried the Live CD of Version 5.05 for Macs, which ran OK on the iBook, just couldn't get it to mount the 2nd and 3rd partitions on my external.  But the bad thing is now that I'm back in OS X 10.2.8 I can't get my volume, brightness, eject or Number lock keys to work any more. This is unacceptable, does anyone know of a way to get the function back?

---

### Post by Len on 2005-07-06
The only possible thing the Live CD could have modified is the PRAM. Try this:

Hold apple + alt + P + R when powering the mac. It should chime again (release the keys then). Date and time are reset.

Doesn't work?

Hold apple + alt + O + F when powering the mac. It should greet you with a white screen and black letters. Type: 
```
reset nvram
set-defaults
reset-all
```
The mac should reboot now. Date and time are reset.

Still doesn't work? Then the LiveCD could have done some weird stuff... Try removing the battery from the main board (you have to open your machine...) for a few minutes (with the power and battery UNplugged).

That must work. If that doesn't work, the LiveCD took no part in your function keys not working. Could be an OS X problem, try booting from the OS X installer CD and see if the keys work there.

These actions are safe, they'll not destroy any data from your HD. Only the battery trick is a risk because you have to open your machine (or maybe not, I don't have an iBook so I don't know...).


Let us know what worked. Before I read this I was telling everyone that the LiveCD is safe to use you know... didn't know it could modify the PRAM or other chip settings. It definitely shouldn't.

---

### Post by Duo Maxwell on 2005-07-22
[QUOTE=Len]The only possible thing the Live CD could have modified is the PRAM. Try this:

Hold apple + alt + P + R when powering the mac. It should chime again (release the keys then). Date and time are reset.

Doesn't work?

Hold apple + alt + O + F when powering the mac. It should greet you with a white screen and black letters. Type: 
```
reset nvram
set-defaults
reset-all
```
The mac should reboot now. Date and time are reset.

Still doesn't work? Then the LiveCD could have done some weird stuff... Try removing the battery from the main board (you have to open your machine...) for a few minutes (with the power and battery UNplugged).

That must work. If that doesn't work, the LiveCD took no part in your function keys not working. Could be an OS X problem, try booting from the OS X installer CD and see if the keys work there.

These actions are safe, they'll not destroy any data from your HD. Only the battery trick is a risk because you have to open your machine (or maybe not, I don't have an iBook so I don't know...).


Let us know what worked. Before I read this I was telling everyone that the LiveCD is safe to use you know... didn't know it could modify the PRAM or other chip settings. It definitely shouldn't.[/QUOTE]
 Sorry it took so long to reply back, been busy.

The keyboard problem seems to have fixed itself and I could still get the function if I used the all to easily forgotten fn key

---

### Post by Ptero-4 on 2005-07-23
[QUOTE=Duo Maxwell]Sorry it took so long to reply back, been busy.

The keyboard problem seems to have fixed itself and I could still get the function if I used the all to easily forgotten fn key[/QUOTE]
 It also happened to me with hoary on my old iBook (I now have an eMac 1.42GHz). It fixed itself also, the LiveCD and the install CD doesn't change anything what happens is that hoary handles the funtion key a bit differently from the way OSX and warty did and that kinda confuses OSX.

---

