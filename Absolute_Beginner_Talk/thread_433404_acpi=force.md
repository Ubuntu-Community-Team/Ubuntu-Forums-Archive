---
title: "acpi=force"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by pgrayf81 on 2007-05-04
Last night, I installed Ubunutu 7.04 alternate CD on my laptop with no problems. But, when I try to boot Ubuntu it comes up with a screen that says "acpi=force is required to activate acpi"', then the ubuntu logo comes up and has a loading bar and when that finishes my screen goes blank every time. Since I have never used Linux before, can someone help?

---

### Post by teddybairs1 on 2007-05-04
Have you tried running the live installer? A livecd is a good idea to check for hardware compatibility. Where did you get the alternate install from? Is it a recent release image or a beta image? What are your system specs?

---

### Post by ajmorris on 2007-05-04
> **pgrayf81 said:**
> Last night, I installed Ubunutu 7.04 alternate CD on my laptop with no problems. But, when I try to boot Ubuntu it comes up with a screen that says "acpi=force is required to activate acpi"', then the ubuntu logo comes up and has a loading bar and when that finishes my screen goes blank every time. Since I have never used Linux before, can someone help?

edit your /boot/grub/menu.lst (or /boot/grub/grub.cfg for Grub2)

Find this entry (your kernel and hard disk/partition specifications might be different and you may not have a UUID entry) and add the part in **bold** to yours.

"title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3015a7a1-6e5d-42d6-934d-193459bed89b **acpi=force**
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault"

---

### Post by Linux_oid on 2007-05-05
On my box I have this message

<some digits> BIOS age (1999) fails cutoff (2000) acpi=force is required to anable ACPI.

The box is working anyway.

---

### Post by jimrz on 2007-05-05
> **ajmorris said:**
> edit your /boot/grub/menu.lst (or /boot/grub/grub.cfg for Grub2)

Find this entry (your kernel and hard disk/partition specifications might be different and you may not have a UUID entry) and add the part in **bold** to yours.

"title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3015a7a1-6e5d-42d6-934d-193459bed89b **acpi=force**
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault"

if acpi=force causes issues with your pcmia cards (wifi, nic or whatever), as it does on my old laptop, use:
```
acpi=force pci=noacpi
```
and the problem goes away

---

### Post by bruban on 2007-05-09
I have the same problem on an P4 PC.

Under Ubuntu 6.10 on this pc, acpi=force worked OK.

After upgrade to Ubuntu 7.04, acpi=force ceased to work. I've also had no luck using pci=noacpi as well.

The only difference to the pc was that I disabled the onboard network card and installed a D-Link DGE-530T Gigabit PCI network card.

---

### Post by bruban on 2007-05-28
Upgrading to kernel 2.6.20-16-generic has not fixed the problem.

I've tried omitting the acpi and pci options, adding acpi=force and also adding pci=noacpi.

Does anyone have any other ideas?

Bruce

P.S.

Relevent grub config line below:

kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/vg--system-lv--ubuntu ro quiet splash acpi=force pci=noacpi

---

### Post by Ned490 on 2007-10-28
For the benefit of other newbies, ACPI is what enables your box to power down on its own after a *shutdown -h* command.

I have an elderly 500MHz Celeron HP that I intend to use as a headless server.  Don't want to tie up a screen and keyboard; I will control it entirely from a remote shell.

The remote shell is disconnected before the end of the shutdown process so you can't see the messages that indicate that it's safe to turn off the power.

I knew that the hardware was capable of shutting down under OS command because Win 98 could do it.  Ubuntu 7.10 Server didn't.  Adding *acpi=force* as instructed above fixed it.  I am grateful the information was here.

Kind of OT, but you might be wondering about a headless machine:  You must attach a screen and keyboard to do the initial installation, which should include *openssh server*.  After the initial install, remove the screen and keyboard.  From a Windows machine, connect to the Linux box via PuTTY (free and good).   You'll probably also want vsftp and/or Samba, but that's another topic.

Ned

---

### Post by DrJohn999 on 2007-11-25
This weekend I loaded Gutsy desktop onto an old Dell Optiplex R450 (Pentium-II 450 MHz, 384 MB, 2 x 13.6 GB drives) that I'm intending to use primarily as a thin client in a mixed LAN with a terminal server.

The install went very smoothly, and this old faithful now runs as a terminal server client with no problems, as well as handling Thunderbird and Firefox pretty well (a little sluggish but acceptable).

I ran into the ACPI problem: the system would not power itself down. The BIOS is the last one Dell published for this system. 

I added "acpi=force" to the kernel line in /boot/grub/menu.lst and now the system shuts down w/o a problem.

However, the error message "... BIOS age (1999) fails cutoff (2000) acpi=force is required to anable ACPI." persists on boot.

Any way to get rid of the message?

Thanks,

Dr John

---

### Post by ronniemiller on 2007-11-26
> **DrJohn999 said:**
> However, the error message "... BIOS age (1999) fails cutoff (2000) acpi=force is required to anable ACPI." persists on boot.

Any way to get rid of the message?

I am having the same issue. I installed 7.10 on an old 700Mhz AMD system, added acpi=force to the boot loader,  which fixed the shutdown issue. However, I am still getting the same message on startup.

"... BIOS age (1997) fails cutoff (2000) acpi=force is required to enable ACPI."

Its not a huge deal, but getting rid of it would be nice :)


Anyone have an idea to fix this?

Thanks,
Ron

---

### Post by alienexplorers on 2007-11-26
I just edited my menu.lst file and inserted in any open space in the list.  It has worked fine on my comp.
Example:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

#Enable ACPI
acpi=force

# Pretty colours
color cyan/blue white/blue


---

### Post by ronniemiller on 2007-11-26
Hi alienexplorers,

I tried what you suggested, but I am getting the same message. It didn't cause anything to work differently, just didn't take the message away.

---

### Post by alienexplorers on 2007-11-26
I still get the message, but now my computer powers off when asked and before adding this line it did not.

---

### Post by Tea, anyone? on 2007-12-12
My computer powers off now I've added acpi=force pci=noacpi, but bootup is extremely slow and the desktop unresponsive.  Further investigation beckons...  what was I planning on doing this evening???

---

### Post by Tea, anyone? on 2007-12-12
Still no good.  I've tried acpi=force both with and without pci=noacpi in both the kernel line and in open space, all with the same result.  After the ubuntu splashscreen, descriptive text comes up:

Reading files needed to boot...
(Re)generating splash steps for: sed: can't read /etc/inittab: no such file or directory
Preparing restricted drivers....
Setting the system clock.
Starting basic networking....
Starting kernel event manager
Loading hardware drivers...

and it holds on loading the hardware drivers for some minutes before proceeding through some more stuff.  When the desktop loads, everything is slow and sometimes there is a problem with the gnome panel.

My kernel bit looks like:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=86e07f63-6bd9-4364-a64b-ae7e08f575b4 ro quiet splash acpi=force
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

Computer is a Toshiba Satellite Pro 4300

Any ideas?

I'm looking at this too:
[http://ubuntuforums.org/showthread.php?t=623237&highlight=acpi%3Dforce](http://ubuntuforums.org/showthread.php?t=623237&highlight=acpi%3Dforce)

---

### Post by dthuk on 2007-12-31
I had exactly the same experience using acpi=force. Under 7.04 it all worked fine (but like others I could never get rid of the message telling me to use acpi=force but that's just cosmetic). However, since using 7.10 my computer runs terribly slowly, so I have had to do without acpi=force. Clearly something has changed between the two versions but what?

I also am running an elderly Toshiba Satellite Pro although it is the slightly different 4270. Any clues in that ?

I'll be really grateful if anyone has any ideas.

---

### Post by Tea, anyone? on 2008-01-07
I'm just putting up without acpi at the moment, I had tried to get apm working instead, figuring that this might work better on an older computer, but no success there either.  From what you say, dthuk, perhaps I'll try 7.04

---

### Post by xmastree on 2008-03-24
Having just installed 7.10 on my Toshiba 4300, I'm now faced with the same issue.

Did you fix yours?

---

### Post by raydar on 2008-03-24
I just tried the fix of "acpi=force" in the kernel line of menu.lst on (this perhaps being a contest for the oldest hardware :) ) an old Compaq PII machine, running straight Ubuntu Gutsy.  

On shutdown, it used to just sit there with the Ubuntu logo after the progress bar emptied to the right, but now it turns itself off like it's supposed to.  

Always nice when the fix works on the first try; I wish I could help those of you this didn't work for. :\

---

### Post by P86 on 2008-03-30
> **xmastree said:**
> Having just installed 7.10 on my Toshiba 4300, I'm now faced with the same issue.

Wow, I can't believe it, but I also just installed 7.10 on a Toshiba 4300. Do we have any reason to believe 8.04 will solve the problem?

---

### Post by P86 on 2008-04-04
I just installed the 8.04 beta using WUBI and I am glad to say acpi=force now works! The laptop boots normally and the fans kick on when it gets hot. I don't think CPU scaling is activated, but I found another post that may solve that issue. I am very happy with 8.04 and am glad I didn't have to go back to 7.04.

---

### Post by giancast on 2008-05-18
I just did the acpi=force on the kernel line of the file boot/grub/menu.lst and it is working again.
One thing to remember for everyone having issues after an upgrade. When you upgrade ubuntu adds a new line to the menu.lst and this line will not have the acpi=force anymore, so it has to be entered by hand. 

I started with 6.04 and upgraded to 8.04. My menu.lst had separate entries for every upgrade.

Just for information.

Enjoy.

---

