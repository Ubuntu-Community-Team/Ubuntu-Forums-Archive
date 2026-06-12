---
title: "Help install/boot black screen"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by sexymomma on 2007-07-24
My specs are: Msi 939 board, AMD 3800+ dual core CPU, 1 gig Ram, Ati X1300Pro Video, Acer 19" widescreen Monitor, 250 gig IDE hdd, 250 Sata hdd just installed, I had Ubuntu 7.04  x86 installed on a partition with an 80 gig IDE hdd dual booted with Windows XP Pro, until a week ago. That install was easy to get around by choosing F4 and choosing 1024x768, and install and boot went fine. Gave away my 80 gig to child, and already formatted it, and now I have Windows Xp installed on the IDE, and I want to put Ubuntu onto the Sata hdd. I tried installing the x86 version,(the x64 version gave nothing but problems on last hdd) and clicking on install shows the white cursor for a few seconds and then black screen. I've tried the other methods of F4 vga, and F6 other options, and Cntrl-Alt-F1 to get update and fglrx driver. I then downloaded and installed the Ubuntu Alternative iso, and using text install it seemed to work. I chose use entire hdd of Sata, and when I rebooted I have the choice to boot into either operating system, but choosing Ubuntu, I get black screen, and I hear the login screen music, but can't see nothing. Even booting in safe graphics mode doesnt help. I can still boot into windows, that's how I'm searching for answers now.:( I really like Ubuntu and want to switch over, once I'm comfortable with the gui, but for now I'm really stuck.
Help.

---

### Post by benx009 on 2007-07-24
hmmm.... can you at least boot up in text mode?  try pressing Alt+F1 right after selecting ubuntu at the boot menu and see try to keep track of any useful text output/error messages.  if you can't see anything at all, you would definitely want to reinstall.

---

### Post by sexymomma on 2007-07-25
I haven't tried Alt-F1, but I have tried reinstalling X86 desktop version, and I still get black screen trying all the options I did the first time. I'll give that a try, and post back.

---

### Post by sexymomma on 2007-07-25
Tried Alt-F1 the only error was usb device error -62, which is probably my usb hub. But that shouldn't interfere with installation I wouldn't think.

---

### Post by sexymomma on 2007-07-25
I turned up my speakers and heard the login sounds, and blindly typed in username and password, heard the start of gnomes' nautilus, but still black screen, with monitor displaying no signal. There has to be some workaround whether the problem is the 19" lcd monitor or the ati x1300. It worked on my 80 gig ide, before I gave it away, using the same video card and monitor, and the only thing different is I added a sata hdd, but for some reason the sata registers in the bios as Third master. I tried switching the hdd around making the Sata the first master, and loaded windows onto it, and no operating system would boot. So then I installed windows on Ide, and it showed dual boot, both with windows, and made ide boot drive, and sata system drive, I formatted the sata drive with the ubuntu alternative iso and installed but now am at a stand still with this black screen problem. Should I maybe partition my 250 gig IDE drive to dual boot on the same drive? I prefer not to because I have about 170gig used, and alot of stuff to backup. But Really want Ubuntu. I can't stand it when something isn't working, even though I know ubuntu is normally good.

---

