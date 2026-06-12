---
title: "(POWERPC) screen goes blank while installing Ubuntu from CD"
date: 2016-10-17
forum: Apple Hardware Users
---

### Post by boyborg690 on 2016-10-17
While I'm upgrading my school's old PowerMac G5 (Adding 8 GB of ram, installing a new hard disk, adding linux .etc)
My computer crashes whenever I get to the "UBUNTU 12.04" loading screen. I chose the 64 bit ISO and burned it onto a CD with Disk Utility and I restart the computer holding C. It came up to the black screen that comes up like MS-DOS in full screen. I press enter and it does its normal boot sequence from the black screen to a white screen to the Ubuntu 12.04 loading screen. Its just plain text 

                                              ([B]Like this.) [UBUNTU 12.04 &#8203;]
                                                                                     .  .  .  .  .
[/B]

And it seems to be booting fine until it goes black screen. The computer is still going but the display turns off. It has a green LED while its displaying but when there's no input it goes orange. I'm using an AGP Radeon 9600 with a dual link DVI-D to VGA display adapter. a few days ago it would do this after about 3 minutes of installing it but 4 days ago it stopped. Any help here? There's not much else I can say.

---

### Post by ajgreeny on 2016-10-17
Why 12.04 which will lose support in April next year?

You would do much better to use either 14.04 or 16.04 both of which have 5 years support from their first release, ie April 2019 and April 2021, and you may even find that the problem you have with 12.04 is gone with the later versions.

Other than that I can not help as I have almost no knowledge of Apple hardware.

---

### Post by ernsteiswuerfel on 2016-10-17
@boyborg690:
You can try booting the ISO with *live-nosplash* at the MS-DOS-like boot-prompt. Press *tab* at the boot-prompt for showing all possible options. Then you should get at least more output where the boot-process stalls.

Or you could try recent Ubuntu MATE 16.04.1/16.10 with *live-nosplash radeon.agpmode=-1* at the boot-prompt and create a suitable /etc/X11/xorg.conf like in this [thread]("https://ubuntuforums.org/showthread.php?t=2339861").

---

### Post by boyborg690 on 2016-10-17
I'm using 12.04 because for 1 its UBUNTU not LUBUNTU (I don't want lubuntu because my teacher asked for UBUNTU) and i'm not using a newer distro because the PPC has an IBM CPU not an Intel CPU. They're not compatible in the slightest so 12.04 is my only option. I don't want the server version either.

---

### Post by ernsteiswuerfel on 2016-10-17
> **boyborg690 said:**
> [...] i'm not using a newer distro because the PPC has an IBM CPU not an Intel CPU. They're not compatible in the slightest so 12.04 is my only option. I don't want the server version either.
If you want something which has the look of Ubuntu 12.04 try [Ubuntu MATE]("https://ubuntu-mate.org/download/") 16.04/16.10. There is also a PowerPC available which of course runs on a G5. As a matter of fact I am posting this from a PowerMac G5 right now, runnung Ubuntu MATE 16.10. There are also PowerPC versions from openSUSE, Debian, Fedora and Gentoo.

---

### Post by apple-apple on 2016-10-18
I've got to agree on Ubuntu Mate. A few of us with G5's are running it. Works well.

---

