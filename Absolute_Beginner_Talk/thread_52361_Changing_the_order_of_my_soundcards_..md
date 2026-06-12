---
title: "Changing the order of my soundcards ."
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by leppasanis on 2005-07-27
First of all, Hi everybody ...Ubuntu what a great community.

Im a newbie, Im trying to get my sound to work.
When I do the following command to see the order of soundcards on my system,

              cat /proc/asound/cards

I see this :

0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                     Intel 82801BA-ICH2 with AD1885 at 0xe800, irq 17
1 [Audigy         ]: Audigy - Sound Blaster Audigy
                     Sound Blaster Audigy (rev.3) at 0xdf80, irq 22
2 [Bt878          ]: Bt87x - Brooktree Bt878
                     Brooktree Bt878 at 0xf47ff000, irq 21

I have read that I have to chance the order of the soundcards and It will work.
I should edit /etc/modprobe.d/sound:

But I dont have such directory/ file .

If any one could help a ubuntu fan !

---

### Post by varunus on 2005-07-27
Try the following howto to configure multiple sound cards:
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

---

### Post by leppasanis on 2005-07-28
Yo Thanx from the bottem of my heart....
Its working !
 :grin: 
(music was my first love and It will be my last)

---

