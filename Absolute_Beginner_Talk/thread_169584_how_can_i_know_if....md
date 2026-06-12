---
title: "how can i know if..."
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-02
if ubuntu recognizes my ati radeon 7500 32mb video card? and if it's actually *using* it?

---

### Post by Jason_25 on 2006-05-02
```

lspci

```
should show the card.  Maybe 
```

lspci | grep ati

```
if you can't find it.  Ubuntu is using it if your monitor is connected to it and it's showing a picture.

---

### Post by user1397 on 2006-05-02
ok yea it shows up...but how? i thought in ubuntu only radeon 8500 and up worked? something about drivers? well, w/e it works fine for me!
thanks for the reply

---

### Post by evilgold on 2006-05-02
A good indicator is "glxinfo | grep direct" if that says direct rendering: yes, your card is most likely working.

Make sure your using the radeon driver too, it will work a lot better then ati with 3d acceleration. I believe you can get XGL working with some tweaking.

Edit: Scratch the part about fglrxinfo, that only works with newer cards.

---

### Post by Jason_25 on 2006-05-02
Almost any video card will work with ubuntu.  It's a matter of using it's features  like mpeg-2 decoding or open gl acceleration that's the trick.

---

### Post by user1397 on 2006-05-04
[quote=Jason_25]Almost any video card will work with ubuntu.  It's a matter of using it's features  like mpeg-2 decoding or open gl acceleration that's the trick.[/quote]
Awesome! so how can i get my card's features to work, if it has any? and how can i know that ubuntu is recognizing those features?

---

### Post by Jason_25 on 2006-05-04
Try what evilgold said.  Post the contents of your xorg.conf if it doesn't say Direct Rendering:Yes.

---

### Post by user1397 on 2006-05-04
[quote=Jason_25]Try what evilgold said.  Post the output of your xorg.conf if it doesn't say Direct Rendering:Yes.[/quote]
it does say yes!

---

