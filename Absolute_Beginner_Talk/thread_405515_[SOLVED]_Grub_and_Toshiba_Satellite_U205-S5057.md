---
title: "[SOLVED] Grub and Toshiba Satellite U205-S5057"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by jsr on 2007-04-09
Hi all,
This is my first post here...

I got my shiny new Toshiba 12" laptop last weekend. Installed Ubuntu every thing working well.. but for some issues with the Grub. 

I have shrunk the existing partition of 160G to 80 which had Vista installed. installed Ubuntu on the rest.  Installed grub on hd0. 

1. After reboot. The grub menu showed up and I could boot on Ubuntu but Vista did not boot up.. just the Vista progress bar shows thats all, nothing happens.. 

2. The Grub menu never shows up after a hard boot :-O, It directly boots into Ubuntu.
3. While soft booting (clicking System | Reboot) Grub shows up

any clues.. how to get these fixed? 

thanks 
--
jsr

/boot/grub/menu.lst
-------
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda8 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
boot

title           Windows Vista/Longhorn (loader)
root            (hd0,1)
makeactive
chainloader     +1

---

### Post by jsr on 2007-04-09
any clues.... I am not sure what I am doing wrong

---

### Post by Austin_KW on 2007-04-10
You only mention creating 2 partitions, but menu.lst is showing 8 partitions with vista on the second, What is the output of "sudo fdisk -l /dev/sda"

---

### Post by jsr on 2007-04-10
> **Austin_KW said:**
> You only mention creating 2 partitions, but menu.lst is showing 8 partitions with vista on the second, What is the output of "sudo fdisk -l /dev/sda"

yeah thats true, those are the extended partitions.. 

To pin out the problem with Grub not showing up on the Boot up, I removed evertyhing from the HDD, Installed ubuntu with it "Use entire HDD" option, It created 1 primary partion and a extended which has the swap.. thats it.. 

But still when I hard boot my Laptop the Grub does not shows up..

I get the TOSHIBA Splash screen and then a very bright white screen and directly boots to Ubuntu.. 

On a soft reboot.. The TOSHIBA splash does not show up, but now 'GRUB' shows up with the boot menu.......... 

man.. this is driving me nuts.. any clues?? :confused: :confused: :confused: 

--
jsr

---

### Post by Austin_KW on 2007-04-10
check your  /boot/grub/menu.lst

What is the timeout value set to, or is hiddenmenu set, Have you tries hitting/holding the escape key on cold boot

---

### Post by jsr on 2007-04-10
this is the menu.lst
timeout is set to 5

--
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

---

### Post by Gazneth on 2007-04-10
Here is a link on this forum to try and correct your problem.
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)
This seems to be a common Vista problem, don't give up on Ubuntu because of this bad experience.

---

### Post by Gazneth on 2007-04-10
Here is an even better tutorial on how to dual boot Vista and Ubuntu.[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by jsr on 2007-04-13
Nope I do not give up so easily :) 
I know there was something wrong with the way I was doing this, to isolate the problem "i.e GRUB menu not showing up at cold boot on my laptop" 

I removed all the partiotions, created new ones, installed just Ubuntu only... no other OS and the grub on the MBR, i.e. grub-install hd0... but still the problem persists... It has something to do with the Laptop I guess.... The Toshiba U205-S5057... 

Still the GRUB menu don't show up at cold boot :confused: :confused: :confused: 

When I reboot.. I get

1. a bright white screen (like the brightness is set at 100% ) with a blinking cursor.
2. Press Esc, nothing happens
3. automatically boot to Ubuntu.... 

Soft boot,
GRUB menu comes up, and all is fine.......... 'does that ring a Bell??? """ 

--
jsr

---

### Post by pjssilva on 2007-04-18
Just to let you know. Same thing here with a U205-S5067.

On cold boots I get Ubuntu directly. Grub menu only appears if I restart the computer.

However I found a better workaround to get grub menu in a cold start. In the Toshiba boot screen press Esc, then press F1 to enter Bios Setup. Then press Esc again to leave Bios Setup without makin any chnges. It will ask for a confirmation (leave without saving (y/n)). Confirm pressing Y. The system boots into Grub. 

Even though it is a little convoluted the above solution is faster then booting into Ubuntu and then restarting to go to Windows. 

Better yet, do as I do, don't boot in Windows anymore :-D

---

### Post by jsr on 2007-04-20
wow... so I was right... I knew there was something wrong with this Laptop/bios or something else... that creates this problem during cold boots.. 
But still I am not convinced that this laptop cant bring up Grub on cold boots, there should be something :confused: 

BTW I just have Ubuntu and Debian installed no more Vista :)

--
jsr

---

### Post by pjssilva on 2007-04-24
I may have found a good solution:

Turn the computer on and press ESC followed by F1 to enter the BIOS setting page. Keep on pressing the down arrow key until the option "Diagnostic mode" is selected. Press the space bar to change its status from "Disabled" to "Enabled", press End to exit the BIOS (and save your chages by confirming using the Y key).

Now your laptop won't show the Toshiba logo when its start. It will show some self tests (that take little long: it tests the memory four times!). After the self test the computer boots and grubs always work. If you can wait the self tests, leave it like this.

A funny thing is that after seeing the self test for some boots I entetered the BIOS again and pressed the HOME key to restore the original settings and saved the new status. The Toshiba logo was back on boot, but grub kept on working. It seems like the simple fact of saving different values on the BIOS solved some weird BIOS bug.

Can you confirm if the above steps work on your U205?

---

### Post by Austin_KW on 2007-04-25
Does that toshiba come with a hidden or recovery partition? Just wondering if the bios is booting the first partition rather that the mbr.

---

### Post by pjssilva on 2007-04-25
Cfdisk says it has a little partition of unknown type (27) at the start, then the NTFS windows partion and finally the linux partitions. 

The bootable partition is the windows partition (windows).

Note that the system is not trying to boot directly into windows. It boot directly into linux under cold boots.

---

### Post by jsr on 2007-04-28
> **pjssilva said:**
> I may have found a good solution:

Turn the computer on and press ESC followed by F1 to enter the BIOS setting page. Keep on pressing the down arrow key until the option "Diagnostic mode" is selected. Press the space bar to change its status from "Disabled" to "Enabled", press End to exit the BIOS (and save your chages by confirming using the Y key).

Now your laptop won't show the Toshiba logo when its start. It will show some self tests (that take little long: it tests the memory four times!). After the self test the computer boots and grubs always work. If you can wait the self tests, leave it like this.

A funny thing is that after seeing the self test for some boots I entetered the BIOS again and pressed the HOME key to restore the original settings and saved the new status. The Toshiba logo was back on boot, but grub kept on working. It seems like the simple fact of saving different values on the BIOS solved some weird BIOS bug.

Can you confirm if the above steps work on your U205?

pjssilva!!  :guitar: :guitar: :guitar: It WORKED !!!!!!!!!!!!!! :biggrin:
I think that is really a weird BIOS bug, It would be really nice to know how saving different values on the BIOS changes the behaviour.. just wondering..

thanks a lot bother for finding a way out of this problem..

--
jsr

---

### Post by jsr on 2007-05-09
> **pjssilva said:**
> I may have found a good solution:

Can you confirm if the above steps work on your U205?

I thought It worked for me! But after few days I am not sure what I did on the BIOS settings, again It is back to the bright screen -> no grub menu and directly booting to the default OS installation.

BTW Another way which I use now to overcome this problem, is I changed the boot sequence to LAN/CDROM/HDD... by using this setting the GRUB selection menu always shows up now! I am not sure what are these weired BIOS bugs, I guess this is a fool proof work around for that nasty cold boot | No Grub menu problem.. 

let me know if it does not work for anyone. 

--
jsr

---

### Post by Ozeuss on 2007-05-09
this reminds me of a post i saw [earlier today]("http://ubuntuforums.org/showthread.php?t=438025&highlight=boot+cold+windows").
now, from what it seems, the situation is not identical, so i dunno if this is the right thing to do. but you can explore in that direction.

---

### Post by absol_of_doom on 2007-07-31
Thank you people so much.  I have been tearing my hair out and reinstalling obbsesively because I had that problem with my Toshiba...  If I hadn't found this thread I surely would have gone insane! :)
I have been trying to restore grub and all kinds of crap tryin to figure out what was wrong.  I did figure out, however, that the grub menu is still there.  If you press up or down you'll see dotted green lines and you can change it that way...just memorize how many times to press up/down. (I couldn't take it anyway because I have OCD and everything has to work perfectly.)  THANK YOU FOR THESE FIXES!!!!!!!:)

---

### Post by vx220 on 2007-08-29
It is always a relief to find a forum that lists exactly the problem that you are having!
I did the - edit BIOS trick (I used the re-order the boot sequence) and now GRUB reappears :)

---

