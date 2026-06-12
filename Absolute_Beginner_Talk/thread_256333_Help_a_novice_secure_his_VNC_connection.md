---
title: "Help a novice secure his VNC connection ?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Copps on 2006-09-12
Hi all,

I need to be able to access my Ubuntu desktop from a remote Windows machine. 

I have added vnc4server and xinetd via aptitude, set config, and can start an ubuntu session locally via vncviewer:localhost:1

I can also start a session using tightvnc.exe on a Windows machine on my local network. What I've read about accessing sessions through VNC remotely doesn't fill me with much confidence! From what I understand of SSH tunnelling, I could connect remotely to my Ubuntu machine via SSH and begin the desktop session by running the same command as above, "vncviewer:localhost:1"

This is where my understanding may be drifting off. Is this SSH tunnelling? When I try to do this, I get "Error! Cannot open display!"

Here are the things I can't figure.

Do I understand what SSH tunnelling really is?

How can I access an Ubuntu desktop session remotely AND securely using SSH tunnelling?

Do I need to port forward SSH traffic to my Ubuntu machine, which is sat behind a router?

How can I change the SSH connection port to something else to help prevent unauthorised access?

Thanks for any help anyone can offer!

---

### Post by Copps on 2006-09-13
Hm, OK I've made *some* progress here.

I have switched the access port for SSH in sshd_config, and set up port forwarding on my router to the new SSH port.

I've set up a SSH tunnel using the notes at http:[www.brainonfire.net/2006/08/21/vnc-over-ssh/](www.brainonfire.net/2006/08/21/vnc-over-ssh/).

Now here's the thing. I can connect to SSH on my Ubuntu machine via Windows Putty if I use the 192.168.* IP address, and the port number I specified. If I try to connect using the external fixed IP that my ISP has given me, from the same Windows machine, I get "Connection refused" - [http://www.tartarus.org/~simon/puttydoc/Chapter10.html#errors-connrefused](http://www.tartarus.org/~simon/puttydoc/Chapter10.html#errors-connrefused)

I'm far from being an expert as you can probably tell, but this suggests that the port forwarding I have set up on my router is OK, and Ubuntu itself is refusing the SSH connection! Yet it permits the SSH connection when I connect using Ubuntu's internal IP address.

Further, I've double-checked the port is open using [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and everything checks out, and confirmed my external IP address at [http://www.whatismyip.com](http://www.whatismyip.com)

Anyone got an idea why the SSH connection fails to work only when I try to connect on my external IP?

---

### Post by benfindlay on 2006-09-13
I'd check port forwarding is set up ok in your router. Also, if youve changed the ssh port from the default 22 you will need to edit ubuntu's firewall I believe to notify it of the change. SSH is secure. As for VNC, with putty, you point VNC at 127.0.0.1 (localhost) and you set a tunneling rule up in your putty connection so that it routs the VNC conenction through itself to the ubuntu computer. As for enabling remote VNC access, you need to go into System>>Admin>>Login Window (might be System>>Preferences>>Login Window, not at my ubuntu pc, sorry!) and choose the remote tab. In there there is an option for sessions; you need to set it to "same as local" or "minimal graphics" option. This should allow you to view your session ok

Hope this helps

---

### Post by steve.horsley on 2006-09-13
You will not be able to connect to your external IP address from inside your home. That would involve going out and back in, and doing two NAT translations (one in each direction). It won't happen. If all is set up right, you should be able to ssh in from work (or anywhere else) though.

---

### Post by Copps on 2006-09-13
Thanks all. After a convoluted process, I eventually connected to my works VPN from my home Windows PC, used remote desktop to connect to my work PC, managed to get a SSH connection onto Ubuntu from there, and was able to connect back to Ubuntu using tighvnc viewer from work. Phew!

Anyhow, am I right in thinking I can now remove VNC port forwarding (5900) from my home router, and this means SSH tunnelling is the only way that a VNC graphical session can be established on my Ubuntu PC?

---

### Post by benfindlay on 2006-09-13
Yep thats right, just uncheck/delete the rules for vnc from your router and apply the changes. Since VNC goes through SSH, you only need your SSH port forwarded. Thats exactly what I have to connect to my ubuntu pc at home; works a treat! ;)

---

### Post by steve.horsley on 2006-09-13
> **Copps said:**
> I right in thinking I can now remove VNC port forwarding (5900) from my home router, and this means SSH tunnelling is the only way that a VNC graphical session can be established on my Ubuntu PC?

Absolutely. Don't leave VNC open any longer that necessary - it's an open invitation, and it **will** be found.

---

