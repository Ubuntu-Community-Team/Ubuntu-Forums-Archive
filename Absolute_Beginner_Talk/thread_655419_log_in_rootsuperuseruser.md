---
title: "log in root/superuser/user"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by jesse c on 2008-01-01
Very basic stupid nube question. While following various forums and misc web tutorials trying to teach myself to use linux(UBUNTU GUTSY) i keep running across warnings to not do stuff as root or superuser but as user instead. How do i know what im doing stuff as?When i bring up terminal it starts with the identity that i put in when i installed my os.I dont know if that makes me the superuser or what.Should i have made up some other user identity seperate from that of the install identity?How can i check out whats what in my system?   thanks  JESSE

---

### Post by taurus on 2008-01-01
As long as you don't include sudo/gksudo in front of a command, you are running that command as a regular user.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jesse c on 2008-01-01
thanks for quick reply,taurus. Is that both words with the slash because i think i have followed some tutorials that had me start with just sudo but i just copied and pasted into terminal so i might be wrong.Im not having any problems and theres no critical data on this new computer to mess up(yet) but i would like start some good/safe habits.  thanks  JESSE

---

### Post by taurus on 2008-01-01
Sudo is for a terminal while gksudo is for GUI.  For instance, if you want to edit something that you need root privilege, you should use gksudo with gedit graphical editor.  But if you want to use a terminal editor like nano or vi (or vim), then you would use sudo.  So basically, both sudo & gksudo accomplish the same thing, allowing you to be root.

---

### Post by LordTyrans on 2008-01-01
Hi,

I wasn't sure if what had already been said had answered your question so... 

I believe the identity that you set when you install Ubuntu is a normal user account not the "superuser or Root". If you do need to log in as the root user you would have to change a few settings. To see the different users of the system you can go to the System/Administration menu and select "Users and Groups", here you can also make it possible to log in as the "superuser" known as "root". I hope that answers your question if it has not already been answered.

---

