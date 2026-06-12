---
title: "ssh on diffrent ports ????"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Red-Shield on 2008-01-10
i want to run ssh on a diffrent port one that i choose i have portforwarded all the proper things and i have tried to nano the sshd_config and the ssh_config to change the ports for the program to listen on and i have even asked ssh to listen on a specified portin the terminal two diffrent ways and still nothing any one out there have any ideas??????

---

### Post by mrphud on 2008-01-10
why do you need a different port?

```
ssh username@server.blah
```

and enter you password.

I do know that on gutsy there is the terminal server client that allows you to choose your port. Is there anything like that on feisty?

that terminal server client is under application>internet for gutsy

---

### Post by kvizz on 2008-01-10
edit your /etc/sshd/sshd_config and then restart ssh: sudo /etc/init.d/ssh restart. then connect to your ssh server by usind ssh [email]user@server.com[/email] -p12345

---

### Post by Red-Shield on 2008-01-10
i want the port for security purpose to be a random number but i bet that i did not restart it and that could be the answer now please tell me if the above command is the only way to0 restart ssh what about restarting the machine as a whole would that restart ssh thanx for the help.....

---

### Post by kvizz on 2008-01-10
well, you can just reboot your pc
and for security reasons you may want to install fail2ban or denyhosts

---

### Post by wickstopher on 2008-01-10
kvizz: not exactly

the file is actually located at /etc/ssh/sshd_config

edit that file using the text editor of your preference (using sudo for root permissions).

```
sudo (nano/gedit/vim/kate/whatever) /etc/ssh/sshd_config
```

Near the beginning of the file, there are a few lines:

```
# What ports, IPs and protocols we listen for
Port xxx
```

change xxx (default port is 22) to whatever port you desire (i.e. whatever port you have your router set up to foward).

then, execute this command:

```
sudo /etc/init.d/sshd restart
```

or, if you didn't already have the ssh daemon running:

```
sudo /etc/init.d/sshd start
```

you should be good to go.

from a command prompt, type in (again, with xxx being your desired port):

```
ssh -p xxx username@hosname
```

---

### Post by kvizz on 2008-01-10
wickstopher: you're right, thanx.
but on my machine  sudo /etc/init.d/ssh restart somehow works very well =)

---

### Post by Red-Shield on 2008-01-10
i have done all of the above and it denies me when inside my network i have not tried it outside the net work and it just says connection ferused on port 4130and still by default it listens on port 22 if not specified why must i give a port number if i have told it to listen on that port in the /etc/sshd_config file can i listen on multiple ports like mabey three ports or just one

---

### Post by wickstopher on 2008-01-10
I must say that your post is a bit confusing in its' wording.  I'll try to answer your questions to the best of my interpretive ability.

when you edit the sshd_config file, you are telling the SERVER, i.e. the computer that you are attempting to connect to what port it should be listening on.  The reason you need to specify when you connect is that any ssh client by default connects to port 22.  As detailed in my previous post, you need to use the -p argument to specify which port you want to connect to.

There are a few things that you may be doing wrong.

A previous user in responding to this post specified an incorrect location for the sshd_config file.  Said user said that the file was located at /etc/sshd/sshd_config.  This is wrong.  

Make absolutely certain that you are editing the file in this location:
/etc/ssh/sshd_config

also, make absolutely certain that you are using sudo (root permissions) when editing the file, and make sure that you save the file.  If you do not use sudo, it may seem as though you are editing the file, but you will not be able to save the changes.

Lastly, make sure to restart the ssh daemon, as mentioned in my previous post.  If the ssh daemon was not already running, make sure that you start it, as mentioned in my previous post.  Let me know if you have any more problems after verifying all of this.

---

### Post by hyper_ch on 2008-01-10
I fail to see why running sshd on a different port should make it more secure?

Use nmap and check out all ports before you attempt to "hack" it. So port number is IMHO not a matter or security. Rather use a strong password for logging in and auto-ban tools like DenyHosts or Fail2Ban.

---

### Post by Red-Shield on 2008-01-10
first let me thank all of you for the info  the info is good and correct let me try one more time and yes thank you for all your help i love this forum :::: i want to change the port because i dont like to leave common ports open i feel better if random ports are open i have edited the correct files using nano and did so as root and then i try to connect ( ssh -p xxxx [email]red@xxx.xxx.xxx.xxx[/email]) and it says connection refused on port xxxx when i am outside my home network but dose work inside the network for example it workes when i give this command [ssh -p 4130 [email]red@192.168.1.xxx[/email]] a linksys IP
dose not work when i give this command [ssh -p 4130 [email]red@64.13.122.xxx[/email]] my true IP address.

---

### Post by hyper_ch on 2008-01-10
well, from outside you'll have to forward the according port from the router to your computer...

---

### Post by wickstopher on 2008-01-11
Right...you need to know both IP addresses.  The IP address of your computer on your home network is different from the actual IP address when trying to access outside of your home network.  I remember making this mistake back when I was first starting to use ssh.  Make sure that port forwarding is enabled on your ROUTER to the correct port (this may be tricky...TWC customer support told me that it wasn't supported, and I had to find the administrative password via google to login to my router and change port forwarding settings), and then make sure that you are using the correct IP.  In my experience, most home routers use 192.168.0.x for the addresses of different computers within the home network.  The actual IP is going to be different.  I can't currently remember the command to display your ip address (there are various karamba widgets that display it, and also logging into your router you should be able to find it).  Hope this helps.

---

