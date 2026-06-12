---
title: "Audio and Brightness not working on Macbook."
date: 2009-10-02
forum: Apple Hardware Users
---

### Post by God of the Meeps on 2009-10-02
I posted the following in the Hardware and Laptops area before I realized there was an Apple Users subforum.

"Hello everybody.

I recently obtained a successful dual-boot of Ubuntu on my Macbook (the higher end 13", as shown on the Apple website, no other modifications).

However, the brightness control does not work. As well as this, no sound comes out of the speakers, whether it be my earbuds or built-in speakers, so I suspect it is a driver problem.

I've already checked the Ubuntu guide to installing the correct drivers, and have ALSA present. It seems to recognize it, but there is still no sound.

Does anyone have suggestions?

Thanks in advance."

Also, I'm running 9.04 Jaunty on it.

---

### Post by ichigo on 2009-10-04
Hi!

I've got the same laptop! Installing the nvidia-190 drivers from the PPA [https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa) did the trick for me.
([https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Keyboard](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Keyboard) hinted me to that)

As for the sound: Alsa mutes all audio channels during install. Run "alsamixer" in a terminal and check if all volumemeters are muted or not.
(&#8592;&#8594; to navigate, &#8595;&#8593;to change the level, M to mute/unmute)

---

