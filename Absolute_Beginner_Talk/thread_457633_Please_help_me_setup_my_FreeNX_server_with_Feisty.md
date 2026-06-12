---
title: "Please help me setup my FreeNX server with Feisty"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-28
Ok Ive installed nxclient, nxnode, and nxserver from the seveas repository.  Using localhost as the server, I can connect to my own maching with ssh.  Im not exactly sure how to configure the nxserver -- seems like directories are much different that the only Dapper tutorials I could find.  I did add myself as a user with a password to the nxserver -- a dsa key was created in the ~/.ssh/authorized_keys2 file.  

I did add to the /etc/ssh/sshd_config file the following:
AuthorizedKeysFile %h/.ssh/authorized_keys2


Using the client, this is the error message I get:
NX> 203 NXSSH running with pid: 22455
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


Ive read about Nomachine but dont quite fully understand setting the server up with this option since aptitude installed the server.

Any help would be appreciated.

---

### Post by Austin_KW on 2007-05-28
Try 
sudo /etc/init.d/ssh restart

sudo dpkg-reconfigure freenx ( and accept the nomachine key until you get it working)

I am using it on a LAN so I just use the nomachine key, if you create your own keys you will have to add them to the server with reconfirgure as above and to the nx client configure>general>key>import

---

### Post by Austin_KW on 2007-05-28
One other thing, It is not your user that accesses the nx server but rather the user "nx" If you changed the ssh config to not allow all users then you have to allow user nx

---

### Post by kevdog on 2007-05-29
Dont understand your last post.  Did you mean ssh config or sshd_config to accept all users??? I looked in both files (/etc/ssh/sshd_config) and ~/.ssh/config and didnt find the section you were addressing.

I did reconfigure the package with machine keys as you suggested in the 2nd post (thank you).

I still however receive this error when trying to login into localhost from the client:

NX> 203 NXSSH running with pid: 26498
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


The problem is that there is a lot of tutorials or instructions to set up found in google, but all are slightly different. Ive read about having to change file permission and copy nx keys to different directories.  
Certainly there must be a more precise way to do this??

---

### Post by kevdog on 2007-05-29
OK Ive really got a problem.  I thought nx generated dsa keys.  I tried something different with the client and typed for the location 127.0.0.1 instead of localhost.  Again I couldnt log in but I got the following:

NX> 203 NXSSH running with pid: 27864
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 127.0.0.1 on port: 22
NX> 211 The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is cb:4a:93:ef:c6:ef:17:a9:20:ba:c4:b6:c8:2e:83:59.
Are you sure you want to continue connecting (yes/no)? 
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


Where did this RSA key come from????

---

### Post by kevdog on 2007-05-29
Sorry the last question was stupid, that was the host rsa key.

---

### Post by kevdog on 2007-05-29
Ok Ive gotten a little farther with the problem.

One thing that the default nx installation creates with machine keys is to make an authorized_keys2 file rather than authorized_keys.  I dont know why they do this, since the sshd_config file can only take one parameter for the AuthorizedKeysFile.  By default on my machine this parameter was set to .ssh/authorized_keys.  In order to authenticate I needed to copy the authorized_keys2 file in /var/lib/nxserver/home/.ssh to authorized_keys (please note to change ownership of this file to nx).

Ok, once doing that I could log in, but now receive the following message:
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '4107'.
Session: Starting session at 'Tue May 29 03:55:22 2007'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using lan link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-rle-9' with session 'unix-kde'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using persistent cache.
Info: Listening for font server connections on port '11000'.
Session: Session started at 'Tue May 29 03:55:22 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Error: No response received from remote proxy while waiting for the shutdown.
Session: Session terminated at 'Tue May 29 03:56:03 2007'.

Any suggestion??

---

### Post by Austin_KW on 2007-05-29
Probably a silly question, you you do have kde installed on the server as you have chosen an KDE session.

I did not need to copy the authorized_keys2 file, The commented out line in the config file implies authorized_keys but it was looking for authorized_keys2.

---

### Post by kevdog on 2007-05-29
Actually I had kde and gnome installed on the localhost machine.  I get a slightly different error message when trying to do a gnome session, than kde, but both choke at the same point.  Ive spent hours looking at other posts and have seen this error come up a handful of times but with no resolution.  Someone suggested changing .xaurthority file which I did but didnt help.

---

### Post by kevdog on 2007-05-29
Since my problem is now with nxproxy, is their a way to troubleshoot this problem by hand -- ie run nxproxy on localhost from command line??  I cant see to find this program.

---

### Post by kevdog on 2007-05-29
Just as another test I downloaded the nomachine nx client for windows for my winxp box.  I can not find a log file for the client on windows.  What I see however is that after authentication, a client window opens for a brief time (it is black), and then suddenly closes.  A popup box informs my that there was a connection error.  Thats all.  

This leads me to believe there must be something wrong with the server configuration rather than the client since but linux and windows clients are dying at the same point!

---

### Post by Austin_KW on 2007-05-29
Do you have any firewalls/filters.
As well as the ssh connection to port 22 I am seeing a connection to the server nxagent on tcp port 5000 from the client nxssh.

---

### Post by kevdog on 2007-05-29
With the localhost client/server I turned off the firewall.  Im running nomachine 2.x as the client??  Is there a possible problem with this version???

---

### Post by Austin_KW on 2007-05-29
No should be fine, My versions;
/usr/NX/bin/nxclient --version
NXCLIENT - Version 2.1.0-17

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

 nxserver --version
NXSERVER - Version 1.5.0-60 OS (GPL)
Usage: nxserver <option>
--passwd: Change password

Here is the log form one of my current connections (ignore the port 6000 for sound) but you are not establishing a connection to port 500x on the servers.
[I]
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '9570'.
Session: Starting session at 'Tue May 29 14:14:41 2007'.
[B]Info: Connecting to remote host 'gabby-pc:5000'.
Info: Connection to remote proxy 'gabby-pc:5000' established.[/B]
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using adsl link parameters 512/24/1/0.
Info: Using cache parameters 4/4194304/16384KB/16384KB.
Info: Using image streaming parameters 50/128/1024KB/2048/256.
Info: Using image cache parameters 1/1/65536KB.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression 3/3/0.
Info: Using ZLIB stream compression 6/6.
Info: Using cache file '/home/austin/.nx/cache-unix-gnome/S-0AE4FA2A97AE8C129E1EC1C3DE39EFD9'.
**Info: Using remote server 'gabby-pc:5000'.**
Info: Forwarding multimedia connections to port '6000'.
Info: Listening for font server connections on port '11000'.
Session: Session started at 'Tue May 29 14:14:41 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/4096K.
Info: Forwarded new connection to media server on port '6000'.
[/I]

And similar with a local host connection to 500x on the same server
[i]
NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '18306'.
Session: Starting session at 'Tue May 29 17:02:52 2007'.
[B]Info: Connecting to remote host 'localhost:5001'.
Info: Connection to remote proxy 'localhost:5001' established.[/B]
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using wan link parameters 768/24/1/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/3072/384.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde'.
Info: Using ZLIB data compression 1/1/0.
Info: Not using ZLIB stream compression.
Info: Using cache file '/home/austin/.nx/cache-unix-kde/S-08DFDF727D718CC4D7C74D6F0BE50C7A'.
Info: Using remote server 'localhost:5001'.
Info: Listening for font server connections on port '11001'.
Session: Session started at 'Tue May 29 17:02:52 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
[/I]

---

### Post by kevdog on 2007-05-29
Thanks for your help.  I see that my port assignment is different than yours, however Im not sure what to do to change this.  In fact I dont know what to do at all.  

The only thing I can think of is that I installed the server directly from the seveas repositories, rather than from .deb files directly.  Could this be the problem???

Who knows??

Maybe I'll try posting in the networking forum.  Im out of ideas.

---

### Post by Austin_KW on 2007-05-29
did you install the nomachine version. I did and had to clean out the /usr/NX structure before I installed freenx or it would not work.

I also installed directly from the seveas repos. I did not modify the sshd_conf, I just "sudo dpkg-reconfigure freenx" and selected the nomachine keys.

It might be worth trying the nomachine server, remove everything then down load the .debs from nomachine.com and install in order (client, node and free server). The only problem I had was then going back to the freenx; I had to manually clean out the directory.

Or try a new post in the networking forum.

---

### Post by kevdog on 2007-05-29
> 
It might be worth trying the nomachine server, remove everything then down load the .debs from nomachine.com and install in order (client, node and free server). The only problem I had was then going back to the freenx; I had to manually clean out the directory.


I can tell you I didnt install them in that order.  I did freeserver, node and then client.  So maybe that is the problem.  Worth a shot since it isnt running in the first place.  

> 
I also installed directly from the seveas repos. I did not modify the sshd_conf, I just "sudo dpkg-reconfigure freenx" and selected the nomachine keys.


One thing I dont get is this.  The nomachine public key is kept under authorized_keys2.  My sshd_config file states:

AuthorizedKeysFile authorized_keys

Wont this cause a problem??? For my resolution I simply copied the nx authorized_keys2 file to authorized_keys in the same directory and everything worked.  Strange you didnt have to do this.. Hmm

Ill clean out everything and restart -- What the hell!

---

### Post by kevdog on 2007-05-29
I see the order of the package installation you give me, but if I look at the seveas repositories I dont see any package called nxnode (such as on the no machine website).  Do I need all the packages from the seveas repository in order for freenx server/client to work??

[http://seveas.ubuntulinux.nl/dists/feisty-seveas/freenx/](http://seveas.ubuntulinux.nl/dists/feisty-seveas/freenx/)

---

### Post by kevdog on 2007-05-29
Screw This!!!

This is totally ridiculous.  Followed instructions on [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) -- which of course were not complete.

If anyone has successfully installed freenx on feisty using only seveas repository executables -- I would like to here about it.  It certainly doesnt work for me.  And there is nothing in the logs that help me.  

Here is all I can find in the client logs --
Loop: WARNING! Disabling NX delta compression.
Loop: WARNING! Disabling use of NX persistent cache.
Proxy: PANIC! No response received from the remote proxy on FD#9 while waiting for the shutdown.
Killed by signal 15.

Whatever any of that means!!

---

### Post by Austin_KW on 2007-05-30
The order was only important when installing the nomachine.com (.debs) and these do not automatically resolve dependancise.

One of my ubuntu PCs sshd_conf has "#AuthorizedKeysFile     %h/.ssh/authorized_keys" This implies that it is looking for authorized_keys but it is not. It is actually looking for authorized_keys2 (I assume that this goes with the protocol version). The line is commented anyhow so has no effect

My other PC has the line uncommented and changed to "AuthorizedKeysFile     %h/.ssh/authorized_keys2" 
Either way appears to work.


I still think you problem is the connections to the proxy on port 5000. Are you sure that you have no filters in place. Try "sudo iptables -F" to flush all the rules.

---

### Post by Arisna on 2007-05-30
I have a working FreeNX server on my Feisty box with Seveas packages.  To do this, I added the repository to my apt sources and then used my package manager to install the package "freenx."  Dependencies were dragged in automatically.

Next, I modified /etc/nxserver/node.conf to tell NX my ssh port.

Also on the subject of ports, I forwarded my SSH port to my computer on my router.  I also forwarded ports 1000-1100, which I believe NXServer needs.  This, obviously, would not matter on the LAN, however.

When I connected through localhost or the LAN, the default settings on nxclient for Windows or the GNU/Linux version available through seveas were sufficient.  When I went over the WAN, I had to enable SSL encryption to make it work.

Note that I did not do anything as far as generating/copying keys.  I am unsure after reading this thread whether I should have done so as a security measure or not.  Possible security concerns aside, this setup is fully functional.

---

### Post by kevdog on 2007-05-30
Look I appreciate the help from all, I was successful in getting it up and running but it took a lot of work. 
The problem really boiled down to the xserver not being able to find the appropriate font.  After enabling the level 7 error logs within the server, I kept finding this error - could not open default font 'fixed'.

I first found that the FontPath variables located in my xorg.conf were all wrong.  (Never had a problem with this before even though the paths were set with the installation disk!).  I changed them.

This however did not really change the situation.
I finally modified the server configuration (node.conf)  adding the following line:

AGENT_EXTRA_OPTIONS_X="-fp /usr/share/fonts/X11/misc/"

That was basically the solution.

My only last question, (someone commented on it before) was to know what ports to open up on the router.  Obviously port 22 (or the ssh port) needs to be forwarded, but are their any other ports that need to be opened beyond 22.  I would really like to limit the number of ports opened if possible.  

Once I get the server tested, I would like to write a "how-to or tips and tricks" for ubunutu users since documenation on the whole process is extremely sparse, the posts contained within the ubuntu forums specifically address Dapper and the nomachine debs (not the opengl seveas repositories), and really contain no useful tips if the default installation does not succeed.

Port assignment is my last major hurdle.

---

### Post by kevdog on 2007-06-04
OK I answered my own question -- if you tunnel your freenx connections through ssh -- only port 22 or the ssh port needs to be open on the router.  Nothing more!

---

### Post by dasbooter on 2007-06-04
Way to go Kevdog. I have been following this thread closely nice to see it is working for you finally. Nice trouble shooting I have to admit I probably would have given up myself. I am just switching over from a Suse installation in which installing freenx with your own keys was pretty simple hopefully I can get through this with no problems. Still If I have a similar problem I will be back :)

---

### Post by dfreer on 2007-06-26
Sorry to barge in on this thread here, but I want to see if I understand things correctly. First, here's what I've done so far:

I just finished setting up x11vnc over ssh, and am disatisfied with the performance although it is quite secure.
Basically, I just set up a standard ssh server, login in from the client with ssh -X, and once logged in I run the **server's** copy of vncviewer like so:
```
vncviewer localhost
```
the x11vnc server will only listen to connections from localhost, which heightens security even more. All sound is output to the server's speakers, and it does not have seperate sessions (the server and client share the same session). But all data is sent over port 22, and no other port needs to be opened.

So how does FreeNX differ, other than the speed increase that sounds quite awesome. From what I read, in this thread and others, is that it defaults to using port 22. 
(1) But it may need other ports opened as well? What are those ports for, and are they secure? 
(2) Will I need client software installed specifically for my ubuntu client, or can I use client software on the server similiar to vncviewer? 
(3) Can you have seperate sessions (two different users logged in on seperate accounts, seeing seperate desktops), and/or shared sessions (helping one user by controlling their desktop)?
(4) Can you use local client devices (speakers, cd drives) with the remote desktop?

I want to make a good guide, but unfortunately I don't know enough yet :D

---

### Post by kevdog on 2007-06-28
Ive posted a guide on how to setup the FreeNX server -- its in the tips and tutorial section.  It should help you.

Ive used FreeNx -- I like it -- better than VNC -- but I dont use it alot.  So hopefully I can answer your questions

1. If you tunnel FreeNX -- you dont have too -- only port 22 needs to be open or the port you run ssh over.  Nothing more.

2.  You will need client software -- its similar to VncViewer.  The client software is free.  Viewer platforms are unix, mac, windows.  The client software if available from the NoMachine website.  Supposedly there is some way to get FreeNx running through http or a web browser.  Ive done that with VNC but not FreeNx.  Ive always found the client software to be faster.

3.  As far as I know, FreeNx is only for separate sessions.  I was hoping it would be for same sessions, but havent found a way to do that.

4. I dont know the answer to this question since I havent tried.   Wish I could tell you more!!

From the history of this post, you can tell it was a struggle for me to set it up, because there was no good information available.  Like anything, now that I know how to do it, it wouldn't take me 15 minutes to get the server up and running.  Take a look at my guide.  I think it gives good debugging steps along the way.  Sorry I dont have the link for it -- its in the Tips and Tutorials section

---

### Post by dfreer on 2007-06-29
[http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219) for anyone following me.
The main thing for my is VNC is proving too slow, although I didn't try using the tightvnc viewer or anything like that.

(2). Yeah, supposedly according to FreeNX website you can embed a client in a web page, I assume for making an HTTP frontend for a virtual machine server. Nice idea.

Thanks for the how-to, I'll be checking it out and if I have any problems I'll post them in there!

---

### Post by kevdog on 2007-06-29
If you can figure out how to embed on a HTTP page, I will definitely add it to the tutorial.  I struggled for a long time to get the server up and running, so once I achieved that goal, I didnt pursue any "optional" accessories

---

### Post by bandoba on 2007-07-20
> **kevdog said:**
> Look I appreciate the help from all, I was successful in getting it up and running but it took a lot of work. 
The problem really boiled down to the xserver not being able to find the appropriate font.  After enabling the level 7 error logs within the server, I kept finding this error - could not open default font 'fixed'.

I first found that the FontPath variables located in my xorg.conf were all wrong.  (Never had a problem with this before even though the paths were set with the installation disk!).  I changed them.

This however did not really change the situation.
I finally modified the server configuration (node.conf)  adding the following line:

AGENT_EXTRA_OPTIONS_X="-fp /usr/share/fonts/X11/misc/"

That was basically the solution.

My only last question, (someone commented on it before) was to know what ports to open up on the router.  Obviously port 22 (or the ssh port) needs to be forwarded, but are their any other ports that need to be opened beyond 22.  I would really like to limit the number of ports opened if possible.  

Once I get the server tested, I would like to write a "how-to or tips and tricks" for ubunutu users since documenation on the whole process is extremely sparse, the posts contained within the ubuntu forums specifically address Dapper and the nomachine debs (not the opengl seveas repositories), and really contain no useful tips if the default installation does not succeed.

Port assignment is my last major hurdle.

Hi kevdog,

I had faced similar problems and finally I was frustrated and gave it up. But now I am back to trials. I just found this thread and saw your above post. I tried adding that option and restarting NXserver but I still see same error as before.

I have not copied authorized_keys2 file to my home/.ssh folder. I believe that must be causing this issue. But before I copy that I was wondering what shall I do with my existing authorized_keys file. Shouldn't these two files be merged together?

Also it seems to me that you made 2 changes
1. Updating node.conf as mentioned above
2. Copying authorized_keys2 file as you mentioned in previous posts 

Can you confirm?

Thanks!

---

### Post by bandoba on 2007-07-20
Hello,

After reading kevdog posts again, I realized that he is talking about copying /var/lib/nxserver/home/.ssh/authorized_keys2 file to authorized_keys file in the same folder and not to his home folder/.ssh. So I tried that, actually I created soft link instead of copying and got NX working.

I then remove the AGENT_EXTRA_OPTIONS_X="-fp /usr/share/fonts/X11/misc/" line from node.conf file and NX connection worked fine.

Hope this helps.

BTW, I observed that when I connect from Windows NX client, the session was very slow. I then changed communication preferences to Modem instead of LAN (even though both machines are on same LAN) and it worked like a charm.

Thanks to kevdog again! I feel like back in business.

PS: I checked "Enable Multimedia" and the sound worked too! Wow, it is just amazing to see FreeNX working with so much speed.

---

### Post by kevdog on 2007-07-24
Ive documented my working setup in a How-To.  Hopefully this will help anyone else because I had a hell of a time getting this thing working.  Once I did however, I really liked it.  Works a lot faster than VNC.

[http://ubuntuforums.org/showthread.php?t=467219&highlight=freenx+server+feisty](http://ubuntuforums.org/showthread.php?t=467219&highlight=freenx+server+feisty)

---

