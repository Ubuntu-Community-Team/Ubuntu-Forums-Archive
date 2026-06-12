---
title: "Powerbook experience report and Question"
date: 2005-05-17
forum: Apple PPC Users
---

### Post by karl_kashofer on 2005-05-17
Hi all !

I recently got an Apple Powerbook Pismo 400 mhz, and put 256 MB RAM into it.
I decided to go with Ubuntu and here is my report on what works and so on:

Install from Hoary CD: 
had an issue with the DVD drive, would stall on "Configuring apt ... 25% "
Swapped to a CD-ROM and everything went smooth. This seems to be a known problem with some drive/CD combinations. Try a different drive or burn the CD with slower speed.

Other than that no issues during install.
(Screen, Network, CD, Sound, Sleep work, booting takes 2 minutes, but after that all is well)

Watch Divx:
Totem did not play my Divx videos. It complained about a missing codec, but after install of all gstreamer codecs it would just crash after opening a divx.
I installed Xcine from Universe, which works well.

Speed and Graphics:
The builtin ATI graphics card was properly recognized, but the ColorDepth was wrongly set to 24 bits.
I only noticed this when I tried to watch DivX videos, which would drop too much frames and get out of sync very fast.
Fix: open /etc/X11/xorg.conf and change the ColorDepth from 24 to 16
Now DivX plays fine in fullscreen.

Power management monitor:
The battery meter on the gnome panel does not work.
I removed the powermanagement icon from the panel (right click (= F12) on the panel, then properties)
Then I installed all pmud software from universe (pmud-tools, pmud, gpmud-applet) and after that added the pmud panel via the aforementioned properites.
Seems to work fine. The powerbook now even goes to sleep when the lid is closed.

Others:
On a Lombard the touchpad seems to be different than on the Pismo, because on the Pismo the tap-click works.

And here is the question:
We all know that F12 is a poor replacement for the right click.
Now, on the Pismo the tap-click on the touchpad works, so the mouse button could actually be mapped to the right-click ?

If anyone knows how to achive that please reply. :)

Ubuntu rocks !
Cheers,
Karl

---

### Post by willnight on 2005-07-29
thnx for starting this thread!

i have a pismo. it was stable under warty. i've recently upgraded to hoary and things are a bit ... peculiar.

one specific item is the monitor dimming after about 10 secs if inactive (mouse movement), then goes into sleep mode. it is the most annoying thing!  :mad: 

 i can't seem to figure out why it's doing it!

any idea?

---

### Post by pierba on 2005-07-30
[QUOTE=karl_kashofer]Hi all !
And here is the question:
We all know that F12 is a poor replacement for the right click.
Now, on the Pismo the tap-click on the touchpad works, so the mouse button could actually be mapped to the right-click ?[/QUOTE]

You can change this part:

> # Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 87
dev/mac_hid/mouse_button3_keycode = 88

in /etc/sysctrl.conf an replace whith code for the keys that you prefer. 

Pietro

---

### Post by harryc on 2005-07-31
What happens if you hold down the ctrl key then tap?

---

