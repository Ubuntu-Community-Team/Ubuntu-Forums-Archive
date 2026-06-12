---
title: "Running a program (synergy) at boot?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Thief X on 2008-02-27
I am currently running two systems side by side with synergy*, and it works really well, but I was wondering if anyone could help explain to me how to get it to run at boot...I currently have it auto-running at the start of my GNOME session(so the problem i read about the client connection being cut off when you log in is solved), which works great, but i have to have a keyboard attached to the client computer in order to log in.

I have read about adding a command to /etc/rc.local or something to that degree, but it didn't work correctly, So if anyone could tell me how to do that correctly that would be great, and explain what they are doing, so i can understand what is going on.

The command to run the synergy client in the terminal is:
```
synergyc -f [IP ADDRESS]
```

Thanks in advance

*Synergy is a program that allows you to run two computers with two separate monitors using only one keyboard and mouse, through your home network.

---

### Post by neurostu on 2008-02-27
Great question, I actually don't have the answer, but I am going to recommend that you use ssh to connect your two machines. The reason why is that synergy doesn't encrypt or try to secure the information that it sends.  

So if either of your machines get compromised by a malicious packet sniffer it can send all your keystrokes back to a 3rd party, potentially given them your passwords, website logins, etc.  

Anyway its really easy to set up the security. I use what is called reverse port forwarding or reverse tunneling

Here is how I do it ( I use synergy everyday)

I will use two machines one I will call laptop the other is desktop.  Since I use my laptop keyboard and mouse I will run the synergy server on it, I will run the synergy client on my desktop

Code to ssh from laptop to desktop:
```

usr@laptop$ ssh -R 24800:localhost:24800 <ip_of_desktop>

```
This code sets up a reverse tunnel from my desktop to my laptop so any activity on port 24800 of laptop gets forwarded to 24800 of desktop and visa versa
Note: after the above code runs you will see the command line of the desktop, where I type
```
 usr@desktop$synergyc -f localhost 
```
I use the -f option so I can see what is going on, it is totaly optional though.

Then on laptop I run
```

usr@laptop$synergys -f -c .synergy.conf 

```  the -f is the same as above and the -c is so I can specify the location of my synergy config file. Also i would highly recommend leaving the -f argument for the server as synergy clients have a tendancy to not shut down sometimes (or maybe i'm just sloppy) but the -f will let me see when multiple clients of the same name are trying to connect and then I just run: ```
 killall synergyc 
``` to kill them all.


Anyway I would ** HIGHLY ** recommend doing it this way as your keystrokes are secured with ssh.

Let me know if these instructions help and if you have any problems with them.

---

### Post by neurostu on 2008-02-27
Also the great thing is, when I leave with my laptop I just lock the screen of my desktop.  When i return i re-establish the tunnel, restart the client if it isn't running, then using the mouse and keyboard of my laptop I can unlock the desktop.

---

