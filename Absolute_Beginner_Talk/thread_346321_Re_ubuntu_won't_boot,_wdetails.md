---
title: "Re: ubuntu won't boot, w/details"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by razz6 on 2007-01-24
New user, Installed ck after unplugging usb stuff, rebooted and the grub loaded, picked ubuntu and got Loading and nothing happened, ran the repair mode, rebooted same thing. any suggestions, I'm dying to dump Windows!!

---

### Post by geek_Man on 2007-01-24
Can you repost that in a slightly clearer manner?

---

### Post by razz6 on 2007-01-25
When I  come to the grub page and choose ubuntu, i go forward to a blank screen with system loading and and a flashing -. I ran the recovery and it lock up at this point.

[171795070.480000] ENABLING 10.apic IRCs
[171795070.480000] ..Vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

The last two entries, any ideas

---

### Post by Kobalt on 2007-01-25
What are your system specs ? It seems you need to boot with noapic nolapic options to me ... 
Did you manage to get a working Live CD session booting and runing before installing Ubuntu ?

---

### Post by razz6 on 2007-01-25
System: hp pavillion; pentium 4 cpu 3.00GHz 1.00 GB ram 60 gb partition for ubuntu on a 230 gb drive. XP service pack 2, Radeon x300 vid, realtech HD audio, Happauge win tv pvr pci

---

### Post by razz6 on 2007-01-25
System: hp pavillion; pentium 4 cpu 3.00GHz 1.00 GB ram 60 gb partition for ubuntu on a 230 gb drive. XP service pack 2, Radeon x300 vid, realtech HD audio, Happauge win tv pvr pci
yes the CD loaded fine..and it worked from the CD

---

### Post by crispingatiesa on 2007-01-25
First try this:

Go to the computer BIOS and disable APIC.

Boot....

If doesn't work, while in Grub choose (F2 or F6 I can't recall now) to edit the booting sequence,
it will bring you to an editor in which you can edit the booting command.

Go to the second line (Kernel) and add "noapic" anywhere to the right of "root=/dev/hd*"

press return to save a reboot....

If it doens't work ... do the same but adding "acpi=off" as an option as well.

If it doesn't work  .. post here again and we'll try something else...

good luck

---

### Post by rsambuca on 2007-01-25
I assume you mean you went through the installation process and now what - neither XP nor ubuntu will boot, or just XP, or you have a choice but ubuntu doesn't work?  what version of ubuntu?

---

### Post by housam on 2007-01-25
Did you complete the install w/o problems? (by the way , which version of ubuntu ?).
did you get the grub menu ? if yes, you may need to reinstall grub or use the super grub disk to fix it.

---

### Post by Kobalt on 2007-01-25
I also have a HP laptop and I had to use the noapic option to boot as well... Do as crispingatiesa  described and it should work.

---

### Post by razz6 on 2007-01-26
OK, here we go.  There is no way to disable apic in my BIOS, I have American Megatrends  3.10 11/12/2004. the f2 and f6 keys did not work but it had  an edit (e). I added "noapic" ( without hyphens) when i tabed to check it I got error 11 unreconised    drive sting, I added acpi=off and got error 1 filename must be absolute (missed word) or blocklist. If i hit enter after the changes it would show it as edited but would not let me save the changes. I tried to put both changes in and repeated the process in every possibable combination i could think of.
 one other thing, the "root=/dev/hd" instead of hd, mine has sda.3 could this mean something?  I've been trying to download Super Grub but have been unable  to so as the link to the page had been dead, will try again.  Thanks all for your help..I've tried Linux before and quit but there will be no Vista in my life this time..

---

### Post by JamieC on 2007-01-26
"sd" instead of "hd" indicates SATA drives. If you got the errors you described, my guess is you added it incorrectly. Follow the following instructions:-

Power on your computer, press the ESC key repeatedly to show the grub menu if it does not do so automatically.

Then, press 'e' to edit the first option. Scroll to the kernel line and press 'e' once again.

Find (assuming your drive is sda3 as you mentioned):
```

root=/dev/sda3

```

Replace With:
```

root=/dev/sda3 noapic

```

Hit return and then press 'b'. This should boot the choice you just edited. What is the result of this?

---

### Post by razz6 on 2007-01-26
I had done that before and repeated it exactly as you instructed, with the same results, go's to starting up, and a flashing cursor. the same results as before, when i went back to reedit it had not saved the changes. when i try to use the save feature on the grub, it won't work. It's loading on my 5year old Toshiba satalite  fine so far, knock on wood. we'll know in 15 min.

---

