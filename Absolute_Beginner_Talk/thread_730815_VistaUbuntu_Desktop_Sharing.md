---
title: "Vista/Ubuntu Desktop Sharing"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-03-21
Is there a known way currently to enable desktop sharing from Vista to Ubuntu? My search has proven mostly fruitless, RealVNC seemed like it wanted to work, but then didn't ;]
Perhaps it was because of ports? 
On the Vista machine, I'd only unblocked the windows firewall, and not the router, and hadn't done anything but enable desktop sharing on the Ubuntu box, I assumed this automatically opened the appropriate ports.. 
Do I need to open certain ports on the router for it to work?

---

### Post by Hospadar on 2008-03-21
do you want remote desktop, or [desktop sharing]("https://help.ubuntu.com/community/SynergyHowto")?  If you are just looking for remote control the best solution is ssh on the linux machine, puTTY+Xming on the vista box.  For synergy you'll probably need a monitor for each machine (I believe, but maybe not)

---

### Post by torgrot on 2008-03-21
First, you will need to install VNC on the Vista computer.  Ubuntu calls it desktop sharing, but it is in reality VNC.  If you want to get the Ubuntu desktop on Vista, you need to click on System -> preferences -> Remote Desktop Preferences and select allow others to see your desktop.  Now on the Vista machine start VNC and enter the name of the ubuntu computer.  You may have to enter a password.  
If you want to get to the Vista Desktop from Ubuntu, you need to start the VNC server on the Vista box.  You can run it as a service to allow access at any time, even when not logged in.  On the Ubuntu box you will run Application -> Internet -> Terminal Server Client.  Enter the name of the Vista box and possibly a password and you should have your Vista desktop.  

torgrot

---

