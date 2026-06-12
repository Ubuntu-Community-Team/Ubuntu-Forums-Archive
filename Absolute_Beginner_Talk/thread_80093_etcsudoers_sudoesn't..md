---
title: "/etc/sudoers sudoesn't."
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by deiniol on 2005-10-21
For some reason, when I tried to run synaptic or the update manager nothing would happen. Nor could I open a root terminal window. So I tried to check /etc/sudoers with visudo. However, I get an error message saying ">>> sudoers file: syntax error, line 24 <<<" and visudo won't open. So I can run sudo on anything :( Please let me know how I can fix this!

---

### Post by Kyral on 2005-10-21
Try rebooting and selecting Recovery Mode.

This SHOULD put you in Root. Then just find the line and fix the error :D

---

### Post by deiniol on 2005-10-21
[QUOTE=Kyral]Try rebooting and selecting Recovery Mode.

This SHOULD put you in Root. Then just find the line and fix the error :D[/QUOTE]
I'm going to embarrass myself now. How do I reboot into Recovery Mode? :oops:

---

### Post by Jussi Kukkonen on 2005-10-21
IIRC, if you don't normally get the GRUB menu on startup, you need to press ESC when GRUB starts to see it.

---

### Post by Kyral on 2005-10-21
Yah, get to the GRUB Menu (Hit Esc when it says "Press ESC for Menu" ) and select the option that says Recovery Mode (should be second on the list)

---

### Post by lurongai on 2005-11-01
I broke my sudo too, by editing my /etc/sudoers file! The problem is that at any time I use sudo, I have this "sudoers file: parse error", and so, I can't administrate anything. If only I had my root enabled... but how do I do it without sudo?
Maybe that is what you explain above, but I don't get it...
Anybody? Thanks for your future help.

---

### Post by danron on 2005-11-01
If you reboot in recovery mode you'll be automatically logged in as root. So then there's no need to sudo because sudo does just that, log you in as root temporarily while issuing a command. When you are logged in as root you just open /etc/sudoers, fix the problem and save it. It should work!

---

### Post by lurongai on 2005-11-01
Sorry, I was too hurry to ask help. I tried what you just say, but my problem was that I had to enter a password for root in recovery mode. But I do not have it (suppose because it is not activate, and password of main user does not work).
I used the idea explained [here]("http://www.ubuntuforums.org/showthread.php?t=14050&highlight=chroot+sudoers") with Live CD.

- create an /ubuntu directory
- mounting my /dev/hda1 on it
- using sudo <my-text-editor> /ubuntu/etc/sudoers to correct my parse error.

Thanks anyway.

---

