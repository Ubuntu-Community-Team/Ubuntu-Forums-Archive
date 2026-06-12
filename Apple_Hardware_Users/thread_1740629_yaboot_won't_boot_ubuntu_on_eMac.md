---
title: "yaboot won't boot ubuntu on eMac"
date: 2011-04-27
forum: Apple Hardware Users
---

### Post by benlippincott on 2011-04-27
Hey-lo! I’ve got a strange problem. I am trying to install Ubuntu  10.10 on an old eMac my science teacher has. There is this school  program called BOSS where you do all sorts of missions in “outer space”  and fly a space shuttle simulator. The problem was, Macs don’t like the  insert key, (they use a help key) nor could I figure out how to open the  Dosbox keymapper in Mac OS X. This was a problem because insert is a  vital control for Microsoft Space Simulator, the program we are using.  So, in a fit of sudden creativity, I suggested we install Ubuntu. I knew  that Apple didn’t support Intel processors until the white iMacs came  out, so I downloaded the PowerPC version. I burned the 710 MB ISO to a  700 MB CD-RW, using ImgBurn on a Windows PC, which I chose because  ImgBurn supports overburning. I had ImgBurn verify the CD, and it came  up with no errors.
Next I placed the CD in the CD tray of the eMac, then booted up from it.  I booted to the Ubuntu Live CD with no problems, then installed Ubuntu  to /dev/hda/ with the default partitioning. PPC Ubuntu uses yaboot to  boot up, and when I restarted, I got stuck at the yaboot menu. I just  let yaboot do it’s thing, but it just sits there without doing anything.  I really need an answer ASAP.
 BL

---

### Post by conal on 2011-04-27
When you say "default" do you mean you wiped the had-drive and installed ubuntu insead of os x or you resized the os x parition and installed ubuntu after it?. I installed MintPPC on an eMac the other day and it worked very well - you may want to try this if you have no luck with Ubuntu.

---

### Post by linuxftw3 on 2011-05-01
> **benlippincott said:**
> Hey-lo! I’ve got a strange problem. I am trying to install Ubuntu  10.10 on an old eMac my science teacher has. There is this school  program called BOSS where you do all sorts of missions in “outer space”  and fly a space shuttle simulator. The problem was, Macs don’t like the  insert key, (they use a help key) nor could I figure out how to open the  Dosbox keymapper in Mac OS X. This was a problem because insert is a  vital control for Microsoft Space Simulator, the program we are using.  So, in a fit of sudden creativity, I suggested we install Ubuntu. I knew  that Apple didn’t support Intel processors until the white iMacs came  out, so I downloaded the PowerPC version. I burned the 710 MB ISO to a  700 MB CD-RW, using ImgBurn on a Windows PC, which I chose because  ImgBurn supports overburning. I had ImgBurn verify the CD, and it came  up with no errors.
Next I placed the CD in the CD tray of the eMac, then booted up from it.  I booted to the Ubuntu Live CD with no problems, then installed Ubuntu  to /dev/hda/ with the default partitioning. PPC Ubuntu uses yaboot to  boot up, and when I restarted, I got stuck at the yaboot menu. I just  let yaboot do it’s thing, but it just sits there without doing anything.  I really need an answer ASAP.
 BL


try completely erasing the hard drive and reinstalling ubuntu.):P

---

### Post by vu3bjt on 2011-10-17
I have the same problem on my iBook G4 12" 1.2 Ghz with 60 GB HDD, i am getting an error at end of installation, yaboot is not properly installed, 
1. i have used the live cd of 11.10 ppc, booted from cd, ggot the desktop.
2. from my desktop i clicked on install ubuntu 11.10 and 90% installed
3. I got an error mirror not found, and after it few seconds I got Installation >crashed, continue the  testing

---

### Post by rsavage on 2011-10-17
That is not the same error.  No way. That emac had a black screen because it was suffering from a graphics problem.  There are are like a gazillion threads on how to solve that problem.

You are installing from 11.10 which is new and as far as I can tell still in a state of flux.  Do you get the yaboot screen when you reboot?  Maybe this will help [http://ubuntuforums.org/showthread.php?t=1861871](http://ubuntuforums.org/showthread.php?t=1861871) .

---

### Post by rsavage on 2011-10-17
Any progress with this?
 
Do you get the screen to press 'L' for linux?
 
What about the screen after? What does it do there? Does it just sit there?
 
What happens if you type at the prompt any of the following:
 
Linux root=/dev/sda3 
 
/boot/vmlinux root=/dev/sda3
 
hd:3,/boot/vmlinux root=hd:3
 
/pci@f4000000/ata-6@d/disk@0:3,/boot/vmlinux root=/pci@f4000000/ata-6@d/disk@0:3 
 
/pci@f4000000/ata-6@d/disk@0:3,/boot/vmlinux root=/pci@f4000000/ata-6@d/disk@0:3 initrd=/pci@f4000000/ata-6@d/disk@0:3,/boot/initrd.img
 
The above is assuming the root partition is #3. This should be the case if you've just got ubuntu installed and gone with the default settings.

---

