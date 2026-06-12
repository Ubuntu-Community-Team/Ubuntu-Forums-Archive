---
title: "Struggling with Remote Desktop, pls help! (FreeNX Server-Ubuntu, FreeNX Client-WinXP)"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-05-24
I've searched and searched and searched and I'm about at my wits-end.  Worst of all, I'm a noob.  ](*,)   I've looked through [http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx](http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx), [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX), searched and googled to no avail. 

I'm trying to connect to my Ubuntu Breezy box at home from work (WinXP).  The breezy box is behind a router so I've forwarded port 8888.  I read on [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) that some ISP's block port 22 traffic and so the tutorial used 8888 successfully.  I also modified /etc/nxserver/node.conf to reflect port 8888 instead of 22 as well as the /etc/ssh/sshd_config file.  I uncommented the line in node.conf per the instructions.  

When I try to connect from work OR home on my LAN, I get the following error: 
NX> 203 NXSSH running with pid: 1860
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
ssh: connect to host ##.###.###.## port 8888: Connection timed out

I have the FreeNX server installed correctly using the NOMACHINE key option and currently running at home.  I installed it last night and was able to bring the server down and back up, so no problem there.  I was NOT able to connect from a WinXP machine on my LAN either, using its internal address to connect instead of its external.

I'm just not real certain where to turn at this point.  I don't know if I should try a different port, is there something I'm missing in my router settings?  Do I need to do something in my FreeNX client?  Is there something with the "Key" in the FreeNX client that I need to modify?  

BTW, below are my current settings in my FreeNX client.  If there is anything else I can post to help figure out the problem, please let me know!  

Thanks SO MUCH in advance for the help, you guys are great!

[IMG]http://www.lbcflint.org/cjs/images/FreeNXClient.JPG[/IMG]

---

### Post by Stealth on 2006-05-24
Well, why don't you try a regular ssh session to see if that works? Using [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") try logging into your machine. Of course, using that 8888 port. If it doesn't work, then try leaving the default ports.

---

### Post by Getwild2 on 2006-05-24
[QUOTE=Stealth]Well, why don't you try a regular ssh session to see if that works? Using [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") try logging into your machine. Of course, using that 8888 port. If it doesn't work, then try leaving the default ports.[/QUOTE]
Well that didnt work, so what does that tell me?  I tried ports 8888 and 22 just in case.  

So putty would work with the FreeNX server for text-only?  That would be nice.  Once I get putty working I can steer towards fixing the FreeNX client's issues, then again once putty is working, FreeNX may work as well.

---

### Post by Getwild2 on 2006-05-24
Alright, I went back to the default settings of Port 22 across the board.  I did figure out why I wasnt even getting any authentication, its because I didnt set a static IP of 192.168.0.2 for my Breezy box.  Once I did that, the router knew where to make the connection.  

Now that I can actually authenticate, I'm receiving the error I've pasted below.  

[IMG]http://www.lbcflint.org/cjs/images/FreeNXError.JPG[/IMG]

When I click "Detail", I receive the following output:

[COLOR="Red"]NX> 203 NXSSH running with pid: 1404
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.0.2 on port: 22
NX> 211 The authenticity of host '192.168.0.2 (192.168.0.2)' can't be established.
RSA key fingerprint is 0f:d1:bb:4c:40:6b:20:1f:c2:40:ed:77:87:b9:e7:6e.
Are you sure you want to continue connecting (yes/no)? 
Warning: Permanently added '192.168.0.2' (RSA) to the list of known hosts.
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: cstiff
NX> 102 Password: 
NX> 103 Welcome to: ubuntu user: cstiff
NX> 105 listsession --user="cstiff" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'cstiff' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: cstiff
NX> 105 startsession --session="Ubuntu Box" --type="unix-kde" --cache="8M" --images="32M" --cookie="******" --link="lan" --kbtype="pc102/en_US" --nodelay="1" --encryption="1" --backingstore="never" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1280x770x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: ubuntu-1000-64B2678F5F1F535566C39833F2F4D7C2
NX> 705 Session display: 1000
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: dbf15199ad658c51536eb58fbac4dae8
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: dbf15199ad658c51536eb58fbac4dae8
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
Killed by signal 15.[/COLOR]

Any ideas now?  

Thanks again for ALL of the help!!  :)

---

### Post by Getwild2 on 2006-05-25
Nevermind, I figured it out.  If you notice my screenshot in the first post, I have KDE chosen.  Well I'm running Gnome so it was erroring off.  Once I switched it worked perfectly.  Actually I'm at work right now, typing this on my home machine using nxserver/client through ssh.  :D

---

### Post by hvc123 on 2007-10-07
your work may have a proxy server (almost a given that it has) port 8888 may not be allowed by your proxy server. the best thing to try (its a little dangerous(open to hackers)) is to use port 80 or 443.(web and secure web) as these are the most common open ports and will be open on you proxy.


i remote from my work through a proxy and i use the 443 secure web port. works like a treat

---

