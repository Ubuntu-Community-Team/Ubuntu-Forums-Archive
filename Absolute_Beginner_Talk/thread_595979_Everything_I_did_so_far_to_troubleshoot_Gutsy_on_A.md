---
title: "Everything I did so far to troubleshoot Gutsy on Acer Aspire 5100"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by ensign.slasher on 2007-10-29
Here's what I did so far to make Gusty work as normal as it can on my laptop. I hope it helps somebody and I hope to get some feedback too :popcorn:

1. Solved the splash screen problem (it didn't show) by doing the following changes (found it in some bug report):
- edited the file: /etc/usplash.conf
- changed the resolution inside the conf file to mine (it was 1280x1024, I put 1280x800)
- run: sudo update-initramfs -u
Correct after reboot.

2. Turned the desktop special effects on with "sudo aptitude install xserver-xgl" and "sudo aptitude install compizconfig-settings-manager". BUT this is how to do it properly [http://ubuntuforums.org/showthread.php?t=569654&highlight=splash+screen]("http://ubuntuforums.org/showthread.php?t=569654&highlight=splash+screen") ... So now I'm unsure if I did everything right or what? It works so I'll not be fixin' someting that works :) It really pays off to learn various shortcuts accesible through the "Windows" key. Like Expose: WinKey+e, or WinKey+TAB for shifting windows.

3. Added codecs using the "Add/Remove" app. They are under "All avaliavle apps.", "ubuntu-restricted-extras". I used this page to help me out: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats"). But DVDs are still not playing because there is no decoder - using VLC Player for that, but I don't actually need this supported because I don't use it.

4. Part of the interface is curently in slovene language and part is english. This happened emediatelly after Gutsy fetched and installed updates after the instalation. How do I fix that?

5. How do I add the dictionaries to Openoffice.org? I'm missing the slovene dictionary and I can't figure out what happened to the englihs one.

6. Suspend and hibernate do not work because of a bug and becuase of compatibility issues with desktop special effects. Turned them of with "sudo gedit  /etc/default/acpi-support" to avoid accidental use. I hope this gets fixed some day but for now Gutsy boots fast enough for me.

7. Bluetooth is not supported yet - it appears to be working but it doesn't do anything. Cardreader is only partially supported, but it never actually worked as advertised in WindowsXP either.

8. I use wireless to access my router. I suppose wired LAN works. It should, it always did work on this laptop. But I have no way of testing the modem for dialup access - this is not important for me because I don't use that anymore and don't know anyone who still does either.

9. I have a Wacom Volito 2 Tablet. Check the end of your /etc/X11/xorg.conf file for "# Uncomment if you have a wacom tablet" and do it :) If only Gimp and Inkscape gave me preasure sensitivity now...

10. I get the "BIOS BUG #81[49435000]" and it looks like it must be related to the card readers, firewire port, or the bus these are connected to. Also it could be powermanagement or the kernel probing for something my BIOS doesn't support. I'll wait for next kernel update since this doesn't break anything... yet.

Helpful resource: [http://ubuntu-tutorials.com/]("http://ubuntu-tutorials.com/") and this here forums.

---

### Post by jinnman on 2007-10-29
Thanks for your post.  I am slowly getting up the courage to dual boot Vista and Ubuntu 7.10 on my Acer Aspire 5100-5023.  I can see myself referring to this thread in the future.

---

### Post by ensign.slasher on 2007-10-29
@ jinnman: Be careful before doing that! Vistas NTFS partition should not be resized with linux tools - it crashes it. Use Vistas tools to resize it's partition.

---

### Post by jinnman on 2007-10-30
Thanks for the warning.  I had already resized in Vista.  I think I'm ready to go.  May install tonight.  Wish me luck!

---

### Post by skygoya on 2007-12-21
jinman  how did your installation go?  i have the same computer and i dont this i can get compiz fusion to work because of the 1100 graphic driver.. let me know if you did

---

