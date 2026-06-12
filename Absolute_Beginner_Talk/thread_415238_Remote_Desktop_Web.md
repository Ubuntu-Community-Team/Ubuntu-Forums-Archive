---
title: "Remote Desktop Web"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Fields987 on 2007-04-20
Hi. I am a complete noob to Linux. I really want to learn it, and become comfortable using it. So I downloaded Ubuntu 7.04 last night, and was wondering if there is anything out there like Remote Desktop Web for Windows Boxes. I was able to successfully set this up on XP, but I dont even know where to begin on Ubuntu, if it is even an option. Any information would be greatly appreciated. Thank you.

---

### Post by eentonig on 2007-04-20
To connect to Windows machines, you can you the Terminal Service Client, which uses the RDP protocol.

To connect to your Ubuntu machine remotely, you'll be using vnc or derivates.

---

### Post by Kobalt on 2007-04-20
VNC over SSH is a good and easy way to go in my opinion : [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by bribri124 on 2007-04-20
Yeah I don't believe there is anything like what you are looking for.  I have looked around before, but I can only connect via vnc or ssh.

---

### Post by rich.bradshaw on 2007-04-20
What about System/Preferences/Remote Desktop?

Other computers connect to you using VNC - you can download this for windows or linux. TightVNC will let you do it.

This is to connect to your Ubuntu computer from anotter computer.

What exactly are you trying to do?

---

### Post by Fields987 on 2007-04-20
Here is what exactly I am looking to do. If I am working on someone else's pc at their house, I have needed to connect to my pc to pull files, and documentation and the like. And instead of worrying whether or not they had client software on their pc's I set up remote desktop web connection on mine so that I could connect through internet explorer. I set up IIS,, I registered a domain name, and subscribed to dynamic dns service and I edited the activex control so that I could connect local hard drives, and I had no problem using it. I am looking for an alternative for Ubuntu. Something that I can open a web browser and type in the url, and bring up a login page that will open a remote desktop session. I've found a program that will do this, but it requires client software, and that is what I am trying to get away from for the purpose of compatibility will all platforms. This program is called Nomachine just in case anyone is interested.

---

### Post by Kobalt on 2007-04-20
If you're only willing to access files and not launch apps then simple [SSH]("https://help.ubuntu.com/community/SSHHowto") is the best/easier/quicker way for me...

---

