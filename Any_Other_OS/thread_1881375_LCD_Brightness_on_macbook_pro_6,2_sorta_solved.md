---
title: "LCD Brightness on macbook pro 6,2 sorta solved"
date: 2011-11-15
forum: Any Other OS
---

### Post by ceratophyllum on 2011-11-15
My mid 20100000 macbook pro has not had working LCD backlight control since Maverick. Now I've been running Linux Mint 11 (massaged Natty) for a while because I'm not wild about all the new bloaty UI changes in Ubuntu's latest.

apple-backlight, a little c++ program floating around these forums, allows me to adjust the backlight from the command line.  But I have to specify **--intel NOT nvidia**, even though the closed-source nvidia drivers are loaded?! (Using --nvidia has no effect and apple-backight always reports a brighness of 0.) 

I had no luck horsing around with different nvidia_bl_dkms module versions. The slider provided by pommed moves when F1 F2 are pressed, but the brightness never changes.

How does the ubuntu handle the 2 cards in the MBP? 

Is there a better solution to get the F1, F2 keys working again?

---

### Post by lael on 2011-11-15
I have a 6,2 as well.  

That was the fix when it first came out too.  There are 2 GPUs in it.  The embedded Intel one and the Nvidia Discrete one.  The code fix had something to do with controlling the brightness via the first gpu (intel) so it sounds like you are on the right track.

I've been using mpb_nvidia_bl on 10.10 though.

---

### Post by Zarathustra2 on 2011-12-26
Hello, same problem here.

I'm using Linux Mint LMDE so the (Debian Version) but i think the solution would be the same. Or very simular.

But I have a Macbook Pro from late 09 (MacBook Pro5,3) With 2 GPUS.

The 9400 and the 9600GT both Nvidia cards.

I heard from a friend with a simular problem (He had Intel & Nvidia) he installed some drivers direct from Nvidia. Could the same solution work for me?

---

