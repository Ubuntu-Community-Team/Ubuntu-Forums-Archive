---
title: "Password woes..."
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by ranman on 2006-02-24
I did quite possibly the stupidest thing I have ever done... (well thats not true but... it seemed like a good idea at the time) I tried putting a character not represented on the keyboard like null (ALT+255) in my password and despite everything i have tried I still can't get onto my machine... is there something I should do? is there a way I can recover it? or do I have to re-install?

---

### Post by Xian on 2006-02-24
To reset your password reboot into Ubuntu in the recovery mode, which will drop you to a shell with admin priviledges. Then issue the proper command:

# passwd <username>

---

### Post by codejunkie on 2006-02-24
[QUOTE=ranman]I did quite possibly the stupidest thing I have ever done... (well thats not true but... it seemed like a good idea at the time) I tried putting a character not represented on the keyboard like null (ALT+255) in my password and despite everything i have tried I still can't get onto my machine... is there something I should do? is there a way I can recover it? or do I have to re-install?[/QUOTE]
at the grub menu choose recovery mode option this will give you temporary root access, when you reach the terminal enter ```
passwd yourusername
```this will let you change your password when your done enter ```
shutdown -r now
```to reboot and login as you normally would.

---

### Post by ranman on 2006-02-24
How do i get into recovery mode though... I messed up my boot loader a long long time ago...

nvm I fixed grub on my own thanks for the help everyone! tyvm sorry I am so dumb!

---

### Post by Xian on 2006-02-24
[QUOTE=ranman]How do i get into recovery mode though... I messed up my boot loader a long long time ago...[/QUOTE]

At the Grub login screen edit the kernel line for Ubuntu and append the word 'single' at the end. Afterwards, please fix things as they occur instead of waiting for further disasters. And if you are unsure about system changes you are contemplating (like odd password keystrokes) it is best to present them in the forum and get some feedback.

---

### Post by patrick295767 on 2006-02-24
[QUOTE=ranman]I did quite possibly the stupidest thing I have ever done... (well thats not true but... it seemed like a good idea at the time) I tried putting a character not represented on the keyboard like null (ALT+255) in my password and despite everything i have tried I still can't get onto my machine... is there something I should do? is there a way I can recover it? or do I have to re-install?[/QUOTE]
  
Also ... 

How to change your root password (if you forgot it) ?
------------------------------------------------
U can boot ur pc with knoppix or liveCD,
mounting ur partition, (mount ...)

then go into the shadow file of the /etc/
and copying the encrypted password of an user (password known)
or resetting the password of root ...(i guess 0:0 should work, ...I have to check)

Then, u reboot normally ur pc, and once root !
type to redefine ur root password:
passwd

Good luck, please let me know about ur results !!!
('cos I forgot a bit)

Patrick

---

