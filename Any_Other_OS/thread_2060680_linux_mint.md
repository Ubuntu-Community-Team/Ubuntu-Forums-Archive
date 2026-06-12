---
title: "linux mint"
date: 2012-09-20
forum: Any Other OS
---

### Post by jakespet on 2012-09-20
Hi, 
I just installed Ubuntu alongside Linux mint. I thought I would be able to run Linux Mint but for some reason I can't. When I first installed Ubuntu, I assumed I would be able to run Linux Mint because it told me it would be installed to run along side of Ubuntu. 
So, now I have a problem. how do I recover Linux Mint? Any help would be appreciated.
Thank you.

---

### Post by Karlchen on 2012-09-20
Hello, jakespet.

I am not quite sure I understood the details of your report correctly.
So from what I understand

[LIST]
[*]Your first operating system is Ubuntu. Installed first.
[*]You installed Linux Mint next, alongside Ubuntu.
[*]When you boot your machine no bootmenu is displayed giving you a chance of selecting to boot Ubuntu or Linux Mint. Instead Ubuntu is booted automatically.
[*]So currently you are logged in to Ubuntu.
[/LIST]

Provided that my assumptions are correct, 

[LIST]
[*]open a terminal session
[*]run the commandline ```
sudo update-grub
``` This should make the Ubuntu Grub realize a second operating system, Linux Mint, is present and add it to its Grub boot menu
[*]Once the command has terminated successfully, close the terminal session. Close all running applications and reboot.
[/LIST]

Chances are that you will be presented a boot menu which offers you a choice to boot

[LIST]
[*]Ubuntu
[*]Ubuntu (recovey mode)
[*]Linux Mint
[*]Linux Mint (recovery mode]
[*]Memtest
[/LIST]

Select **Linux Mint**.
Hopefully Linux Mint will come up as expected.
Please let us know whether things worked out this way.

Kind regards,
Karl

---

### Post by tumutanzi.com on 2012-09-21
I tried Linux Mint, there is no Gnome that I need, though you may say I can install Gnome desktop, I will not do that.

---

