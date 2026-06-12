---
title: "Cannot Install Ubuntu"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by tj71587 on 2007-06-20
I recently built a computer with an Intel Core 2 Duo and a Seagate Hard Drive and when I start my disk the Ubuntu bar comes up and goes full and takes me to a black screen, can anyone please help.

---

### Post by bobplano on 2007-06-20
what is the graphics card on this computer? also have you check the cd/iso for errors?

---

### Post by drivel on 2007-06-20
I think it's your graphics card err or problem

---

### Post by tj71587 on 2007-06-20
I have an Nvidia 8800 GTS, if that is the problem, how would i resolve it?

---

### Post by MichaelLerch on 2007-06-20
> **tj71587 said:**
> I have an Nvidia 8800 GTS, if that is the problem, how would i resolve it?

Have you tried installing Ubuntu through its text-based installer?

I've noticed that some people are have problems installing Ubuntu 7.04 [Feisty Fawn] under high-end cards [ [see this thread here]("http://ubuntuforums.org/showthread.php?t=414194") ].  I haven't experienced this problem, and I'm running a ATI Radeon X1800 XT 256MB PCI-E.

Try the text-based installer and let me know if you have any problems.

If and when you do get Ubuntu installed - download, install, and run this application [here]("http://www.albertomilone.com/nvidia_scripts1.html").  It will ask you if you want to INSTALL or UNINSTALL the Nvidia graphics driver.  You will want to INSTALL it of course, and upon that the applet named Envy will download the appropriate drivers, install them, and ask you if you want it to write to the xorg.conf file.  Say yes to that, restart your machine.. and you're done!

PS.  The text-based installer should be easy to use, I don't imagine it being extremely difficult.

---

### Post by tj71587 on 2007-06-20
Thank you very much, I will run that tonite and post how it goes.

---

### Post by tj71587 on 2007-06-23
I installed it with the text based installer and it installed fine, but when i tried to boot it, it would go to a black screen, this also broke my windows xp install as I am tryin to dual boot.  Does anyone have any suggestions?

---

