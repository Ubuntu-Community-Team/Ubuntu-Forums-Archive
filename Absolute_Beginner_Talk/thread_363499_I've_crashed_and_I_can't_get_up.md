---
title: "I've crashed and I can't get up"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Aricml on 2007-02-17
I am new to Ubuntu and Linux in general, as such I searched the forums but could not find an answer to the problem I am experiencing.

      About a week ago I got fed up with Windows and decided to switch to Ubuntu (as it seemed to be thought of as a very user friendly Linux distro.) So I backed up all my important files on CD's, made an installation CD for 6.10 and installed. 

      Things were going great, it seemed rock solid reliable and I'd used Automatix to get more compatibility than I thought I was going to have.  So I was ripping my songs off CD's back on to my hard drive when my system just froze, and hard.  I could move my mouse but everything else was unresponsive, after trying a few of the function buttons on my keyboard the screen just went black, and my computer restarted.

      At first I wasn't too worried, as a long time Windows user, crashes aren't something that catch me too far off guard.  But instead of loading to the Ubuntu desktop, my computer goes through the following steps

1.) Motherboard splash screen
2.) Loading GRUB screen
3.) Ubuntu splash screen
4.) It gets 3 little yellow bars into loading, then freezes, the computer turns off and restarts its cycle.
(Sorry thats the best I can describe these)

      I was worried I may have somehow corrupted something in Ubuntu (since I know almost nothing about it yet)  and I took my Ubuntu CD.  Popped it in and tried to load from that.  Same cycle.  Then I tried in graphics safe mode.  Ditto.  

      And thats really about as far as I know how to try to fix this.  Do any of you have any suggestions as to something I could do?  I'm on a different computer right now and could make an image CD of a different version of Ubuntu if installing that was either possible or helpful. 

      With the CD not working and me being unfamiliar, I'm panicked thinking I may have messed up hardware on that computer, but I don't know how to know if thats the case or what to look for.  As I said, if any of you have any ideas or suggestions as to how to get my machine running again it would be fantastic. Thank you in advance

-Aric

---

### Post by Aricml on 2007-02-17
The closest thread I found to my problem is this [thread]("http://ubuntuforums.org/showthread.php?t=361277").  However I cannot get Ubuntu to work off the Live CD either.

      I was able to get to the prompt where I entered the prescribed $ startx.  It seemed like the result was able to help someone figure out what was wrong with his setup, therefore in case it helps any of you help me out, here's the result that showed up on my screen.

ng enabled
[17179570.088000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.092000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.092000] mice: PS/2 mouse device common for all mice
[17179570.092000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024
locksize
[17179570.092000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.092000] ide: Assuming 33MHz system bus speed for PIO modes; override
ith idebus=xx
[17179570.092000] PNP: No PS/2 controller found. Probing ports directly.
[17179570.092000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.092000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.092000] EISA: Probing bus 0 at eisa.0
[17179570.092000] EISA: Detected 0 cards.
[17179570.092000] TCP bic registered
[17179570.092000] NET: Registered protocol family 1
[17179570.092000] NET: Registered protocol family 8
[17179570.092000] NET: Registered protocol family 20
[17179570.092000] Using IPI No-Shortcut mode
[17179570.092000] ACPI: (supports S0 S1 S3 S4 S5)
[17179570.092000] VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
[17179570.092000] Please append a correct "root=" boot option
[17179570.092000] Kernel panic - not syncing: VFS: Unable to mount root fs on un
known-block(8,1)
[17179570.092000]  _


And thats where it ends. Hopefully that helps someone out a bit. Thank you again

-Aric

---

### Post by Aricml on 2007-02-17
One more afterthought, in case system specs would help at all I have a few for anyone who'd be able to help.

I have a;

Asus P4S800D motherboard
Intel Pentium 4 2.8 GHz
2x256 MB Kingston DDR
Nvidia Geforce 128MB 5600
ATA 80G Hard drive

Thanks again!

-Aric

---

### Post by rccharles on 2007-02-17
> **Aricml said:**
> 
[17179570.092000] VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
[17179570.092000] Please append a correct "root=" boot option
[17179570.092000] Kernel panic - not syncing: VFS: Unable to mount root fs on un
known-block(8,1)
[17179570.092000]  _


And thats where it ends. Hopefully that helps someone out a bit. Thank you again

-Aric

Are you booting off of the CD here?  

These lines seem to be saying there is a problem with the harddrive, but I am not sure.

I try booting into single user mode from a live cd.

Robert

---

### Post by Aricml on 2007-02-17
I was booting from the hard drive to start with, then I tried booting form Live CD and it still froze at the Ubuntu splash screen.  When I looked into the other thread I saw how to use the prompt to get that error message.  So neither Live CD or hard drive boots seem to be working for me, which is why I'm so confused.

-Aric

---

### Post by Dylnuge on 2007-02-17
I had the VFS problem with gentoo. Your hard drives are ATA, correct? 

Ok, some steps:

1. Can you boot into recovery mode (not graphics safe)? I assume that that is where you typed startx. If so, then do it.

2. Do you know how to operate the terminal. If not, go to Linuxcommand.org and read a bit there. These next few operations may be complex and terminal understading will help.

3. Post the contents of your /boot/grub/menu.lst, /usr/X11/xorg.conf, and /etc/fstab files here.

4. Post the results of lspci and fdisk -l here. (Thats an L, but lowercase).

5. If all of this checks out, we may need to step into the kernel configuration. Post here first, then standby for more details.

I have nothing to do tonight, as all of my troubleshooting issues are fixed, so I have no problem helping out.
If any of this seems complicated, don't be scared. Some of this stuff is advanced, but if an issue like this arose on windows, there would probably be no solution besides a complete reinstall. The terminal will be second nature soon enough. Since you can't get a GUI loaded, you are going to need to work with it right now, but a lot of this stuff can be done in the GUI as well.

PS: I notice that you are able to access the internet, but assume that you are using a different computer. Since I need this data as exact as possible, I recommend getting the machines as close as possible or getting pencil and paper to copy over. You can ignore anything with one or more # signs in front of them, they are comments and don't matter. i.e, if the file looks like this:
```
#This reboots the system
reboot
```
You can just post this:
```
reboot
```

---

### Post by ppl on 2007-02-17
The live CD should be able to boot even when the data in harddrive is corrupt/unreadable. I think the reason of not being able to boot should be something to do with your hardware but not your harddrive, my 2 cents.

---

### Post by nanotube on 2007-02-17
since you cannot even boot from the livecd, it appears to be a likely hardware problem - or a bug in the software. i looked around on google, and found this ([http://www.mepis.org/node/12509](http://www.mepis.org/node/12509)) seems that this may be a bug with a newer kernel? before ripping out your hair or doing anything fancy, i'd suggest downloading ubuntu 6.06 (dapper), and trying with that one. dapper would have an older (and hopefully more stable) kernel in it. see if that works - if so, then you have narrowed down the problem somewhat, at least :)

---

### Post by jjf on 2007-02-17
Before retyping everything you see, I'd make an attempt at copying the files Dylnuge wants onto a thumbdrive and transferring them to your new computer.

I'm a newb myself, so someone correct me if I'm wrong here, but I think these will be the commands you want:

```

// plug in your thumb drive

// make a directory where you will mount your thumb drive (/media/usb)
cd /media
sudo mkdir usb

// mount your usb drive (/dev/sda1) as /media/usb
sudo mount /dev/sda1 /media/usb

// copy the necessary files to your usb drive
sudo cp /boot/grub/menu.lst /media/usb
sudo cp /usr/X11/xorg.conf /media/usb
sudo cp /etc/fstab /media/usb

// unmount your thumb drive
sudo umount /media/usb

// unplug your thumb drive

```

---

### Post by Dylnuge on 2007-02-17
Even if it is a hardware problem, VFS is the Virtual File System. However, the fact that it refuses to start any GUI strongly points to a graphics adapter or graphics driver.

If possible, I would still like to see all of that data. At least the xorg.conf and fstab files and lspci resuts.

Last time I had this issue, it was with the kernel. Downgrading might be helpful.

---

### Post by r4ik on 2007-02-17
Is you're HD set cable select ?
If yes set it master and reboot.
(everyone is going to say i am crazy oh well...)

---

### Post by Dylnuge on 2007-02-17
> **jjf said:**
> Before retyping everything you see, I'd make an attempt at copying the files Dylnuge wants onto a thumbdrive and transferring them to your new computer.

I'm a newb myself, so someone correct me if I'm wrong here, but I think these will be the commands you want:

```

// plug in your thumb drive

// make a directory where you will mount your thumb drive (/media/usb)
cd /media
sudo mkdir usb

// mount your usb drive (/dev/sda1) as /media/usb
sudo mount /dev/sda1 /media/usb

// copy the necessary files to your usb drive
sudo cp /boot/grub/menu.lst /media/usb
sudo cp /usr/X11/xorg.conf /media/usb
sudo cp /etc/fstab /media/usb

// unmount your thumb drive
sudo umount /media/usb

// unplug your thumb drive

```

Good advice with a few problems.

1. You list the USB as sda1. This is because the USB is a SATA, ATA, or SCSI device. Most USB drives are. However, this user has an ATA hard drive. This means that sda1 is already taken by the first partition on his primary hard drive. As such, the usb would be called sdb1.

2. Since he is running in recovery mode, he is already root. There is no need to use sudo.

3. Here are a few additional commands that should help:
```

lspci > /media/usb/lspci_results.txt
fdisk -l > /media/usb/fdisk_list.txt

```

In case you are wondering, the > changes the location of the output. Instead of sending the results to the terminal, it will send the results to a file (located at the defined position).

-Dylan

PS: Check about the hard drive as well, like r4ik mentioned. Just open your computer and locate your hard-drive. It should have a little port with six pins, like so:
* * *
* * *
Two of these pins should have a jumper laid over them, like so
* | *
* | *
Look at the letters below the jumpers. They should read CS, Master, and Slave (or some abbreviations of them).
* | *
* | *
C M S
S  A L
If these jumpers are located above CS or Cable Select, switch them to Master.
Thats all there is too it.

PPS: Absolutely do not open your computer if it is a laptop. Also, if it is CS, and that is causing a problem, I would be pretty shocked. After all, it worked before, and something tells me the jumpers don't actually jump. (Sorry for the bad pun). However, if it is CS, r4ik is right, it could cause a problem.

---

### Post by Aricml on 2007-02-17
Ok, I got my digital camera and took as many pictures of different screens as I could find. I get different results with hard drive or Live CD so I'll post them here starting with what results from a hard drive boot.

1.) Motherboard splash screen

2.) Black Screen with the following;

Silicon Integrated Systems Corp. RAID BIOS Setting Utility v1.05_964
(c) 2003-2005 Silicon Integrated Systems Corp. All rights reserved


Press <Ctrl><S> to enter Setup Menu or <ESC> to skip waiting.

Primary Master  :      < SATA Device Not Found >
Secondary Master :   < SATA Device Not Found >

3.) Black Screen with the following

GRUB Loading stage1.5.

GRUB Loading, please wait...
Press 'ESC' to enter the menu... 0

4.)Here the problem diverges, if I allow the OS to continue to load normally, it goes to an Ubuntu Splash screen, the progress bar gets three yellow squares in and then freezes and eventually turns my computer off, otherwise if I press ESC I enter this screen

________________________________________________
Ubuntu, kernel 2.6.17-11-generic
Ubuntu, kernel 2.6.17-11-generic (recovery mode)
Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+


_________________________________________________
Use the (up) and (down) keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the
commands before booting, or 'c' for a command-line

5a.)When I hit 'e', I get this screen

_________________________________________________
root    (hd0,0)
kernel    /boot/vmlinuz-2.6.17-11-generic root=/dev/hdal ro quiet splas>
initrd      /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot


__________________________________________________


5b.)When i hit 'c', I get this screen

[  Minimal BASH-like line editing is supported.  For
   the first word, TAB lists possible command
   completions.  Anywhere else TAB lists the possible 
   completions of a device/filename. ESC at any time
   exits. ]

grub>


I don't think some of the first screens were important but since I dont really know too much about this, I just wanted to include as much information as I could to make helping me easier. With a live CD in I still see screens 1 and 2 then it goes to an Ubuntu splash-looking screen with the following options.

3.)
      Ubuntu

Start or install Ubuntu
Start Ubuntu in safe graphics mode
Check CD for defects
Memory test
Boot from first hard disk



F1 Help   F2 Language   F3 Keymap   F4 VGA   F5 Accessibility    F6 Other Options

4.) When I hit F6 I get the same screen but a ?prompt? pops up that reads

    Boot Options ._size-1048576 root=/dev/ram rw quiet splash --|


This ?prompt? is where I entered $ startx and got the previous screen information that didn't make sense to me.

If it is a hardware problem, is there any way I could narrow down what components might be fried?  Until then I have a buddy making a disk of Dapper for me to see if that could come in handy in this situation.  Until then I'm going to read the [www.linuxcommand.org](www.linuxcommand.org) so I can try to understand better exactly how to give you the results you wanted for /boot/grub/menu.lst, /usr/X11/xorg.conf, and /etc/fstab.  Thanks again for all the help so far!

-Aric

---

### Post by Velotix on 2007-02-17
I have no clue how likely it is that this is related to your problem, but because it's such an unusual, seemingly random error, it somehow seems to fit with this piece of advice from another topic:

> Don't go cheap on the power supply, you'll regret it later. How do random reboots sound?

Are you certain your computer's power supply is operating correctly? An overworked power supply is one of the more likely reasons for a computer shutting down randomly on its own, or an ineffective cooling fan (though if it were a fan, the computer wouldn't be rebooting straight away, so that isn't it).

It could be that you just need a better power supply - have you added or upgraded any components lately? If the new parts use up more power than the old ones, it may be that your power supply used to be fine but you're now asking too much of it - I recall a friend of mine having problems with his PC shutting down playing games because there wasn't enough power to keep his GPU's fan running properly, so it kept overheating and killing the computer.

Just a thought.

---

### Post by Dylnuge on 2007-02-18
> **Aricml said:**
> This ?prompt? is where I entered $ startx and got the previous screen information that didn't make sense to me.

Ok. That is actually a selection of boot options, and entering startx there won't do much.

> **Aricml said:**
> 
4.)Here the problem diverges, if I allow the OS to continue to load normally, it goes to an Ubuntu Splash screen, the progress bar gets three yellow squares in and then freezes and eventually turns my computer off, otherwise if I press ESC I enter this screen

________________________________________________
Ubuntu, kernel 2.6.17-11-generic
Ubuntu, kernel 2.6.17-11-generic (recovery mode)
Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+

Get to this screen again.
Ignore the prompts about editing and command-line. Instead, choose this option:
```
Ubuntu, kernel 2.6.17-11-generic (recovery mode)
```
(To choose the option, use the down arrow key to scroll to it, and then press enter, spacebar, or the right arrow key to load it).

Now, there are going to be two possible things here:
1. You get an error message while loading. Recovery mode is verbose, which means that you will be able to see everything the computer was doing. Post the last 5-10 lines on the screen, including the error message at the end.

2. You will get a prompt that looks like this:
```
root@localhost.localdomain$[CODE]
(Don't worry if the words localhost and localdomain are different).
Now the next step depends on if you have either a floppy or flash drive. jjf recommended using a flash drive to save the files too, and I stand by him on that. If you have a flash drive, plug it in and enter the following commands:
[CODE]mkdir /media/flash
mount /dev/sdb1 /media/flash
```
Now, if you have a flash drive put this after every command:
```
 > /media/flash/<filename>
```
Where <filename> is the name of the file or command. So:
```
 lspci 
```
Would Become:
```
 lspci > /media/flash/lspci [CODE]
(Note that if there is already a file named lspci on your flash drive, this will not work. To replace the files, use >> instead of just >. In fact, since >> works even if the file does not yet exist, it might be a good idea to just use >>).
For the files, use less to view them (or send them), so
[CODE] less /boot/grub/menu.lst 
```
Would become
```
 less /boot/grub/menu.lst >> /media/flash/grub.conf 
```

Now, whether or not you have a flash drive, here are the commands. If you have a flash drive, then remember to add the >> /media/flash/<filename> to the end of the command. If you don't, then just copy the info and post here. (By the way, press Q to leave the files if you are viewing them with less).
```
 less /boot/grub/menu.lst
less /usr/X11/xorg.conf
less /etc/fstab
lspci
fdisk -l
```

Ok, hope this helps.

PS: Unless you built your own computer, the odds the power supply is malfunctioning is very unlikely, especially since it keeps crashing at the same exact point, regardless of how long you wait before getting to that point.
However, the answers to these questions, in addition to the results of the above commands, would be nice:
1. Are you on a laptop or desktop.
2. Did you build or buy it? If buy, then what model is it?
3. Do you own a flash drive that you are using?

PPS: Cannot believe I did not ask this before, adding it now:
4. What recent changes have you made to your system? Installations, upgrades, etc.

PPPS: I just quickly looked at the contents of LinuxCommand.org to see which pages are most important to read. Reading everything up to Permissions will really help, and reading Permissions can help too (although you will already be the superuser if you can get into recovery mode). Just note that su is **not** the command to use in a regular terminal to become the super user, because it asks for the root password (which is scrambled on Ubuntu systems). Instead, use sudo (which asks for your password, to confirm that you are you). (Note that you can read as much as you want, however only the stuff before Permissions is really nessicary).

---

### Post by Hugzy on 2007-02-18
*OFF TOPIC:* This forum is incredible. You guys have totally convinced me to ditch XP and give Ubuntu a whirl. Top stuff.

---

### Post by Dylnuge on 2007-02-18
> **Hugzy said:**
> *OFF TOPIC:* This forum is incredible. You guys have totally convinced me to ditch XP and give Ubuntu a whirl. Top stuff.

Thanks for saying so. Hope you enjoy Ubuntu, but here are a few suggestions:

1. Download the LiveCD and play around in it for a while. It is essentially a "trial" of Ubuntu without any installation ready. Go ahead and run the files in the Examples folder to ensure that your video and sound card work with Ubuntu. You should also be able to get online (WPA does not work in the LiveCD, however, so if you have a WPA network you either need to switch it to WEP temporarily while you install WPA support or directly connect your computer to the internet via an ethernet cable).

2. If you decide you like it, go ahead and install. If you want, you can dual boot your computer with Windows. Its pretty simple with Ubuntu, but you need to partition your hard drive first. Norton PartitionMagic will work pretty well, since it does not damage data, there are also guides on how to move data to the front of the drive so it is not lost (essentally, it involves defragmenting until there are no files in the portion of the drive you want Ubuntu on). 

3. Be aware that you will need to find equivilents for a lot of Windows software. [This chart]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html") is very useful, but some of the links are outdated. Also, most of your video games will not have an equivalent in Linux. You can also install WINE, which will run a lot of Windows programs in Linux.

4. If you have any problems, go ahead and post in the forums. However, I would recommend not posting in this topic. (In fact, I really should not have replied, since I am moving the posts off topic).

Hope you enjoy Linux, and hope everything works well.

---

### Post by Dylnuge on 2007-02-18
Bumping post so original poster will not lose track.

---

### Post by Aricml on 2007-02-18
First off I wanted to thank everyone for the help you've been giving me, I haven't gotten it working yet, but I never imagined that I would've gotten as much help as you've all been giving so far. So thank you for that. 

Now on the me trying to describe a little more of the problems;

> Get to this screen again.
Ignore the prompts about editing and command-line. Instead, choose this option:
Code:

Ubuntu, kernel 2.6.17-11-generic (recovery mode)



I had already tried each of the Operating Systems on that list and even the memtest86+, because why not.  And even in recovery mode It would do the same thing.  An incredible amount of text flies by and then almost out of nowhere the computer just restarts.  I believe I was able to get a photo of what it says right before turning off though, so here it is;

 usb-0000:00:03.0-1
[17179586.108000] usbcore: registered new driver usbhid
[17179586.108000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179586.312000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.368000] sis900.c: v1.00.09 Sep. 19 2005
[17179586.368000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) ->
IRQ 217
[17179586.368000] 0000:00:04:0: Realtek RTL8201 PHY transceiver found at address
1.
[17179586.380000] 0000:00:04.0: Using transceiver found at address 1 as default
[17179586.380000] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 217, 00:17:31:7
7:63:a5.
[17179586.452000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.488000] agpgart: Detected SiS655 chipset
[17179586.492000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179586.536000] parport: PnPBIOS parport detected.
[17179586.536000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17175986.592000] ACPI: PCI Interrupt 000:00:02.7[C] -> GSI 18 (level, low) ->
IRQ 225
[17179586.744000] ts: Compaq touchscreen protocol output
[17179587.016000] intel8x0_measure_ac97_clock: measured 56333 usecs
[17179587.016000] intel8x0: clocking to 48000
[17179587.020000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) ->
IRQ 177
[1779587.024000] BUG: unable to handle kernel paging request at virtual address



I'm fairly positive that this is the last screen that shows before it restarts, it happens quite fast but I think this is the correct screen.  Also I'm just guessing but the line that says BUG looks like a bit of a problem to me.

I checked my hard drive and the jumpers were in the master position so no problem there

> 
// plug in your thumb drive

// make a directory where you will mount your thumb drive (/media/usb)
cd /media
sudo mkdir usb

// mount your usb drive (/dev/sda1) as /media/usb
sudo mount /dev/sda1 /media/usb

// copy the necessary files to your usb drive
sudo cp /boot/grub/menu.lst /media/usb
sudo cp /usr/X11/xorg.conf /media/usb
sudo cp /etc/fstab /media/usb

// unmount your thumb drive
sudo umount /media/usb

// unplug your thumb drive

I do have a thumb drive and I'd love to take this advice but I just can't seem to get to a prompt where I can enter these commands and have my computer respond to me.

And to answer a few other questions, its a desktop I built myself about 6 months ago, it still has the power supply that Raidmax sent with the case and while I do want to eventually replace it, I believe its still working OK because as Dylnuge said, the problem keeps happening in the exact same spot. Also I haven't added any hardware recently.  The only change I made was switching to Ubuntu from XP. 

Also quite a few of you were saying you thought it could be a graphics card problem, in which case I have an  older 64MB card in a box somewhere in my basement, I'm going to go get that and install it to see if it doesn't make any difference.  

Again I just want to thank all of you, especially Dylnuge for all the wonderful help, I'm just floored by it.

-Aric

---

### Post by nanotube on 2007-02-18
did you get your hands on the dapper cd yet and give it a shot? i'm very curious to see the result of that.

also, if you have more than one memory chip, try swapping the chips - this could be a ram problem, and if you swap and get different results, you will be pretty sure it's the ram.

and one more thing, for some of the other thread posters: since it is patently clear from the get-go that he can't even get to a console shell (in the second post, the panic happens during hardware detect, before the system finishes booting, and certainly before it even thinks of starting X), what's up with posting all those commands to try, contents of files to look at, mounting usb drives? it doesn't even get to a shell, so it's not possible to do any of those things! all that just confuses the issue (and the issuer). unless i'm the one missing something, it seems that you might consider reading the posts more carefully. :)

---

### Post by Dylnuge on 2007-02-18
> **Aricml said:**
>  usb-0000:00:03.0-1
[17179586.108000] usbcore: registered new driver usbhid
[17179586.108000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179586.312000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.368000] sis900.c: v1.00.09 Sep. 19 2005
[17179586.368000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) ->
IRQ 217
[17179586.368000] 0000:00:04:0: Realtek RTL8201 PHY transceiver found at address
1.
[17179586.380000] 0000:00:04.0: Using transceiver found at address 1 as default
[17179586.380000] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 217, 00:17:31:7
7:63:a5.
[17179586.452000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.488000] agpgart: Detected SiS655 chipset
[17179586.492000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179586.536000] parport: PnPBIOS parport detected.
[17179586.536000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17175986.592000] ACPI: PCI Interrupt 000:00:02.7[C] -> GSI 18 (level, low) ->
IRQ 225
[17179586.744000] ts: Compaq touchscreen protocol output
[17179587.016000] intel8x0_measure_ac97_clock: measured 56333 usecs
[17179587.016000] intel8x0: clocking to 48000
[17179587.020000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) ->
IRQ 177
[1779587.024000] BUG: unable to handle kernel paging request at virtual address

This is most likely the last screen, and I aggree, the BUG sounds like it would be a problem. Once again, it sounds like a reference to the virtual file system, specifically the paging file. Since you cannot boot into a LiveCD or recovery environment, I would think that there is a hardware problem somewhere. However, since it is difficult to determine the location of the hardware problem without any access to the computer, a bit more troubleshooting before replacing the parts of your machine could be helpful. (Go ahead and try that old Graphics Card though). In fact, this problem seems very mixed. The fact that Ubuntu ran smoothly before points to software, as does the lack of changes, but all other issues, including the failure for any environment to load, point to hardware.

However, I recently had a thought. While it may seem unlikely, it is possible that the LiveCD and the computer itself are two seperate issues (the error message on each is different, so this is more possible then if they were the same). Therefore, if possible, burn another LiveCD and try loading from that. For that matter, download 6.06 LTS (Dapper) instead of 6.10 (Edgy). If this is not possible, try your current LiveCD on another machine. (You don't have to install, just see if it works).

Most likely, you will get the same error message with the separate LiveCD, or will not get the error message on another machine.

If the other CD works, post here and we will work from that cd (there are a few simple commands that will allow you to access the shell in your installation from the LiveCD). If not, then reboot your system with your Windows CD and see if that works.

> **Aricml said:**
> I do have a thumb drive and I'd love to take this advice but I just can't seem to get to a prompt where I can enter these commands and have my computer respond to me.

Hopefully, we will get to this point soon. I have never seen anything like this before (I have had the VFS error, I have seen problems where the computer constantly restarts (the LiveCD worked, however), but I have never seen something this deep occur, especially not when no apparent changes have been made).

I notice that there are two kernels on that list however. Do you remember updating your system soon before the crash? It seems unlikely that that would be it, considering that you have tried the older kernel, but perhaps something that upgraded with it would be the problem. Of course, this scenario would be a software issue. I am interested in seeing how that graphics card works, as sometimes things just die unexpectedly. However, it looks like it could be the hard drive. VFS is a hard drive error usually caused because the kernel cannot support your hard drive (in the case I had it before, SCSI support was not compiled into the kernel). The mention to a paging file could also be related to the hard drive. Therefore, if the graphics card and the new LiveCD both fail, try another hard drive. Even though the LiveCD does not use the hard drive, it could be attempting to mount it.

If your system supports two hard drives, there is a chance we can still save the first one.

> **Aricml said:**
> Again I just want to thank all of you, especially Dylnuge for all the wonderful help, I'm just floored by it.

You're welcome. :) Hope you have more pleasant experiences with Ubuntu from this point on.

Addendum:
I notice nanotube beat me to the LiveCD thing. Nice to know we are all on the same page.

Also, on further thought, the hard drive failure seems more likely. The only thing against it is the LiveCD failure, but I am not sure how much the LiveCD uses the hard drive (pre-installation that is). Therefore, if you have an alternate hard drive, try it. (Using the LiveCD, since Ubuntu is not yet installed). Not to mention that hard drives are the most common component to fail, and seem to fail spontaneously at times. Of course, they are the only moving part of a computer. 

**I have codeblocked the following segment because I essentially went off on my own topic. While it is still available to read, it is not relevant to the topic.**

```
I think that the technology used in jump drives will eventually replace them (first jump drives were seen
as floppy replacements, since you can't write files as easily to a CD. Now they are seen as CD/DVD-ROM
replacements, since they can hold more and act as a CD too (U3 ones, at least). How long before they are
hard drive replacements? Then again, $8/GB for non-U3 or $15/GB for U3, the technology must become
equivalent to todays $1/GB or less external hard drives (and then become internal as well). 
```

Good luck!

---

### Post by Aricml on 2007-02-18
VICTORY!

So I swapped out for my older graphics card and I'm happy to say that I'm posting from my own computer again! At first Ubuntu did not seem to like this card but I just reinstalled from the CD I made and things seem to be running great now. It's sad that apparently my graphics card just failed on me, but it's nice to finally have figured it out.  

I have to say, some of you put some really helpful links on here that will be great for me to, in general,  learn more about Linux/Ubuntu.  It's just great to know that there's such community support in case I ever need it again (knock on wood.)

Thank you to you all!

---

### Post by Dylnuge on 2007-02-18
Looks like it was the graphics card after all. Glad everything is up and running.

Enjoy Ubuntu. (Also, if your graphics card is new enough, see if you can get it replaced by the company that sold it to you, nVidia, or ATI).

---

### Post by revoltism on 2007-02-22
I'm pretty sure it's a kernel issue. I got the same after an kernel update.

---

