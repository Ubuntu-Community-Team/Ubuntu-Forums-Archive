---
title: "firefox 1.503 and clicking on mailto:links"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-06-16
Whenever I click on links in a firefox window I cant get them to open a compose window in thunderbird 1.5 How do I fix this. Using breezy 5.10 . I would like to correct this before I upgrade to the new version.
Keheikev
I wont give up if you dont! :KS

---

### Post by BitTorrentBuddha on 2006-06-16
Is Thunderbird set to your default mail program under System -> Preferences -> Preferred Applications? If so, what is it doing when you click mailto: links?

---

### Post by keheikev on 2006-06-16
Yes its my default mail handler but nothing happens when I click on mail too links.
Keheikev
:mad:

---

### Post by keheikev on 2006-06-16
Heres my preferred applications path /usr/lib/thunderbird/thunderbird "%s" in system/preferred applications/ mail reader tab
Kev

---

### Post by BitTorrentBuddha on 2006-06-16
Try running firefox from a terminal, click a mailto: link and see if there's any output, also try removing quotes from "%s".

---

### Post by nanotube on 2006-06-16
[QUOTE=keheikev]Heres my preferred applications path /usr/lib/thunderbird/thunderbird "%s" in system/preferred applications/ mail reader tab
Kev[/QUOTE]
make that
```
/usr/lib/thunderbird/thunderbird -compose %s
```
and try again.

---

### Post by keheikev on 2006-06-16
Well I did the removing of the quotes and added -compose in the preferred applications applet. No joy just yet I will try a restart and if that doesnt work maybe I will just upgrade the whole thing from synaptic.
Kev

---

### Post by keheikev on 2006-06-16
just to update the path I modified from the applet not terminal window is now /usr/lib/thunderbird/thunderbird -compose %s and I checked the run in terminal box but now a brief terminal window blinks open and closes.
TIA
Keheikev

---

### Post by BitTorrentBuddha on 2006-06-16
Run it in the terminal while all other firefox windows are closed, otherwise firefox sees the command and opens it as the same process.

---

### Post by i8bugs on 2006-12-02
> **BitTorrentBuddha said:**
> Is Thunderbird set to your default mail program under System -> Preferences -> Preferred Applications? If so, what is it doing when you click mailto: links?

Didn't even know that little app was there.  Solved my problem!
STICKY PLEASE!

---

