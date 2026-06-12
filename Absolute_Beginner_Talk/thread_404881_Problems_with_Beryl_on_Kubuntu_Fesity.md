---
title: "Problems with Beryl on Kubuntu Fesity"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-04-09
Hi everyone:

I installed Beryl as mentioned on the Wiki for Beryl on Beryl's website and I followed the directions for Kubuntu Feisty. Everything seems to have installed fine but when I switch to Beryl windows manager, the desktop goes black. The windows which are open in the taskbar at the bottom, also go black. When I place the cursor on any of the windows in the taskbar I see a small preview of that window and when I switch the desktops I can see the beryl effects. So, after switching to beryl, the effects are there, but I can't see anything on the desktop except the taskbar at the bottom. I will greatly appreciate any help regarding this problem. Thanks.

P.S.: I have NVidia G-Force FX video card.

---

### Post by MasterOfDisaster on 2007-04-09
How much RAM does your video card have?  The black windows are a known bug for nvidia cards.  Have you tried starting Beryl with all windows closed, and then opening one at a time?

---

### Post by kvonb on 2007-04-09
You don't need to do a manual install of Beryl for Feisty, it is available from synaptic.

Maybe remove all the hand installed stuff and try using the official synaptic version.

---

### Post by keith11 on 2007-04-09
I  have 768 MB of RAM and even with all the windows closed and then opening one by one, I face the same problem.

About installing manually, let me mention that when I coiped the text for manual install from beryl's wiki, it didn't install anything, I don't know why. So then I installed beryl from the repos. So basically my beryl is installed from synaptic. 

Any more ideas please? Thanks.

---

### Post by vatechtigger on 2007-04-09
> **keith11 said:**
> I  have 768 MB of RAM and even with all the windows closed and then opening one by one, I face the same problem.



he was asking about how much video ram you have, not system ram. Perhaps your card is no good enough?

---

### Post by keith11 on 2007-04-09
My video card has 32 MB of RAM. I read on the NVidia forum that using a combination of "Use COW" for "Composite WIndow Overlay" and "Copy" for "Rendering Path" can eliminate the problem and it did for me. The risk is that by using those options the frame rate is killed as precisely said by someone who proposed that option on NVidia's forum. The additional downfall I found is that I am not able to play an avi movie in Mplayer in the full screen mode. I am using Kubuntu feisty and I don't know why Kaffeine wouldn't play the movies and amarok, the sound files. Any suggestions? Thanks.

---

### Post by kvonb on 2007-04-09
Yeah, my card is a 128 meg 6600GT and I still get black windows!


Beryl 1.4 was fine and I didn't have the black screen problem, maybe try to downgrade to that version?

The only other suggestion is to turn off as many effects as you can, like cubecaps / skydome / plugins / 3d stuff etc'.

Or try Compiz instead as it doesn't have any speccy effects!

Regards, Kev :)

---

### Post by kvonb on 2007-04-09
....or another not so useful suggestion:

Buy a newer video card :D

(sorry, just had to!)

---

