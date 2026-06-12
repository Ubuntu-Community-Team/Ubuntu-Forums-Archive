---
title: "Artifacts when GUI first loads"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by D_jmc on 2006-11-16
Hi, This is my attempt at the world of open source OS's.

I already downloaded Ubuntu 6.10, created the cd, it boots, I get the menu to either install, load with safe graphics memtest, etc.

I first chose install, it started to load up, got the ubuntu graphic and a status bar. It seems to load up fine, what happens next is that I get a an orrange screen and the mouse cursor. Then the what would be a splash screen (i've already tried it on another pc so I Know what supposed happen) but it looks corrupted and also little black lines randomly dotted around the screen, and then it hangs.

I've also tried it with safe graphics and the same happens,
amd 3700
2gb ram
250gb hdd
geforce 7900gt 

I would appreciate any help offered, thanks!

---

### Post by wpshooter on 2006-11-16
Try the ALTERNATE CD.

---

### Post by D_jmc on 2006-11-16
Thanks for the quick reply, downloading now. Is this a known problem, does the alternate cd tend to get round this?

cheers.

---

### Post by lapsey on 2006-11-16
i think it's to do with the live cd drivers not covering your hardware fully. I know I had that problem with integrated intel gfx (dell optiplex)

install ubuntu in text mode will let you install but you **may** need to configure x.org yourself on the command line to get graphics going since the default config may not be suitable for your hardware. there are guides on that tho, and its quite easy.

---

### Post by D_jmc on 2006-11-16
Yeah its definately a driver issue, used the oem setup all was fine, got to the username/password screen, no artifacts and as soon the desktop loads i get the artifacts again.

Again, thanks for replies, off to find details on how how edit x.org.

Cheers

---

### Post by D_jmc on 2006-11-16
Sorry to keep posting guys,

I cant seem to find a way to correct this problem. All I want to be able to do for now is boot into Ubuntu, then I will tackle the nvidia problems.

After some poking around on the web sounds like its the NV drivers loading up and crashing the system, so if I configure to use Vesa drivers it should work right?

Can someone tell me how to edit xorg.conf so that it will use the basic Vesa drivers? its all a little bit daunting for me at the moment, but I'm sure I'll get the hang of all this with help you lot.

Cheers. Once again.

*nevermind, managed to boot ubuntu using vesa drivers instead of NV, just got to figure out how to get my nvidia card to work so that I dont have to wait half an hour to scroll down on a website.*

*resolved*

---

