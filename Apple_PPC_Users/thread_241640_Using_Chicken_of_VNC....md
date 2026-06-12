---
title: "Using Chicken of VNC..."
date: 2006-08-22
forum: Apple PPC Users
---

### Post by timka1 on 2006-08-22
I have loaded vncserver on my Ubuntu machine (Dapper) and I want to be able to access it via the Chicken of VNC (version 1.3.6)  I use on my iMac G5 running OSX 10.4.7.

Although the vncserver appears to have started up OK and prompted me for a password when I try to connect I immediately get an error message:
 
connection refused: connect()

There doesn't appear to be any message on the Ubuntu vncserver log and I'm sure that the password supplied is OK.

Anyone out there using vncserver successfully from a Mac or any educated guesses as to what's going wrong?

---

### Post by nquinnathome1 on 2006-08-28
I have run the default VNC and vncserver on Ubuntu without any problems using CotVNC; are you definitely connecting to the right port on Ubuntu? I know by default Chicken tries port 5900, but for some reason my vncserver defaulted at 5901 (I changed it later on); maybe you should try:

<ubuntu-box ip address>:5901

in your CotVNC connections dialog and try again.

---

