---
title: "Permission to modify menu.lst"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-26
Hi
I have less than 48 hours of Linux experience but quite some familiarity with Windows.
I set up my machine to dual-boot WinXP and Ubuntu 5.10 late on Monday night.
Since then I have really just looked around as to what's available and what are the differences from Windows.
However, one thing I would like to tidy up as soon as possibleis the following: 
When the boot menu comes up, I have a total of EIGHT (8) options available:
1) Ubuntu kernel 2.6.12-9-386 (normal and recovery mode)
2) Ubuntu kernel 2.6.12-10-386 (same two versions)
3) Ubuntu memtest 86+
4) Three WinXP options (of which only one works).

I have looked in the /boot/grub/menu.lst file to try to find what's happening here. The three WinXP "options" arise from me having copied much of my system disk some time ago to a partition on one of my external HDs. Even though this partition is unbootable, apparently grub decided it was.
Nevertheless, the real problem is that my menu.lst file is READ ONLY and I just can't figure out how to upgrade my permission so that I can change it and tidy up (take out the unnecessary options) the boot option list.
Can anybody point me in the right direction?

TIA
Paul

Dell 4550 Desktop
WinXP Home SP2/Ubuntu Linux
CPU P4, 2.53 GHz
1.0 GB RAM
Int HD 80 GB Partitions: Dell (FAT16), Windows (ntfs), Linux (SWAP, ext3)
Ext HD 160 GB ntfs, 3 partitions
Ext HD 250 GB ntfs, 4 partitions

---

### Post by bensexson on 2006-07-26
Have you tried sudo gedit /boot/grub/menu.lst?  If so try sudo chmod +w /boot/grub/menu.lst.

---

### Post by PaulFXH on 2006-07-26
Hi bensexson
Thanks for your reply.
Actually, I had not tried either of the suggestions you made.
But, I have now and, unfortunately, neither proved useful.

Here's what happened:
For sudo gedit/boot/grub/menu.lst the term password: came up but (as I have seen with other similar attempts) the pasword just would not type in. IOW, even though I was pressing the keys, nothing showed up in the password: box.

For sudo chmod +w/boot/grub/menu.lst the message "too few arguments" appeared. I then tried chmod---help but I'm afraid that what appeared may as well have been written in Swahili.

So, no progress so far

Paul

---

### Post by _simon_ on 2006-07-26
it will not display the password as it's typed.

When it prompts for password, just type it in and press enter... it will be accepted.

Normally you edit the menu.lst like this:

sudo gedit /boot/grub/menu.lst

Remember though that if you remove any linux kernels they are ONLY being removed from that menu, not your system. i use Synaptic to remove kernels I no longer use. Just use the search button to locate them then right click and select remove then click apply.

---

### Post by pistcivet on 2006-07-26
gksudo gedit /boot/grub/menu.lst

Type password and press enter.
Nothing will show on screen as you type - security feature. :)

---

### Post by PaulFXH on 2006-07-26
Hi
Thanks to everybody for your replies.
OK, so using sudo gedit /boot/grub/menu.lst has now worked for me (once I knew that nothing shows up in the password box) and I have finally been able to tidy up my boot menu.
Do I understand then that any text message can only be edited by using sudo gedit (or other command)?
IOW, it cannot be edited just by going into a text editor?
Thanks again
Paul

---

### Post by _simon_ on 2006-07-26
Basically any file NOT in your /home directory will need "super user access" to edit it. "sudo" stands for "super user do".

If you ever have a problem where you can't get to the desktop but need to edit a file e.g. xorg.conf then you would use nano instead of gedit e.g.

sudo nano /etc/X11/xorg.conf

You can also use nano instead of gedit from the terminal if you want.

---

### Post by stimpsonjcat on 2006-07-26
PaulFXH,
I think you should read [this]("https://help.ubuntu.com/ubuntu/desktopguide/C/index.html").
especially the part about [permissions and users]("https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html").
Oh, and welcome to ubuntu!! :)

---

### Post by PaulFXH on 2006-07-26
Thanks to Simon for the explanations and to stimpsonjcat for the documents and the welcome.
Actually, I'm amazed I haven't come across these documents before as they seem to be just what I need to get me over all of these initial newbie barriers.

I hope you will alow me to "append" two further questions that (more or less) emanate from comments/remarks in the thread so far:

1) Will the fact that I have TWO Ubuntu kernels loaded contribute to a degree of "Bloat" in my configuration? I ask this because I find Ubuntu to be VERY MUCH slower than WinXP in retrieving web pages. What takes only 1-2 seconds in Windows takes 40-50 seconds in Ubuntu (on the very same machine).

2) I had tried out Ubuntu 6.06 on LiveCD before I installed any Linux flavor but found it to be "unusably" slow. I understand this was due to some kind of bug. It is for this reason that I downloaded Ubuntu 5.10.
However, can I deduce fromn the fact that a lot of people in this group use Ubuntu 6.06 that I should go ahead and upgrade to this?

Thanks
Paul

---

