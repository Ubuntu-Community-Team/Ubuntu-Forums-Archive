---
title: "NeroLINUX"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Ssj3_man on 2007-06-19
I installed NeroLINUX CD/DVD Burning Software, but know i can't find it. Can you help me find it? Where is this; will also add a shortcut to NeroLINUX in the debian-menu subsystem repository. How do I navigate to it?:(

---

### Post by starcraft.man on 2007-06-19
> **Ssj3_man said:**
> I installed NeroLINUX CD/DVD Burning Software, but know i can't find it. Can you help me find it? Where is this; will also add a shortcut to NeroLINUX in the debian-menu subsystem repository. How do I navigate to it?:(

Best advice I have for you is to uninstall the Nero burner from Linux and try K3B/Gnomebaker (both installable via synaptic/terminal). Nero is not worth the money and K3B does everything one could need, it is also free. I took the Linux version of Nero for a spin a while back and honestly, its not worth it... I wasn't impressed with anything.

Working off the best of my memory, I am pretty sure it launches from the command "nerolinux". I could be wrong. Thus you can run it via a launcher with that command (for desktop) and a menu entry for that. I recommend against it still though, if you waste money, I told you so.

---

### Post by Ssj3_man on 2007-06-19
Where do I find K3B, i have it installed?

---

### Post by crispy_420 on 2007-06-19
I second that motion. Nero Linux is no where near what it is like in Windows. It is extremely stripped down and has no where near the options of k3b. I have used it before and ended up picking k3b instead.

Hope you got it free.

---

### Post by starcraft.man on 2007-06-19
> **Ssj3_man said:**
> Where do I find K3B, i have it installed?

System > Administration > Synaptic > Search "K3b"

Find the following packages in the list:
```
k3b libk3b2-mp3    
```

Check them off on the left and push apply. This is one of the methods for installing things. [ This is a good tut about installing in general.]("http://www.psychocats.net/ubuntu/installingsoftware") It shows mostly the terminal, I just showed you the GUI way. They both rely on the same packages.

That should do it, it will appear in the multimedia section of the applications menu.

---

### Post by bodhi.zazen on 2007-06-19
> **Ssj3_man said:**
> Where do I find K3B, i have it installed?

If you installed Ubuntu you have gnomebaker.

Right click on an iso and record to disk :)

I also like k3b. you can install it from synaptic, search for k3b.

Or in a terminal :```
sudo aptitiude install k3b
```

What I like about k3b is it checks the integrity of the burn.

---

### Post by Golyadkin on 2007-06-19
I was sooo happy I got rid of Nero once I started using k3b in Ubuntu. It was really a breath of fresh air for me. In my opinion it is ridiculous Nero for Windows has grown to be a 600MB program, it is almost as big as the installation cd for entire Ubuntu with 1000 packages installed.

---

### Post by dpar on 2007-06-19
I have to agree with everyone else. Nero in Windows was a bloated piece of dung that wanted to take ownership of every file extention on my computer.
K3B is definatly the way to go!

---

### Post by Ssj3_man on 2007-06-19
Can we make a short cut to go a long that bar that goes from right to left at the top of the screen? I'd hate to have to remember a DOS code to launch that program.

---

### Post by Golyadkin on 2007-06-19
Rightclick that panel, choose "add to panel" and click the "Application launcher" button and choose K3B from the list.

---

### Post by ounn on 2007-06-19
If you use gnome you would prefer install Brasero instead k3b. It does tha same thing and look good in your desktop. It is also in repos.


ounn

---

### Post by kelvin spratt on 2007-06-19
Don't take any notice of that load of rubbish Nero 3 Is the burner section of Nero 7 in windows, you can even
drag and drop TS files into it and burn without having to make ISO images Its Not Free but apart from that it is one of the best burners on the market, Brasero is a far better burner than K3b its not consistent and quality results using my plextor are medicore at best, Brasero are good, Nero Excellent, i only use Verbatim and burn at max that gives the best results, thats a full DVD in 5 mins 96-98% Quality readings all the time.

---

### Post by Ssj3_man on 2007-06-19
> **Golyadkin said:**
> Rightclick that panel, choose "add to panel" and click the "Application launcher" button and choose K3B from the list.

Thank You :D

---

### Post by Brightbelt on 2007-06-19
Also, just to clarify options in case others are looking in, K3B is available thru Add/Remove as well.

Frank B.

---

### Post by kelvin spratt on 2007-06-19
You may need to reinstall Nero To get it to appear in ADD REMOVE it can be a bit stubborn at times, try a restart as that might prompt it to start if that fails go into filesystem  d click USR,  D click BIN, scroll down till you find NERO copy paste to deskdop or right click top panel,  ADD to PANEL click custom,  browse, file system
USR- BIN -  Nero that will place it on the top panel

---

### Post by noynac on 2007-06-19
> **kelvin spratt said:**
> Don't take any notice of that load of rubbish Nero 3...

I think you need to insert a period to make things clear (LOL). 

I tried Brasero and k3b and had trouble with both of them with  erasable DVD's, which I use a lot. I got Nero Linux 3, and it has worked great. People should try all of the available burning programs and see what works for them, but don't dismiss Nero Linux 3 out of hand.

BTW, during the installation process, Nero Linux 3 added a link to the program in the "Sound and Video" menu.

---

### Post by wink on 2007-06-19
> BTW, during the installation process, Nero Linux 3 added a link to the program in the "Sound and Video" menu.

Same thing happened during my installation of it - as well as when installing K3b. 

BTW, to clarify, Nero Linux is actually only the "Nero Burning ROM" portion of the Nero Suite. 

Is anyone aware of a Ubuntu_Linux equivalent for Nero Vision? When converting DVDs from another region to region 1 it so far has produced the best results for me.  Sure it takes a long time but the result is definitely better than that produced by a simple IFO edit.  

wink

---

