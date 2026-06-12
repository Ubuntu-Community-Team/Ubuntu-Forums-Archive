---
title: "Creative Zen 20GB Player +LG Phone"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by makz 18 on 2006-04-29
I have a creative zen 20gb player and the software only has a windows driver. Do i have to run it off of a windows emulator, or is there 3rd party software which will work? Also, to save space, all my songs are in wma format, are there any players which will handle these files? I know XMMS handles mp3s, but its to much hassle to convert all the songs back again.

Likewise, i have a LG u8368, will i need to run the software for it with a windows emulator, or is there 3rd party software? Also, if i transfer using bluetooth, will it work?

Cheers

Makz 18

---

### Post by tseliot on 2006-04-29
[QUOTE=makz 18]I have a creative zen 20gb player and the software only has a windows driver. Do i have to run it off of a windows emulator, or is there 3rd party software which will work? Also, to save space, all my songs are in wma format, are there any players which will handle these files? I know XMMS handles mp3s, but its to much hassle to convert all the songs back again.

Likewise, i have a LG u8368, will i need to run the software for it with a windows emulator, or is there 3rd party software? Also, if i transfer using bluetooth, will it work?

Cheers

Makz 18[/QUOTE]
Xmms plays also wma.

Does your Creative Zen has a USB port? If so, you should be able to connect it to your computer and to browse its contents as if it were a common usb storage media.

If you want to use bluetooth:
```
sudo apt-get install gnome-bluetooth kdebluetooth
```

---

### Post by qamelian on 2006-04-29
If you Creative player doesn't use one of the newer firmware versions, it should work with Gnomad or Neutrino, both of which can be installed from the Ubuntu repositories. If you have a player with one of the most recent firmware versions, it get's tougher as the new firmaware only supports Media Transport Protocol which requires libmt and requires you to compile Gnomad from source. This isn't usually very difficult, but I have yet to get libmtp working correctly. :o(

---

### Post by makz 18 on 2006-04-30
The player does have one of the newer firmware versions, and the comp couldn't locate any files when i plugged it in so i guess i'll just run the creative software with wine or something.

---

### Post by Omnios on 2006-04-30
Hi I have a 6 gig zen micro and had a few problems with it, First off it came with the new firmware which I solved by going to the Creative site and downloading and installing the win98 firmware from there. You will still need to do this in windows thoguh and I have not tryed it in wine. Lastly you need Gnomad2 to put files onto it, I used the Drapper package as recomended on this site as the other package did not work for me. Also you will need to run gnomad2 as root with sudo for it to see the usb port.

---

