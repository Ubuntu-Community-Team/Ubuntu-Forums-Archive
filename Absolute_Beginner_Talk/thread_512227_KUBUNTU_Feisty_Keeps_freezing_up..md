---
title: "KUBUNTU Feisty Keeps freezing up."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Nld331 on 2007-07-28
Let me start by saying that I am  proficient with windows, but kubuntu is kicking my tail. I am very interested in Linux and have been trying to migrate away from windows for a few years, but I have never made the move. Last month I decided that I was going to build a new desktop, but instead of loading windows, this was to be a my Linux machine. The specs are as follows: 

             AMD Athlon 64 Processor 3000+
             ATI Radeon X1600
             Western Digital Raptor x 150 Gig SATA hd
             1 Gig DDR2 ram 
             ASUS M2V-MX Mother Board
              HP LightScribe DVD Burner
 
Now for the problem, Most of the time, the computer boots fine, but it will freeze up( mouse cursor will not move) several minutes into a session. I was able to down load the patch for the ATI X drivers, and this has not helped. It is possible that I am missing something, so if anyone of you has any advice it would be greatly appreciated. I really want to make the migration from windows to linux.

---

### Post by wolfen69 on 2007-07-28
you might want to try regular ubuntu. me and my friends have never had it freeze. besides, you can always install the kde desktop on top of ubuntu.

---

### Post by DBStevens on 2007-07-28
Have you run any diagnostics on the base hardware after assembly?

Are you running the restricted ATI drivers?

Are any keyboard lights flashing when the lock up occurs?

Can you provide the output from:

dmesg

and

lspci

---

### Post by zero244 on 2007-07-29
Look at your System Logs under Administration and see if your seeing any errors related to apic. If you are they should show at the bottom and if they are repeating the error every few seconds, that could be at least part of the problem.
That was part of my problem with Feisty which I think is fixed.
I think Feisty is running stable now with Beryl, but Im going to wait a few days to make sure.
I have had Edgy running very stable but I had to install Feisty on this machine to get my wireless working.
Good Luck.

---

### Post by Nld331 on 2007-07-29
I am sorry I am a total noobie to Ubuntu Dmesg lspci are these terminal commands?

---

### Post by DBStevens on 2007-07-29
Yes those are terminal commands.

---

### Post by Nld331 on 2007-07-29
I installed my drivers per the directions on the absolute beginners page.  I can copy the terminal output here but it is rather long, so if there are any key things that I should be looking for I can do that to prevent taking up so much space here.

---

### Post by DBStevens on 2007-07-29
Put them up as an attachment, we are looking for anything that is not normal.  In short any message could have the information we are looking for.  Don't be shocked if I ask for more logs to be made availible.

This may come as a surprise to you, drivers that are not fully open are the very last thing I'd install when setting up a freshly built system.  But that is probably just me and a desire to reduce the number of potential causes of trouble when I don't even know if I managed to get the system properly built and all of the possible little issues like poorly seated PCI cards etc... taken care of

Just reducing the possibilites.

---

### Post by desrt on 2007-08-06
Same problem here on a M2V-MX board with a 3800+ Athlon 64 x2.

This machine has a GForce 7600 GT, though... so it seems unlikely that the problem is ATI-related.

Running 32bit.

Odd thing: when the machine locks up, caps lock doesn't work, but numlock does (USB keyboard).  After a while of being locked up (15 seconds, maybe?) even numlock stops working.

---

### Post by desrt on 2007-08-06
I have found the solution.

According to the ASUS website, the "cool and quiet" feature of the BIOS causes lockups under Windows Vista.  Turns out that the same problem also affects Ubuntu.

As a workaround, disable the "Cool and Quiet" feature in BIOS or flash your BIOS to the latest version.

---

### Post by guillaumeavril on 2007-08-15
Hi!

I am french so excuse my poor english. I've read the thread about your problem and I think that I have the solution. There is a problem with the Asus M2V motherboard and the linux kernel.
After the certain amount of time, ubuntu will freeze. The problem is related with the apic gestion and a driver in the kernel. I've got an Asus M2V motherboard and the solution was for me to add pci=nomsi in the kernel boot line.

To do that:

sudo gedit /boot/grub/menu.lst

And modify the boot line of the first kernel by adding pci=nomsi at the end.

Exemple: 
title           Ubuntu, kernel 2.6.22-9-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-9-generic root=UUID=47499ff0-d484-46e1-82fb-ce6de7a412fa ro quiet splash [COLOR="Red"]pci=nomsi[/COLOR]
initrd          /boot/initrd.img-2.6.22-9-generic
quiet
savedefault

---

