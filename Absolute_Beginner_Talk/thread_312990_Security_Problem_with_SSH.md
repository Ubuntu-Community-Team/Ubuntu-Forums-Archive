---
title: "Security Problem with SSH ?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Panasonica on 2006-12-05
I've just installed Ubuntu (Dapper) for the first time. Hooray :D .

I've installed SSH (using Syanptic) so that I can open a graphical Ubuntu session from my XP machine on the same LAN.

But I read the following warning on a website about installing SSH onto a graphical Linux machine:

>   If you have a GUI session open on one of your Linux systems, that host is probably listening to TCP port 6000 (between 6000 and 6063).  You can check this with the netstat -tna command.  It is okay for it to be listening on the 127.0.0.1 address, but not on 0.0.0.0 or your Ethernet address(es).  Although this is not an X over SSH problem, it is a typical issue with running a GUI desktop on one of your machines.  This can leave you vulnerable to keystroke sniffing, destruction of windows, unrequested windows popping up, arbitrary commands being executed, or your screen being grabbed.  There are two easy ways to handle this, assuming that the only remote X access will be through SSH:


a)  start your X session with the "-nolisten tcp" option, either in your command line or your GUI startup scripts.  You will probably have to dig into the documenation if you want to do this in runlevel 5.  If you start your X sessions from the command line in runlevel 3, you can enter the following:

startx -- -nolisten tcp     or    startx -- :1   -nolisten tcp     (and so on...)  


b)  use your ipchains or iptables firewall to block TCP ports 6000-6063 on your Ethernet addresses.


Indeed, netstat confirms that  I do have a TCP port listening on my 0 ethernet address in the above port range (6000 to 6063).

Can someone help me with the following points:

1) Why is it dangerous to have an open port listenting in the range 6000 to 6063 ?
2) How can having this port listening, enable keystroke sniffing, destruction of windows, unrequested windows popping up, arbitrary commands being executed, or your screen being grabbed ?
3) How can I start my X session with the "-nolisten tcp" - which configuration file do I have to change ?
4) What effect will starting my X session with the "-nolisten tcp" have on other Ubuntu programs/processes ?
5) Why does Ubuntu running SSH listen on port range 6000 to 6063 ?

Many thanks in advance for your help to a worried beginner,
P

---

### Post by sardion on 2006-12-05
If you have a port in the 6000 range for X open to the general internet then someone can connect to your computer essentially without a password (not entirely true but for the purposes of answering a beginner's question its close enough).

You need to make sure that the port in question is only open to the localhost (127.0.0.1) so that the *only* way to connect to it is by using ssh to get in first, in which case you are perfectly secure (well, as secure as ssh and your password, etc.).

SSH does not listen on these ports.  SSH listens on port 22.

How do you connect from the XP machine to the Ubuntu machine?  Using SSH?

On the ubuntu machine, run

netstat -l

and look at the top part of the output, it will look like:

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN  


And some more lines, then there will be a section about Active UNIC domain sockets which we don't care about for this issue.

Look at that list and look for anything in that 6000 range under Local Address.  If there is anything, make sure it says localhost:60XX not *:60XX.

If there is no *:60XX then you are safe and secure.  If there is, post again and we can get you fixed up.

On a side note, if your machines are all behind a firewall/router and you control who has access to them (physically) then you probably don't have to worry about security much when it comes to this kind of stuff.

---

### Post by steve.horsley on 2006-12-05
It is not normal for Ubuntu to listen on those port numbers. The command **sudo netstat -plant** will tell you which processes have opened listening ports, and this might be interesting.

---

