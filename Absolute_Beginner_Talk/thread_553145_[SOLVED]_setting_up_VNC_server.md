---
title: "[SOLVED] setting up VNC server"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by vikram on 2007-09-17
I am trying to access my desktop running Kubuntu 7.04 from my work laptop running windoze using realvnc.

I used [https://help.ubuntu.com/community/VNC?highlight=%28vnc%29](https://help.ubuntu.com/community/VNC?highlight=%28vnc%29)

as a guide. However I dont have the KDE packages installed so I have to ssh into the linux box and run
```
vncserver :1
``` from the command line. This works.

A few questions:

1. What do i have to install to get the KDE packages so that I can send personal invitations ? I need this functionality as I want my family to use linux and I'd like to remote desktop to troubleshoot.

2. Complete the wiki documentation so that newbies and/or people who dont want to use the command line dont have to.

3. Currently works only when I turn off my firewall. Do I only need to open 5901 ? If you can tell me the iptables command to enable that will also help.
Is it
```
iptables -A INPUT --protocol tcp --dport 5901 --source 10.0.0.0/24 \
      -m state --state NEW -j ACCEPT

```I am using a modified version of this as my firewall script 
[http://users.piuha.net/martti/comp/ubuntu/en/install.html#11](http://users.piuha.net/martti/comp/ubuntu/en/install.html#11)

4. Uinsg realVNC I can open apps in linux but can move this windows around/ resize them. Is this normal or am I missing something ?


Thanks in advance
Vikram

---

### Post by ryanbelv on 2007-09-18
Wow...I can't believe nobody answered this.  Not even to say, "See this post."

That's kind of discouraging...I'd like to see the answer to the questions.

---

### Post by kebes on 2007-09-18
> **vikram said:**
> 3. Currently works only when I turn off my firewall. Do I only need to open 5901 ?
Since you launched VNC on ":1" then you need to open port 5901 to connect to the VNC server. But, actually, there is another way of doing it that removes the need for opening that port, and is more secure, too.

Basically, since you can SSH to the remote computer, you can use that SSH connection to "tunnel" the VNC traffic. This is more secure because you don't need to open another port, and all the SSH traffic is encrypted (whereas VNC is not). This is actually important if you're doing remote administration, since you might end up typing passwords through the VNC session.

A Google search for "tunnel VNC over SSH" will give you lots of good guides on how to do this. I'll briefly outline the steps (feel free to ask for clarifications):
1. You connect to the remote computer using SSH, but you do a "port forward" for port 5901, like so:
```
ssh user@remotecomputer -L 5901:localhost:5901
```
where "user" is the account on the remote computer, and "remotecomputer" is the IP address or server name of the remote system. The above is from a Linux commandline. If you're connecting from a Windows computer, you can do port forwarding using PuTTY (see [screenshots here]("http://martybugs.net/smoothwall/puttyvnc.cgi")).

2. In the SSH session, start the VNC server on the remote computer (if it is not already running), using:
```

vncserver :1

```

3. Now, on your local computer, open up the VNC client, and connect to "localhost:1":
```
vncviewer :1
```

Because the local port 5901 is being forwarded over the SSH connection, you will actually connect to the remote port 5901. You should have a normal VNC session, without having to open up the firewall on either computer.


> 1. What do i have to install to get the KDE packages so that I can send personal invitations ? I need this functionality as I want my family to use linux and I'd like to remote desktop to troubleshoot.
Using the above trick, you actually don't need to wait for them to send an invitation. As long as you can SSH into their machine, you can initiate the entire VNC session yourself. (This lets you see a GUI of their system... however if you want a "shared desktop" so you can both interact with the same windows, etc., then you may have to use the "personal invitation" route...)

I'm not sure what packages need to be installed for that to work (I have all of KDE installed). I believe in GNOME it's called "Remote Desktop" but I'm not sure.

> 4. Uinsg realVNC I can open apps in linux but can move this windows around/ resize them. Is this normal or am I missing something ?
I'm afraid I don't understand this question. Do you mean that you cannot move the VNCviewer window on your local computer? Or do you mean you cannot move the windows *within *the VNC session?



I hope that helps. As always, feel free to ask any more questions if you need clarification...

---

### Post by vikram on 2007-09-20
Thanks kebes for the detailed instructions.this worked and I could use VNC viewer on my windows machine to view my linux desktop. 

For anyone else reading this thread - 

The personal invitations are send by Desktop Sharing (krfb). I didn't have this in my menu's but was already installed. 

I didn't like the original screen that VNC showed my because I couldn't move the windows around, resize them etc. By using the standard kde window manager I got around this problem. to do this replace the last line twm& with startkde& in the file your-home-dir/.vnc/xstartup like so ...

```

~$ cat .vnc/xstartup
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startkde &


```

---

### Post by vikram on 2007-09-20
added reference to krfb to wiki

[https://help.ubuntu.com/community/VNC?highlight=%28vnc%29](https://help.ubuntu.com/community/VNC?highlight=%28vnc%29)

---

### Post by uufan on 2008-06-16
I have met the similar problem as your question 4. There is no any "sidebar" or "topbar" for the default xterm window, therefore I can not move the window at all.

The problem is: you may not have "twm" installed in your default ubuntu package. "twm" is default window manager for vncserver. 
Just run: sudo apt-get install twm.

I prefer "twm" or "mwm" for vncserver since they are much faster than those graphical window managers like kde.


> **vikram said:**
> 
...

4. Uinsg realVNC I can open apps in linux but can move this windows around/ resize them. Is this normal or am I missing something ?

...

Vikram

---

