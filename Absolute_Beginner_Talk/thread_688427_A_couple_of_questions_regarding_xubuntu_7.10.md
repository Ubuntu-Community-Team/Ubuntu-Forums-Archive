---
title: "A couple of questions regarding xubuntu 7.10"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-05
A couple of questions I have regarding xubuntu 7.10 are; Does xubuntu have e-mail? Or do I need to add Thunderbird? I can't seem to find any kind of e-mail program after the install. 

Another question; When I plug in my mp3 player it recognizes it and I can open the songs but the Totem movie player will not play this kind of file. What can I do to get the Totem player to recognize the file or song?

One more question, Why does'nt xubuntu shut the computer down totally after I select shutdown? It shuts down the xubuntu but the machine continues to run and I have to push the power button.

Also will I need a firewall or any other type of protection from threats of any kind?

Alot of questions I know but so far I really like the feel of xubuntu and I've only had some minor issues so thats good. I still need to know more about installing plugins but that is something I'll do when I get the small stuff figured out.

Thanks for your time and responses so far with this endever I really have appreciated all the help I get from this forum! You all have been great and patient with me.:)

Neal

---

### Post by LowSky on 2008-02-05
Does xubuntu have e-mail? **Its called evolution..its alot like thunderbird, if you dont like it then install thunderbird, in synaptic**
Another question; When I plug in my mp3 player it recognizes it and I can open the songs but the Totem movie player will not play this kind of file. What can I do to get the Totem player to recognize the file or song?

as long as the files are not protected (like itunes files) **in terminal type ```
sudo apt-get xubuntu-restricted-extras
```**

One more question, Why does'nt xubuntu shut the computer down totally after I select shutdown? It shuts down the xubuntu but the machine continues to run and I have to push the power button.

**How old is the computer, I know some  older machines cannot auto shut off (my old Win98 comp couldnt auto shut off)**
Also will I need a firewall or any other type of protection from threats of any kind?
[B]
linux is very safe,and xubuntu it has a built in firewall, youll be fine.[/B]

---

### Post by plucky on 2008-02-05
Xubuntu uses **Thunderbird** as it email client and should be located under **Applications > Internet**.

Indy452,

Can you list your system specifications, Cpu,memory,video card etc.

---

### Post by Indy452 on 2008-02-05
> **plucky said:**
> Xubuntu uses **Thunderbird** as it email client and should be located under **Applications > Internet**.

Indy452,

Can you list your system specifications, Cpu,memory,video card etc.

Its an older "donor" computer I've doctored up a little. Its a Gateway with a 750mh p3 processor and it has 320MB ram. Seems to run real good so far, I really enjoy it but I will need e-mail and its not on the desktop so I have to find and seek you see.

Thanks I'll look when I get home from work.

Neal

---

### Post by bodhi.zazen on 2008-02-05
See this link for information re: security : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

Linux uses iptables as a firewall. With a default install the firewall is permissive to all traffic. Again, with a default install there are no servers listening for connections so a firewall is not needed (this is different from windows). If you install a server, part of the process is to learn to secure it.

You do not need antivirus or anti spy ware packages at this time.

---

### Post by plucky on 2008-02-05
Indy452,

For your power off problem, try this ```
sudo nano /etc/modules
``` add this line at the end of the file ```
apm power_off=1
```

Do you get a **BIOS** error message on boot? Something about pre 1999 bios date which causes an ACPI error. If so you need to add these values at the end of the kernel line in /boot/grub/menu.lst
```
 sudo nano /boot/grub/menu.lst
``` and add this ```
acpi=off apm=on
``` so that it looks like ```
kernel          /vmlinuz-2.6.22-14-generic root=UUID=c65f00cc-bb55-4e82-acea-922fe8e691c6 ro quiet splash acpi=off apm=on
```


Hope this helps

---

### Post by Indy452 on 2008-02-10
> **plucky said:**
> Indy452,

For your power off problem, try this ```
sudo nano /etc/modules
``` add this line at the end of the file ```
apm power_off=1
```

Do you get a **BIOS** error message on boot? Something about pre 1999 bios date which causes an ACPI error. If so you need to add these values at the end of the kernel line in /boot/grub/menu.lst
```
 sudo nano /boot/grub/menu.lst
``` and add this ```
acpi=off apm=on
``` so that it looks like ```
kernel          /vmlinuz-2.6.22-14-generic root=UUID=c65f00cc-bb55-4e82-acea-922fe8e691c6 ro quiet splash acpi=off apm=on
```


Hope this helps


Do I need to type this into a terminal or at the grub boot screen?  All of it or just the part about the BIOS error message on boot about pre1999? 

I need to get this solved soon also so I don't walk away after I think I shut down and it really does'nt completelly.

Thanks, Neal

---

### Post by plucky on 2008-02-10
> Do I need to type this into a terminal or at the grub boot screen?

Yes, open a terminal and type ```
sudo nano /etc/modules
``` this will open the file modules using the **Nano** editor and then you add the line ```
apm power_off=1
``` to the file.To save to the file type **Ctrl O** and to exit from the editor **Ctrl X**

And the do the same for the **menu.lst** file.


Good luck

---

### Post by Indy452 on 2008-02-10
> **plucky said:**
> Yes, open a terminal and type ```
sudo nano /etc/modules
``` this will open the file modules using the **Nano** editor and then you add the line ```
apm power_off=1
``` to the file.To save to the file type **Ctrl O** and to exit from the editor **Ctrl X**

And the do the same for the **menu.lst** file.


Good luck


Am I making this harder than it is,  or does it just not work on some machines?   Plucky, are these directions also for xubuntu? 

When I get into the grub menu I get sort of freaked out and I'm not sure I'm selecting the right menu or whatever.  Should the last line read quiet acpi=off apm=on?  Or should it read  sudo nano /boot/grub/menu.lst acpi=off apm=on?  I'm confused by the original code you you have in the top box then you say add this in the next box.  When do I add the second code? After I hit enter or something?    :confused:

Thanks, Neal

---

### Post by Bartender on 2008-02-10
I've seen the exact same behavior with PC's of about that vintage.  With one of them I downloaded the latest BIOS for the PC, flashed the BIOS, and shutdown started to work like you'd expect it to.  So you could try that, although flashing the BIOS is of course not without risk.
The BIOS version should show up during POST (when the PC is first starting)  Write it down, then compare at Gateway website and see if there's a newer BIOS available.

---

### Post by rkd on 2008-02-10
> When I get into the grub menu I get sort of freaked out
You use the command:```
sudo nano /boot/grub/menu.lst
```to open the Grub menu file for editing. If you don't like nano, use your favorite editor.

In the Grub menu, look for every line that starts with the word "kernel" followed by something starting with "/vmlinuz", then add ```
acpi=off apm=on
``` to the end of the line. Make sure you leave a space between "acpi" and whatever was originally at the end of the line. 

There should be at least two kernel lines to change. There would be more than two lines only if you have several versions of Ubuntu on the computer.

Save the file and exit the editor, then restart the computer and try a shutdown to see whether it works properly.

---

