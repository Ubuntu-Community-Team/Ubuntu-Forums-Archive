---
title: "Help"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by kistan on 2007-01-22
](*,) ](*,) ](*,) ](*,) 
My son installed ubuntu on his computer but cannot get past username//password.how does he get round this or alternatively how do I delete so I can reinstall

---

### Post by xyz on 2007-01-22
Thanks for providing more infos!
What flavor of Ubuntu? Install CD? Desktop/Live CD? and the likes of it.

---

### Post by steve.horsley on 2007-01-22
At the boot-up prompt, you should be offered the choice of recovery mode. Choose this.
You should be dropped into a text screen with a prompt that ends in a hash "#" character.
Then at this prompt, use this command to see what user name was chosen by the installer:
**ls /root**
Once you know the user name, use this command to change the password for that user (replace the name xyz with the username you discovered above):
**passwd xyz**
Now reboot (Ctrl-Alt-Delete or the command **reboot**) and let it boot to the normal login prompt. Use the username and password from above.

When installing, you are given the option to erase the entire disk, whihc would wipe out your problematic install anyway.

Good Luck.

---

### Post by mikewhatever on 2007-01-22
How come he does not remember the chosen username and password. How old is your son? :D
Seriously now. As xyz said, more info is required.

---

