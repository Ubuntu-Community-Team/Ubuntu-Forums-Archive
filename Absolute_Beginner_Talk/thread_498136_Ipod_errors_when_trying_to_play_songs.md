---
title: "Ipod errors when trying to play songs"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by devapea on 2007-07-11
I have an Ipod that seems to mount ok but I cannot get any songs to play.  Ive installed nearly all the players banshee, amarok, Floola, gtkpod and Rythmbox.  I try to play a song and the program scrolls thru all the songs leaving red error flags behind.  I have gstreamer installed.  Im thinking that its a format issue or plugin issue.  I have the name of the ipod in the mount point (is this correct?) but Im not sure what to list as the file system.   Thanks in advance for any help!

Ipod stats:
gen:  fifth
model videowhite
model # xA444

---

### Post by tgalati4 on 2007-07-11
If the songs have DRM then they might be difficult to play.  Do you have standard mp3 songs on the iPod?

---

### Post by devapea on 2007-07-11
yes I tried playing the mp3 songs as well and no dice.  I also copied one of the mp3's to the hardrive but am unable to play it as well.  error states "**could not open resource for writing**."
Interesting to note that the ipod mounted and worked fine before upgrade to newest ver. of feisty fawn. thanks again.

---

### Post by tgalati4 on 2007-07-11
That's key information.  Post relevant portions of dmesg.

---

### Post by devapea on 2007-07-11
Hopefully this helps:

[   57.229681] NET: Registered protocol family 10
[   57.229793] lo: Disabled Privacy Extensions
[   68.185353] eth0: no IPv6 routers present
[  658.358244] usb 4-1: new high speed USB device using ehci_hcd and address 2
[  658.492220] usb 4-1: configuration #1 chosen from 2 choices
[  658.621317] usbcore: registered new interface driver libusual
[  658.632609] Initializing USB Mass Storage driver...
[  658.632745] scsi0 : SCSI emulation for USB Mass Storage devices
[  658.632812] usbcore: registered new interface driver usb-storage
[  658.632816] USB Mass Storage support registered.
[  658.632985] usb-storage: device found at 2
[  658.632987] usb-storage: waiting for device to settle before scanning
[  663.628409] usb-storage: device scan complete
[  663.629158] scsi 0:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  663.685182] SCSI device sda: 14651280 2048-byte hdwr sectors (30006 MB)
[  663.686544] sda: Write Protect is off
[  663.686547] sda: Mode Sense: 68 00 00 08
[  663.686550] sda: assuming drive cache: write through
[  663.688664] SCSI device sda: 14651280 2048-byte hdwr sectors (30006 MB)
[  663.689914] sda: Write Protect is off
[  663.689917] sda: Mode Sense: 68 00 00 08
[  663.689919] sda: assuming drive cache: write through
[  663.690341]  sda: sda1 sda2
[  663.702358] sd 0:0:0:0: Attached scsi removable disk sda
[  663.718753] sd 0:0:0:0: Attached scsi generic sg0 type 0

---

### Post by tgalati4 on 2007-07-11
dmesg looks normal.  What was the last update that you applied to Feisty?

---

### Post by devapea on 2007-07-11
well besides installing and unistalling all those different media players that I mentioned Ive just been installing the usual feisty updates that come in every couple a days.  Last ones dealt with updates to open office mostly. I'm gonna try my friends creative player on my computer and I'll try my ipod on my friends computer.  Thanks.

---

### Post by tgalati4 on 2007-07-11
Can you play any mp3's on your system?  Perhaps you borked the mp3 libraries?

What happens when you do:

aplay mycheesymp3testfilethatIknowworksproperly.mp3

---

### Post by devapea on 2007-07-11
Ok first of all You're a genius!! I'm gonna name my firstborn after you .  Tgalati4 will be a strange name for a lil girl or boy but he'll/she'll get used to, or maybe I shouldnt even breed but I digress.

So I downloaded an mp3 of the web and of course it didnt work in any of my players.  So I searched around for help on the forums and found the pages dealing with restricted codecs such as gstreamer.   Long story short I'm now able to play mp3s on half my players ( the other half say that they cannot write from source)  I'm also able to load and play my Ipod on Amarok so happy for the day.  Thanks again.:)

---

