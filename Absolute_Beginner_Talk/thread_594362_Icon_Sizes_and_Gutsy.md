---
title: "Icon Sizes and Gutsy"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by demonicdude on 2007-10-27
Hello,

Just upgraded from Feisty to Gutsy. Love the visual effects =). Only thing that is bothering me right now is the icon sizes. I've looked everywhere to figure out how to change them. I've right clicked them but there is no "stretch icon" button i can click. Here is a screenshot:


If you see at the bottom right near the four panels, my volume icon is small, just the way i want the rest of the icons. Everything else (the firefox icon, the trash icon, the four panels) are all way to big.

I was picking different screen resolutions at the time i believe this happened. All the icons were small in size, but then they all changed to be big and now i can't change them back =(.

---

### Post by demonicdude on 2007-10-28
bump.

---

### Post by mikeyphi on 2007-10-28
Right click on an empty part of the panel - select properties - reduce size to 24 pixels.
That's the only control I know about!

---

### Post by daimaru on 2007-10-28
that exact same thing just happend to me ( its caused by the moomex theme ) after using it i tried switching back to other themes, but the icons stayed big. rightclicking panel and trying to size them back to 24 did not work it won't go under 33.. so i added new panel and deleted my old one , as well as the moomex theme which i wont use again :)

---

### Post by demonicdude on 2007-10-28
Alright i'll give that a shot. In the mean time though i've gotten another problem. In my attempts to get a bigger screen resolution, i completely messed up the stuff lol. Now i only have 800x600 and 640x480. I used to have 1152x768 which i want back, but there is no option for it now :(. Anything i can do?

---

### Post by daimaru on 2007-10-28
you can edit your /etc/X11/xorg.conf file 
```
sudo gedit /etc/X11/xorg.conf
```
heres mine. under the subsection display just write in your desired resolutions then hit ctrl + alt + backspace to restart x server log back in and i should be on the highest resolution you put into xorg.conf
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Samsung SyncMaster 214T"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection
```

---

### Post by demonicdude on 2007-10-28
Thank you for that :P. I remembered i made a backup copy of xorg.conf THANK GOD :P. All is well, going to try out the new panel stuff and see if that works, i'll be back...


Edit: AHA looks like it was the moomex theme that wasn't allowing me to change the size of the panels :). Well, i switched out of that theme and now i've gotten it small thank you daimaru and 
mikeyphi =). Now to find a  theme that was just as nice as moomex ....

---

