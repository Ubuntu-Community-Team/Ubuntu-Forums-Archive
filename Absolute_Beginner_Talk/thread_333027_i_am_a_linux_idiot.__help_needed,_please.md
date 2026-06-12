---
title: "i am a linux idiot.  help needed, please"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by bibliolib on 2007-01-06
i would like to switch to ubuntu on my desktop.  i can't get my dial up modem to work, however.  i have run a scan modem and can post the results, if that will help anyone.  i would like help with how to get the modem to work so that i can actually switch from windows to linux.  thanks!  :-?

---

### Post by MkfIbK7a on 2007-01-06
first of all you arent an idiot:D
second try posting scan modem and we will try to help

---

### Post by Maxcribbin on 2007-01-06
I agree,   Anyone wanting to switch from windows is no idiot!

Best thing i've ever done.



Carl.

---

### Post by bibliolib on 2007-01-06
i am feeling like a total idiot.  :-?   i don't understand any of the linux speak.    for example, i would have no idea how to put script into something.  so yes, i am an idiot.  maybe i will learn through all of this however.  

here is the scanmodem information:

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2006_December_25


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:09.0	11c1:048c	11c1:044c	Communication controller: Agere Systems V.92 56K WinModem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:09.0 ----
[17179570.176000] PCI: Error while updating region 0000:00:09.0/0 (20000000 != 00000000)

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:11.6	1106:3068		Communication controller: VIA Technologies, Inc. AC'97 Modem Controller 

 Modem interrupt assignment and sharing: 
201:       1331   IO-APIC-level  VIA8237

 --- Bootup diagnositcs for card in PCI slot 00:11.6 ----
[17179631.692000] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[17179631.692000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179631.692000] PCI: Via IRQ fixup for 0000:00:11.6, from 0 to 9
[17179632.444000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179632.948000] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[17179632.948000] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13

 The PCI slot 00:11.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

PCIbus=00:11.6
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Flags: medium devsel, IRQ 201
	I/O ports at dc00 [size=256]
	Capabilities: <access denied>

---

### Post by bibliolib on 2007-01-06
i forgot.  i should mention that i have switched the bios to be a non pnp os.  but that is all i have done.  also, i can't switch to broadband because it's not available where i live yet.  so i am stuck with dial-up.  i so hope there is a solution to my problem.  :???:

---

### Post by Maxcribbin on 2007-01-06
Erm... Move house??

There will be a solution, im new here too and still learning.
I use the search facility on the forum homepage.

Use keywords and you can usually find what you need.

All i can say is, make sure the modem is attatched properly.
(I've made that mistake before!)

Carl.

---

### Post by macogw on 2007-01-06
Well, I don't use dial-up so I can't help with that, but I can answer something else you said.  When we give you a code to copy and paste or type in, click at the top at Applications, then go to Accessories, and click on Terminal.  Put the commands in one liine at a time, hitting enter in between (if there are multiple ones).

And honey, you're not an idiot.  I spent the first month of Ubuntu IMing and pestering an online friend constantly looking for help on various things.  They weren't configuration things, but I was trying to get my mp3 player to work.  I never did figure that one out, since it broke 2 weeks later (non-replaceable dead battery).  I got lucky in having most everything work OOTB, but I still managed to find a lot of things to need help with like setting it up to type in Japanese and Russian aside from English, WPA support, etc.  I've been using it for 6 months, and trust me, after the initial difficulties, it gets amazingly easy.  All the help I got on here taught me to not be afraid to use the terminal and that the terminal is usually much faster than the GUI way.  It's a steep learning curve, but you'll be able to diagnose other people's problems faster than you could on your old OS.  I still need to actually see the computer to fix a Windows computer because I never really learned how it all worked, but with this, I do get how it works.  You'll learn too, and you'll learn fast.  That's how Linux is.  If you set out to learn to do anything, you'll learn 10x more than you expected.

---

### Post by bibliolib on 2007-01-06
> **macogw said:**
> Well, I don't use dial-up so I can't help with that, but I can answer something else you said.  When we give you a code to copy and paste or type in, click at the top at Applications, then go to Accessories, and click on Terminal.  Put the commands in one liine at a time, hitting enter in between (if there are multiple ones).

oh thank you!!!!  i was worried i would never know what i was supposed to do!!!  i had no idea where to put anything were someone to tell me to put something somewhere.

---

### Post by bibliolib on 2007-01-06
anyone?  :(

---

### Post by Maxcribbin on 2007-01-06
Try here  [http://www.linmodems.org/]("http://www.linmodems.org/")

an here  [http://ubuntuforums.org/showthread.php?t=262666&highlight=installing+dial+up+modem](http://ubuntuforums.org/showthread.php?t=262666&highlight=installing+dial+up+modem)


Carl.

---

### Post by d4ndy on 2007-01-06
Is your modem internal or external? If it's an external modem, I might be able to help cos that's what I've got. My box came with an internal (win)modem built in, but I got tired of downloading drivers from Linmodem or wherever everytime I upgraded my kernel, so I popped for an external hardware modem. It kinda looks, though, like you've got a so-called "soft modem."
Ubuntu (or any linux, really) will find a hardware modem straight off, and then it's just a matter of setting up the dialing program (pppd or others).

---

### Post by bibliolib on 2007-01-06
> **Maxcribbin said:**
> Try here  [http://www.linmodems.org/]("http://www.linmodems.org/")

an here  [http://ubuntuforums.org/showthread.php?t=262666&highlight=installing+dial+up+modem](http://ubuntuforums.org/showthread.php?t=262666&highlight=installing+dial+up+modem)


Carl.

i've sent the scanmodem to the linmodems discussion group.  i will look at the other link.  thanks.  :-)

---

### Post by bibliolib on 2007-01-06
> **d4ndy said:**
> Is your modem internal or external? If it's an external modem, I might be able to help cos that's what I've got. My box came with an internal (win)modem built in, but I got tired of downloading drivers from Linmodem or wherever everytime I upgraded my kernel, so I popped for an external hardware modem. It kinda looks, though, like you've got a so-called "soft modem."
Ubuntu (or any linux, really) will find a hardware modem straight off, and then it's just a matter of setting up the dialing program (pppd or others).

it's an internal modem.  pci.

---

### Post by bibliolib on 2007-01-07
i ran aida (?) and it says i have no modem, after i took the pci modem out.  however, when i run some other program that starts with an l and has about 5 other random letters (i was on the phone with my boyfriend and he talked me through all that), it says i have a via tech ac'97 modem controller.  does anyone know what that means or how to disable that?  i can't find it on my bios.  i'm still trying to get ubuntu to work, but i'm about to give up.  :-(

---

### Post by ardvark71 on 2007-01-07
Hi....

I will happily give you the same advice that has helped me and that I've given to others on here....buy a serial external hardware modem. They usually work with Linux out of the box with very little configuration. You can usually buy them cheap on ebay or other online auction sites. I would also recommend a program called "Gnome PPP" as a means to getting online but it's a matter of personal preference. "Networking" does the same job too.

Best Regards...

---

### Post by Duck2006 on 2007-01-07
[http://www.compuvative.com/ac97-modem/](http://www.compuvative.com/ac97-modem/)

This may help

---

### Post by houstonbofh on 2007-01-07
Just remember as you go though this.  There is a difference between ignorance and stupidity.  Ignorance can be cured,  Stupidity is forever. :D

That said, Winmodem support is flat out bad.  Try installing drivers for one on Windows if you don't know the model or have a driver disk.  I have a box full of them because I can't find Windows drivers.  (Most of my clients are on Windows...)  Getting a real modem can solve that problem quite well.

---

### Post by Cariboo1938 on 2007-01-07
Hello and welcome to the Ubuntu community.
I had also problems with the Dial-Up connection.
What kind of modem do you have. Extern or intern? Winmodem or chip set based (hard ware) modem? Mine for example is TOPIC SEMICONDUCTOR Corp TP560 Data/Fax/Voice 56k modem.
Open a terminal and check if your system detected a modem by typing the command```
sudo lspci
```You should find a line similar to this:> 02:07.0 Communication controller: TOPIC SEMICONDUCTOR Corp TP560 Data/Fax/Voice 56k modem
There is also a How-To install a dial-up connection where you find important info on this issue...click [HERE]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")
Good luck :)

---

### Post by bibliolib on 2007-01-13
ok.  i got a hardware modem - conexant hcf by dell.  i installed unbuntu after i put the modem in so no going back now!  :-)  i ran scanmodem and it is still showing the via tech modem controller, but it also shows the hcf modem.  i have downloaded drivers i think will work, but i've not had a chance to install them yet.  how do i know ubuntu is recognizing my modem?  i did aida and it sees it.  i will do lspci when i get home and see if it is recognizing it as well.  when i try to do a /proc/pci, i get no such file exists, though.  and i don't know which port the modem is on and don't know how to find it.  nothing that i have found in online instructions really addresses this for me yet.  i have also downloaded gnome ppp and will try to install it as well.  do i need anything else?  sorry for all the questions, but since i have gotten the hardware modem and have installed the os, i am really excited about using ubuntu.  all i need now is to get the modem to work!!!  :-)

---

### Post by bibliolib on 2007-01-13
anyone?  here are the results of the scanmodem after i installed the hcf modem.  

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2006_December_25


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:09.0	14f1:1033	13e0:020d	Communication controller: Conexant HCF 56k Data/Fax Modem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:09.0 ----

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:11.6	1106:3068		Communication controller: VIA Technologies, Inc. AC'97 Modem Controller 

 Modem interrupt assignment and sharing: 
193:       1352   IO-APIC-level  VIA8237

 --- Bootup diagnositcs for card in PCI slot 00:11.6 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

PCIbus=00:11.6
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Flags: medium devsel, IRQ 193
	I/O ports at c800 [size=256]
	Capabilities: <access denied>

---

### Post by houstonbofh on 2007-01-14
Go into your BIOS and disable the onboard modem.  That will get rid of the false detection of the Via modem, and should allow you to go on and configure the conexiant.  Good Luck!

---

