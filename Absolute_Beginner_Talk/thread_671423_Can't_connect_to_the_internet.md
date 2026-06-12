---
title: "Can't connect to the internet"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Trasher on 2008-01-18
I get the message that i am connected to the network but when i try to browse the web i get "server not found'. I have the name and password from the isp. In windows i just created a broadband connection, entered the name and password and i was good to go.:confused:

---

### Post by Amstell on 2008-01-18
are you refering to a dial up connection?

---

### Post by Trasher on 2008-01-18
I don't have any phone number for that. All i usually did was to enter the name and password when creating a new connection.

---

### Post by Trasher on 2008-01-18
To create a new connection i just went in "network connections" selected create new connection > connect to the internet > set up my connection manually>connect using a broadband connection that requires an username and password>isp name>username and password>finish

---

### Post by kvizz on 2008-01-18
i guess it's either ppoe or pptp connection
if it's ppoe then you need to run sudo pppoeconf
it it's pptp then you need to grab [network-manager-pptp]("http://packages.ubuntu.com/gutsy/net/network-manager-pptp") (gui for creating pptp connections) and [pptp-linux]("http://packages.ubuntu.com/gutsy/net/pptp-linux") from ubuntu repos.

---

### Post by Trasher on 2008-01-18
pppoe. i went in the terminal but after i type sudo pppoeconf i have to enter the pass. first. but when i press an key nothing happens. i can type it in an text editor but not in the terminal. I mean after i type sudo pppoeconf

---

### Post by kvizz on 2008-01-18
when you type your password after sudo letters just doesn't show up to you. just type your password and hit enter.

---

### Post by Captainm on 2008-01-18
Beaten to it.

---

### Post by Trasher on 2008-01-18
"sorry, try again" and the cursor does not move:confused: sry i didt explain it right the first time :/

---

### Post by lswest on 2008-01-18
means you misspelled your password, or maybe the caps was on? the cursor won't blink, just re-type the pass and hope for the best^^

---

### Post by Trasher on 2008-01-18
didn't misspell, and when i hold down any key the cursor just stops blinking until i stop pressing the key

---

### Post by Trasher on 2008-01-18
suddently it started working again but ty anyway -.-'. edit: nvm still not working. i just exit the pppoeconf and it started working but when i typed it back in it stopped again

---

### Post by Trasher on 2008-01-18
Just leave a message... I gtg for now.

---

### Post by Trasher on 2008-01-19
Hehe it was my bad... I didn't type PPPoEconf just pppoe thats why it didnt activate normally.

---

