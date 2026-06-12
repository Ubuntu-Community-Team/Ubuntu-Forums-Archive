---
title: "Installed app causing lockup @ boot - how to uninstall while in Live CD?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by mdpalow on 2007-12-15
I believe my problem is a result of some compiz manager (can't remember the name) app I installed last night. Problem is my back-up was made after installing it, so using my back-up is out.

I'm in Live CD now and would like to know how to uninstall compiz from my actual system. I'm assuming sudo aptitude remove <some app> isn't going to work 'cause I'm in Live CD and it won't actually take it out of my actual system configuration.

I wish I could remember the name of the app.. all I can remember about it was the name had both compiz and manager in it, but when I look Synaptic now, I can't even find that name anymore. It's just a simple app that brings up a couple options (cube, etc) and sets them. It can even be placed in the system tray. Bring anything to mind?

Right now, when I turn on my computer I get to the progression bar and then it locks up.

thanks for any help you can provide...

---

### Post by toddward on 2007-12-15
The best way to get into the disk is to chroot to it.

There's a guide [here]("http://ubuntuforums.org/showthread.php?t=157250")...but I pulled out the statements that you'll really need to know.

[LIST]Mount the disk / partition that contains your ubuntu installation.[/LIST]
[LIST]chroot /dev/sda1 (or whatever your hdd is)[/LIST]
[LIST]Once you've successfully chroot'ed to the drive you can issue commands such as an apt-get uninstall command (man apt-get for more information on how to do it).[/LIST]
[LIST]Once finished, umount the drive and reboot into your regular system.[/LIST]

---

### Post by mdpalow on 2007-12-15
well, that didn't do it for me, so I did a re-install.

I think it didn't work because there might have been something else I either loaded or did. Maybe Compiz wasn't the culprit.

Thanks very much for your input... At least I learned something new about chroot; that's a good tool to have in your toolbox.

---

### Post by toddward on 2007-12-16
Definitely, I've used it more than once.

---

