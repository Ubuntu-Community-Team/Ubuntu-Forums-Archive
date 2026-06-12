---
title: "Connect to Widows remote desktop"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by winvado on 2006-11-29
On my Windows latop I can in 5 minutes (and setup) dialup & log into the company VPN via pptp then connect to windows 2003 server via remote desktop and use various applications all easy and simple as pie on XP.

On my Dapper box at home I have managed to use the pptp client and get connected, ping the server and confirm a connection... 
then I have tried lord I have tried to connect via Remote Desktop Client , however, nothing- it just times out .. am I missing something? Does the server need special sofware so that a linux box can connect to a windows remote desktop. After searching the forums there seems to be (is) no documentation. If ever there was an issue for linux it is compatability and easy connection with windows. Can someone help.. its been fun so far and I can Putty and WinSCP ( via ddclient), Unison etc but I'm stumped this time.

---

### Post by timcredible on 2006-11-29
rdesktop is great (works faster on same hardware than windows).  command is:

rdesktop <remote machine name or ip>.

you can add some stuff too, here's an example:

rdesktop -g1024x768 -a16 -utim -dtimsplace -psecret timsxpmachine

the above would connect to the machine named timsxpmachine at 1024x768 resolution, 16bit color depth, and automatically put in the username tim with domain timsplace and password secret.

---

### Post by civic_si on 2006-11-29
theres a GUI for that as well that looks similar to others. i use the remote desktop feature alot because i dont want to walk to my other computers.

---

### Post by nickburns on 2006-11-29
Go to Applications >> Internet >> Terminal Client and put the IP number and choose Remote Desktop Protocol to get up and going.

---

