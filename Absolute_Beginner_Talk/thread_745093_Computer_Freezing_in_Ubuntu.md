---
title: "Computer Freezing in Ubuntu"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Clodd on 2008-04-04
Hello, I'm pretty new to Linux and I've been having some Problems with getting Ubuntu (gutsy) to work on my new PC.

My main problem is that my whole computer will sometimes freeze up for no real reason, usually when I am not directly using it, but playing music in Amarok or downloading something. My first thoughts are that this could be a driver problem because I looked in the hardware information and when I clicked on the processor there doesnt seem to be any information associated with it, but I'm no expert.

My first minor problem however is that after turning my computer off after a freeze I am now stuck in the terminal instead of going to the login screen, with a 

"Kinit: trying to resume from /dev/disk/by-uuid/a7a48c92-9d4f-4981-b958-280d1868e174

kinit: No resume image, doing normal boot..."

attempting to launch anything in this terminal will result in a "symbol lookup error: /usr/lib/libXext.so.6 undefined symbol: _XlockMutex_fn

So my first question is how do I get back to the login screen from here. I'm stumped to be honest.

Secondly if anybody could help me with my issue with Ubuntu freezing, I would much appreciate it.

Thanks.

---

### Post by stevesheldon on 2008-04-04
You aren't using an Nvidia vidao card by any chance are you? As there has been issues with 64bit and Nvidia drivers from time to time.
Do you have desktop effects enabled? If so, try running the machine with them turned off and see if you get the same issues.
Regards
Steve

---

### Post by Clodd on 2008-04-04
Ah thanks for the reply, yes I am using a geforce 8800gtx at the moment, I'll try it without desktop effects once I get going again and hope for no more freezes :)

Cheers.

---

### Post by Clodd on 2008-04-04
Right well it froze again, I did a memtest and I'm gettin' some 700,000 errors, fairly ridiculous if you ask me since I only bought the computer a week ago. Does this memtest refer to the ram or hard drive or graphics card? I need to know what I'm going to have to replace since this definately seems like a hardware issue.

*sigh*

Can anyone give me any advice?

---

### Post by spiderbatdad on 2008-04-04
could you run ```
dmesg
``` in the terminal. Copy and paste it into your gedit text editor then right click the file and select create an archive. Upload that archive into your next post with the manage attachments option you see under Additional Options when you scroll down a little below the reply window.

---

### Post by Clodd on 2008-04-04
here we go :)

---

### Post by spiderbatdad on 2008-04-04
These lines can be problematic:
```
26.788382] EXT3-fs: INFO: recovery required on readonly filesystem.
[   26.788383] EXT3-fs: write access will be enabled during recovery.
```

If you edit your /boot/grub/menu.lst with the command```
gksu gedit /boot/grub/menu.lst
```

Then scroll way down to lines like this :```
## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 lapic quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 lapic quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2fba1ac8-918c-49d7-b41d-102ca84fda26 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

From the entries on the lines that begin with "kernel" remove the "ro"  You can see in my kernel line it says "lapic quiet splash" yours says "ro quiet splash" I didn't see any acpi problems in you dmesg, so I don't belive you need to add "lapic" just delete "ro" and save the file. Then Reboot...Then open the terminal again and run: ```
sudo dpkg-reconfigure xserver-xorg
```answer the questions by readin the dialogue carefully. Use arrow keys to select "ok" or scroll any options and enter to enter selections.  After That is done, Reboot once more...

If you are dual booting, do not hibernate windows prior to booting ubuntu...always shut down windows cleanly first.

---

### Post by Clodd on 2008-04-04
Thankyou very much for the help, I followed the instructions you provided, would you be able to explain what I fixed by doing this?

---

### Post by spiderbatdad on 2008-04-04
I can try....but I am not an expert.
A combination of factors: Most likely some elements involving acpi configuration needed overwriting due to your bios settings...some things can be fixed in your bios...like cpu performance. Your dmesg was a little truncated, I believe, but what I saw indicated the boot process wanted to write (some frimware maybe, or config files...but EXT3 FS was read only), anyway...the clue was in the dmesg, as we saw. I have learned through a little practice that "ro" in the kernel line was read only.
Finally, I suspected your xorg.conf was incomplete due to this problem. So once you fixed the boot process, you reconfigured xorg. You did great. Welcome to the forums.

---

### Post by Clodd on 2008-04-05
*smiles*

Thanks once again, you really saved the day there =)

---

### Post by spiderbatdad on 2008-04-05
Now this is done and xorg.conf seems to be configured right...put "ro" back in the  kernel line to protect your file-system. Run ```
sudo update-initramfs -u
``` And you should be all set.

---

### Post by wthoang on 2008-04-26
i'll just say that im not completely sure whether this is fixed or not..it happens all the time...but sometimes my session may go for ages...thnx to clodd for bringing me here..the questions had me a little...i wasnt sure with completely wat i was doing...but i can just hope for now...and in regards to the last bit of code...should i do that straight up..or should i wait to see wat happens if it freezes or not..??

---

