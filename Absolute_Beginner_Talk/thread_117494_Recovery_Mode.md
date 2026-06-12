---
title: "Recovery Mode?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by nu2this on 2006-01-15
1st I'm dualbooting my question tho involves something I see every time I start up the PC. On what I think(correct me if I wrong) is the grub screen is Ubuntu the kernal number( 2.16 or something) then below that is Ubuntu Recovery Mode then Windows. 
My question is what is the recovery mode? How would I need it? what would it do once activated?

---

### Post by 23meg on 2006-01-15
It logs you in as root and lets you edit configuration files to recover from errors that prevent you from running Ubuntu normally.

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=nu2this]1st I'm dualbooting my question tho involves something I see every time I start up the PC. On what I think(correct me if I wrong) is the grub screen is Ubuntu the kernal number( 2.16 or something) then below that is Ubuntu Recovery Mode then Windows. 
My question is what is the recovery mode? How would I need it? what would it do once activated?[/QUOTE]
It is a single user mode where you log in to reset forgotten passwords, etc.  Somewhat like recovery mode in Windows.

---

### Post by nu2this on 2006-01-15
[QUOTE=cwaldbieser]It is a single user mode where you log in to reset forgotten passwords, etc.  Somewhat like recovery mode in Windows.[/QUOTE]

So as such then would it  put my Ubuntu back to like it was when I first installed it or have a restore point?
If it is back to the original that 'd mean I'd not need to re-install from the disk just the recovery mode. Then re-install all the apps I had later. Do I have that right?

---

### Post by 23meg on 2006-01-15
No, it simply logs you in as root in single user mode to the current state of your installation so that you can fix problems with your installation that you may not be able to fix in normal operation mode.

---

### Post by nu2this on 2006-01-15
So all will be the same until I change it & only those items I change will be.
An example: if i go in to change say Mplayer then the Home folder would be untouched, only Mplayer would be affected & those apps that use it.

---

### Post by 23meg on 2006-01-15
[QUOTE=nu2this]So all will be the same until I change it & only those items I change will be.[/QUOTE]Right; think of it as a root terminal running in single user mode without a GUI.

---

