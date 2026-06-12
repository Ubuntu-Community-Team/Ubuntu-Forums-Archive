---
title: "VNCvier from windows"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-20
I have vncviewer for both OS's. How would I connect to my ubuntu dektop using windows.

The only way I have been able to conect is through the local network.

---

### Post by johnnymac on 2007-03-20
Be a bit more specific.  Are you talking about connecting from say - school to your home network in order to VNC into your system?

---

### Post by ProjectWhat on 2007-03-20
johhnymac right on the money!!!!

---

### Post by ProjectWhat on 2007-03-20
I know theres a way. Come one someone. please help.

---

### Post by slayerboy on 2007-03-20
Most schools and companies with good security will NOT allow you to VNC into a machine unless you have specific rights to do so.  I cannot VNC from my work machine to my home machine.  I couldn't even access my slimserver when I was running it, but seems like everyone else could LOL.

I'm thinking your school has a restrictive policy on connection types, so you're probably not going to be able to do this.

---

### Post by ProjectWhat on 2007-03-21
Well I still need this to conect to my pc when im at my friends house, or other familys house to get a file, etc. So please help me.

---

### Post by Mr. C. on 2007-03-21
1) Set up an SSH server at home
2) Configure your SSH server to allow tunneling
3) Open your firewall to allow SSH connections
4) Connect remotely with SSH to your home SSH server, with port 5900 tunneled
5) Use your VNC client to connect to localhost:5900

MrC

---

### Post by ProjectWhat on 2007-03-21
Why can't anyone help me with what I need. I dont want ssh. I want to use vnc. I want to use windows to connect to my ubuntu pc using vnc.:( :mad:

---

### Post by Mr. C. on 2007-03-21
If you want better help, spend a few minutes thinking about what you actually want, and write a clearer description of your needs.  If you are too lazy to type, don't expect better answers.

So skip SSH if you don't care at all about security.  What's the problem?

It's the same setup, without SSH or the tunnel.

Turn on Remote Desktop, open your firewall, and connect with a VNC client.

MrC

---

### Post by h0ax on 2007-03-21
I will help you, sure.

Set up a VNCSERVER running on your ubuntu PC at home.  Make sure you OPEN the ports on your router for running a VNCSERVER (I forget off top head maybe 3881? dunno) google it.

Now - once it is up and running and you have opened the port on your router, test it by going to another computer (or the same one) and running VNCVIEWER and inputting your IP address (WAN side)

you can get that from [www.whatismyip.com](www.whatismyip.com)

Don't be pushy on the forums - we're here to help, but there are plenty of HOWTO's available by either searching the forums or searching on google.

Either way - enjoy!

---

### Post by ProjectWhat on 2007-03-21
Thank you, The port starts at 5900 and goes up from there depending on how many connections you have. Like this:
1st client: 5900
2nd client:5901
3rd Client:5902
and so on...

---

### Post by Mr. C. on 2007-03-21
... and virtual screens.

So its working for you now?

MrC

---

### Post by ProjectWhat on 2007-03-23
Yes it works thank you

---

