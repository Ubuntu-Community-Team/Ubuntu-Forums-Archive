---
title: "Warcraft III odd problem"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-10-01
Ok, i have a dell inspiron 2350 no modification, just 1 gig of ram.

I installed warcraft III on my ubuntu after some trial and error, and it will start up, but it looks all messed up, and i have no idea why, i wanted to see if you can help me,i took a screen shot of how it looks. thanks!

anyhelp would be great!, i really want to play, but i dont want to give in and use windows...
[IMG]http://img.photobucket.com/albums/v390/RitterRav/Screenshot.png[/IMG]

---

### Post by PmDematagoda on 2007-10-01
What's the VGA you use?

---

### Post by ritterrav on 2007-10-01
I dont have a video card, its the built in one that came with my PC
i dd not think warcraft III was a demanding game, resource wise.

---

### Post by PmDematagoda on 2007-10-01
When I run Warcraft III on Wine it uses a lot of processing power, not sure if it may apply for the VGA. How much memory is being dedicated to the onboard VGA?

---

### Post by ritterrav on 2007-10-01
i think it has either 64mb or 32mb of its OWN ram. how can i check? and can i give it more?

---

### Post by PmDematagoda on 2007-10-01
Yes, you can, have a look in your BIOS, there may be an option for you to increase the amount of RAM which is left for the VGA card.

---

### Post by ritterrav on 2007-10-01
oh ok, ill restart and check. and thanks man for the fast reply, i heard its an awsome game, and i really want to try it. brb

---

### Post by ritterrav on 2007-10-01
ok, i gave it a whack, and it is a no go. i cannot give my VGA more memory or anything.

anything else i can do? i have another VGA but i think the specs on that one are lower, but when i switch to that one in peripherals and restart ubuntu wont load for some reason? any reason why?

---

### Post by PmDematagoda on 2007-10-01
You will have to reconfigure X-server, using:-
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ritterrav on 2007-10-01
How much KB should i give to it?

---

### Post by PmDematagoda on 2007-10-01
As it isn't an integrated VGA card, just leave that option blank.

---

### Post by ritterrav on 2007-10-01
well that did not work, i allocated 128mb to it, and nothing, i still have the same problem. damnit.

---

### Post by PmDematagoda on 2007-10-01
Now, the card you are trying to use is not integrated is it? What brand is it? And what type of problems do you face?

---

### Post by ritterrav on 2007-10-01
I am currently using my integrated VGA, and i belive that it has 32 mb of its own ram. 
the other one, i dont remember what brand it is, but i believe it is weaker then my integrated/onboard vga. and i believe i allocated 128mb to that onboard vga. or 128,000kb. 

and the problem i am coming to is that screenshot i showed earlier. But i dont think it is the VGA, because i played the demo on my friends PC (he has XP) and my pc is stronger then his onboard vga does not even have its own memory, it borrows 32mb from his PC ram to the onboard vga, AND he only has 512mb ram. and the demo played flawlessly, so i know the game is not that demanding.  Is there ANYTHING i can do,  want to play the game, but i dont want to have to give in and go to windows (i see it as a failure to myself).

---

### Post by ritterrav on 2007-10-01
Anybody? help?

---

