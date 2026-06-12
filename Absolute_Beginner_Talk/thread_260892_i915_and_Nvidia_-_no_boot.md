---
title: "i915 and Nvidia - no boot"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Mothium on 2006-09-19
I'm pretty new to linux, i used to have mandriva (when it was called mandrake) a few years ago but i never stuck with it. I thought i'd come back and give Ubuntu a go.

I downloaded the Live CD, it wouldn't boot, it got stuck when it was installing the hardware drivers.

I downloaded the alternate CD, installed in text mode, it didn't boot - getting stuck at the installing hardware drivers.

After some research i think i've found the problem, i have an intel 915M chipset with onboard graphics AND an Nvidia 6600LE. I found [this]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55104") and i've tried to follow it but my experience with linux is extremely limited. I put the script mentioned on the page in "\etc\init.d\nVidia-on-intel" by mounting the drive on XP.

It still doesn't work (i'm not that surprised!). What should i be doing? I'm not even 100% sure that this is my problem.

My hardware is:

Intel P4 3.2Ghz
512 DDR2
Terratec Aureon 5.1 Sky (soundcard)
Nvidia 6600LE
Intel i915M
160GB hdd

Thanks in advance

---

### Post by coffeecat on 2006-09-19
I haven't got much to offer except a couple of comments/questions.

First, I guess you know your own machine but are you sure you have onboard Intel graphics? Intel chipsets with graphics should have a G in the identifier, making yours something like i915GM - I would have thought.

You say you added the script by mounting the drive in XP. How exactly did you do that? I know you can add a driver to Windows to let it access ext2/3 partitions, but I wouldn't like to write config files with Windows myself. Have you tried booting into recovery mode? It might bypass the hardware drivers that are causing the problem. If so, you'll
get into a text command line terminal where you could edit/create the script in nano.

I would have thought the combination of an Intel chipset board with a Nvidia card would be a common one and we would have heard more about this issue. I wonder if it only affects some motherboards. Whatever, have you looked in your BIOS to see if you can inactivate the onboard graphics?

---

### Post by Mothium on 2006-09-19
I just checked, in XP, device manager says i have 2 display adapters one is a 910GL/GV (i don't know where i got 915 from)

Recovery mode does the same thing.

I mounted the drive using a driver i found on sourceforge, things do seem a bit different (some files have a few bytes of data but when i open them in a text editor theres nothing. This is showing up my lack of linux knowledge.

I looked around the BIOS and i can't find an option to turn the onboard off. I'm not 100% sure there isn't one, but its not obvious and i don't have a manual for the board so i don't fancy pressing random buttons.

I would have thought it was a fairly common config, which is why i was sceptical that it was the problem.

---

### Post by coffeecat on 2006-09-19
> **Mothium said:**
> I mounted the drive using a driver i found on sourceforge, things do seem a bit different (some files have a few bytes of data but when i open them in a text editor theres nothing. This is showing up my lack of linux knowledge.

I once had a problem editing a Linux-created file with the Windows text editor because the file didn't have a .txt extension, but you're doing something different - trying to create a Linux script with the Windows text editor. But there is a potential problem - something to do with the difference in the way newlines are done in Windows and Linux text files. It could be that your Windows created file is not being read properly in Linux.

The only other suggestion I can make is to create the nVidia-on-intel file using the Ubuntu live CD on another machine (on which it works). Save the file directly to a usb storage device, and then use Windows to copy it from the usb device into /etc/init.d on your Ubuntu install. A bit of a long shot though, but might be worth a try.

---

### Post by Mothium on 2006-09-19
I'll give it a shot, although i'm not actually writing the script myself, i just downloaded it and moved it. Is there something else i need to do make it use this script?

I just rebooted into recovery mode to get a bit more information. It gets stuck and the kernal panics, theres lots of mentions of intel-agp and other intel things, something mentions 915 so thats probably what made me think that was what i had.

EDIT:

Just thought i would mention that the Nvidia card is a PCI express card if that makes any difference.

---

### Post by coffeecat on 2006-09-19
> **Mothium said:**
> Just thought i would mention that the Nvidia card is a PCI express card if that makes any difference.

I don't know, but that's very interesting. I'm actually posting at the moment from Ubuntu Dapper in a machine with Intel 915G/P/GV/GL/PL/910GL chipset (according to lspci) and a nvidia geforce 6200 PCI express card. I've set it up as a multiboot and I've had no trouble installing or running a variety of distros on it. Makes me think that your problem is not related to the reported bug, or this is something that affects only some motherboards.

As far as the text file and Windows is concerned, if you copied and pasted this newline/carriage return business should have made no difference, but you never know with Windows. But the question whether you should do something else with it, my apologies for not noticing before, I think, yes. The writer of that script says, 'It must be ran quite early - before the restricted modules are loaded - that's why I  named it /etc/rcS.d/S06nVidia-on-intel,' so I guess it would have to be called from a bootup script somewhere. But how you do that I don't know - I'm out of my depth here. Your link is a number of devs discussing this issue. They would know how to.

Sorry I haven't got anything else to offer.

---

### Post by Mothium on 2006-09-19
Thanks for your help, i'm doubting whether that is my problem now. I'm able to load an old (3.7) Knoppix CD but i don't really know what i can do from there.

Theres a *.deb file on that page aswell, i'm just figuring out how to use that from loading a terminal from GRUB, if that doesn't work i'm about ready to give up and wait for a new release.

Thanks all the same, i'm subscribed to this thread so if you come up with anything i'll see it.

---

