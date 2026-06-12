---
title: "Installation help needed on G5 System"
date: 2005-02-05
forum: Apple PPC Users
---

### Post by Thomas Ferreira on 2005-02-05
I have a G5 Dual 2GHz and trying to install via the 4.10 PowerPC Edition CD I just received in the mail.  To leave my stock 160GB HDD drive alone, I just installed a 120GB drive in the 2nd bay to install Linux on it.  I installed the CD and boot the G5 holding down the C key and get a text based window that explains I can do the standard Install or an Expert install.  I originally typed just the word install and I then get a white screen with the following data:

...ok
opening display /pci@0, F0000000/ATY, SimoneParent@10/ATY,Simone_B@1_

It sits there and then does nothing.  After a minute or so the CD stops spinning and then my G5 FANS start slowly speeding up and get real loud.  Is it doing something and I need to leave it on for many minutes or my guess is it is just locked up.  

I booted again and typed the word expert at the prompt this time and got the same thing.  I even tried that expert ofonly text it said to do.  All give me the same results.

Any clue what is going on?

Thanks

Thomas

---

### Post by Thomas Ferreira on 2005-02-05
OK, I have explored a little more and this time hit the TAB key at the prompt to look at all the options I have.  So, I selected "install-power4" since I own a G5 and walla, this time I do get a graphic window where I now must first select my language.  Problem is, no keyboard commands do anything as if it does not see the keyboard.  I try the arrow keys to see if I can go up or down to choose my language, hit the Enter and Return keys, nothing.  The mouse which is connected to the keyboard has no red beam so it is like the keyboard goes dead at this point although it allowed me just seconds earlier to hit the tab key to see my options and type in my command.  So, is the stock Apple keyboard that came with the G5 not useable for this install or something or ??  I happen to have a MacAlly keyboard lying around so will try that for the heck of it.  What a pain.  Should not be this hard to just get the installer started.

By the way, my config is:

G5 2GHz with 1GB Memory
22" Cinema Display
Stock keyboard and Mouse

I guess for the heck of it I will unplug all my USB devices to see if this helps to gain keyboard control.

any input would be nice.

Thomas

---

### Post by Thomas Ferreira on 2005-02-06
Well, continuing onwards, I unplugged my Apple keyboard and mouse and just direct connected to the G5 a MacAlly keyboard, did the install-power4 command, got the menu, and this time could use the arrows to go up and down to select my choice for language.  Then it asked for state and I selected United States, where now it locks up again.  The whole screen was blue with the menu selections but after selecting the United States, a white border at the bottom of the screen shows up and the system locks up from further install.  I notice if I type letters and symbols show up down in the white border area.

This is like pulling teeth!  Sheesh!

I give up for now and will wait for some of your tips as maybe someone else here had the same issues as I have tonight and can guide me further.

Thanks for any tips you can offer.

Thomas

---

### Post by humberto on 2005-02-06
[QUOTE=Thomas Ferreira]I have a G5 Dual 2GHz and trying to install via the 4.10 PowerPC Edition CD I just received in the mail.[/QUOTE]

I'm pretty sure 4.10 (Warty Warthog) won't work on your G5. I got a working install on a dual g5 with 2 hard drives using the Hoary Array 3 CDs in beta.

[http://archive.ubuntulinux.org/cdimage/releases/hoary/](http://archive.ubuntulinux.org/cdimage/releases/hoary/)

I haven't tried array4 yet.

To get dual processor support you need to install the power4-smp kernel, but at least the setup works with array 3. I'm using an Apple keyboard and a logitech wheelmouse. I did pull out a Nvidia 6800 card and replace it with an ATI, as I had problems with the Nvidia card.

---

### Post by Thomas Ferreira on 2005-02-07
Downloading large files via the Direcway Satellite service is real bad.  They have FAP (Fair Access) so if I try to download more than a 169MB file, it bogs and slows down the remainder of the download to snail pace.  I am trying the power-4 version via bit-torrent to see if that works.  Thanks,

Thomas

---

### Post by Thomas Ferreira on 2005-02-07
Anyone know of a bittorent download of the array 3 of Unbuntu Hoary Array CD image.  The array 4 bittorent did not work.

Thanks

Thomas

---

### Post by humberto on 2005-02-08
[QUOTE=Thomas Ferreira]Anyone know of a bittorent download of the array 3 of Unbuntu Hoary Array CD image.  The array 4 bittorent did not work.
[/QUOTE]

I just think no one is downloading it. I got it over http and fed it to bittorrent, so you could try again:

[http://archive.ubuntulinux.org/cdimage/releases/hoary/array-4/hoary-install-powerpc.iso.torrent](http://archive.ubuntulinux.org/cdimage/releases/hoary/array-4/hoary-install-powerpc.iso.torrent)

---

### Post by Thomas Ferreira on 2005-02-08
I am giving it a whirl right now.

Thanks for the torrent.  

By the way, I know just enough about torrent files that I have the proper application on my system to download them but curious, what is a torrent file download and how is it different than a normal download?  I do know that you can continue downloads of torrent files if you should be disconnected so that is good for large downloads like this.

Thanks

Thomas

---

### Post by humberto on 2005-02-08
[QUOTE=Thomas Ferreira]what is a torrent file download and how is it different than a normal download? [/QUOTE]

Bittorrent is a peer to peer download system. When many people download a file from a torrent, the bandwidth to each INCREASES, instead of decreasing as when you download a file from a conventional server.

A torrent is divided into many pieces, you can download each piece from a different peer, and as soon as you have a piece of the file, you can upload it to other peers that need it.

From looking at my upload statistics, you're the only person downloading it right now.

I'll leave my torrent up indefinetely.

---

### Post by Thomas Ferreira on 2005-02-09
I ended up downloading the array 3 and array 4 iso files at work as we have a T1.  Both downloaded fine but Disk Utility on my iMac G5 at work and an eMac G4 do not like the ISO files.  OS X opens them fine in the Finder.  But, Disk utility does not like the files.  Locks it up.  Something about a background file that is needed was not launched so something about these ISO files Disk Utility does not like.  So, how else can I make a bootable CD with these files.  I just copied them to CD so I could bring them home tonight and hope some other utility can make these ISO's into bootable CDs.

Anyone else have this issue.  I even downloaded the file again and gives me the same message.  I launch the ISO and then launch Disk Utility and it will not launch without the error message.  If I do not mount the ISO, Disk Utilility launches fine.  If I try to mount the ISO afterwards in OS X, or drag the ISO into Disk Utility, same error.

Thomas

---

### Post by Thomas Ferreira on 2005-02-10
[QUOTE=humberto]

I haven't tried array4 yet.

To get dual processor support you need to install the power4-smp kernel, but at least the setup works with array 3. I'm using an Apple keyboard and a logitech wheelmouse. I did pull out a Nvidia 6800 card and replace it with an ATI, as I had problems with the Nvidia card.[/QUOTE]

By the way, what is the difference between the array 3 and array 4.  I did find a ISO app at versiontracker.com that did allow me to create a CD from the array 4 iso I downloaded and I was able to install, at least so far, from this CD.  It booted, I typed install-power4, and it did its thing.  I did quickly see a message as all the text scrolled with the word FATAL in it but did not have time to read it all but the install let me go past that and it installed on my 2nd drive and ejected the CD when it finished that portion of the install.  Now, tomorrow morning, I will boot the G5 with the OPTION key and tell it to boot from the new Linux drive and see what happens.  Was too tired tonight to try that.

Thanks

Thomas

---

### Post by Thomas Ferreira on 2005-02-10
Well, I just could not go to bed without trying to go further with the linux install/boot.  So, I booted the G5 holding down the OPTION key and then selected the hard drive icon with TUX on it, I then get a text only screen and it says t6 type l for linux, x for os X, or c for CD.  It appears to not take any of them, at least a letter does not show on the screen.  It then somewhat fads out the hard drive icons and stays on the same screen where I select what drive to boot from.  So selecting the TUX hard drive icon does get me the text screen for me to select what I want to boot but it will not go past that point and returns me back to that same screen time after time.

Any guidance would be great.

Thanks

Thomas

---

### Post by Thomas Ferreira on 2005-02-10
I decided to go through the install again, an "install-power4" but this time using the array3 ISO, and although the install appears to go fine and the CD spits out letting me know it is doen with the first stage and after reboot, I will have more questions to answer, it never reboots to these new questions.  I get stuck in an endless loop of the what hard drive to boot from when holding down the OPTION key at boot and when the text screen comes up asking me to boot from Linux, OS X, or CD, it accepts me typing in the letter "L" but it spins the clock for a few minutes and lands me back to that same screen.  The only letter it will take is the "X" to boot to OS X which works fine.

I will look through other messages here to see if anyone has had this happen but in the meantime, if anyone is reading this, and has some words of wisdom, please let me know.  I seem to almost be there but can't get booted.

Thanks

Thomas

---

### Post by markusk on 2005-02-11
Hi Thomas,

Only after having read your reply to my entry "G5 Installationproblem: no yaboot-screen after stage 1" I went through this posting of yours. 

The boot problem you describe in the last of your own replies - or additions - is exactly the one I am experiencing on my G5!! 

Is there any other G5-owner out there who was able to install Ubuntu on a second hard drive successfully?

Markus

---

### Post by Thomas Ferreira on 2005-02-11
Just as an FYI, I could not even install it on a single drive setup.  I disconnected the cables from my main 160GB drive and installed it on my new 120GB drive, install again went fine, this time after it ejects the CD and reboots the system, it boots to Yaboot, I select "L" and now I get a flashing ? and Mac Face icon in the middle of the screen.  Not your normal flashing ? like in OS X but a different one so it is looking for something to boot but blah, nothing.

Thomas

---

