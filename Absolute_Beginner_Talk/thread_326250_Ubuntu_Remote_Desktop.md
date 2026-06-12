---
title: "Ubuntu Remote Desktop"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by tenwesta on 2006-12-27
Need some help with ubuntu remote desktop. I was told that VNC is quite good for this, but actually i dont have a clue how does it work. The point is : I have to get two laptops with ubuntu "talk" with each other. So if plz someone could explain me in few steps what should i do to make that work???? THNX

---

### Post by BarfBag on 2006-12-27
I've never done this myself, so I can't offer any help beyond this.  This link might help you out.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access)

---

### Post by jonathan.lees on 2006-12-27
If you click on system > Preferences > Remote Desktop this will allow you to turn on Remote desktop, Click in the allow other users to view your desktop button, click off the require your permission if you like and click on the require user to enter a password. Enter a password and click on close.

Now open a terminal and type ifconfig and make a note of your IP address.

Go to the other machine, open a terminal and type vncviewer (IP address of other machine)

For example: vncviewer 192.168.1.1

A vnc window opens and prompts you for the password you entered earlier. Enter it and you can now control the machine as if you were there.

---

### Post by Generalspuddog on 2006-12-27
damn that seems really easy. Is there a command for a windows machine to "dial" in and access the computer without going through all the NX or VNC setups?

---

### Post by jonathan.lees on 2006-12-27
If you want to access with this method via Windows, then you'll need to install a VNC client. In my experience RealVNC is good. You can download it [here]("http://www.realvnc.com/").

---

### Post by Generalspuddog on 2006-12-27
does Ubuntu remote desktop work with DHCP? If not how do i go about setting up a static IP so i can use it? I have a Linksys Wireless router (WRT54G)

---

### Post by Generalspuddog on 2006-12-27
never mind I got it to work! Your server can be using DHCP you just have to prefix what your IP address is. Use ifconfig and pick the first ip and use that on your windows side to "dial" in. 

Now is there anyway I can "dial" in withing having my linux box be signed in to a user? Like can i dial in at the username / password screen?

---

### Post by jonathan.lees on 2006-12-28
The term you are using "dial" refers to connecting to another computer or a server via a modem and phone line, you should be using the term "connect". In the configuration that you have for remote desktop you can only use the account that is logged in at that time.

---

