---
title: "MSI K8n Neo4 motherboard drivers..."
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Good Ol' Ramos on 2007-08-15
Heya folks. I made the switch to Ubuntu many months ago, but switched to Vista once it was released due to ease of use. I just didn't have the time to learn Linux from scratch. Anywho, now that I do, I decided to look around for all the drivers I need, and alas, I cannot find anything for my motherboard. I've tried looking everywhere, and I tried searching for a solution ad nauseum on this forum. So... anybody have a clue how I'm supposed to go about getting these drivers? Thanks a million!

---

### Post by irish_flu on 2007-08-15
Maybe you'll have better luck coming at it from a different angle.  As in, what do you want from your motherboard that you're not getting now?   Are you missing any motherboard-embedded things (built-in sound, some chipset features, etc)?

Oh, and if nobody has said it before: Welcome!  I hope you enjoy Ubuntu, and I hope you find these forums helpful.

---

### Post by overdrank on 2007-08-15
> **Good Ol' Ramos said:**
> Heya folks. I made the switch to Ubuntu many months ago, but switched to Vista once it was released due to ease of use. I just didn't have the time to learn Linux from scratch. Anywho, now that I do, I decided to look around for all the drivers I need, and alas, I cannot find anything for my motherboard. I've tried looking everywhere, and I tried searching for a solution ad nauseum on this forum. So... anybody have a clue how I'm supposed to go about getting these drivers? Thanks a million!

HI I am running the same board and have no problems, what type of problems are you having?

---

### Post by amazingtaters on 2007-08-15
Have you tried installing yet? Your motherboard itself shouldn't need any drivers to run Ubuntu. If you are using integrated sound or something you may need drivers, but this is not critical to install. If you are having trouble installing post what type of errors you are getting. I've installed Ubuntu to an MSI K8 Neo2 before and it worked fine.

---

### Post by r4ik on 2007-08-15
[http://global.msi.com.tw/index.php?func=prodpage2&maincat_no=1&cat2_no=171&cat3_no=6](http://global.msi.com.tw/index.php?func=prodpage2&maincat_no=1&cat2_no=171&cat3_no=6)

[http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=249](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=249)

If i am correct.

---

### Post by Good Ol' Ramos on 2007-08-15
Well, I need the onboard NIC driver, and I suppose the onboard audio driver as well because my Sound Blaster card doesn't have input for coax or fiber optic audio cables, but the board does... but I rant. Anywho, I guess that's it. NIC and sound.

---

### Post by Good Ol' Ramos on 2007-08-15
> **r4ik said:**
> [http://global.msi.com.tw/index.php?func=prodpage2&maincat_no=1&cat2_no=171&cat3_no=6](http://global.msi.com.tw/index.php?func=prodpage2&maincat_no=1&cat2_no=171&cat3_no=6)

[http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=249](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=249)

If i am correct.

Well, that's the page I saw, and I couldn't find any Linux support. It was all Win2K, WinXP, WinVista.

---

### Post by overdrank on 2007-08-15
> **Good Ol' Ramos said:**
> Well, I need the onboard NIC driver, and I suppose the onboard audio driver as well because my Sound Blaster card doesn't have input for coax or fiber optic audio cables, but the board does... but I rant. Anywho, I guess that's it. NIC and sound.

HI this is my nic card and it works great no problem right out of the box
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)

And this is my sound and it has been the same as the nic 
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

Can you verify that you have the same and if different post back here.

---

### Post by Good Ol' Ramos on 2007-08-15
I do believe you're checking that through Linux. I don't see that information at all in Device Manager in Windows. All I get is "nForce Network Adapter" and "Realtek AC97 Audio Device".

---

### Post by lemmy999 on 2007-08-15
Ramos

Why don't you download the liveCD and try it.It's a great way to test all of your hardware before you install.

---

### Post by Good Ol' Ramos on 2007-08-15
I suddenly feel stupid. I was just in the LiveCD earlier today. Apparently, I need to download the nVidia driver, which I have. Internet works just fine, so I guess that solves that? I get sound, too, so... hot diggity dawg. Thanks for the assisted epiphony.

---

### Post by irish_flu on 2007-08-15
AWESOME, glad to hear they work for ya.

---

### Post by Good Ol' Ramos on 2007-08-15
Now, I want to install Ubuntu on my 4.3GB HDD... think there'll be any problems? It's just temporary until I  know that everything will work and I can get rid of Vista.

---

