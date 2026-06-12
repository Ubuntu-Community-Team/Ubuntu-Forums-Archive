---
title: "How do you run Vino?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by NightShade001 on 2007-05-04
Hi, im very new to linux and would love to learn how to use it. There's one problem, I have one moniter and 5 computer's....you see? Well anyways I downloaded Vino and TightVNC, but i cant seem to figure out howto run them. The distro im running is Kubunto the latest build. Could someone please help me and possible direct me to a few new user guides. Thank You

Also forgot to add the other machines will be running windows with VNC im not sure if it will work or not...

---

### Post by benanzo on 2007-05-04
are all these computers running Linux?

If they are running say Ubuntu, you can use XDMCP to login remotely as if it is on the local machine, not just the screen in a window.

Otherwise, just make sure that the TightVNC server is running on each machine that you want to connect to and use Terminal Server Client (tsclient) to connec to them.  I wouldn't worry too much about Vino.

You can also just type ```
vncviewer <ip/hostname of the machine to connect to>
```

---

### Post by NightShade001 on 2007-05-04
No, only the one machine is running linux the other's are windows xp i plan to use the linux pc as a server and control it remotely on a windows machine but for some reason vino is not in the service list and when i try to do a application>run programs>type"vino" it says program not found i downloaded vino useing the pakage manager

---

### Post by jfinkels on 2007-05-04
So you have an Ubuntu computer, from which you want to reach Windows computers?

Type the following command:
```

tsclient

```
which will open the Terminal Server Client (it's interface is extremely similar to the interface for Windows' Remote Desktop Connection). Then just type in the address and user (probably use RDP protocol) and connect to the windows computer.

If you want to use the VNC protocol, you will have to install a VNC server on each of the Windows computers, then use 
```
vncviewer
```
or ```
tsclient
``` again, but this time choose the VNC protocol.

If you want to connect TO the Ubuntu computer FROM the Windows computer, you need to install a VNC client on the Windows computer (like TightVNC) and then, on the Ubuntu computer, type ```
vino-preferences
``` and make sure to check "Allow incoming connections" or something similar. It should be the first check box.

---

### Post by NightShade001 on 2007-05-04
That actually got me into something i can see! thanks lol but im stuck again -_- the server(soon to be) is refuseing connections is there a place were i can change that someweres? its probly really simple but again im a complete noob i appreate the help guys and yes i did hit the check box to enable incomeing connections as well as remote control and i set a password

---

### Post by jfinkels on 2007-05-04
> **NightShade001 said:**
> That actually got me into something i can see! thanks lol but im stuck again -_- the server(soon to be) is refuseing connections is there a place were i can change that someweres? its probly really simple but again im a complete noob i appreate the help guys

When you say server, what do you mean? Also, are you using the RDP protocol now, or the VNC protocol?


Reasons why your connections might be refused: 

1. I think you can only log in to a remote computer with a user who is NOT currently logged in on that computer. Try logging out all users, then trying.

2. You have a software firewall up (i.e. Windows Firewall) on the Windows computer which does not allow connections on the standard VNC port (5900). Disable Windows Firewall, or make an exception on the VNC port.

3. You have to allow incoming connections on the Windows Computer. I don't have a Windows computer on hand, but from memory, I think you do something like right-click on My Computer, then go to one of the tabs where you will have the option to allow incoming requests. Sorry, that's the best I can do from memory :D

---

### Post by NightShade001 on 2007-05-04
using vnc i plan to make it into a server but im going ot play with that later after i get the basics down umm basicly connecting windowsxp>Kubunto
windows says refuseing connection when trying to connect to the linux pc

---

### Post by jfinkels on 2007-05-04
> **NightShade001 said:**
> using vnc i plan to make it into a server but im going ot play with that later after i get the basics down umm basicly connecting windowsxp>Kubunto
windows says refuseing connection when trying to connect to the linux pc

So your current problem is a refused connection when trying to use a Windows computer to connect via VNC to the Linux computer? Please be very clear with the description of your problem and use correct grammar, it really helps us out when trying to diagnose and solve the problem :D

This should allow you to connect to the Linux computer from the Windows computer:

1. Login to Ubuntu, reinstall Vino if it's not working for some reason:
```

sudo aptitude reinstall vino

```

2. Type the following:```
vino-preferences
``` and select "Allow other users to view your desktop" and "Allow other users to control your desktop". You may also want "Require the user to enter this password".

3. On the Windows computer, install TightVNC client (or both the client and the server if you're going to need the server later on, as you seem to be saying).

4. Open TightVNC viewer (Fast Compression), type the IP address of the computer, and enter the password. You should be good to go.

If something is going wrong here, please explain what exactly you are seeing and what exactly is the error message.

Remember to check if your computers are turned on and connected to your network. :D

---

### Post by NightShade001 on 2007-05-04
Ok i set all of the settings on the kubunto machine and when i try to connect useing tightvnc on the windows machine its now giveing me this "Failed to connect to listening VNC viewer" all firewalls have beend disabled on the windows machine and i dont think there are any on the kubunto unless theres ones that come with it so im kinda at a loss

---

### Post by jfinkels on 2007-05-04
> **NightShade001 said:**
> Ok i set all of the settings on the kubunto machine and when i try to connect useing tightvnc on the windows machine its now giveing me this "Failed to connect to listening VNC viewer" all firewalls have beend disabled on the windows machine and i dont think there are any on the kubunto unless theres ones that come with it so im kinda at a loss

Hmmm I'm not really sure what to tell you here. Are you sure that your Ubuntu computer is connected to the network? You may want to give your computers static IP addresses.

Can you ping the Ubuntu computer from one of the Windows computers?
```

ping 192.168.1.2

```
replacing 192.168.1.2 with the actual IP address of the Ubuntu computer.

---

### Post by NightShade001 on 2007-05-04
Ping worked beautifully. er....i dont get it i can ping to the pc but vnc cant connect? even though its running i believe...its not in the services list though but i can get into the settings and change them

---

### Post by jfinkels on 2007-05-05
> **NightShade001 said:**
> Ping worked beautifully. er....i dont get it i can ping to the pc but vnc cant connect? even though its running i believe...its not in the services list though but i can get into the settings and change them

One way to see if Vino-server is running is by typing the following command:```
pidof vino-server
```
which returns the process id of the specified process (in this case vino-server).

If you get a number back, then vino-server is running and I don't know how to help you beyond this point.

However, if you don't get a number, then it's not running. You can start it by typing the following:```
/usr/lib/vino/vino-server
```

---

### Post by NightShade001 on 2007-05-05
Well i typed in the pidof vino-server command and it didnt say anything at all so i typed in the /usr/lib/vino/vino-server command and it started then i tried typeing the pidof command again and it still didnt show anything at all siwtched pc's and tried to connect same problem


even if you cant help me any further i would like to thankyou for responding so proptly and trying to assist

oh one thing i forgot before im running xubunto i said i was running kubunto sorry..

---

### Post by jfinkels on 2007-05-05
> **NightShade001 said:**
> Well i typed in the pidof vino-server command and it didnt say anything at all so i typed in the /usr/lib/vino/vino-server command and it started then i tried typeing the pidof command again and it still didnt show anything at all siwtched pc's and tried to connect same problem


even if you cant help me any further i would like to thankyou for responding so proptly and trying to assist

oh one thing i forgot before im running xubunto i said i was running kubunto sorry..

I'm not really sure what to do if it doesn't look like vino is starting, even when you type that command. Another way to see if vino is running is o take a look at all the processes running on your computer and see if vino is among those listed. Type the following command:
```

ps ax | grep vino

```
If it's not there you can try installing tightvncserver on your Ubuntu computer and see if that works for you.

```

sudo aptitude install tightvncserver

```

Start that and see how it works out.

---

### Post by NightShade001 on 2007-05-05
that did not work ether one the first command i couldnt figure out howto type in do to the line in the middle but i tried the second command and it says that it cant be found the program i mean so i went to the package manager and verified that its installed and it is but thats ok that its still not working ill figure it out some other time i bought a belkin FLIP wich is working it basicly lets me switch pcs by pressing a button apparently belkin likes linux since they say its a supported os

Sorry for the bad spelling and puncuation but thankyou everyone who tried to help

---

### Post by jfinkels on 2007-05-05
That's a vertical pipe symbol, on my keyboard it's above the \ symbol ("above" meaning I can access it using Shift+\). Do you have some strange keyboard that doesn't have punctuation or something?

To install tightvncserver, you may need to enable the "Universe" repository. Go to "System > Administration > Software Sources" and enable the Universe repository.

---

