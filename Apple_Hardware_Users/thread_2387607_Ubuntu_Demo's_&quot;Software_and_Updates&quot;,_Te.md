---
title: "Ubuntu Demo's &quot;Software and Updates&quot;, Terminal, and Install not working"
date: 2018-03-21
forum: Apple Hardware Users
---

### Post by mkulnar7 on 2018-03-21
I accidentally left my computer on while on Ubuntu 16.04 (which is on a thumb drive), thru which it was not installed. I came and after having to restart another demo of Ubuntu, it asked me to log in. So I restarted to see if it would work. It logged me in automatically but Terminal won't open when I click the icon. Neither will Software & Updates. I just want to use the demo again so I can install up to wifi again. If there's a way to just use wifi without terminal I'd that would be great too.

---

### Post by captionopen2 on 2018-03-21
Do you have the wireless drivers installed?
Can you open network-manager and configure your wifi through their? Preferences > Network Connections
Do you have a wired connection when booted from thumb drive? or are you connected from the original Operating system?
I don't know if you can run software updates from a liveusb, but I could be wrong.

You're also saying that the usb just has the Ubuntu 16.04 iso image written to it, it's not actually installed onto the thumb drive, correct?

---

### Post by mkulnar7 on 2018-03-21
No it's not installed on the thumb drive (dont know how to do that using only thumb drive and Mac OS).

Thats what I need I think: wireless drivers.

I can add wifi through "Network" but I can't find my Device (eth01). All I can get is the HWaddr and what I think is the bssid.

Otherwise, wifi doesn't show up at all in Network.

EDIT: I don't think I can run updates either. Honestly, I just want to have wifi again.

---

### Post by captionopen2 on 2018-03-21
Alright, and I'm sure not being able to open terminal isn't very helpful either...

Can you get any of your wireless info? Here's a link to the sticky page from the wireless forum > [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

If you can't open terminal, maybe you can be able to save this file - as mentioned in link above - [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) on your computer and execute it in ubuntu.

---

### Post by ajgreeny on 2018-03-21
I'm afraid I am not totally clear about your current situation, but I assume you are saying the thumb drive has a live Ubuntu OS on it, which is normally not writeable when you're running it, so in theory it should be exactly the same now as the last time you booted to it.  Is this live OS, if that's what it really is, running in persistent mode where changes you make are retained?

If you can't open a terminal from the live system, try Ctrl+Alt+F1 to get to a tty, ie, a command-line only screen, and from there login with username **ubuntu**, (if it asks for one, and password leave blank; just hit Enter) though a live system should not need either.
From there use command **lspci**, or **lsusb** if the wifi is a USB device and report back here the output.

---

### Post by mkulnar7 on 2018-03-22
I dont think it's persistent because I don't see any of the apps I installed or any other files, though what I was using was Supposed to be persistent based on some instructions I followed online.

Ctrl+Alt+F1 doesn't pull anything up.

---

### Post by mkulnar7 on 2018-03-22
Yeah i cant open terminal at all :( ... And I can't use wifi. So should I log in thru my Apple HD and download it?

---

### Post by ajgreeny on 2018-03-22
> **mkulnar7 said:**
> Yeah i cant open terminal at all :( ... And I can't use wifi. So should I log in thru my Apple HD and download it?

Download what?

---

### Post by mkulnar7 on 2018-03-23
Sorry...  that was meant for captionopen2. Since ctrl+alt+1 doesn't load anything is there another shortcut for MacBook keyboards?

---

### Post by wildmanne39 on 2018-03-23
*Thread moved to **Apple Hardware Users for better support**.*

---

### Post by mkulnar7 on 2018-03-23
I figured out that fn+ctrl+alt+F1 was the correct shortcut. I entered Ubuntu as a username and left the password blank. It then said:
... Zlib decompression failed, data probably corrupt... Amongst other things. 

Here is a screenshot:
[IMG]http://roadtrips101.tumblr.com/image/172190755351[/IMG]

---

