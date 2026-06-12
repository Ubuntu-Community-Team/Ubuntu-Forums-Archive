---
title: "Won't boot after upgrade"
date: 2011-06-29
forum: Any Other OS
---

### Post by MarcG on 2011-06-29
I performed an apt-get update, apt-get upgrade and now I can't boot up. It goes as far as the Automatic Login window, but that's messed up. The field that formerly let me choose "Automatic Login" is now a small slit, and the buttons below that to get into auto login or cancel are not there. I hit all different combinations of keys, Esc, Tab, Enter, Ctl-Alt-<all function keys>, and who knows what random assortment of key presses, but no luck. Also, Cap Lock and Num Lock don't seem to function. No mouse, but that's how it operated previously.

Hitting Esc and other Ctl-Alt-Function Keys before I get to the auto login screen changes the display, but doesn't get me into anything where I can halt the process and run from a console. Esc let's me see some kind of boot progress, but I don't see anything useful there.

Any ideas? I'm running Linux Mint Isadora (Ubuntu 10.04).

---

### Post by dino99 on 2011-06-29
reboot in recovery mode, then select "repair packages"

---

### Post by MarcG on 2011-06-29
> **dino99 said:**
> reboot in recovery mode, then select "repair packages"

Thanks. I've searched and found two ways to get into recovery mode. One is hit Esc during boot, but that didn't work. The other was hold onto Shift while booting, which I haven't tried (but will tonight). Any other ways to get into recovery mode?

I'm also bringing home a few recovery disks to try if I can't get to rescue mode: Rescatux, Ubuntu Rescue Remix, and Super Grub. And as a last resort I'll have the latest Ubuntu Install CD and USB stick. Luckily I have the boot drive on its own partition, so I wouldn't lose my /home stuff if I decide to do a new, fresh install.

Anything else anyone can recommend I pack home for my latest adventure? I've got a fast network here at work, so I can make CDs all day. Comcast is being stupid at home and downloading a CD image can take hours.

---

### Post by dino99 on 2011-06-29
to get grub menu: hold "shift" key down at bios end process.

---

### Post by Perfect Storm on 2011-06-29
Moved to Other OS/Distro Talk.

---

### Post by MarcG on 2011-06-29
> **dino99 said:**
> reboot in recovery mode, then select "repair packages"

OK, got to GRUB menu and tried to boot recovery mode, but it hangs at line ```
[2.9140000] Console: switching to colour frame buffer device 80X30
```

Only ctl-alt-del seems to get it out of that, but then it just reboots and I'm back to autologin that doesn't work. I never saw any "repair packages".

Next I tried the different rescue disks. They boot fine and Rescatux lets me access my file system. I tried going into /etc/gdm/custom.conf to change AutologinEnable to False, but it was already there. I renamed custom.conf to hide it, but no luck there, either.

---

### Post by NightwishFan on 2011-06-29
When you get to the menu to choose recovery mode, highlight it, then press 'e' to edit the entry. Find the line that ends with 'quiet splash'. Add a space at the end and then (no quotes) 'nomodeset'. Press ctrl+x to boot.

Does this let you access recovery mode?

---

### Post by MarcG on 2011-06-30
> **NightwishFan said:**
> When you get to the menu to choose recovery mode, highlight it, then press 'e' to edit the entry. Find the line that ends with 'quiet splash'. Add a space at the end and then (no quotes) 'nomodeset'. Press ctrl+x to boot.

Does this let you access recovery mode?

Thanks, but I broke things even more and couldn't get back to any kind of recovery mode. It looks like something I did with Rescatux (probably their grub update) removed my kernel, so all I got when booting was the grub prompt. It couldn't find any kernel to boot, and I couldn't find one, either.

So I just re-installed my original Mint Isadora. I tried the latest Mint 11, but that wouldn't boot - just like Ubuntu 11. It turns out there's a bug and the latest kernels don't work with my eMachines E725. I didn't need that to compound things :/

Anyway, I'm back up and thanks to all!

---

### Post by buntumonkey on 2011-10-02
Are you by any change running an ATI card in your machine?

This helped me get from a non-responsive black screen back to a normal boot. The problem was with my ATI HD video card and the proprietary drivers I installed directly from AMD's site.

First I purged fglrx following these directions:
[URL="http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx"]http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx
[/URL]

And then I reinstalled the newest drivers from amd's site:
[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")


It works fine now, though I am wary of running apt-get update/upgrade, cause that's what been breaking my machine, though I could probably just run these steps again if it does.

---

