---
title: "Booting on winXP cd..?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by junn on 2006-08-08
Hey Guys!

First of all... Im a noob to Linux, but I love it >) I do have a slight problem though which I hope u can help me out with:

I was running a winXP HE SP2 when I decided to tryout Ubuntu. So I plugged in my live cd, and selected the "delete harddisk" option at the installation guide. Big mistake. I want to run XP as well but now I cant even boot on my xp cd because my keyboard aint working before Ubuntu has loaded. I cant even get to my BIOS because my keyboard wont work :S 

Why doesent my keyboard respond?
What can I do to format my harddisk?

Thanks!

 /Junn

---

### Post by loserboy on 2006-08-08
from one noob to another here....

there isnt any reasn I know of that ubuntu should effect you keyboard before it starts booting through grub, so you should at least be able to change your bios settings.

make sure you keyboard is connected well (which u prolly already did)

is it a usb or ps/2 connection, if its usb i would suggest testing it with a ps/2 if you have one lying around.

---

### Post by bscbrit on 2006-08-08
loserboy is probably correct.  You will need to use a PS2 keyboard because the USB drivers are not loaded until the OS is installed.  You can use a USB to PS2 connector to overcome this problem but, unless you are an ubergeek, you probably haven't got one lying around.

---

### Post by loserboy on 2006-08-08
lol i have 3 right next to me  and a couple of those stupid digital to analog adapters for monitors  :)

---

### Post by xpod on 2006-08-08
my usb keyboard worked fine in cd mode install mode and installed mode?

---

### Post by bscbrit on 2006-08-08
Welcome to the forum! :D

---

### Post by bscbrit on 2006-08-08
xpod - it depends on whether your motherboard's BIOS contains USB drivers. Some do, some don't.  Some have them but they are switched off by default and you have to get into the BIOS to turn them on - pressing Del during boot - but you haven't got a keyboard because it is turned off in the BIOS - ..... you get the picture.

---

