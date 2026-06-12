---
title: "issues with running games on ubuntu......"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by jeetmcp on 2007-04-04
hi,
i have recently installed Ubuntu 6.10 Edgy. graphics, media and videos are excellent but i have an issue with running games on it. games are really slow and sometimes they don't even launch.sometimes they also crash the system. i have an AMD X2 2200+ 512 MB RAM and an ASUS motherboard with an in built 64 bit graphics card. its just been two days Ubuntu has been really great except games. can anyone suggest me what to do?

---

### Post by LaRoza on 2007-04-04
What games are you trying. Many computer games are written for Windows. In fact, Vista is only good as a gaming and multimedia platform.

---

### Post by Terl on 2007-04-04
Like LaRoza asked.... Are these windows games via Wine or Cedega?  If so, you might not have enough ram depending on the game.  Are they 3d games?  Did you set up your graphics card?

---

### Post by jeetmcp on 2007-04-04
pouet chess, billiard gl are very slow.
armagatron crashes the computer and lx doom does not even start.
i have a motherboard with an ASUS platform that has an inbuilt VIA KM 890 on an M2VTVM platform.the AGP aperture size is 128 bit.tell me if you need any other data and please help me.

---

### Post by cypherzero on 2007-04-04
Now you see why people still buy from Microsoft

You can always use WINE though, especially if you have Windows to get the dlls from (assuming you haven't already tried, because it doesn't work for everything)

---

### Post by LaurelLynn on 2007-04-04
Dear jeetmcp,

A windows game should have refused to install without Wine.

¨Very slow¨ with a few crashes is usually typical of a graphics driver problem. I have three systems with Ubuntu and the one with the VIA chipset is the one that would only start in VGA, by switching to the VESA drivers I got full SVGA resolutions but no hardware accelleration.

I searched the web for a solution but apparently I have the worst possible chipset combination for X. None of the solutions I found worked, so I¨m stuck, you might not be.

First look in the ¨/etc/X11/xord.conf¨ file. The section labeled ¨Device¨ will list what you are currently using.

To try the basic VESA drivers I used (your system may have different bus settings):

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

¨Cntl-Alt-Backspace¨ restarts X

They are still slow, but shouldn´t crash, and they will render GL programs. So if the crashes stop your driver was likely the problem and you need to find another. If not something else would seem to be at fault.

Good Luck, Laurel Lynn

---

