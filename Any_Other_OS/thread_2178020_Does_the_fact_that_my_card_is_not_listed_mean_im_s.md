---
title: "Does the fact that my card is not listed mean im screwed"
date: 2013-10-01
forum: Any Other OS
---

### Post by daveyman123 on 2013-10-01
where do i begin in getting this installed. I mean the very first step one would take to figuring out ubuntu and wireless cards like this???

---

### Post by daveyman123 on 2013-10-01
I followed the steps to identify my wireless card and it is not listed. I also checked to see if the card was listed in the supported wireless cards sticky. However it is not there either. Am i screwed?

---

### Post by poettone on 2013-10-01
daveyman123, can you include your hardware specifications here, what type of system are you on, cpu, memory, board, wireless card model etc. 

This would allow more assistance to be provided.

Thanks,

---

### Post by daveyman123 on 2013-10-01
intel cpu. backtrack version 3.0. Wireless card: Asus pci-n15. Asus motherboard.  I just told you that i couldnt find it in the list of supported cards. Please help answer that question. Not to be an ass. but thats what im wondering about.  Thanks, David

---

### Post by 1clue on 2013-10-01
@daveyman123,

It's not so much whether your card is listed as much as if its chipset is listed or if somebody knows some other driver works.  Most cards are similar to some standard.

We don't know if you're screwed or not, but if you keep talking like that you'll have to do all the research on your own.  We're helping you, not the other way around.  Nobody is being paid to help you.  Show some respect.

---

### Post by daveyman123 on 2013-10-01
Ok ok im sorry 1clue and poettone. please accept my apology. Im just frustrated is all.

---

### Post by 1clue on 2013-10-01
I'm going to give you some ideas on how to figure this out.  I'm not going to do the work for you.

What happens when you type **lspci** ?  Which device is it?  It may not show up as the same card you think it is, it may appear as some other device.  Change your google searches to be whatever it shows up as.

When I'm puzzled on this, I go to this site:  [http://kernel-seeds.org](http://kernel-seeds.org)

It's not an Ubuntu site and it's focused on compiling kernels, but as far as finding out what kernel driver to use it seems to be better than most.

Search on "how to use..." and follow those instructions, you may come up with something.

You can decide how much work you want to put into this.  If your setup is fairly mainstream then chances are it's supported, but if all else fails you can get a USB wireless card and plug it in, and it'll probably work out of the box.

---

### Post by daveyman123 on 2013-10-01
I tried two wireless cards out of the box and they dont work for me when i plug them in. I just dont udnerstand what im supposed to do with the drivers. They have them online and i can download them and find them i just dont know what to do with them after that.

---

### Post by daveyman123 on 2013-10-01
like i say before. when i do that command it doesnt come up showing my wireless card. What can be done now from this point moving forward?

---

### Post by 1clue on 2013-10-01
Is this a usb card or an on-the-motherboard card, or a plug-in-the-internal-slot card?

See if you can find anything that looks like a network card when you type one of these commands:
[LIST=1]
[*]lspci
[*]lsusb
[/LIST]

Please show anything that looks like a network adapter.

---

### Post by daveyman123 on 2013-10-01
here is lpci. It is a network adapter purchased to go in pci slot. the name is 
```

Asusu PCI-N15 in backtrack linux 3.0   
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)  
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]  
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)  
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter  
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02) 
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service 
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01) 
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB  
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)  
00:0d.0 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
```

---

### Post by 1clue on 2013-10-01
Can you please edit your post and put it wrap it with the code tags?  It's the # button on the advanced editor.  Your text is wrapping.

*done - sandyd*

---

### Post by chili555 on 2013-10-01
In a virtual machine, are we? Network cards are handled a bit differently: [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

### Post by daveyman123 on 2013-10-01
It should be noted that i can get the wireless card to work fine in windows 7. However i can not still get it to work in backtrack 3.0. (within a virtual machine i should also mention this)....      On windows 7 it says that the location of the wireless adapter (asus PCE n-15) is located on PCI bus 4. I dont know if this helps or not but i hope to hell it does. please and thank you very much for help!  -David

---

### Post by daveyman123 on 2013-10-01
Thank you for nice response. I will try to read this and see where it takes me. THank you.  -David

---

### Post by QIII on 2013-10-01
*Moved to **Other OS/Distro Support***

---

### Post by daveyman123 on 2013-10-01
I read chapter 6.1 on virtual hardware. Yet i am still confused by some of the concepts. I dont really want to have to learn that much about drivers to be able to do this. What do i do from here?   thanks david

---

### Post by chili555 on 2013-10-01
> **daveyman123 said:**
> I read chapter 6.1 on virtual hardware. Yet i am still confused by some of the concepts. I dont really want to have to learn that much about drivers to be able to do this. What do i do from here?   thanks davidPlease keep reading. It means roughly that the virtual machine generally uses a virtual interface which is bridged to your host (Win 7??) network device. Somewhere in your virtual machine setup, you select that one of the virtual devices,  Intel Corporation 82540EM Gigabit Ethernet Controller for example, bridges to the host's wireless.

---

### Post by 1clue on 2013-10-01
> **daveyman123 said:**
> I read chapter 6.1 on virtual hardware. Yet i am still confused by some of the concepts. I dont really want to have to learn that much about drivers to be able to do this. What do i do from here?   thanks david

What they're saying is that they offer several types of virtual network cards.  You pick one that has built-in support in the operating system you're going to install on it.  Almost all the operating systems they feel you are likely to install support the default card (AMD PCNet FAST III) but you might have to use an Intel PRO/1000 MT Desktop if you use a newer Windows like Vista, or something else if you have some other less-common operating system.

I had no idea you were using a virtual machine when you originally posted this thread.

Here's how I'd try it:
[LIST=1]
[*]Only have one network adapter at a time until you get one working.
[*]Delete the existing card, then add the default card.  Use NAT for now.
[*]Boot, and see if your OS comes up.
[*]If you get networking, you're done.
[*]If not, go back up to step 2 and try again with a different type of card.
[*]Repeat until you have access to the Internet or until you run out of cards.
[/LIST]

---

### Post by chili555 on 2013-10-01
Awesome, 1clue, thanks. Great explanation!

---

### Post by 1clue on 2013-10-01
Oh yeah.  You have to shut the guest OS down and power off before you can delete or add network cards.

---

### Post by 1clue on 2013-10-01
The next section can't really be boiled down all that much.  The only way to minimize it is to tell you to read the sections on NAT, Bridged or Host-Only.  Those are the most common ones, and in that order.

It's pretty important that you understand what your needs are, so pay attention for that part.

---

### Post by QIII on 2013-10-01
Threads merged.

---

### Post by daveyman123 on 2013-10-01
Thank you all for all the help. Very much appreciated. I am looking into the issue now as i have been pulled aside for work but have free time now. Again. much appreciated here. thanks!

---

### Post by daveyman123 on 2013-10-01
"then add the default card".... what do you mean by add "default card"   do i have to change these settings? is that what you mean?  



[IMG]http://i968.photobucket.com/albums/ae166/dg4y8/NetworkingBT_zps18d7ee7d.png[/IMG]the default card"? I have

---

### Post by 1clue on 2013-10-01
I'm looking at the link provided to the VirtualBox documentation mentioned earlier.  Here it is:  [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

I'm talking about Adapter Type, which is partially hidden by the pop-up menu in your screen shot.

The menu as shown -- Attached to -- should be NAT for now, because it's easiest to get working.  If you don't get that working then probably it won't work at all.

The default card according to the docs is the AMD PCNet FAST III, Am79C973.  It's the default because it's supported by almost every guest operating system.  But if you're using one of the few that doesn't support it, then you need to try something else.

---

### Post by daveyman123 on 2013-10-01
Intel PRO/1000 MT Desktop (82540EM) is the name of the Adapter Type that was obscured in the photo. THank you again for your thoroughness on this. So now i need to download something in windows 7 that will make it possible to emulate that chip in Backtrack virtual box?

---

### Post by 1clue on 2013-10-02
So you're using Windows 7 as the guest?

You shouldn't have to load a driver for Windows 7.  One of those adapters you have in the list should work fine with Windows 7.  Windows 7 comes with a bunch of drivers that fit most network cards, and probably one of them will work with one or more of the cards in your list.

So shut down your guest.
delete the network card you have.
create another network card of a different type.
make sure it's NAT.
start the VM.
see if you have net access.
If not, go back to the list above and try a different card.

---

### Post by daveyman123 on 2013-10-02
backtrack is guest. Windows = host... I have wired connection in both with NAT. Your saying i must delete the windows seven wireless adapter driver and redownload the emulater one?

---

### Post by 1clue on 2013-10-02
OK then.

The network card you're choosing is the one that the guest (backtrack) thinks you have.  VirtualBox takes care of the host (windows) side.

---

### Post by daveyman123 on 2013-10-02
so i need to download the Intel PRO/1000 MT Desktop (82540EM) which generally should support the emulation of the guest *(backgrack) wireless card? (asus pce-n15)

---

### Post by 1clue on 2013-10-02
You shouldn't have to download anything.  The cards in the list are the ones VirtualBox knows how to emulate.

You need something that Backtrack knows about.  Which, since it's Linux, should be pretty much any of the cards in the list.  You may need to download a driver into backtrack, but if you're using a modern release of it it should have several of those cards and should just recognize the one you hook up.

Did you see this?  [http://www.backtrack-linux.org/wiki/index.php/VirtualBox_Install](http://www.backtrack-linux.org/wiki/index.php/VirtualBox_Install)

---

### Post by daveyman123 on 2013-10-02
The process for downloading drivers for the card is very difficult for some reason. I have found some and I download them and then the steps for actually extracting them and getting them to install confuses me. I try all the command line that is recommended in the forum posts but still cant seem to follow. I guess I will continue to dig. Thanks again. very helpful replies. I may go to bed soon now... gnight -Dave

---

### Post by 1clue on 2013-10-02
I'm having extreme difficulty believing that your backtrack iso doesn't have at least one of those cards on the installer ISO.  It's been years since I installed a Linux distro that didn't want or even insist on networking during the install, and those are the most common cards out there.

In other words, you shouldn't have to download and install a network card driver.  It should be on your iso.

---

### Post by varunendra on 2013-10-02
@ daveyman123,

What is your objective? Getting the wifi card or just an internet (or network) connection in the virtual machine?

If it is the wireless card, you can forget it now. A virtual machine DOES NOT SEE your actual hardware, so it can't see any PCI cards you may have installed either. It can 'see' only virtualized hardware, for which, virtualbox itself provides drivers for all supported Operating Systems.

If you need specifically "Wireless" in the virtual machine, get a USB wifi adapter (supported in Linux) and make sure USB support is enabled in virtualbox.

However, if it is just a network or internet connection you want, you don't need to manually download and install any drivers. Although I doubt you'd need to manually install ANY drivers for a generic card that VBox uses, just install "Guest Additions" from the "Devices > Install Guest Additions...." menu of the running virtual machine window (not virtualbox's window) to be sure. It is same like inserting a driver cd in the virtual machine then installing the included package from there (virtualbox will tell you how to install it). If you face any problems installing the Guest Additions, ask for help with that instead.

Once the 'Guest Additions' are installed, you will have all the required drivers for your virtual machine. Configuring the network and making it active is another thing then. By default, the network is kept "down" in BackTrack (for security). You just need to bring it up with -
```
sudo ifconfig eth0 up
```
..assuming you haven't did anything wrong with the virtual machines network settings configuration (by default, DHCP over NAT is on, so nothing more than the above command should be needed).

To check if the connection became active in the virtual machine -
```
ifconfig
```
see if it got IP.

---

### Post by daveyman123 on 2013-10-02
Thank you Varunendra for this long reply. And thank you 1clue last night for all your help.. In response to Varun. I believe that the issue isnt with getting internet connection. I am able to connect fine in my guest(backtrack) fine with eth0. However,  I cannot connect with the wireless card for the reasons you just stated most likely... I have tried two USBs in the past and had problems ones a netgear and other is Belkin. I have them lying around and will try them again when i get home. IIRC when i tried to use the USB adapters in the past, the issue was with them not being compatible somehow and i would get errors before even being able to connect, which was very frustrating and led me to buy a wireless card... 

sorry for long post but i will look into the exact issue when i get home

again thanks and see you later!
-David

---

### Post by steeldriver on 2013-10-02
What exactly are you trying to achieve? the GUEST doesn't need to have a wireless interface in order to connect to a wireless network via the HOST - for example I'm running a Mint13 VM inside VirtualBox on a Windows 7 laptop, as far as Mint is concerned it's connected via eth0 to a router (NAT) using the default Intel GiGE virtual adapter - whereas the host Win7 is connected wirelessly via the REAL adapter.

---

### Post by 1clue on 2013-10-02
Shoot.  The VM guest doesn't know what kind of adapter you have on your host.  It only cares that you have one.  You can use wireless on your host and have it look like ethernet on the guest.  Or vice versa.

---

### Post by daveyman123 on 2013-10-02
> **1clue said:**
> Shoot.  The VM guest doesn't know what kind of adapter you have on your host.  It only cares that you have one.  You can use wireless on your host and have it look like ethernet on the guest.  Or vice versa.

Ok.

---

