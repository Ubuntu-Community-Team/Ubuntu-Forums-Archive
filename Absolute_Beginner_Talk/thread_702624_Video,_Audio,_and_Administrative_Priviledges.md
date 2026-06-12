---
title: "Video, Audio, and Administrative Priviledges"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by uhrohraggy on 2008-02-20
I have three problems, two of which I expect are related and the other disjoint.

1) Booting up my computer one time, I noticed that there was no sound coming from my computer. This happens from time to time due to updates, the alsa muting itself and the like. However, I checked all of my settings and everything seemed to be okay (by the way, there are three audio devices: The internal intel (HDA Intel), Soundblaster Audigy 2 [unknown], and a SigmaTel OSS mixer. I've installed the drivers through Synaptic for the Audigy 2, but even the internal ALSA is not working.

2) All video (around the same time as the audio problem) causes the program in which it is run to freeze and subsequently force quit. This includes Totem, VLC media player, Firefox...and any video format (mov, wmv, avi, mpeg, flash, etc.). I have an NVidia GeForce 6 series card and the drivers work fine. I removed the drivers and am using the internal graphics  to see if that was the problem, but still no luck. 

3) Whenever I start up my computer or come back from hibernation, I have to use my password to both get access to one of my drives and start any administrative task (i.e. Synaptic). It's as if I am not an administrator or it doesn't let me default that I am the administrator. Is there a way for my drive to auto-remount, and for the computer to recognize me as an administrator?

I'd appreciate any help or suggestions anyone might offer. Thanks a lot.

---

### Post by spiderbatdad on 2008-02-20
Generally, you are logged in as a user. The file system and synaptic are owned by root, for your protection. At least every 15 minutes you have to renew your password to access synaptic or alter the file system. You can disable your security: [http://www.tech-recipes.com/rx/2746/ubuntu_stop_sudo_commands_prompting_password](http://www.tech-recipes.com/rx/2746/ubuntu_stop_sudo_commands_prompting_password)
But the article leaves out the need to edit this line :%admin ALL=(ALL) ALL   shold be %admin ALL=NOPASSWD: ALL

There is no reason for that to not work. Just be sure that you have defined properly the user running sudo to allow it to run the cat (/bin/cat) program. For example one user that will only be allowed to run cat would look like:
(in /etc/sudoers):
some_user ALL = NOPASSWD: /bin/cat
(or allow the user to run all commands with sudo:
some_user ALL = NOPASSWD: ALL)

---

