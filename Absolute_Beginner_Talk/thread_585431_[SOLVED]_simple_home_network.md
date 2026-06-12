---
title: "[SOLVED] simple home network?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by mikeize on 2007-10-21
[SOLVED]

Here's the situation:  I have an ubuntu desktop connected to a router via ethernet cable.  I have two laptops (one xp and one ubuntu) connected wirelessly to the same router.  My internet is served by my university so they have some sort other router between me and the internet as well I guess.

What I want:  filesharing (omnidirectional!).  I don't understand "mounting shares" but it doesn't sound like something I want to do.  Essentially, I would like to see a folder representing the other two computers, from which I can browse, copy to/from my designated folders.

I want this to work automatically (either always connected, or connect with a double-click and admin pword)-- ie with WPA protection.

A MAJOR bonus would be the ability to connect to my desktop remotely (away from home).

My status:  I think I've read all the tutorials for various methods on these forums and many elsewhere.  I haven't been able to share a single file-- but now I wonder if my settings are all wacked from all these failed networking attempts.

Sorry for the long post, but I want to be clear about my situation/desire.  I am not looking for another dense, 2-3 page "easy way" tutorial, lol.  If there's no simple way then there's no simple way, and I'll just keep hoping for someone to write the ubuntu home networking wizard.

-mike

---

### Post by HermanAB on 2007-10-21
First of all, it is not easy.  It requires a certain amount of familiarity to get networking of any kind to work.

Secondly, you have to pick a file sharing protocol:
a. Samba
b. NFS
c. FTP
d. SSH

Windows, by default uses SMB (Samba).  However, Windows can also do NFS and  FTP.

If you want to have a secure system, then you have to use SSH, since it is encrypted.  SSH also contains SFTP, a secure kind of FTP.

If you wish to have the same system all around, then you should go to Sourceforge.net and get FileZilla server and client and install it on each machine, then you can go nuts with FTP.

Cheers,

Herman

---

### Post by mikeize on 2007-10-21
Thanks, but this doesn't tell me anything I don't already know.  I've tried using tutorials for each of these methods, and can't get any of them to work.  What is the fundamental reason why no one has come up with a simple method of doing this?  I'm guessing security, but I can't understand why sufficient encryption/passwords/certificates shouldn't be enough.

Just frustrated.  Though I never tried this hard with windows, I couldn't figure that out either!  The best I could do was a program called avvenu (which was awesome, frankly), but I can't find anything like that for ubuntu, and it won't work with wine.

Guess I'm sol until I meet an ubuntu guru who will come to my house and set it up for me.

-mike

---

### Post by Mondoman on 2007-10-21
Mike, did you try the Filezilla suggestion above?

---

### Post by mikeize on 2007-10-21
I can't remember if I tried filezilla, but I did try an ftp solution.  I got to where I had the ftp folders mounted and showing on my desktop, but I couldn't share anything.  I don't know if the computers were connected or not --and that was just between the two ubuntu computers-- I didn't try involving my wife's xp laptop.  I'll take a look at filezilla, but I can't manage optimism at this point.
Thank you though, I would like to solve this.

-mike

---

### Post by mikeize on 2007-10-21
... on to the filezilla tutorials!  I'll post back my results.

-mike

---

### Post by bodhi.zazen on 2007-10-21
> **mikeize said:**
> Thanks, but this doesn't tell me anything I don't already know.  I've tried using tutorials for each of these methods, and can't get any of them to work.  What is the fundamental reason why no one has come up with a simple method of doing this?  I'm guessing security, but I can't understand why sufficient encryption/passwords/certificates shouldn't be enough.

Just frustrated.  Though I never tried this hard with windows, I couldn't figure that out either!  The best I could do was a program called avvenu (which was awesome, frankly), but I can't find anything like that for ubuntu, and it won't work with wine.

Guess I'm sol until I meet an ubuntu guru who will come to my house and set it up for me.

-mike

Pick a protocol, stay with it, ask for help with a more specific question.

I would advise samba if you share with windows

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by HermanAB on 2007-10-21
Well, laak ah sed - it ain't easy.  

There are lots of things that can be wrong with your setup:
Windows may be running a firewall.
Linux may be running a firewall.
Linux may be running tcpwrappers too.
The machines may be on different subnets.

So, you need to clue yourself up on networking and firewalls in general first and if you cannot ping and telnet from one machine to another then nothing is going to work until you fix the networking first.

When playing with firewalls:
SSH runs on port 22.
FTP runs on port 21 and a random high port.
NFS runs on port 2049 and a random RPC port.
SMB runs on ports 135-139 and 445, but it can run on port 445 only in a pinch.

The easiest one of the lot to get to work is SSH, but SSH has different solutions on Windows and Linux.

FTP has similar tools on Windows and Linux, so that is the one I suggest to try first for anything to anything file sharing.

So, if you are hell bent on using Ubuntu, then you need to invest some time in this and it will be time well spent.  There is no single magic bullet.  The problem is that Ubuntu is *not* the simplest Linux out there - it is middle of the road, the beige minivan of Linux - not the simplest and not the hardest.

The only simple solution is to quit Ubuntu and install Mandriva Linux, since it has wizards for everything, including Windows file sharing, SSH and FTP servers: [http://torrent.mandriva.com/public/](http://torrent.mandriva.com/public/)

Cheers,

Herman

---

### Post by mikeize on 2007-10-21
whoops double post

---

### Post by mikeize on 2007-10-21
thanks bodhi and herman,

filezilla sure looks easy, at first...  but yeah, I don't know anything about networking etc, so even running the setup wizard is too complicated for me.  I get errors on the test at the end **(the server sent an unrecognized reply)**.  Neither machine is (currently) running a firewall, and both are on the same subnet, and as far as I can tell neither lists tcpwrappers (I don't know what that is) as a running process.  Both have similar (sequential) ip addresses, and identical broadcast, default route and primary dns addresses.  

Don't get me wrong, I'm really enjoying ubuntu, and I've already learned a lot about it.  Of course I've spent a fair amount of time banging my head on the desk trying to figure out some problem.  My level of interest for starting over with a third OS is practically nil, lol.

If I can't get this to work, well I'll just keep using flashdrives to transfer files and check from time to time on the progress being made in this area.

-mike

---

### Post by HermanAB on 2007-10-21
OK cool, first get Filezilla Server to run on Windows.  That should be easy.

Now open a DOS box and check it out to make sure it really is working:
c:\> telnet localhost 21

If you get connection refused then FileZilla is NOT running.

Once telnet gets a prompt also try the Windoze ftp client:
c:\> ftp localhost

If it won't work from Windows itself, then there is no hope in hell that it will work from another machine...

Now, mosy on over to the Ubuntu machine and repeat the above:
$ telnet windozeipaddress 21

If that doesn't work, then you have a firewall problem.

If it works, try the Linux ftp client:
$ ftp windozeipaddress

If that works, then you are in business and can go graphical, either with FileZilla client, gftp or konqueror.

Once it works you can try to get a FTP server running on Linux, either FileZilla server, vsftpd or proftpd.

'Hope that helps!

Herman

---

### Post by HermanAB on 2007-10-21
Note that FTP, Samba and NFS are *insecure* and should only be used on a LAN.  If you wish to use file transfer over the internet, then you should use SSH for best security.

You can use FTP over the internet if you follow a few basic precautions:
1. Use a different username and password for FTP only and be sure that the password is very long >9 characters.  This username and password is sent in plain text over the net so it is easy to sniff anywhere along the wire.
2. Limit FTP to two separate directories, one for upload and the other for download.  This way, someone cannot set up a porn cache on your machine, since one cannot download whatever has been uploaded!  If you need to share files and need a read/write directory, then be sure to check it regularly for abuse.
3. For further security, you could run FTP on a non-standard port, for example 2121.  This simple trick will throw most script kiddies off, since most script kiddies are stupid, however it is not the stupid ones that you need to worry about.

Cheers,

Herman

---

### Post by dwhitney67 on 2007-10-21
I can't help you with your Windows machine, but concerning your two Ubuntu systems, can you please do the following:

1)  Obtain the IP addresses that each is assigned.  Run this command on each system:  */sbin/ifconfig*

2)  Have each system ping each other.  The command for that is *ping [IP address]*

3) Once you have verified that the systems "see" each other on the network, install the SSH package onto each system.  To do that, run:  *sudo apt-get install ssh*

4)  Verify that the SSH-daemon is running on each system with this command:  *ps -ef | grep sshd*

5) Attempt to connect via SSH from one system to another, using this command:  *ssh userid@othersystem*, where the *userid* is a _valid_ login ID on the remote system and *otherSystem* is the IP address of the remote system.

You will be prompted for a password when you run step 5.  You should enter the password of the account on the remote system.

Btw, it might be easier if you assign aliases for your machines so that you do not have to remember their IP addresses.  Aliases are inserted in the /etc/hosts file, which requires root (or sudo) privileges to edit.  A typical entry in the /etc/hosts table might look like:
[INDENT]
[FONT="Courier New"]desktop <tab> 192.168.1.100[/FONT][/INDENT]

If none of the information above works for you, then I'm am at a loss.  Setting up SSH is not rocket science.  If nothing works, then perhaps you can shed some light (e.g. post error messages) so that someone can assist you in resolving your system's problem(s).

P.S.  Here's the [official guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server") on how to setup SSH on Ubuntu.  I believe there is some info concerning how to setup stuff on the Windoze machine.

---

### Post by mikeize on 2007-10-21
Thanks for taking the time to help me.

i've been messing with port forwarding stuff, with no success-- the only thing that changed was that the 'test' in filezilla took a really long time... and then failed.

@dwhitney:

my ubuntu laptop pings my desktop (i think, there was an infinite list of results), but trying to ping the laptop from my desktop returns:  

```
ping: icmp open socket: Operation not permitted
```

-mike

edit:  for the heck of it, i tried to ssh from my laptop to the desktop, but the connection timed out

---

### Post by R_U_Q_R_U on 2007-10-21
I have been using Ubuntu Linux for only a few months (that is my total Linux experience) and was able, with a  little work, to get my XP and Ubuntu boxes talking.

I know the OP said he did not want to read but these two threads are as easy as it gets and I KNOW they work. One thing, make sure your Linux firewall is setup to accept incoming from all machines on your home network. The rule should be 192.168.1.1/24 or whatever your internal IP's are.

Read this for Samba:

[B]HOWTO: Setup Samba peer-to-peer with Windows : [http://ubuntuforums.org/showthread.php?t=202605&highlight=how+to+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=how+to+samba)

[/B] and this for NFS:

**HOWTO: NFS Server/Client:**
[B][http://ubuntuforums.org/showthread.php?t=249889&highlight=how+to+NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=how+to+NFS)


[/B]These two articles should solve your problem.

---

### Post by mikeize on 2007-10-21
I tried these tutorial threads and couldn't get anything to work.  I know, I know, I must be completely stupid-- I've long suspected it, but simply insisting that these instructions are a clear map to success doesn't change the fact that they are beyond my abilities.  Incidentally they aren't 70 pages of "thanks this worked"!

-mike

edit:  so I figured out, that from my desktop I have to do sudo ping [ipaddress]

---

### Post by mikeize on 2007-10-21
dwhitney,

so I can sudo ssh from desktop into laptop, but only command line.  Two questions:
can I do this as a regular user somehow?, and is there a graphical method (nautilus) of accessing the other computer?

Thanks for your help!

-mike

---

### Post by magli on 2007-10-21
Using SCP is extremely easy. The only thing you will not be able to do is connect to a windows machine from a linux machine. (But you could set upa samba share with windows which would allow you to do that with relative ease.)

Using SCP:
One both of your ubuntu machines, install the SCP server with this command:
```
$sudo apt-get install openssh-server
```
Now, assuming you are using gnome, go to "Places->Connect To server" Select SCP, and enter the IP/Username/password of the machine you are want to connect to. It will then create a shortcut on your desktop, giving you quick access to that machine over scp.

For the windows machine, you can install winscp:
[http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

It really isn't that hard.

---

### Post by dwhitney67 on 2007-10-21
The "ssh" command is definitely a command-line interface.  If you want graphical, look in **Places -> Connect to Server...**

I have not personally used that interface in a while (I prefer the command-line), but I believe it is intuitive to set up.

Btw, you should not have to use "sudo" to run ssh, scp, or even ping.

---

### Post by mikeize on 2007-10-21
> **HermanAB said:**
> 

Now, mosy on over to the Ubuntu machine and repeat the above:
$ telnet windozeipaddress 21

If that doesn't work, then you have a firewall problem.

Herman

Everything works up to this step, and it just hangs.  I have firewalls disabled on both machines!  Arrgh!

---

### Post by mikeize on 2007-10-21
> **magli said:**
> Using SCP is extremely easy. The only thing you will not be able to do is connect to a windows machine from a linux machine. (But you could set upa samba share with windows which would allow you to do that with relative ease.)

Using SCP:
One both of your ubuntu machines, install the SCP server with this command:
```
$sudo apt-get install openssh-server
```
Now, assuming you are using gnome, go to "Places->Connect To server" Select SCP, and enter the IP/Username/password of the machine you are want to connect to. It will then create a shortcut on your desktop, giving you quick access to that machine over scp.


I go to Places>Connect to server>... there is no SCP option.  I already have openssh server installed.  

@ dwhitney:  I can't ping without using sudo, but I can SSH.  probably something I messed up in the long course of trying to sort this mess out.

-mike

---

### Post by magli on 2007-10-21
> **mikeize said:**
> I go to Places>Connect to server>... there is no SCP option.  I already have openssh server installed.  
Sorry - select the "SSH" option, not "SCP".

---

### Post by ginestre on 2007-10-21
I didn't have any problems with a small network (3 ubuntu connected to the router via cable, 1 laptop windows me via wireless and one win98 via cable). It sort of worked out of the box. All I did was
1) install ssh server on the ubuntu machines, and 
2) set up (via connect to server->ssh->IPaddress) connecctions to teh ubuntu machines
and 3) set up windoes share connetions (via connect to server->windows share -> ip address)

I don't know if it's relevant but username and password are the same on all machines. But it just worked.

---

### Post by mikeize on 2007-10-21
> **magli said:**
> Sorry - select the "SSH" option, not "SCP".

holy ****.  it worked!  well actually, it works desktop-->laptop, but hangs in the other direction.  "Opening "ipaddress" you can stop by pressing cancel."  and then nothing.
almost there!

-mike

---

### Post by magli on 2007-10-21
Are you sure you installed openssh-server on your desktop?

Also, you may be intersted in a tool called "nmap" - it can scan ports on a computer, and tell you what services are running.
```

$sudo apt-get install nmap
$nmap DESKTOP_IP

```
Will, for example, tell you if ssh is running

---

### Post by mikeize on 2007-10-21
Thank you, I got nmap, and ssh is running.  I also have netbios-ssn and microsoft-ds running.  I suspect these may be left overs from other (failed) attempts at networking.
But I don't know if they are causing any trouble.

-mike

---

### Post by magli on 2007-10-21
That is strange - if you have ssh running but simply cannot connect.. I doubt that the other services would be causing any problems. I suggest you try connecting via the command line: it may give you more feedback. 
```
$ssh username@DESKTOP_IP
```
Make sure to enter the user name for the account on the dektop computer. It will prompt you for your password, and then ask you a question about keys, to which you have to accept.

As for the netbios-ssn and microsoft-ds which are running.. I think that they indicate that a samba share is running. Just out of curiosity, try this:
```
$smbclient -L DESKTOP_IP
```
It will prompt you for a password, which you should be able to leave blank (just hit enter). With some luck, it may list any samba shares on your dektop. You can also try this with your windows box ip address if you have shares on that.

---

### Post by rudeboyskunk on 2007-10-21
I'm not sure if this is the solution you're looking for, but I always used Samba.  It was pretty easy, and it's what Windows uses.

The way I did it was in Windows I would right click on a folder, go to "Properties," and make sure I allowed it to be shared on the network.  Then, under Ubuntu, any folder I wanted shared on the network, I could go to System>Administration>Shared Folders, and add the folder to that.  To get on the network in Windows, I would go to "Network Neighborhood" and in Ubuntu I would go to "Network Places."  I always named my network "mshome" for simplistic reasons.

It sounds as if you've tried that though, if you've tried all the different "howto"s and tutorials out there.

---

### Post by mikeize on 2007-10-21
ssh from commanline is the same:  simply times out

smbclient -L:  timeout, timeout, error connecting (operation already in progress), failed

I feel like maybe it's connecting to a blocked port (it says 22), but I'm not sure, and I don't know how to check/fix it.

-mike

---

### Post by _oOMOo_ on 2007-10-21
Hi mikeize, have you set your router to allocate the same IP address to your computers whenever they connect?

---

### Post by mikeize on 2007-10-21
> **rudeboyskunk said:**
> I'm not sure if this is the solution you're looking for, but I always used Samba.  It was pretty easy, and it's what Windows uses.

The way I did it was in Windows I would right click on a folder, go to "Properties," and make sure I allowed it to be shared on the network.  Then, under Ubuntu, any folder I wanted shared on the network, I could go to System>Administration>Shared Folders, and add the folder to that.  To get on the network in Windows, I would go to "Network Neighborhood" and in Ubuntu I would go to "Network Places."  I always named my network "mshome" for simplistic reasons.

It sounds as if you've tried that though, if you've tried all the different "howto"s and tutorials out there.

yeah, I've tried samba and I still have the vestiges of it on at least one of my machines.  I couldn't get it to work either.  I think I have one problem that prevents any of these from working, but I don't know how to diagnose it, so they all fail.  I bet once I get one to work, they'll all work.

-mike

---

### Post by mikeize on 2007-10-21
> **_oOMOo_ said:**
> Hi mikeize, have you set your router to allocate the same IP address to your computers whenever they connect?

I'm pretty sure they do this, but I don't think I set it that way.  For example, my laptop dual boots, and keeps the same IP address across boots (though it is wubi).  I just have barely gotten my feet wet with configuring my router.

-mike

---

### Post by magli on 2007-10-21
If both ssh and smbclient timeout, it would seem that you are having a more basic networking problem. Can you ping your desktop? You said you were able to scan the ports using nmap - if you can, and nmap lists port 22 (ssh) as open, but you cannot connect to it.... then I am stumped.

---

### Post by mikeize on 2007-10-21
> **magli said:**
> If both ssh and smbclient timeout, it would seem that you are having a more basic networking problem. Can you ping your desktop? You said you were able to scan the ports using nmap - if you can, and nmap lists port 22 (ssh) as open, but you cannot connect to it.... then I am stumped.

Yes, I can ping my desktop, and running nmap on both machines shows port 22 as open (ssh).  Desktop can ssh to laptop, but laptop times out when attempting ssh to desktop.


-mike

---

### Post by _oOMOo_ on 2007-10-21
If all three maintain IP addresses then you should be ok but if you haven't specifically set it up then ssh will be a nightmare if the router allocates different IPs on reboots / out of signal ranges etc.

There's a handy bit of freeware called winscp which you can use to connect to the Ubuntu boxes from windows over ssh.

If you want to connect to your desktop from the net you'll need to dig around in the router to set up port forwarding :)

---

### Post by magli on 2007-10-21
Does your router have a DMZ port on it? If so, it would probably be physically indicated on it.

Otherwise, check the contents of your "/etc/hosts.allow" and "/etc/hosts.deny" files on the desktop computer. These files can be used to restrict access to only certain machines. However, I do not think this is the problem, as I would have expected that you would get a connection refused, not timeout if this were the case. Worth a look though.

---

### Post by mikeize on 2007-10-21
> **_oOMOo_ said:**
> If all three maintain IP addresses then you should be ok but if you haven't specifically set it up then ssh will be a nightmare if the router allocates different IPs on reboots / out of signal ranges etc.

There's a handy bit of freeware called winscp which you can use to connect to the Ubuntu boxes from windows over ssh.

If you want to connect to your desktop from the net you'll need to dig around in the router to set up port forwarding :)

Okay, I'm sure that my desktop at least has a permanent (static?) IP.  To clarify port forwarding...  I set my router to forward port 22 to the IP address of my desktop, correct?

-mike

---

### Post by magli on 2007-10-21
You are correct on the port forwarding. However, you are probably behind a university firewall of some sort, and you would have to be able to forward port 22 from their router/firewall to your router in order to have access from the internet. I doubt they allow that.

---

### Post by mikeize on 2007-10-21
> **magli said:**
> Does your router have a DMZ port on it? If so, it would probably be physically indicated on it.

Otherwise, check the contents of your "/etc/hosts.allow" and "/etc/hosts.deny" files on the desktop computer. These files can be used to restrict access to only certain machines. However, I do not think this is the problem, as I would have expected that you would get a connection refused, not timeout if this were the case. Worth a look though.

It doesn't have a physical DMZ port, but it does have DMZ configuration options.  The hostsallow/deny files look fine to me, but then, I don't know what to look for! lol.  every line is commented anyway.

-mike

---

### Post by dwhitney67 on 2007-10-21
> **mikeize said:**
> @ dwhitney:  I can't ping without using sudo, but I can SSH.  probably something I messed up in the long course of trying to sort this mess out.

-mike
Check the permissions set on the file /bin/ping.  It should look like this:
```
-rwsr-xr-x 1 root root 30848 2007-03-04 20:25 /bin/ping
```

---

### Post by _oOMOo_ on 2007-10-21
> **mikeize said:**
> Okay, I'm sure that my desktop at least has a permanent (static?) IP.  To clarify port forwarding...  I set my router to forward port 22 to the IP address of my desktop, correct?

-mike

Yes, if you're hot on security you can forward a much higher non-standard port (>10000) and alter /etc/ssh/sshd_config on your desktop to accept this new high port (you just add another port entry under the existing port 22 line). This way all local traffic is on 22 but incoming is only on the non-standard port.

Maybe try reinstalling openssh-server on the desktop? Seems very odd it isn't responding.

---

### Post by mikeize on 2007-10-21
> **dwhitney67 said:**
> Check the permissions set on the file /bin/ping.  It should look like this:
```
-rwsr-xr-x 1 root root 30848 2007-03-04 20:25 /bin/ping
```

I can't open /bin/ping -- it's not a text file and gedit won't open it.  double-click ... nothing.

-mike

---

### Post by magli on 2007-10-21
Are you familiar with DMZ? That *could* be your problem. I am not that sure about it, but I think that DMZ can allow you to make a given computer inaccessible from the other computers on your network. The idea being that if you have one computer accessible from the internet, and somone were to hack into it, you do not want them to gain access to the other computers on your network through the hacked computer, so you set up the hacked computer to be in a DMZ. You want to make sure that you do not have any DMZ configured.

---

### Post by magli on 2007-10-21
> **mikeize said:**
> I can't open /bin/ping -- it's not a text file and gedit won't open it.  double-click ... nothing.

```
$ls -l /bin/ping
```

to check permissions

---

### Post by mikeize on 2007-10-21
> **_oOMOo_ said:**
> Yes, if you're hot on security you can forward a much higher non-standard port (>10000) and alter /etc/ssh/sshd_config on your desktop to accept this new high port (you just add another port entry under the existing port 22 line). This way all local traffic is on 22 but incoming is only on the non-standard port.

Maybe try reinstalling openssh-server on the desktop? Seems very odd it isn't responding.

I may well do that later, but right now I'll be happy to at least have "proof of concept" lol.  I will try reinstalling openssh-server.

-mike

---

### Post by mikeize on 2007-10-21
> **magli said:**
> Are you familiar with DMZ? That *could* be your problem. I am not that sure about it, but I think that DMZ can allow you to make a given computer inaccessible from the other computers on your network. The idea being that if you have one computer accessible from the internet, and somone were to hack into it, you do not want them to gain access to the other computers on your network through the hacked computer, so you set up the hacked computer to be in a DMZ. You want to make sure that you do not have any DMZ configured.

DMZ is not enabled on my router.

---

### Post by mikeize on 2007-10-21
> **magli said:**
> ```
$ls -l /bin/ping
```

to check permissions

looks the same as your example except the date and 30856 instead of 30848.

-mike

---

### Post by mikeize on 2007-10-21
In my router options there are two "port forwarding" potentials:  one is "virtual servers" --this is the one I used to forward port 22 to my desktop... ...   and there is "special applications" which is for port triggering.  Would it be better to use that?

-mike

---

### Post by magli on 2007-10-21
Just for the hell of it, you should try sshing into your desktop, from your desktop:
```
$ssh localhost
```
That will at least narrow down the problem.

---

### Post by _oOMOo_ on 2007-10-21
> **mikeize said:**
> In my router options there are two "port forwarding" potentials:  one is "virtual servers" --this is the one I used to forward port 22 to my desktop... ...   and there is "special applications" which is for port triggering.  Would it be better to use that?

-mike

I think you have it right as it is. Have you tried the System > Administration > Network Tools GUI to port scan / ping your desktop?

---

### Post by mikeize on 2007-10-21
> **magli said:**
> Just for the hell of it, you should try sshing into your desktop, from your desktop:
```
$ssh localhost
```
That will at least narrow down the problem.

works fine.

---

### Post by _oOMOo_ on 2007-10-21
one thing did occur to me - on my router there is a wireless isolation checkbox, which basically prevents computers connecting wirelessly from seeing others on the LAN - just a thought,

good luck!

---

### Post by dwhitney67 on 2007-10-21
When you are behind your personal firewall/router, you should not have to mess with anything.  You only worry about port-forwarding if you want access to one or more of your systems from the outside world.

If I were you, I would uninstall openssh-server (or ssh) on the bum machine, and then reinstall it.

By default, there should be nothing set on your Ubuntu system that would prevent you from allowing connections via port 22 once you have ssh-daemon running.... unless you configured something odd (say in /etc/inetd.conf).

If the permissions set on /bin/ping are the same as mine, then you definitely do not require "sudo" to use ping.  Please re-verify the IP addresses of both of your Ubuntu systems and your Windows system.  Also show us how you are using ping.  I hope it is merely like:  $ ping [ip-address]

---

### Post by mikeize on 2007-10-21
> **_oOMOo_ said:**
> I think you have it right as it is. Have you tried the System > Administration > Network Tools GUI to port scan / ping your desktop?

ping works, port scan... scanning... scanning... scanning ... (guessing it will timeout)

-mike

---

### Post by mikeize on 2007-10-21
> **_oOMOo_ said:**
> one thing did occur to me - on my router there is a wireless isolation checkbox, which basically prevents computers connecting wirelessly from seeing others on the LAN - just a thought,

good luck!

That sounds promising, but I can't find anything that is clearly that in my options.

---

### Post by mikeize on 2007-10-21
> **dwhitney67 said:**
> 
If the permissions set on /bin/ping are the same as mine, then you definitely do not require "sudo" to use ping.  Please re-verify the IP addresses of both of your Ubuntu systems and your Windows system.  Also show us how you are using ping.  I hope it is merely like:  $ ping [ip-address]

mike@u-desktop:~$ ls -l /bin/ping
-rwsr-xr-x 1 root root 30856 2007-07-06 03:40 /bin/ping
mike@u-desktop:~$ ping 1**.1**.1.*6
ping: icmp open socket: Operation not permitted
mike@u-desktop:~$ sudo ping 1**.1**.1.*6
PING 1**.1**.1.*6 (1**.1**.1.*6) 56(84) bytes of data.
64 bytes from 1**.1**.1.*6: icmp_seq=1 ttl=64 time=1.99 ms
64 bytes from 1**.1**.1.*6: icmp_seq=2 ttl=64 time=1.65 ms
64 bytes from 1**.1**.1.*6: icmp_seq=3 ttl=64 time=1.35 ms
64 bytes from 1**.1**.1.*6: icmp_seq=4 ttl=64 time=1.59 ms

---

### Post by mikeize on 2007-10-21
reinstalled openssh server and client.  still no joy. :(
as for messing up some config file...  I don't know.  

-mike

---

### Post by Naipes on 2007-10-21
I don't know, but this video helped me.  It's really simple for a home network. 

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

For the machines networked via a router in their own workspace, behind the university firewall, that video should do to the trick.

However, connecting to your machines from outside of the university firewall is another story all together.  One I suspect might be hard to accomplish if the university's IT dept. knows what it's doing... and I suspect they might.

Good luck!

---

### Post by mikeize on 2007-10-21
> **Naipes said:**
> I don't know, but this video helped me.  It's really simple for a home network. 

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

For the machines networked via a router in their own workspace, behind the university firewall, that video should do to the trick.

However, connecting to your machines from outside of the university firewall is another story all together.  One I suspect might be hard to accomplish if the university's IT dept. knows what it's doing... and I suspect they might.

Good luck!

thanks, i've actually watched that before...  I think I have an underlying problem here that precludes me from connecting by any method.

-mike

---

### Post by dwhitney67 on 2007-10-21
I'm going to do a little research on your ping problem.  For now, please try running this command on your "bum" machine and report the results:

[FONT="Courier New"]$ sudo ssh remoteUser@remoteServerIP[/FONT]

P.S.  If you are behind a firewall/router, and your IPs are in the range of 192.168.1.xxx, there is no need to block them from the Ubuntu forum.  That is the typical IP address range provided by routers, and it is not accessible from the outside world.

---

### Post by mikeize on 2007-10-21
> **dwhitney67 said:**
> I'm going to do a little research on your ping problem.  For now, please try running this command on your "bum" machine and report the results:

[FONT="Courier New"]$ sudo ssh remoteUser@remoteServerIP[/FONT]

P.S.  If you are behind a firewall/router, and your IPs are in the range of 192.168.1.xxx, there is no need to block them from the Ubuntu forum.  That is the typical IP address range provided by routers, and it is not accessible from the outside world.

I'm not exactly sure what you mean by my "bum" machine...  From the desktop, I can ssh into the laptop with no problem.  From the laptop trying to ssh into the desktop, it just takes forever and then gives a timeout error.

As for blocking my IP address...  :oops:

---

### Post by mikeize on 2007-10-21
fwiw, from command line, I ssh'd into my laptop, and from there tried to ssh back into my desktop.  It just hangs like it does when I try it from my physical laptop, but it also causes "Gizmo" to restart.

---

### Post by dwhitney67 on 2007-10-21
Mikeize -

I looked briefly into the ping issue.  Most reported that their /bin/ping file was not configured correctly (with the sticky-bit set for root), however from what you reported that is not the case with your system.  Thus I am going to say that I am clueless.

As for your SSH problem, I was using "bum" to refer to your notebook PC that is unable to SSH over to the desktop.  Have to verified that your _desktop_ is running an SSH server?  Have you verified that your notebook's IP address is not listed in your desktop's /etc/hosts.deny file?

If you are able to verify all this, and still can't communicate from the notebook to the desktop, then once again I am stumped.  Btw, what is this "Gizmo" thing?

---

### Post by mikeize on 2007-10-21
here is my hostsdeny file:

```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
```

nmap: 

```
mike@u-desktop:~$ nmap 192.168.1.35

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-21 22:34 EDT
Interesting ports on 192.168.1.35:
Not shown: 1693 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap finished: 1 IP address (1 host up) scanned in 0.195 seconds

```

Gizmo is a VOIP program (gizmoproject).

Anything else I can post please ask.  I really appreciate you and everyone else who has taken the time to help me through this today.

-mike

edit:  I ran > ps -ef | grep sshd
 on both computers and sshd is running on both

---

### Post by _oOMOo_ on 2007-10-22
> **mikeize said:**
> ping works, port scan... scanning... scanning... scanning ... (guessing it will timeout)

-mike

Whoa - so you can ping the desktop, but even though you KNOW port 22 is open, it doesn't show up on a port scan? Also it looks like you don't need sudo to ping from the GUI(you shouldn't of course - but you seem to need it on the command line) - curioser and curioser!

It might pay to reset the router to default settings - if you can't see ANY open ports on the desktop that really is odd. If you try port scanning the laptop from the desktop you should see a couple open.

Another test you can try is to install winscp on the windows laptop and try connecting with that; just to try to narrow the problem down.

Jon

---

### Post by magli on 2007-10-22
This is indeed very strange. Here are a few thoughts:

How is your laptops IP address set up? Static or DHCP? What is it's IP address and subnet mask? If, for example, your IP address on the laptop is 192.168.1.1, and it's subnet mask is 255.255.255.0, then it would not be able to reach a machine with ip 192.168.2.1. (I think)

Also, maybe you want to try connecting your laptop to your router via a cable, and try connecting that way..

---

### Post by mikeize on 2007-10-22
Thanks, I will try your suggestions and post back in a few hours --gotta run to classes.  Thanks.

-mike

---

### Post by mikeize on 2007-10-22
Desktop:

IP address:                 192.168.1.35
Broadcast address:     192.168.1.255
Subnet mask:              255.255.255.0
Default route:              192.168.1.1
Primary DNS:               192.168.1.1
Secondary DNS:           0.0.0.0

Laptop:  (assigned by DHCP)

IP address:            192.168.1.36
Subnet mask:         255.255.255.0
Default gateway:     192.168.1.1
DHCP server:         192.168.1.1
DNS server:           192.168.1.1
WINS server:          192.168.1.35

Gonna wait before I reset my router, to see if this information can solve it.  Connecting to the router via ethernet cable, Ubuntu connects (xp doesn't, it's dual boot), but gets a slightly different IP address, ie,  192.168.1.37, and the other numbers match the desktop numbers.  Still can't ssh from laptop to desktop (long wait and timeout), even though plugged in -- but still CAN ssh from desktop to laptop (with .37 address).
Hope this helps someone to fix my problem!

-mike

---

### Post by magli on 2007-10-22
:confused:

---

### Post by mikeize on 2007-10-22
> **magli said:**
> :confused::lolflag:  me too.  Thanks for trying though!

-mike

---

### Post by dwhitney67 on 2007-10-22
Can you please explain your network setup again?  From what I understood, you have 3 systems:  a desktop running Ubuntu, a laptop running Ubuntu, and another laptop running Windows.

The desktop is hard-wired to the router, and your laptops are using the wi-fi interface.  Is that correct?

I think **magli** is correct in that you should temporarily connect your Ubuntu laptop directly to the router so as to eliminate one variable in the equation.

Btw, what system has the dual-boot WinXP?  I hope your not attempting to SSH to it.

Also, what router do you have?

---

### Post by mikeize on 2007-10-22
Okay, no problem...  my network is as follows:

University mediated internet plugs into my router via ethernet cable.  Desktop (ubuntu 7.10) is plugged into the router via ethernet cable.  My wife's laptop (xp) connects to the router via wifi, but I've been leaving her computer out of this whole thing.  My laptop is a dual-boot xp/ubuntu 7.04 which also connects via wifi.  I mostly use it as ubuntu at home, but at school I have to use as xp.  In general, when I refer to the laptop, I mean ubuntu, unless otherwise specified.
If you read my last post, I did try a hard connection, with no improvement...  and no, I haven't tried to ssh into xp. :)

-mike

edit:  router is a ZyXel P-330W

---

### Post by _oOMOo_ on 2007-10-22
The other interesting thing about ssh is that if it is apparent that the IP is not there at all, then it gives you this error:

```

:~$ ssh 192.168.0.7
ssh: connect to host 192.168.0.7 port 22: No route to host

```

but you get nothing at all....

Is it possible there is a rule set up in the router affecting port 22?

---

### Post by mikeize on 2007-10-22
I have this setting in "Virtual Servers" (port forwarding?) in my router settings, but that's the only one affecting that port.  Also, this is something I've done since I started this thread, so I'm pretty sure it's not the problem.

192.168.1.35 	TCP+UDP 	20-23      ssh


-mike

---

### Post by dwhitney67 on 2007-10-22
Ok, so to recap, your desktop has an IP address of 192.168.1.35, your laptop 192.168.1.36.  Both share the same for:  gateway = 192.168.1.1; broadcast = 192.168.1.255, and (net)mask = 255.255.255.0

The information above can be confirmed by running */sbin/ifconfig* on each system. 

Can the Ubuntu laptop ping the gateway (the router) at 192.168.1.1?  Have you reset the router by chance?  What kind of router do you have?

---

### Post by _oOMOo_ on 2007-10-22
I just had a look on the net and your "virtual servers" is indeed port forwarding as you thought, and as you say it shouldn't really bother LAN-only traffic. Hmmm *scratches head*.

---

### Post by mikeize on 2007-10-22
Desktop eth0 and laptop eth1 are as you noted (correct), except that this command does not display 'gateway' for either one.

and yes, I can ping the router from the laptop.

-mike

---

### Post by dwhitney67 on 2007-10-22
Just for grins, on your laptop, please run these commands:

$ cd
$ rm -rf .ssh
$ mkdir .ssh
$ ssh 192.168.1.35

If your account on the laptop differs from the one on the desktop, try this command instead when SSH-ing:

$ ssh desktopUser@192.168.1.35

If you still fail to connect, verify the contents of /etc/ssh/ssh_config on your laptop to be:
[PHP]
# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no[/PHP]

Then on your desktop, confirm that /etc/ssh/sshd_config appears as:
[PHP]# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
[/PHP]

---

### Post by mikeize on 2007-10-22
Okay, still couldn't connect so contents of /etc/ssh/ssh_config for laptop:

[PHP]# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes[/PHP]

desktop to follow.

-mike

---

### Post by mikeize on 2007-10-22
Desktop:

[PHP]
# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no[/PHP]


so is this backwards from your example?

---

### Post by _oOMOo_ on 2007-10-22
so is this backwards from your example?

Yes can you post the /etc/ssh/sshd_config file from the desktop? Cheers, Jon

---

### Post by mikeize on 2007-10-22
> **_oOMOo_ said:**
> so is this backwards from your example?

Yes can you post the /etc/ssh/sshd_config file from the desktop? Cheers, Jon

My last two posts were that file from my laptop and then desktop, respectively (sequentially).  I labelled them.  Or do you mean something else?

-Mike

---

### Post by _oOMOo_ on 2007-10-22
Hi Mike, yes you posted the/etc/ssh/ssh_config file, which is used by the client part of ssh; it is the /etc/ssh/sshd_config file which configures the server part.

Also did you say in an earlier post that you get some joy issuing nmap your.desktop.ip.address? For instance if I nmap my web server box I get:

```

:~$ nmap 192.168.0.6

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-22 22:06 BST
Interesting ports on 192.168.0.6:
Not shown: 1695 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Nmap finished: 1 IP address (1 host up) scanned in 14.904 seconds

```

Cheers

---

### Post by dwhitney67 on 2007-10-22
The **sshd_config** is the one on your **desktop**.  That is the system running the SSH-server.

The **ssh_config** is the one on your **laptop**, where the SSH-client is being used, and which is having trouble connecting to the server.

You don't need to post your files; just do a spot-check to ensure they are they same as the ones I posted.  I am just trying to eliminate potential issues.

---

### Post by mikeize on 2007-10-22
heheh, sorry, didn't catch that!

[PHP]# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes[/PHP]

and nmap on desktop...

```
$ nmap 192.168.1.35

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-22 17:21 EDT
Interesting ports on 192.168.1.35:
Not shown: 1693 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap finished: 1 IP address (1 host up) scanned in 0.266 seconds

```

---

### Post by magli on 2007-10-22
If I remember correctly, you were able to nmap your desktop, and it showed that samba was running. However, "smbclient -L DESKTOP_IP" also times out, right? Even if samba were not running, you should get a connection refused, not a timeout.

Do you get a timeout when trying to connect to FTP aswell?

---

### Post by mikeize on 2007-10-22
okay, sorry for the sloppiness, I previously posted the sshd for my laptop, here is the ssh file for the laptop:

> 
# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

also, I figure it's better for me to post the whole file, so that you guys have all the info, and also because I'm not sure what I'm looking at!  :)

-mike

---

### Post by magli on 2007-10-22
> **mikeize said:**
> 
```
$ nmap 192.168.1.35

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-22 17:21 EDT
Interesting ports on 192.168.1.35:
Not shown: 1693 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap finished: 1 IP address (1 host up) scanned in 0.266 seconds

```

Did you launch that from your desktop? If so, does it also work when you do it from your laptop? ie, the same command, but from the laptop.

---

### Post by mikeize on 2007-10-22
> **magli said:**
> If I remember correctly, you were able to nmap your desktop, and it showed that samba was running. However, "smbclient -L DESKTOP_IP" also times out, right? Even if samba were not running, you should get a connection refused, not a timeout.

Do you get a timeout when trying to connect to FTP aswell?


```
$ smbclient -L 192.168.1.35
timeout connecting to 192.168.1.35:445
timeout connecting to 192.168.1.35:139
Error connecting to 192.168.1.35 (Operation already in progress)
Connection to 192.168.1.35 failed
~$ 

```

what's the code for testing ftp?

-mike

---

### Post by mikeize on 2007-10-22
> **magli said:**
> Did you launch that from your desktop? If so, does it also work when you do it from your laptop? ie, the same command, but from the laptop.

Yes, that was from the desktop.  Here is the same command (and IP) from the laptop:

```
~$ nmap 192.168.1.35

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-22 17:31 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 3.046 seconds
~$ 

```


-mike

---

### Post by magli on 2007-10-22
OK. Your problem is clearly beyond ssh alone. I think that in an earlier post, you said that you were able to ping your desktop. Did you do this from your laptop?

On your laptop, type:
ping 192.168.1.35

---

### Post by _oOMOo_ on 2007-10-22
Mike you'll need to change the IP address to that of the desktop.....

---

### Post by mikeize on 2007-10-22
yup, ping has worked from the start.  (this thread is getting out of hand, eh?) :lolflag:

-mike

---

### Post by mikeize on 2007-10-22
> **_oOMOo_ said:**
> Mike you'll need to change the IP address to that of the desktop.....

sorry...  for nmap from the laptop?

-mike


edit:  be back in 15 min.

---

### Post by _oOMOo_ on 2007-10-22
Yeah maybe I'm getting confused :) - I thought you said you were nmapping the same IP address from both the laptop and the desktop but you only have one desktop I think? As I said probably me misunderstanding.

---

### Post by mikeize on 2007-10-22
yes, I mapped the desktop IP first from the desktop, and then from the laptop.  (I thought that's what I was asked to do)  anyway, here's nmap laptop IP FROM the laptop:

```
$ nmap 192.168.1.36

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-22 17:57 EDT
Interesting ports on 192.168.1.36:
Not shown: 1690 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
633/tcp  open  unknown
2049/tcp open  nfs

Nmap finished: 1 IP address (1 host up) scanned in 0.418 seconds
~$ 

```

-mike

---

### Post by dwhitney67 on 2007-10-22
> **_oOMOo_ said:**
> Yeah maybe I'm getting confused :) - I thought you said you were nmapping the same IP address from both the laptop and the desktop but you only have one desktop I think? As I said probably me misunderstanding.

Agreed, with such a long post, it might be helpful is Mike creates aliases in the respective /etc/hosts file so that when he issues a command, we know if it is for the 'desktop' or for the 'laptop'.

Mike - Do you know how to do this?

On your desktop:
$ sudo gedit /etc/hosts
<add the following line...>
[FONT="Courier New"]laptop <tabspace> 192.168.1.36[/FONT]

On your laptop:
<repeat, but instead...>
[FONT="Courier New"]desktop <tabspace> 192.168.1.35[/FONT]


Afterwards you should be able to issue a command like "ping desktop", or "ping laptop".

---

### Post by mikeize on 2007-10-22
okay, did that, but when I do "ping desktop" or "ping laptop" I get

```
ping:  unknown host laptop
```

does it matter where I add that line?  I put it at the end of the file.

-mike

---

### Post by dwhitney67 on 2007-10-22
Re-verify the contents of the /etc/hosts on your laptop.  It should appear something like:

desktop <tabspace> 192.168.1.35

and similarly on the desktop, but using "laptop" and "192.168.1.36".

Note the <tabspace> is a tab-space.  Do not type the characters verbatim as I have shown above!

---

### Post by mikeize on 2007-10-22
okay, I figured it out!  I put it in the wrong place, so I can ping, but I still need to "sudo ping" from my desktop.

-mike

---

### Post by dwhitney67 on 2007-10-22
I came across this other [thread]("http://ubuntuforums.org/showthread.php?p=3575037"), where someone else was mentioning the issue with ping.  Maybe it's a "feature" of 7.10.

I've never seen some many basic problems with a distro such as 7.10.

---

### Post by mikeize on 2007-10-22
> **dwhitney67 said:**
> I came across this other [thread]("http://ubuntuforums.org/showthread.php?p=3575037"), where someone else was mentioning the issue with ping.  Maybe it's a "feature" of 7.10.

I've never seen some many basic problems with a distro such as 7.10.

weird, yes...  but do you think that is the basic problem I'm having here?  It seems unlikely to me, but that is hardly an educated opinion! :)

-mike

---

### Post by magli on 2007-10-22
> **dwhitney67 said:**
> I came across this other [thread]("http://ubuntuforums.org/showthread.php?p=3575037"), where someone else was mentioning the issue with ping.  Maybe it's a "feature" of 7.10.

If it is a feature of 7.10, then I need to file a bug report - mine works as user....


Is there any other place which you deny access to certain hosts, other than /etc/hosts.allow and /etc/hosts.deny - even if you could,I guess that in this case it would return permission denied,not just timeout.

I really don't get it. I can't wait to see this thread solved.

---

### Post by _oOMOo_ on 2007-10-22
Why would you need sudo - that is peculiar. Maybe try creating a new user on your desktop that has privileges to administer the system and see if you also need sudo for the new user?

EDIT: I upgraded a pc from feisty to gutsy at the weekend and I had some really odd privilege issues when trying to add a printer, seems something of a theme with 7.10

---

### Post by mikeize on 2007-10-22
okay, so I switched over to my wife's account, and I can "ping laptop" without sudo!  Then I tried to ssh from laptop to desktop, but no dice.

btw, this is a fresh install of gutsy, not an upgrade.  it does have a seldom used xp partition, but I can't see how that would matter.

-mike

edit:  also, I tried networking with feisty, and could never get it to work, but I don't remember the specific problems.

---

### Post by _oOMOo_ on 2007-10-22
That's a tiny bit of progress at least :D

Did you try ssh <your wife's username>@desktop (I'm guessing you did!)?

---

### Post by mikeize on 2007-10-22
yes, I tried that...  nothing.

-mike

---

### Post by magli on 2007-10-22
I think that the problem is some trivial networking setting, either in some obscure place on your desktop or the router.

Maybe it would be interesting, for the sake of experiment, to swap the ips of the two computers.... this would, I think, eliminate the router settings as a possible cause of the problem.

---

### Post by mikeize on 2007-10-22
> **magli said:**
> I think that the problem is some trivial networking setting, either in some obscure place on your desktop or the router.

Maybe it would be interesting, for the sake of experiment, to swap the ips of the two computers.... this would, I think, eliminate the router settings as a possible cause of the problem.

okay.  just tell me how.

-mike

---

### Post by _oOMOo_ on 2007-10-22
Thanks Mike, just to recap:

ping desktop from laptop...........success
ping laptop from desktop...........success

nmap desktop from laptop.........fail
nmap laptop from desktop.........success

ssh desktop from laptop............fail
ssh laptop from desktop............success



You have ftp running on the desktop too I think, do you get a sensible response if you

```
ftp desktop
```

from the laptop?

Cheers, Jon

---

### Post by mikeize on 2007-10-22
yes, that all looks correct.

```
ftp desktop
``` 
from the laptop = timeout

-mike

---

### Post by magli on 2007-10-22
No, that's not correct. You said earlier that you could not nmap your desktop from the laptop.

So essentially, ping is the only thing that works in the laptop->desktop direction.

---

### Post by _oOMOo_ on 2007-10-22
Hi again, you can alter the IP setup with your router in the LAN Interface Setup - I just had a look on the net and it seems the default domain for your router is 192.168.10.0 - could you just confirm what the DHCP client range says?

Cheers

Edit: thanks magli I'll edit that unless Mike confirms

---

### Post by magli on 2007-10-22
> **magli said:**
> No, that's not correct. You said earlier that you could not nmap your desktop from the laptop.
Here is the post: [http://ubuntuforums.org/showpost.php?p=3603790&postcount=90](http://ubuntuforums.org/showpost.php?p=3603790&postcount=90)

---

### Post by _oOMOo_ on 2007-10-22
This is the page - you should be able to see attached devices and assign IP addresses here

---

### Post by mikeize on 2007-10-22
> **magli said:**
> Here is the post: [http://ubuntuforums.org/showpost.php?p=3603790&postcount=90](http://ubuntuforums.org/showpost.php?p=3603790&postcount=90)

yes, sorry my mistake.  that post you linked to has the correct information.

-mike

---

### Post by mikeize on 2007-10-22
DHCP range is:

192.168.1.33  -to-  192.168.1.65

---

### Post by mivo on 2007-10-22
I actually had a similar problem, and while I found a fix, it made no sense. But it still worked. ;)

On the Ubuntu machine that cannot connect to your SSH server, look for the .ssh folder in the home directory. If there is no config file in there, create one (only "config") and add this line:

```
GSSAPIAuthentication no
```

If the file exists, just append the above line. Save and try again. It worked for me, and apparently does not impose any security issues.

---

### Post by mikeize on 2007-10-22
> **mivo said:**
> I actually had a similar problem, and while I found a fix, it made no sense. But it still worked. ;)

On the Ubuntu machine that cannot connect to your SSH server, look for the .ssh folder in the home directory. If there is no config file in there, create one (only "config") and add this line:

```
GSSAPIAuthentication no
```

If the file exists, just append the above line. Save and try again. It worked for me, and apparently does not impose any security issues.

to clarify it should be:  /home/.ssh/config.cfg  ?
                           or:  /home/mike/.ssh/config.cfg  ?
                           or something else?
Thanks for jumping in!

-mike

---

### Post by mivo on 2007-10-22
No, only:

/home/*username*/.ssh/config

No file extension. If this does not work (should not require a restart), remove it again.

Edit:  .ssh is already there. You only have to edit config or create it, but the folder is there in any event. :)

---

### Post by mikeize on 2007-10-22
okay, did that (on the laptop) but still can't ssh into the desktop.  Also it auto created an empty file named "config~" ...  should I do anything with that?

-mike

---

### Post by mivo on 2007-10-22
config~ is just a backup file -- there apparently was an empty config file there before already, so when you overwrote it, an automatic backup copy was created. You could try the same on the other computer, but this does not seem to be the solution to your problem. :(

---

### Post by mikeize on 2007-10-22
Still doesn't work.  Put one in my desktop too, but nothing.  *sighs*

-mike

---

### Post by mikeize on 2007-10-22
just to let people know, I AM able to ssh out from my laptop to an external server address provided to me by a forum member.  

-mike

---

### Post by mivo on 2007-10-23
Yes, that was almost exactly my situation, too. I could ssh to my employer's server, even with Nautilus, but the machine a few meters next to me was a no-go with Nautilus ("connect to..."). It did work mostly with ssh in the shell, though, and adding the line to the config file fixed the problem for good. Did you try it with a wired connection?

---

### Post by magli on 2007-10-23
The problem is not with ssh. It applies to all of the services running on his desktop: he cannot run nmap, ftp, ssh or samba from his laptop to his desktop. They all timeout.

He already tried to connect with a wire with no luck.

I think he is on eastern US time, so will probably be gone for another couple hours.

---

### Post by AngelBreath on 2007-10-23
I m not a networks expert , but with all this tests, configs and files even if he makes the right steps , he will not be able to connect. The best (just my opinion) is to make all steps from the beginning, and try to have just a very very simple netwok. That means uninstall,delete, reconfig everything (if not a clear setup is possible) and try to make the very simple steps. Confusing protocols, serveices, ips and all this will have as result even a right setup to not working. I read that you (Mike) made a clear setup of Gutsy. So my advice is to make a new setup again so we can have a clear machine. After that try ONLY ONE way of connecting and not all together. And if its possible to try the network with camble at first.
 As you can see , many people are here to help you so i think that if you do it from the beginning we ll find the solution, cause of this long thread most of us ( i think ) are already confused of what the situation is.As setting up a network is not the easiest thing in the world , but it doesn't need a SO HUGE thread for setting up 2 pc work together ( i agree with your title "simple home network") i inseast to do everything from the start.

---

### Post by R_U_Q_R_U on 2007-10-23
AngleBreath: your suggestion is spot on. As I mentioned earlier, these two articles absolutely work on a clean Gutsy install:

Read this for Samba:

[B]HOWTO: Setup Samba peer-to-peer with Windows : [http://ubuntuforums.org/showthread.p...t=how+to+samba]("http://ubuntuforums.org/showthread.php?t=202605&highlight=how+to+samba")

[/B] and this for NFS:

**HOWTO: NFS Server/Client:**
[B][http://ubuntuforums.org/showthread.p...ght=how+to+NFS]("http://ubuntuforums.org/showthread.php?t=249889&highlight=how+to+NFS")
[/B]

---

### Post by magli on 2007-10-23
I disagree with you guys.

I think that the problem could even be in the router configuration. Before Mike goes through all the hassle of re-installing his system, I think we should at least rule out the possibility that the problem is with the router.

It could be that there is some rule in the router somewhere which does not allow traffic from his laptop IP to his desktop IP - similar to a DMZ.

Mike, did you say that your ips were both static? If so, you must have set them yourself. I think that can be done by left-clicking on the network manager in the rop-right corner of the screen, and going to "Manual Configuration". Try swapping your IP's around, or setting them to something completely different.

If you are using DHCP, edit the DHCP range in your router, and then disconnect-reconnect both laptop and desktop so that they are given new addresses.

Remember that you can check the current IP of either computer with the ifconfig command.

As for the strange ping issue: I had a thought. It is possible that there are two "ping" commands installed on your system. We have been assuming that the ping which gets executed when you type "ping" is /bin/ping. Maybe it isn't.

To verify, try this:
```
which ping
```
And then check the permissions on the result of the previous command with ls -l

---

### Post by _oOMOo_ on 2007-10-23
> **magli said:**
> I disagree with you guys.

I think that the problem could even be in the router configuration. Before Mike goes through all the hassle of re-installing his system, I think we should at least rule out the possibility that the problem is with the router.l

I have to agree with magli here - Mike did say he could never get networking set up in Feisty either, and all things do seem to point to a problem with the router setup.

---

### Post by mikeize on 2007-10-23
Thanks for the suggestions, and I agree this thread is getting too long for easy understanding of my problem.  I'm really resistant to the idea of a fresh install, since I had problems with feisty, and it seems like a drastic step to test a solution.  I think I'll try a live cd.  

Magli:

here is the ping output you suggested:

```
~$ which ping
/home/mike/bin/ping
mike@u-desktop:~$ ls -l /home/mike/bin/ping
-rwsrwxr-x 1 mike mike 30848 2007-03-04 23:25 /home/mike/bin/ping
$ 

```

I'll try changing IP addresses in a second.

-mike

---

### Post by magli on 2007-10-23
OK.

Your ping command *should* be in /bin/ping, not /home/mike/bin/ping. It seems that you must have installed something at some point which added a ping executable in that directory.

The permissions seem correct though. So it still does not explain the problem.

I bet, however, that you can run ping without sudo, if you type:
```
/bin/ping IP_TO_PING
```

---

### Post by Lord_Dicranius on 2007-10-23
If you guys don't mind, could I get a quick run down? lol  14 pages is a lot to go back and read.  Just items such as:

Desktop/laptop OSs
What can ping/ssh/nmap what

Thanks :-D

---

### Post by mikeize on 2007-10-23
> **magli said:**
> 
I bet, however, that you can run ping without sudo, if you type:
```
/bin/ping IP_TO_PING
```

yes, that works without sudo.

> Mike, did you say that your ips were both static? If so, you must have set them yourself. I think that can be done by left-clicking on the network manager in the rop-right corner of the screen, and going to "Manual Configuration". Try swapping your IP's around, or setting them to something completely different.

I tried what you said, but I think I essentially edited the hosts file.  I changed the laptop IP from the desktop, and vice versa, but each machine lists its own IP as 127.0.0.1.  Anyway, I slightly changed the DHCP range and dis/reconnected each machine, but they get their old IP addresses back, so I guess I didn't do it right :(

-mike

---

### Post by mikeize on 2007-10-23
> **Lord_Dicranius said:**
> If you guys don't mind, could I get a quick run down? lol  14 pages is a lot to go back and read.  Just items such as:

Desktop/laptop OSs
What can ping/ssh/nmap what

Thanks :-D

Hi, and welcome!
desktop=gutsy    laptop=feisty (that's all for now!)

> ping desktop from laptop...........success
ping laptop from desktop...........success

nmap desktop from laptop.........fail
nmap laptop from desktop.........success

ssh desktop from laptop............fail
ssh laptop from desktop............success

-mike

edit:  further, this is the error I get when nmap desktop from laptop:

```
$ nmap desktop

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-23 11:37 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 3.026 seconds

```

---

### Post by magli on 2007-10-23
Just to expand on mike's rundown:

ssh desktop from desktop.......success (so it is running)
nmap desktop from desktop....success (shows ftp,ssh and samba as listening)

samba desktop from laptop....fail
ftp desktop from laptop..........fail

NOTE: ALL FAILS ARE TIMEOUTS - not permission denied, or anything else.

There does not appear to be a DMZ set up on his router.

He has tried connecting the latop to the router via a cable without success.

Also, he has posted the contents of /etc/hosts.allow and /etc/hosts.deny --nothing in either

---

### Post by Lord_Dicranius on 2007-10-23
Awesome, thanks for the run down Mike :)  I've decided to go back and read the entire thread anyways now, that way I'm not repeating things you guys have already tried haha  Be back in a bit if anything comes to mind :)

**EDIT**
Ah, good info.  Thanks magli :)

What kind of router is it?

**EDIT2**
> He has tried connecting the latop to the router via a cable without success.
When you say that, does that mean connecting it to the router via cable didn't fix any of the fails?  When he connected it, was he still able to access the 'net?

---

### Post by magli on 2007-10-23
> **mikeize said:**
> I tried what you said, but I think I essentially edited the hosts file.  I changed the laptop IP from the desktop, and vice versa, but each machine lists its own IP as 127.0.0.1.

The /etc/hosts file does not assign IP addresses. I think it is used to give IP addresses alias names. So, if you want your computer to always translate a name, say wifescomp to a given IP address, you would enter a line in this file.

127.0.0.1 *always* refers to the computer you are on. It is sort of an IP address used internally for a computer to refer to itself. "localhost" is an alias for 127.0.0.1, which is why you see it declared in /etc/hosts. (if you type "ping localhost", your computer will actually ping 127.0.0.1,ie, itself)

I will assume that your computers are using DHCP, as otherwise you would remember assigning their IP addresses.

When you edited the dhcp range on your router, did you make sure to edit it in such a way that the new range does not include the current ip addresses of the computers?

---

### Post by mikeize on 2007-10-23
ok, running livecd (feisty) on desktop now...
from desktop, I can ssh to laptop, but...
still cannot ssh from laptop TO desktop, but...
slightly different:

```
~$ ssh mike@desktop
ssh: connect to host desktop port 22: Connection refused
mikeize@ubuntu:~$ ssh mike@192.168.1.35
ssh: connect to host 192.168.1.35 port 22: Connection refused
~$ 

```

not a timeout.  significant?

-mike

edit:  okay, duh, there is no "mike" when running live cd!  tried to ssh to the IP address, and same thing.

btw router is a ZyXel P-330W

---

### Post by magli on 2007-10-23
> **Lord_Dicranius said:**
> When you say that, does that mean connecting it to the router via cable didn't fix any of the fails?  When he connected it, was he still able to access the 'net?

It did not fix the fails. I think he was still able to connect to the net - though not sure it was attempted.

---

### Post by magli on 2007-10-23
> **mikeize said:**
> ok, running livecd (feisty) on desktop now...
from desktop, I can ssh to laptop, but...
still cannot ssh from laptop TO desktop, but...
slightly different:

```
~$ ssh mike@desktop
ssh: connect to host desktop port 22: Connection refused
mikeize@ubuntu:~$ ssh mike@192.168.1.35
ssh: connect to host 192.168.1.35 port 22: Connection refused
~$ 

```

not a timeout.  significant?



Very significant. This is because the ssh-server is not running on the livecd by default. You can install it:
```
sudo apt-get install openssh-server
```

But the fact that it is responding implies it will probably work. Can you check the ip address of the livecd? Is it the same one as before? (use ifconfig)

---

### Post by mikeize on 2007-10-23
> **magli said:**
> 

When you edited the dhcp range on your router, did you make sure to edit it in such a way that the new range does not include the current ip addresses of the computers?

thanks for clarifying.  I'm almost positive that my IP's are assigned by DHCP.  When I edited the range, I DID include the current addresses-- sorry, I'll change it here...

-mike

---

### Post by Lord_Dicranius on 2007-10-23
It almosts sounds like the desktop is blocking the ports that need to use those specific daemons.  So everything from the desktop to the laptop is successful, but the only thing from the laptop to the desktop that is successful is a ping.  A ping doesn't use a port to communicate, but codes instead (hard to explain if you don't know it already heh).  But when you try to SSH, FTP, etc, those fail.  The only thing that gets me is that nmap couldn't even see the desktop...hmm.  Just for sake of making sure, I'm assuming telnet'ing from the laptop to desktop comes up with a timeout also?

---

### Post by mikeize on 2007-10-23
installed ssh server on live cd desktop.  ssh seems to work, but won't take any passwords (not surprising?), so I get permission denied.

I'll reboot back to my HD and change DHCP range on the router.

-mike

---

### Post by mikeize on 2007-10-23
```
telnet desktop
```
nothing, waiting for it to timeout...

-mike

---

### Post by magli on 2007-10-23
> **mikeize said:**
> ```
telnet desktop
```
nothing, waiting for it to timeout...

-mike

Be careful: if you manage to change your ip addresses by changing the dhcp range, then "desktop" will no longer be an alias to the right IP.. if you see what I mean. You would have to update the "desktop" ip in /etc/hosts to continue referring to that ip with "desktop"

---

### Post by mikeize on 2007-10-23
Okay, changed DHCP range, got new unique addresses for both machines... still timeout when ssh from laptop to desktop.... and still ABLE to ssh from desktop to laptop.

-mike


***edit:  yeah, thanks magli, I just typed out the new ipaddress instead of the alias.

---

### Post by Lord_Dicranius on 2007-10-23
Just another idea: you could try installing an iptables GUI (firestarter, guarddog) and make sure the ports necessary are opened (FTP: 20, 21 | SSH: 22 | telnet: 23).  This is just a shot in the dark, I'm still trying to find out why nmap'ing from the laptop couldn't see the desktop...

---

### Post by magli on 2007-10-23
> **Lord_Dicranius said:**
> Just another idea: you could try installing an iptables GUI (firestarter, guarddog) and make sure the ports necessary are opened (FTP: 20, 21 | SSH: 22 | telnet: 23).  This is just a shot in the dark, I'm still trying to find out why nmap'ing from the laptop couldn't see the desktop...

Maybe nmap could see the desktop, but listed no ports open. That information could have been lost as simply being a "fail" - Mike, maybe you want to run nmap from the laptop to the desktop again..

---

### Post by Lord_Dicranius on 2007-10-23
> ```

$ nmap desktop

Starting Nmap 4.20 ( http://insecure.org ) at 2007-10-23 11:37 EDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 3.026 seconds

```
Did you try nmap with the "-P0" option last time you got this error?  The "-P0" option will assume that the machine is online and skip the discovery process, get right down to the scanning of the ports, might return an error that we could work with better.

---

### Post by mikeize on 2007-10-23
Okay you guys...  you can all get back to your lives now!

I have a firewall, and I'm sure it wasn't running at some early point in this saga, but when I just checked it --it was on!  I turned it off, and voila!  I can ssh and nmap from the laptop to the desktop.  

Either something we did fixed the problem, or I was completely mistaken about my firewall earlier.  I really hope the latter was not the case.

Anyway, problem solved.  If I could send flowers to everyone who put their efforts into helping me out, I would.  

in sincere gratitude,

mike

-now to configure firestarter!:guitar:


****edit:  how do I change thread to "SOLVED"?

---

### Post by Lord_Dicranius on 2007-10-23
Glad to hear it's working! :-D

Edit the first post in this thread and change the subject line.  You'll probably need to click on "go advanced" to modify the subject line.

---

### Post by magli on 2007-10-23
Nice one. Glad to here it is working.

At least you will have learned something along the way.

---

### Post by _oOMOo_ on 2007-10-23
Just got in from work to see you fixed it, fantastic! Now you can have a load of fun configuring port forwarding :D

Jon

---

### Post by mikeize on 2007-10-23
> **magli said:**
> Nice one. Glad to here it is working.

At least you will have learned something along the way.

We can hope, right?  Thanks magli.

> **_oOMOo_ said:**
> Just got in from work to see you fixed it, fantastic! Now you can have a load of fun configuring port forwarding :D

Jon

Oh man, I am DONE for now!  I've been neglecting my school work :).  The next step will be making it gui-fied.  I'm glad to put this thread out of its misery.  Thank you.

-mike

---

### Post by mivo on 2007-10-23
Awesome! Glad you got it to work. :) You showed a great deal of patience during this -- impressive!

---

