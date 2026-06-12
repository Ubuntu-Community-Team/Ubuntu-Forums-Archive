---
title: "Ubuntu + Nvidia 8800 GTS = ...?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by SolaceAvatar on 2007-06-03
My new computer has a Nvidia 8800 GTS graphics card... and the Ubuntu CD I got (admittedly a while ago) will not start with it on (IE a live CD to install it). Doesn't recognize it or something, won't work at all, boots me back to the BIOS or something. Is there a version of Ubuntu that'll work on it, or is there something I can do to make it work? Side note... I can't plug my monitor into my motherboard, because for some reason it's got a male connector, and all my monitors have a male connector, so I'd need to go out and get an  adapter to make that work, and if I could just make Ubuntu work from the start, well, it'd be a lot easier (and I'd need it to work eventually anyway). So... any help will be appreciated. :)

---

### Post by SolaceAvatar on 2007-06-04
Wow, tenth page without a reply. Should I try a different section of the forum, or something?

---

### Post by pappapump on 2007-06-04
What you need for the monitor plug is a VGA  gender changer from radio shack.
To solve your video problems, try going into bios and changing your video card bus type from AGP to PCI if possible.
If your Motherboard is a gigabyte model from mid last year to now or an acer with the same chipset you may have the infamous dissapearing IRQ.
The way to solve this is to try changing the video bus settings to pci, not pcie in bios if no VGA option is available.
THEN if that doesnt work look for the settings that allow you to manually assing an IRQ on the video card.

---

### Post by Feba on 2007-06-04
sounds like your BIOS is trying to use the motherboard graphics, not the NVIDIA. Make sure integrated graphics and the motherboard's video is disabled.

---

### Post by pappapump on 2007-06-04
Now THATS a thought!
He just may have an onboard graphics chipset enabled.
OMG what a conflict.
Windows can handle stuff like that cuz it's sloppy, but linux is either gonna choose one or the other.

---

### Post by Feba on 2007-06-04
If you mean windows can BOOT through that, possibly. I've never heard of leaving both on working for things like games or such though.

---

### Post by SolaceAvatar on 2007-06-04
Well, it works perfectly fine from windows (on that now), even in games, so... well, if it shouldn't, then that's not the problem, I guess. I don't really want to change my video settings in the BIOS... I mean, wouldn't that kind of invalidate the whole purpose of having a video card anyway, making it inoperable? I was just kinda thinking that since Ubuntu apparently comes with drivers for video cards installed already, a new card + old Ubuntu logically would have a missing driver. If there's no way to make Ubuntu work with my video card, then I guess I'm stuck without it... :( I'll try the other stuff tho, if I can get it to work without breaking my computer... >.>;

---

### Post by pappapump on 2007-06-04
You seem to have missed the point bro.
You can't have 2 mismatched video ports enabled.
You choose the slot based one and disable the onboard one, otherwise the 2 will have conflicts.
I have been able to play games as well in windows with the second Video adapter active, but thats because I was fiddling around in bios and forgot to turn it off, call it blind luck.
Having both active is a ridiculous waste of ram and resources unless you use dual monitor in windows AND your onboard Video card is compatible with a dual video setup, which most aren't.
Also remember that onboard Video uses your system ram instead of installed Video ram to function, effectively robbing linux of extra resources it can use.

---

### Post by Feba on 2007-06-04
I said to disable your integrated graphics. Large difference.

---

### Post by pappapump on 2007-06-04
Pass the coffee feba, im a quart low.

---

### Post by Feba on 2007-06-04
I hate coffee. Only supercaffineated beverage I like is Bawls. Man I wish I had some bawls in my mouth right now.

---

### Post by SolaceAvatar on 2007-06-04
Ah, ok, that makes a lot more sense than what I thought you'd said. Thanks. ^^ Now... I feel like a hopeless noob for this, but I've never used this BIOS before and I can't find where the setting to turn off the integrated video is. >.>;; This is the motherboard it came from, and yes, I checked the manual... and unless the "onboard 1394" means integrated video, I'm so very lost... x.x Sad thing is, I've messed with this sort of thing with my old BIOS, so if I could just find the option I'm sure I could fix it...

[http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ClassValue=Motherboard&ProductID=2310&ProductName=GA-M55SLI-S4](http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ClassValue=Motherboard&ProductID=2310&ProductName=GA-M55SLI-S4)

---

### Post by pappapump on 2007-06-04
> **Feba said:**
> I hate coffee. Only supercaffineated beverage I like is Bawls. Man I wish I had some bawls in my mouth right now.

OMG I'm choking with tears in my eyes now
Re-Read your post slowly LMAO!

---

### Post by pappapump on 2007-06-04
Good thing is, you have a gigabyte which is definitely bios flash friendly.
Look at the Gigabyte drivers page and click the bios shortcut and read the update bios instructions.
REMEMBER to WRITE down your bios version which shows up at every reboot BEFORE downloading a bios update, to be sure you don't flash it with the wrong one.
IF the versions match then leave don't flash bios ( I mention this because Gigabyte is always updating their bios)
Your options for entering bios are either, DEL, or F2, you may also see a live bios prompt during bootup, ignore that.
Now just read each screen carefully b4 you adjust anything and also read the little help prompts which describe what each setting does.

---

### Post by Feba on 2007-06-04
1394 = firewire

I don't think you need to update your BIOS, just restart your computer, press ESC/F1/F12/DEL or whatever button the POST (that's the screen that shows up as soon as your PC is turned on) says to press, you should enter the BIOS. Search through your options until you see something about integrated graphics or GPU or etc. and disable it.

I don't think that's your motherboard. It doesn't mention anything about an external VGA port on the rear panel.

---

### Post by SolaceAvatar on 2007-06-04
> **Feba said:**
> I don't think that's your motherboard. It doesn't mention anything about an external VGA port on the rear panel.
Actually, that would explain a lot. Is it possible my motherboard lacks one, and I was just mistaking the serial port (or something) for it?

---

### Post by heldal on 2007-06-07
Nvidia driver-packages are missing a file (x-server-module) that is required to make them work with 8800 GPU's. Installation has to be done in character-mode and either:

1. Install the "nvidia-glx-new" driver which is the one capable of handling the 8800s. Then find a working copy of the missing x-server-module (/usr/lib/xorg/modules/libwfb.so) somewhere (hint: it's part of the package available from nvidia's site). Doing it this way means it'll hopefully get handled properly with future package-updates once the Ubuntu-developers fix their packaging scripts.

2. Drop the Nvidia drivers from the Ubuntu-install. Then download and install the official driver from Nvidia's website instead, following _Nvidia's_ instructions. This means you're on your own later and may have to re-install the driver each time the linux-kernel and/or X-server is updated. 

3. Use one of the 3rd-party packages available to automate the installation of driver-packages. The downside is that there is no guarantee such packages will survive future updates of the ubuntu core.

---

