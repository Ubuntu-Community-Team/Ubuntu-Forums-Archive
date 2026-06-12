---
title: "Mac on linux molvconfig crashes"
date: 2007-02-22
forum: Apple PPC Users
---

### Post by Pappa_Smurf on 2007-02-22
I have a powerbook G4 running a custom kernel (2.6.20).

I compiled mol from source (pain in the ...) but finally everything seemed to be working.

when i run molvconfig everything crashes.  My screen goes all fuzzy like it tried to shrink the resolution of whatever was on it unsuccessfully.  I can see what was on the screen before running molvconfig, it just looks big and fuzzy and hangs over the edges of the monitor.

could this be because i disabled open firmware framebuffer support in my kernel?  I did this to make the brightness settings work on my g4 (I have riviafb instead).

I'm going to try recompiling and enabling both framebuffers to see what happens, but in the meantime, does anyone have advice?

---

### Post by didg on 2007-02-22
Which MOL did you compile on which Ubuntu version?
For Feisty SVN version compile out of the box but need -O2, gcc produce bad code.

Does it run within an X windows?

---

### Post by Pappa_Smurf on 2007-02-22
mol-0.9.71.1 on Edgy but with a custom kernel.

i'm not sure what you mean by "but need -O2, gcc produce bad code."

I cannot run it in any mode because it says "no video modes available" but when I run molvconfig everything crashes.

---

### Post by didg on 2007-02-22
> **Pappa_Smurf said:**
> 
i'm not sure what you mean by "but need -O2, gcc produce bad code."

Yes it doesn't make a lot of sense, I was doing two things at the same time. 

At least when compiled on feisty, gcc -O2 produces bad code and the generated software has weird behavior.

Isn't molvconfig only for fullscreen? try to modify /etc/mol/molrc.video for using xvideo only.

Did you try the molvconfig from the Ubuntu deb?

Last it's possible that movconfig tried a bad mode but that your frame buffer didn't reject it. I doubt that enabling openfirmware will change anything.

---

