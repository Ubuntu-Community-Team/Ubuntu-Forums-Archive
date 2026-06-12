---
title: "screen resolution"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by mactabilis on 2005-07-16
Ive got the live cd of ubuntu and i cant change the screen resolution im stuck in 640x480 can somone please help me here.
Ive gone to options / sreen resolution /and there is no other choice but 640x480 its just stuck there.

---

### Post by sapo on 2005-07-16
[QUOTE=mactabilis]Ive got the live cd of ubuntu and i cant change the screen resolution im stuck in 640x480 can somone please help me here.
Ive gone to options / sreen resolution /and there is no other choice but 640x480 its just stuck there.[/QUOTE]

I ve nerver used a liveCD.. btw..

Try oppening a terminal.. then type:

```
sudo gedit /etc/X11/xorg.conf
```

Edit this section:

```
SubSection "Display"
		Depth		24
		Modes		"640x480"
	EndSubSection
```

Change to this:

```
SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
```

or 1024x768..

Then press:

Ctrl + Alt + Backspace to restart X...

hope it helps  :grin:

---

