---
title: "Start Up Problems With Live CD"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by maltbyc on 2008-03-31
Ok so heres the deal I've tried burning 2 live cds.  One with 7.10 and one with the 8.04 beta.  It get into the main menu and try to start the live ed and I get stuck on
"kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000"
I'm trying to install the 64 bit version.  I'm running laptop with a AMD Athlon 64 X2 dual core Tk-53 with a NVIDIA GeForce graphics card and 2 gigs of ram.  I'm trying to dual boot with vista.  After this my vista has also become very slow, I don't know why this would happen because I didn't try to put anything on my HDD and I already have a partition made for Ubuntu.  I've ran live cds before a couple months without any problems but had installation problems but I thought I'd try it again but it didn't affect my vista installation.  I'm completely new to Linux, the most I've done it clicked around on a live cd of 7.10.  Anyone know what the problem could be?

---

### Post by stevescripts on 2008-03-31
Good info here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope this helps.

Make sure you use a CDR - not a CD-RW

Steve

---

### Post by maltbyc on 2008-03-31
I already have working live cds.  It just freezes at that part.  One of my friends already used the cd with 7.10 to install Ubuntu on his machine.  I get to the main screen where I can pick to start up and stuff.  Thanks anyway though.

---

### Post by ism. on 2008-04-01
Now when you say main menu do you mean the main menu to install Ubuntu or the Ubuntu desktop?

---

### Post by joshrobinson on 2008-04-01
read through this thread, sounds like it will help

[http://ubuntuforums.org/showthread.php?t=420065]("http://ubuntuforums.org/showthread.php?t=420065")

---

### Post by ism. on 2008-04-01
@joshrobinson: If he does the "check cd for bugs" option and it doesnt have any can he install it in text mode or safe graphic mode or anything like that?  Or does it not wok like that?

@maltbyc:  Can you load it in text mode or safe graphics mode?

---

### Post by joshrobinson on 2008-04-01
> **ism. said:**
> @joshrobinson: If he does the "check cd for bugs" option and it doesnt have any can he install it in text mode or safe graphic mode or anything like that?  Or does it not wok like that?

@maltbyc:  Can you load it in text mode or safe graphics mode?

its worth a shot, i havent had this issue to experience it

---

### Post by maltbyc on 2008-04-01
I just left it over night and then tried again in the morning and I installed the 8.04 beta without any issues until I went for the restart.  Then I had the same problem trying to start Ubuntu from the hard drive.  Any ideas?

---

### Post by Therion on 2008-04-01
So you were able to install to the hard drive, correct; you just can't boot from the hard drive?  If so, try this...

Reboot.  
At the GRUB countdown, ESCape out and then use F6.
Use the "E" key to edit the code and remove the word "splash" and add "noapic" to boot command:

From this: kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd **ro quiet splash**

To this: kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=25035697-3e97-4899-a5e0-2b724556f6dd **ro quiet noapic**

If that allows you to boot to the desktop, immediately go to  Applications > Settings > Splash Screen settings and set the splash screen to "none".

Reboot, and you should be good to go.

---

### Post by maltbyc on 2008-04-01
Yeah I tried that and it didn't change anything.  Anyone have any other things to try?  I'm getting really tired of running just vista.  Its horrible.

---

### Post by JonUK76 on 2008-04-01
With one of my PC's I had error messages similar to the above on trying to start the live CD. I had to add the irqpoll option to the boot command, i.e.

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b591c310-e284-4633-9302-ba21d4949de8 ro quiet splash irqpoll

Might be worth a try. If theres a bios update available for your laptop that might be something else to try.

I also can't think of an explanation for Vista performance problems after running a live CD. It should not change anything, like you said. Is there any chance of a hardware problem? Maybe run a memory tester.

---

### Post by maltbyc on 2008-04-01
That didn't work either.  I think i'm just going to install xp and get rid of vista then repartition my HDD then try ubuntu again.

---

### Post by evertsfnic on 2008-04-01
With my computer ubuntu 8 works ok. Theres only one problem my video card does not work 100% with ubuntu 8. I only have 800 resolution. My Video card is 
[IMG]http://img220.imageshack.us/img220/264/holace6.jpg[/IMG]

Thanks for the Free OS.........

---

### Post by maltbyc on 2008-04-01
So I just cleaned off my HDD completely and installed XP instead of vista and made a 30GB partition for the purpose of running Ubuntu but I still have the same problem I initially did with the live CD as I did after I installed Ubuntu trying to start it up.  Anyone know why or what made the live cd boot this morning after the computer being off all night but not now?  I'm baffled by what can be causing this.  When I tried in February I had absolutely no problem running live cds.

---

### Post by maltbyc on 2008-04-02
*bump*

---

### Post by maltbyc on 2008-04-02
I tried updating my bios.  Still nothing.

---

### Post by maltbyc on 2008-04-06
I also tried mandriva and it won't install.  I still have no idea why linux won't install on my computer.

---

### Post by Dellguy on 2008-04-09
I had this problem too & I just read this thread while I was looking for a solution.

Pressg F6 when the install screen comes out. Delete the word "splash" 
you can add "noacpi" too.

After I did that it worked fine. I noticed some USB something something something error immediately followed after that but everything worked fine :D I'm using a USB keyboard & mouse :D

I hope it helps. [http://ubuntuforums.org/showthread.php?t=470880](http://ubuntuforums.org/showthread.php?t=470880)

Specs
P35-DS3l
ATI X300 DVI
Q6600
WifI- Dlink 1320
Kubuntu 7.10 (amd64)

Fedora worked great if you get sick of trying!

---

### Post by maltbyc on 2008-04-10
No i've tried that.  I've tried all the F6 start up options.

---

### Post by Dellguy on 2008-04-15
Another work around. 
I disable USB Keyboard & Mouse support in the BIOS. 
Remove the USB devices & let the PC boot & then plug them in.

---

