---
title: "Booting into CD?"
date: 2007-06-20
forum: Apple PPC Users
---

### Post by BetaMaster on 2007-06-20
I recently bought a G3 Wallstreet PowerBook on eBay. It came installed with OSX. It has a 233MHz CPU and 160MB of RAM. So, needless to say, it doesn't run OSX very well, and I've been trying to install Xubuntu on it. I can't figure out how to boot from CD though, and it only has a 2GB HDD so I can't install Classic to run BootX. Without using BootX, how can I boot from the Xubuntu install CD?

Thanks

---

### Post by linear on 2007-06-21
See [this thread]("http://ubuntuforums.org/showthread.php?t=431907"). You can't get away from BootX.

---

### Post by BetaMaster on 2007-06-23
Okay so I NEED BootX with OS9. Fair enough. I have the OS9 install discs.
I tried installing it today. I couldn't get the laptop to boot from the CD.
I tried holding down C while the computer started up. I'd get the grey background with the classic smiling Mac, then the screen would go black and OSX would start up.
What's the problem?

---

### Post by MACRI on 2007-06-23
i thought you had to hold the del key to boot from disk?

---

### Post by BetaMaster on 2007-06-23
You do? Great, I'll try that!
I had read to hold down C, but that could very well be wrong.
I'll let you know if it works.

---

### Post by stmiller on 2007-06-23
GIYF, and try the search feature on this forum. This is asked weekly. Hold down 'c' to boot from a CD on a Mac.

---

### Post by MACRI on 2007-06-23
im not sure, i do not regularly use macs but a friend of mine was going through some problems and he claims holding the delete or del key worked for him!? maybe this is only on newer intel macs but you never know computers are a tricky thing :/

---

### Post by BetaMaster on 2007-06-23
> **stmiller said:**
> GIYF, and try the search feature on this forum. This is asked weekly. Hold down 'c' to boot from a CD on a Mac.
I already tried holding down 'c' multiple times and never could boot to the OS9 install CD. What's the problem then?

---

### Post by Auria on 2007-06-23
holding down alt works on newer computers, no idea about the older ones though

stmiller: come on he said in his 2 posts before your answer that he was pressing C - before telling newbies to serach the forum, you should perhaps read the thread :-P

---

### Post by pxwpxw on 2007-06-23
> **BetaMaster said:**
> I already tried holding down 'c' multiple times and never could boot to the OS9 install CD. What's the problem then?

I think maybe the problem is that your mac will boot from a macosx cd but not from a macos9 cd ,  because you have a new world mac there, they dont boot from macos9 (i tried it here  on g4 and g5,  but g3 come in old and new world.) 
 
To settle the question of vintage, if you have macosx on your G3, please open a terminal (terminal.app) and check the open firmware setting this way and post the result (if any):
```

sudo nvram -p

```

If its new world you dont need BootX you can boot from open firmware using yaboot on macosx.

EDIT:
WallStreet PB is OldWorld.

---

### Post by BetaMaster on 2007-06-24
Okay I'm sort of confused now. When the OS9 CD is in the drive, and I start up the Powerbook, it shows the classic bootup screen, then promptly reboots into OSX. This happens regardless of if I'm holding down 'c', 'Delete', or nothing at all. If the CD is not in the drive, it boots into OSX, as one might imagine.
What's the problem? Do I have a bad OS9 install disc? I got it with the laptop, which I got on eBay, and the install disc is a copy, but I figured that shouldn't matter.

---

### Post by BetaMaster on 2007-06-24
> **pxwpxw said:**
> I think maybe the problem is that your mac will boot from a macosx cd but not from a macos9 cd ,  because you have a new world mac there, they dont boot from macos9 (i tried it here  on g4 and g5,  but g3 come in old and new world.) 
 
To settle the question of vintage, if you have macosx on your G3, please open a terminal (terminal.app) and check the open firmware setting this way and post the result (if any):
```

sudo nvram -p

```

If its new world you dont need BootX you can boot from open firmware using yaboot on macosx.

Hey, sorry to double-post, the post just above this was typed up several hours ago and I forgot to submit it.
Anyway, I just tried that command. Here's the result:
```

fcode-debug?    false
0 0 1 ck if 0 and else dup 1 = if 3d 0 1 else f 3d 0 2 then ck if 40 or then theunselect-devL$LLover $X $X ;bus ;; ms 0 to &f else drop then ;op then bye ;
screen-#rows    40
boot-file
oem-banner
boot-command    0 bootr 
oem-logo
real-size       0x100000
virt-base       -1
boot-args
input-device    kbd
output-device   screen
boot-device     ide0/@0:5
diag-switch?    false
screen-#columns 100
auto-boot?      true
oem-logo?       false
diag-file
oem-banner?     false
load-base       0x600000
selftest-#megs  0
real-base       -1
virt-size       0x100000
little-endian?  false
pci-probe-list  -1
diag-device
use-nvramrc?    true
real-mode?      false

```

---

### Post by pxwpxw on 2007-06-24
Looks like late OldWorld, but capbable of running MacOSX goodies such as nvram and terminal, might be running classic already?. Also maybe capable of booting a ubuntu install cd using open firmware, and doing away with macosx, but that also requires restarting after the install from open firmware which is decidedly tricky to get set up. (Found some old 1998 linuxppc manuals here referring to g3 booting). But dont change macosx before you know what to do. Can you open the ubuntu install CD from Macosx to check what it sees there?

Macos9 plus BootX is the simplest way to go. Needs about 200MB or less.
A copied Macos9 system install CD will not autoboot unless it was copied using macos9 special disk copying app to get all the macos9 drivers and system files. I have tried that both ways.  

You can get a good macosx 9.2.1 install cd from : 

[http://www.applerescue.com/](http://www.applerescue.com/)

And BootX info and download is at 

[http://penguinppc.org/bootloaders/bootx/](http://penguinppc.org/bootloaders/bootx/)

[http://penguinppc.org/historical/benh/](http://penguinppc.org/historical/benh/). 

Needs macos9 or classic to unsit them I think. For BootX you would need a small macos partition - say 200MB or less.
You have to organise downloading everything you need, say to a usb stick, because this may not be possible after a minimal Macos9 install (no network access). 

 But then it depends on what you want to install and do with it, because disk space is very tight. Perhaps a bigger cheap used drive might be available. An external usb drive might even be a possibility. But scsi drives are a problem for feisty.

There are other distros and desktops that use less space, but for xubuntu -   
2GB HDD would only do for a  minimal desktop,  xubuntu feisty desktop on an ibook used 1.5GB plus a swap partition, but that is before saving any user files, or adding apps for multimedia etc. A good commandline console installation will fit in 800MB plus 200MB swap (one here on an old mac).

Maybe you could try OpenFirmware booting the cd, but you would need to be seriously enthusiastic to sort that one out (its possible, using "quik" or other bootloader for open firmware, but probably not with current installers ).

---

### Post by BetaMaster on 2007-06-24
Okay thanks for helping me out with this. I opened up the Xubuntu install CD, and these were the contents:
```
casper/
dists/
etc/
install/
pics/
pool/
ppc/
preseed/
cdromupgrade
md5sum.txt
README.diskdefines
```
Apparently the CD should boot, I contacted the guy who sold me the laptop and he says he tested it all and it worked. I'm experimenting to try and find out what the problem might be.

---

### Post by pxwpxw on 2007-06-25
That CD is the Desktop CD (it has casper). Your Wallstreet does not have enough ram to run a graphical desktop and install. You will need to download the Alternate or Server install CD iso to use a text mode install. 

While you are experimenting you might try getting the partition info as seen by macosx/terminal, if you can run this from terminal in macosx - very usefull for setting up if it works.
```

 sudo pdisk -l

```
Should produce a listing of partitions and their numbers, linux style.
> 
Apparently the CD should boot, I contacted the guy who sold me the laptop and he says he tested it all and it worked.

The macos9 cd?

Maybe he could tell you exactly how he started it up? (what keys held etc.)

---

### Post by BetaMaster on 2007-06-27
Yes, I meant the OS9 CD, sorry.
I contacted him and it turns out he had sent me a CD of OS9 that wasn't designed for the G3 Wallstreet. I have the correct CD now and am currently installing OS9 onto the Wallstreet.
Once it finishes, I should be able to run BootX by following instructions?
Also, I thought that the Xubuntu Live CD would work if you had at least 128MB of RAM on your computer? I have 160MB so it should run, although not necessarily very well. I have purchased two 256MB sticks of RAM (one low-profile and one high-profile to fit in the Powerbook) so, if it doesn't run, worst case scenario is I'll run OS9 until the RAM arrives, in which case I can replace the memory in the 'book and try it then.

Also, this is slightly off-topic question, but maybe someone can answer it: OSX was obviously running painfully slow. Was this due to the RAM or the CPU? Which would have a bigger impact, or better yet, would the CPU have much impact at running minimal applications (think: Internet, AIM, maybe GIMP at one point or another for drawing)?
I have a 233MHz G3.

---

### Post by pxwpxw on 2007-06-28
Good. Hope you partitoned the disk for free space for ubuntu?
You can run a Live CD, but it will be much slower than a system on the hard disk, and slow to install, and may have graphics problems - but no reason not to try it if you want to, just be prepared to experiment.

BootX will run it, it just needs different kernel settings in BootX. 
There is a howto, if you start from the PowerP-Wiki -> PowerPC FAQ -> Zcats Howto for OldWorld Macs. (kernetl args for Casper). Also you can see these in the yaboot.conf that is on the CD in /etc or /install (but you dont use yaboot).

Its just that MacosX is writen for current Macs, with Ghz CPU speed and fast disks, and GB ram, so can be a struggle for earlier macs.

If you can put maximum RAM in, should be a worthwile improvement. I dont know if it would be possible or cost effective to try to change the CPU speed. Internet and gimp should be quite usable, but not as fast as on a current mac, multi media might be a bit limited, but I cant speak from experience there, maybe others could comment. Main limit would be the disk space I think. An external drive for storage would be good, but I cant remember if your Powerbook has usb/firewire.

---

### Post by BetaMaster on 2007-06-28
No, I didn't partition the free space for Xubuntu, where would I do that? Does the Xubuntu install disk come with GParted? (I haven't set up BootX yet because I just realised my wireless card isn't compatible with OS9)
Alright thanks, I found the howto, and I'll try that later on today.

I don't know if it'd be cost-effective to upgrade the CPU either. I know you can upgrade the Wallstreet to a G4 500MHz CPU but that would cost around $200, which probably isn't worth it.
Hopefully Xubuntu will run fine (and it should) and that'll be all I really need.
I'll let you know if it works!

---

### Post by pxwpxw on 2007-06-28
There is probably a Gparted in the Desktop CD (it needs X windows which is not in the AlternateCD). Yes you can resize the macos partition from either CD, but it can be a problem if the macos files are fragmented over the disk, it s better to just install macos on a smaller partition, leaving clean space for ubuntu.

It will be interesting to see how the Live CD goes.

---

### Post by BetaMaster on 2007-07-04
Well, a little bit of an update. I found a Powerbook Pismo on eBay with a 400MHz processor and USB/FireWire ports, for basically the same price I bought this Wallstreet for. I've decided to sell the Wallstreet and get the Pismo instead.
Thanks again!

---

