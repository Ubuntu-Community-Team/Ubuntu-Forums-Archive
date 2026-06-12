---
title: "Screen Resolution"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-05-26
Hi all!

I have had to reinstall my Breezy Badger, something I did wrong not because of anything to do with the OS, and now it only offers me a max screen resolution of 1024 x 768 whereas before I had 1280 x 1024.  How can I change it?  I have tried the  **System > Preferences > Screen Resolution** but 1024 X 768 is the highest it offers.

Russty

---

### Post by hotbrainz on 2006-05-26
Please try ctrl-alt-backspace and login and try again. This worked for me.

---

### Post by Russty of Oz on 2006-05-26
No!  No luck with that.  1024 x 768 is still the highest res!

I am just not used to everything looking so big.

Russty

---

### Post by hotbrainz on 2006-05-26
try this command:

sudo dpkg-reconfigure xserver-xorg

Hope that helps man

---

### Post by Russty of Oz on 2006-05-26
BINGO!

Thanks hotbrainz!  that did the trick!

Russty.

---

