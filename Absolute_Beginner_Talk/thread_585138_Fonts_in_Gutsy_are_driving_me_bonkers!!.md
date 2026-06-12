---
title: "Fonts in Gutsy are driving me bonkers!!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-10-21
Ive seen other people complain about this however after trying various suggestions I can seem to make it work.  I just upgraded from Feisty to Gutsy.  I have msttruefonts installed.  Fonts in Feisty were great.  Now looking at the fonts in Firefox under Gutsy, its driving me nuts!!  The look horrible.  The font used in the address bar --- Yikes.

I tried subpixel hinting, didnt do anything for me.  

Any other ideas??  Why did they have to do this?

---

### Post by Nevon on 2007-10-21
I agree. They look absolutely horrible in Gutsy. Especially in the top "bar" in firefox.
Btw, how do you install msttruefonts?

---

### Post by llamakc on 2007-10-21
sudo apt-get install ubuntu-restricted-extras

---

### Post by mistergq on 2007-10-21
my problem is the main font for text for my thunderbird and terminal is lighter than it should be.  Any suggestions on fixing this?

---

### Post by ThrobbingBrain66 on 2007-10-21
Can we have some screenshots? Are  the fonts a problem only in Firefox?

If you used mlind's Feisty font-rendering repo, those patches were included into Gutsy so the fonts should be exactly the same.

---

### Post by logos34 on 2007-10-21
try this howto:

**'[Display Microsoft fonts like on Windows]("http://ubuntuforums.org/showthread.php?t=208396")'**

---

### Post by kevdog on 2007-10-21
Here is a screen shot

---

### Post by kevdog on 2007-10-21
Ive tried that Microsoft tutorial way back in Feisty and it worked great.  After the upgrade everything went to hell in a handbasket.

---

### Post by logos34 on 2007-10-21
> **kevdog said:**
> Ive tried that Microsoft tutorial way back in Feisty and it worked great.  After the upgrade everything went to hell in a handbasket.

wow...then maybe I won't upgrade after all.  And if I find out it doesn't work in Gutsy fresh install I stick with Feisty.  Font quality is critical for me.

---

### Post by forestpixie on 2007-10-21
I upgraded ( and then reinstalled - but that's another story) - I'd used the same thread to sort my fonts initially in Feisty, then after finally remembering the thread the other day I've got the same results in Gutsy. So it worked for me

---

### Post by kevdog on 2007-10-21
Begrudgingly Im probably going to have to install from scratch with Gutsy.  Already see some other things not quite working as well after the upgrade.  When you say 

> I'd used the same thread to sort my fonts initially in Feisty, then after finally remembering the thread the other day I've got the same results in Gutsy. So it worked for me

What thread are you exactly referring too??

---

### Post by forestpixie on 2007-10-21
the thread that logos refers to :)

---

### Post by logos34 on 2007-10-21
> **forestpixie said:**
> I upgraded ( and then reinstalled - but that's another story) - I'd used the same thread to sort my fonts initially in Feisty, then after finally remembering the thread the other day I've got the same results in Gutsy. So it worked for me

That's good to hear.

---

### Post by misfitpierce on 2007-10-21
[img]http://i22.tinypic.com/2nhlq1d.png[/img] 

I think fonts look great... Using Sans 7 Slight hinting... :)

---

### Post by kevdog on 2007-10-21
I know fonts are a matter of personnal opinion, however the fonts for both the toolbars in firefox, and the window fonts look much different.  In fact even the terminal fonts (which I didnt include) look different.  


I think Im going to start from scratch.  Something in the upgrade broke something.  Guess I should have expected this since everyone suggested reinstalling from scratch and not upgrading.

---

### Post by nabla on 2007-10-21
Sorry to say, but I did a fresh install and I have the same problems.

---

### Post by kevdog on 2007-10-21
Seems like this problem is more widespread than I thought --- Why the heck would they mess with fonts???

---

### Post by philinux on 2007-10-21
This is weird my upgrade went fine and no font problems.

Just maybe try a theme or two might sort it I know it also changes the way firefox looks.

---

### Post by malk_dvorak on 2007-10-21
just wanted to add that my fonts are fvcked too, the only setting that works for me is to choose 'best contrasts' in the appeareances thing. not ideal but makes websites readable

---

### Post by ntetreau on 2007-10-21
I've had this problem as well.  I fixed it in Firefox by going into about:config (write this in the address bar).  Then search for 
layout.css.dpi

change its value from -1 to 0.  Restart.

For more info, check: [http://ubuntuforums.org/archive/index.php/t-437727.html](http://ubuntuforums.org/archive/index.php/t-437727.html)

---

### Post by hugmenot on 2007-10-22
The default settings were determined by this poll:
[http://ubuntuforums.org/showthread.php?t=555964](http://ubuntuforums.org/showthread.php?t=555964)

I voted for &#8216;slight&#8216;, because it actually looks rather delicious.
Try the &#8216;Slight Hinting&#8217; setting, you might like it.

---

### Post by kevdog on 2007-10-22
I actually found the firefox trick really helped for the firefox fonts -- not so for the others.  I understand the vote -- but seriously did anyone really think the fonts in feisty with the msttruefonts installed were that bad?

---

### Post by nabla on 2007-10-22
Ok, So after some messing around and using different configs for a while, I think Subpixel Smoothing with full hinting is a winner, looks gorgeous. So I've changed my mind, Gutsy kicks Feisty's **** in font rendering.

---

