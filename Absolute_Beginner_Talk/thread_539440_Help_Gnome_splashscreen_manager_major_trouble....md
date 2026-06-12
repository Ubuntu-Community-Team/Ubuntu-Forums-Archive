---
title: "Help: Gnome splashscreen manager major trouble..."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by shrynakesavan on 2007-08-31
ok my mistake , i installed gnome splashscreen manager from my synaptic package manager ... but later i found out it was not needed so i went and removed gnome splashscreen manager with synaptic... i without pausing and thinking removed it completely along with configuration files ... my system was fine untill i restarted it... not after ubuntu boots. and opens in the terminal mode... asks login.. once i login it shows the terminal... but there is no acessing ubunu desktop... but all my "sudo" commands are working, for example "sudo apt-get update" works juss like in terminal.,.. actally it is the terminal... how do i go back to the desktiop.... do i install gnome splashscreen manager again with the command "sudo apt-get install gnome-splashscreen-manager"and let it download and install it... along with the important configuration files... 
.... or dose the display thing has nothing to do with splashscreen manager's configuaration files.... please help i am frightened beyond belief.... for whatever sale please help..!!!

---

### Post by jombeewoof on 2007-08-31
what happens when you startx

---

### Post by Seisen on 2007-08-31
Since your internet connection works you can just apt-get the gnome-splashscreen-manager package and then reboot and it should work or you can try startx which jombeewoof suggested.

---

### Post by shrynakesavan on 2007-08-31
ubuntu boots asks login in the black screen ... like MS Dospromt.... once i login it shows the terminal... which also looks like dos

---

### Post by shrynakesavan on 2007-08-31
what is startx.... how do i type it... is it... " sudo apt-get startx " or juss " startx "

---

### Post by jombeewoof on 2007-08-31
just startx

it will either start xwindow or crash. 
if it crashes write down what it says

---

### Post by shrynakesavan on 2007-08-31
ok i will go home .. and do that and get back to u guys ...

---

### Post by shrynakesavan on 2007-08-31
ok... i ran the apt-get gnome-splashscreen-manager command ., to my absolute surprise.;; it showed that "it and its" configuration files r already installed and updated.... soi had no other choice but to run " startx ".. and it started the xwindow and now i can access my desktop... . now all i wanna know... is why did it happen... and everytime i switch on my comp... will i have to go to the terminal and run " startx " to access  my desktop.... i mean each time... how do i prevent this from happening again...
         Oh and by the way ... now there is no shutdown option.. the power button juss gives the following options,  logout, lock screen, switch user, hibernate and suspend, where as restart and shutdown are missing.... how am i to rectify this plase help... all i can do is logout,.. which takes me back to the terminal... where i give exit... and it goes bact to asking my login: username and paassword... so there all i can do is hit my laptop's main power button.... please help...i am freakin out

---

### Post by shrynakesavan on 2007-09-01
guys please help...somebody please help... since i realized i was logging in through the terminal... to cross check ... i ran " startx " to access the desktop then in the top panel i went to system > Administration and realised the " Login Window" option which was there before is missing... what should i do..

---

