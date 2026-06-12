---
title: "Brightness problem after sleep"
date: 2017-01-19
forum: Apple Hardware Users
---

### Post by joannacw on 2017-01-19
I just installed Xubuntu LTS Xenial Xerus on my M*acBook Pro 1,2 with a 2.16 GHz Intel Core Duo processor and 2GB 667 MHz DDR2 SDRAM  *The brightness is fine at startup and during use, but after sleep the screen is very dark; I could barely see the screen asking me to enter my password, couldn't read anything else, had to use the power button to shut down. How can I set my computer so that it wakes up with reasonable screen brightness? Not sure if this goes in the Apple forum or here; the computer wakes up brightly when running Mac OS X on the other partition.

---

### Post by slickymaster on 2017-01-19
*Thread moved to **Apple Hardware Users**.*

---

### Post by joannacw on 2017-01-19
My latest failed attempt: I added keyboard brightness shortcuts as follows:
[https://ubuntuforums.org/showthread.php?t=2019300](https://ubuntuforums.org/showthread.php?t=2019300)

Specifically, I took these steps:
[COLOR=#000000]1. Edit the grub file:[/COLOR]
[COLOR=#000000]Code:
sudo leafpad /etc/default/grub[/COLOR]
[COLOR=#000000]2. Change the line that reads:[/COLOR]
[COLOR=#000000][I]GRUB_CMDLINE_LINUX=""
[/I]
[/COLOR]
[COLOR=#000000]...to read:[/COLOR]
[COLOR=#000000]Code:
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"[/COLOR]
[COLOR=#000000]3. Save the file.[/COLOR]

[COLOR=#000000]4. Update the boot loader:[/COLOR]
[COLOR=#000000]Code:
sudo update-grub[/COLOR]
[COLOR=#000000]5. Reboot your computer and try again to see if the brightness keys work.

[/COLOR]That gave me a working brightness control while the computer's awake. But when I close the lid and then reopen the computer I still get a very dim password request screen followed by total darkness. What do i need to do to fix this?

---

### Post by joannacw on 2017-01-19
I've tried changing settings in Power Manager; nothing helps there either. Am I dealing with a known bug?

---

### Post by joannacw on 2017-01-19
[COLOR=#333333]I also tried adding these lines in Terminal:[/COLOR]
[COLOR=#333333]sudo apt-get update[/COLOR]
[COLOR=#333333]sudo apt-get install xfce4-power-manager light-locker-settings[/COLOR]
[COLOR=#333333]Light Locker now appears in my Settings, but when I click on the icon it doesn't actually open a control panel--the icon just sits there. What might I have to do to complete the install? (That fix did come from Q&A about Xubuntu 14.04; was that my problem?)[/COLOR]

---

### Post by joannacw on 2017-01-20
On another forum I was advised to enter Terminal and type: [COLOR=#333333] rm ~/.config/autostart/light-locker.desktop
[/COLOR]I did that and got a message saying 

[COLOR=#333333]rm: cannot remove '/home/lorraine/.config/autostart/light-locker.desktop': No such file or directory.[/COLOR]

---

