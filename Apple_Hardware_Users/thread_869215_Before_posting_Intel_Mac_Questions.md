---
title: "Before posting Intel Mac Questions"
date: 2008-07-24
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2008-07-24
You will get the best and fastest help if you make sure to do the following...

[LIST=1]
[*][COLOR=Blue]**If you are working with a Virtual Machine**[/COLOR] (VMWare Fusion, Parallels, VirtualBox, Qemu), this is probably not the forum you are looking for (try your VM's support area). Running Ubuntu in a VM is _completely_ different than running Ubuntu "on your Mac". Feel free to ask your question, but be sure to mention that you are using Ubuntu in a VM and what VM you are using! If you are not using a VM, continue to the next step.
[*][COLOR=Blue]**Determine the type and version**[/COLOR] (generation) of your Mac. This can be found in OS X in the [System Profiler]("http://en.wikipedia.org/wiki/Macintosh_System_Profiler") (in /Applications/Utilities in the Hardware Overview section or through "About this Mac > More Info". It takes the form of "MacTypeX,Y" (See attachment). You can also use dmidecode in Ubuntu to determine your Mac Version as shown [here]("http://www.rickycampbell.com/identify-your-mac-version-in-linux/").
[LIST]
[*]This is your Mac's Identifier.
[*]There are many Mac types: MacBook,MacBookPro, RackMac, MacPro.
[*]The 'X,Y' is your Mac's version or generation. A 1,1 is first generation, 2,1 is second generation, etc.
[/LIST]
 
[*]Once you have determined your Mac version, [COLOR=Blue]**check the appropriate wiki page**[/COLOR](s) for your Mac to make sure the solution is not there. Note that the MacBookPro guides also refer to information in the previous versions' guides:
[LIST]
[*][MacBook1,1 or 2,1]("https://help.ubuntu.com/community/MacBook")
[*][MacBook3,1 or 4,1 ]("https://help.ubuntu.com/community/MacBook_Santa_Rosa")(also called 'SantaRosa')
[*][MacBookPro1,1 or 2,1]("https://help.ubuntu.com/community/MacBookPro")
[*][MacBookPro3,1]("https://wiki.ubuntu.com/MacBookPro/SantaRosa") (also called 'SantaRosa')
[*][MacBookPro4,1]("https://wiki.ubuntu.com/MacBookPro/Penryn") (also called 'Penryn')
[*][MacBookAir1,1]("https://help.ubuntu.com/community/Macbook_Air")
[*][iMacX,X]("https://help.ubuntu.com/community/Intel_iMac") (any _Intel_ version. I think this is >= 4,1)
[*][MacMini]("https://help.ubuntu.com/community/Mac_mini") (needs updating)
[*][MacPro]("https://help.ubuntu.com/community/MacPro") (Any Intel Version)
[*]RackMacX,X (XServes, Anyone care to start a page?)
[*]Any others?
[/LIST]
 
[*]If you have a version number that is new or unlisted, post your Mac version and the output of 'lspci' so that we can see what hardware you have and try to use the wiki page for the latest version of your Mac and note anything that works on your new hardware.
[*]If you cannot find help from the wiki, also check the [Intel Mac FAQ]("http://ubuntuforums.org/showthread.php?t=493393").
[*]Last but not least, when posting please include your Mac version in your post so that we know what hardware you are dealing with.
[LIST]
[*]Additionally, when the solution is found, [Mark the thread solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").
[*]Also, if you figure the problem out yourself, please post the solution so that others might benefit as well.
[/LIST]
 
[/LIST]
Thanks!

---

### Post by kosumi68 on 2008-07-24
Thank you cyberdork, for a very nice summary page!

---

### Post by Frak on 2008-10-30
This may be necromancing, but I'd like to add these, as there are many different platforms
PowerMac G4 line (they differ in hardware)
Power Mac G4 (PCI Graphics) Had only 4 PCI-X slots. No AGP
Power Mac G4 (AGP Graphics) Had a VGA and DVI slot in graphics. No ADC as of yet. Also Sound Ports were aligned vertically on the bottom of the rear ports.
Power Mac G4 (Gigabit Ethernet) Had VGA and ADC, no DVI. Sound ports were aligned horizontally along the bottom.
Power Mac G4 (Digital Audio) VGA and ADC, no DVI. Sound ports were aligned vertically along the top of the rear ports.
Power Mac G4 (Quicksilver) had a silver front face and slender optical ports. There were no mirrors along the front.
Power Mac G4 (MDD or Mirrored Door Drive) had a mirrored optical drive door bay. These models could not boot into Mac OS 9.

Since these vary in hardware significantly, ranging from memory type, hard drive size, optical bay, all the way to how the processor was designed, I thought these would be important.

EDIT
Oh, Power Mac G4 Cube... was a cube...

---

### Post by cyberdork33 on 2008-10-30
> **Frak said:**
> This may be necromancing, but I'd like to add these, as there are many different platforms

Well, now we need to get the title changed!

---

### Post by Frak on 2008-10-31
> **cyberdork33 said:**
> Well, now we need to get the title changed!
Yep, just now read that whole "Intel" thing.

---

