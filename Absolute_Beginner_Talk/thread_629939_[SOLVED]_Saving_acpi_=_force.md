---
title: "[SOLVED] Saving acpi = force"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by MelissaEpiphany on 2007-12-02
I've been having trouble powering down my computer on Gusty. 

'acpi = force' works great when I add it to boot kernel at start up, but I can't seem to save the command permanently.

Someone elsewhere told me to 'sudo gedit/boot/grub/menu.lst' in Terminal (along with subsequent commands to follow once in to save acpi =force parameter,)
but when I do, I only get 'command not found.' 

Also get same response when I try 'sudo gedit etc/module' alternatively. (No I'm not adding the quotation marks.)

Checked usr/bin and $Echo Path to see if my sudo command works. All seems fine and I can use sudo to download well enough in terminal.

Can anyone tell me how I can make acpi = force permament in my boot kernel? And/or why I can't seem to get the boot grub menu?

Cheers, Mel.

---

### Post by GSF1200S on 2007-12-02
> **MelissaEpiphany said:**
> I've been having trouble powering down my computer on Gusty. 

'acpi = force' works great when I add it to boot kernel at start up, but I can't seem to save the command permanently.

Someone elsewhere told me to 'sudo gedit/boot/grub/menu.lst' in Terminal (along with subsequent commands to follow once in to save acpi =force parameter,)
but when I do, I only get 'command not found.' 

Also get same response when I try 'sudo gedit etc/module' alternatively. (No I'm not adding the quotation marks.)

Checked usr/bin and $Echo Path to see if my sudo command works. All seems fine and I can use sudo to download well enough in terminal.

Can anyone tell me how I can make acpi = force permament in my boot kernel? And/or why I can't seem to get the boot grub menu?

Cheers, Mel.

Thats:

sudo gedit /boot/grub/menu.lst

im sure you just made a typo, though.

How about Nautilus as root using:

gksudo nautilus

and manually navigating to that file, modify, and save and exit,

See if that works...

---

### Post by MelissaEpiphany on 2007-12-03
Thanks,

I wasn't typing the command in correctly. kept missing the gap,  (doi, what an idiot.) My computer now shuts down. 

It took me a few tries though, and experimenting with different combinations. I found it near impossible to get the command to save, even after grub update, and every time I shut down and then powered up again I had to do the whole string of commands again for some reason. Finally I got it to stick though.

apm power=off=1 was already in my /etc/modules and so finally acpi=force in boot kernel and then in grub menu list, worked best for me. 

Thank you once again :) I was ready to chuck Gutsy completely and install Feisty.
Only a couple more bugs left now and my computer is perfect.

Cheers Mel

---

### Post by philinux on 2007-12-03
Just remember

Success is never final, failure is never fatal, its having the courage to carry on that counts.

In other words if you had to set up a windoze pc from scratch it would just the same if not worse learning curve.

Also all this free help is here. :lolflag:

---

### Post by MelissaEpiphany on 2007-12-03
... and even though it can be frustrating at times, it's heaps of addictive fun - fuddling around with Linux. I won't be going back to Windows. Love this OS.

---

