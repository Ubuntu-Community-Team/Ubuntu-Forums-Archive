---
title: "Help diagnosing a hardware (?) problem before trying to dual boot"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by starchildmom on 2006-04-18
Now that I have fairly successfully installed Edubuntu on three of the 4 computers we use for homeschooling, my 9yo would like to dual boot his computer. I know how to do the dual boot installation (actually he will be doing it, but he did the entire install and set up on our "lab" computer). Problem is the video is all funky and we want to fix it before installing Ubuntu.

There are mulit-color artifacts all over the screen from the moment the computer is powered on (before the bios even loads). When windows loads there are random artifacts, lines, trails, but the actual rendereing of graphics is fine. I am assuming that since the problems start at the moment of power on that it is a hardware failure, not a driver issue (drivers are up to date). Can I be sure that it is the video card, or could it be the motherboard? How can I tell which one without putting the video card in another computer (none with agp available)?

Video card is a Radeon 7500, motherboard has an ATI chipset with onboard sound but I do not remember the model number. Processr is an AMD 2400, 200 gig hardrive, and it has 512 ddr. I built this computer from scratch four years ago. It is old, but does what he needs. I do not want to spend very much on it though, since replacement desktop will probably be purchased later in the year.

---

### Post by jorn on 2006-04-18
Can't you test with a spare pci-videocard?
Jorn

---

### Post by Chuck_W on 2006-04-18
Maybe my experience will help. My Ubuntu machine is an old Dell Optiplex GX200. It has video built-in on the motherboard. The onboard is flaky ( a known problem with these units). When I had Windows on it I could get around the problem with a PCI card. This doesn't work with Ubuntu. For some reason it ignores the card and tries to use the onboard even though the monitor is connected to the PCI card. If your machine has onboard video that is going bad Ubuntu may not work for you.

---

