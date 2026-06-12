---
title: "Direct Connect File Transfer Setup Problem"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by MikeGreen on 2005-09-12
I've got two computers running Ubuntu connected via an ethernet crossover cable. I'd like to transfer some large files from one to the other.

How do I do this? A step-by-step, easy-to-understand method would be appreciated. I'm totally new to all this but I can follow directions. Don't assume I just "know" where to put IP addresses or the like!

Thank you for any assistance.

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=MikeGreen]I've got two computers running Ubuntu connected via an ethernet crossover cable. I'd like to transfer some large files from one to the other.

How do I do this? A step-by-step, easy-to-understand method would be appreciated. I'm totally new to all this but I can follow directions. Don't assume I just "know" where to put IP addresses or the like!

Thank you for any assistance.[/QUOTE]
Can you clarify-- have you configured these PCs to be on a mini-network, or have you simply attached the cable from one to the other without any kind of software configuration?  Also, is either one connected to another (larger) network?

The basic steps, I think, would be
1) configure your network.
2) Set up ftpd or sshd on the destination machine.
3) Copy the files over with scp or ftp.

We can go over these in more detail once we know a little bit more about your setup.

---

### Post by MikeGreen on 2005-09-12
I haven't configured a thing. Neither is connected at the moment to any other network in any way. Just two computers and a crossover cable between them.

Sorry to have it reduced to such a primitive state, but I really don't know where to go from here.

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=MikeGreen]I haven't configured a thing. Neither is connected at the moment to any other network in any way. Just two computers and a crossover cable between them.

Sorry to have it reduced to such a primitive state, but I really don't know where to go from here.[/QUOTE]
OK, step 1 is to configure them as a mini-network with just two hosts.  There may be an easier way to do this, but this is what I would try:
On machine A:
```

$ sudo ifconfig eth0 192.168.0.2
$ sudo route add -net 0.0.0.0 gw 192.168.0.3

``` 

On machine B:
```

$ sudo ifconfig eth0 192.168.0.3
$ sudo route add -net 0.0.0.0 gw 192.168.0.2

``` 

This configures one machine with IP address 192.168.0.2, and the other with 192.168.0.3.  The default route of each one is the other machine.

Test to see if it works with (from A):
```

$ ping 192.168.0.3

```

---

### Post by MikeGreen on 2005-09-12
For the moment, let's presume your excellent directions work. (I say that because the computer I'm using for this message is one of the two involved in this procedure).

Questions:
1) After I do the configuring, how do I actually move the files? May I use GNOME is some way, rather than a terminal?

2) After I'm done, need I do anything to reconfigure the computers for use on a normal network? In other words, how do I get back to my current configuration?

Thank you for all your help.

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=MikeGreen]For the moment, let's presume your excellent directions work. (I say that because the computer I'm using for this message is one of the two involved in this procedure).

Questions:
1) After I do the configuring, how do I actually move the files? May I use GNOME is some way, rather than a terminal?

2) After I'm done, need I do anything to reconfigure the computers for use on a normal network? In other words, how do I get back to my current configuration?

Thank you for all your help.[/QUOTE]
The commands I gave you should not last past a reboot.  You can also configure the settings back to whatever they were without rebooting, but it takes a little more explaining.  Suffice it to say, by typing the "ifconfig" and "route" commands without parameters, you can see your current settings.

I also assumed that that the ethernet devices would not already be configured-- you might have to take a connection down prior to assigning a new IP address:
```
$ sudo ifdown eth0
``` 

Now, I think you can use an ftp:// or an scp:// in a Nautilus address bar.  It's been a while for me since I primarily use KDE (I know you can do it in konqueror).  The command line will definitely work for moving files.  If sshd is running on the destination server, the "scp" command syntax is just like the cp (copy) command, except you include the user name and server name or address in the path.  E.g.
```

$ scp source_file user@192.168.0.3:/home/user/dest_file

```

FTP is as old as the stone age, but in case you are not familiar with it:  The destination needs to be running some sort of ftp server (like ftpd).  On the client, you change directories to where the files you want to transfer are.  Then you type "ftp dest-name-or-address" to start the ftp session.  Then you can use ftp commands to navigate on the remote host (cd), change to binary (bin) or ASCII (asc) mode, transfer a single file (put), transfer multiple files (mput), turn off interactive prompting for mput and mget (prompt), retrieve a file (get) or retrieve multiple files (mget).  When you are done, you type "bye".

Both techniques require you to log on with a user name and password.

---

### Post by MikeGreen on 2005-09-13
Thank you so much for your time and advice on this matter. I wish I could tell you it all worked out fine, but unfortunately it did not. I could not make  the computers ping one another. I do not know why. Also, I apologize for the confusion about the initial network status. I was thinking of what I would be doing, rather than what I had at the moment.

I am not sure I would have been able to get much farther than that, however. I must admit that I'm somewhat surprised at how much more there is to do to get a file transfer working once the machines are connected. I looked into installing the ssh server and then tried to understand the documentation for Nautilus. I did not want to try to install KDE and Konqueror on both machines to accomplish this one task. I had hoped there would be some simpler method, but hopes don't mean much with Linux.

As it is, I've had to abandon this approach because of time constraints. It proved faster to simply buy a number of CDs and copy all the data to them. Faster is a relative turn in this case. It took many hours.

Thanks again for your well-meant advice!

---

### Post by Neobuntu on 2007-11-06
The fastest solution is to use a flash drive.

You probably needed to turn off your firewall temporarily (or set it to pass the incoming, other "server").

The freaking' planets have to aline. It's sad. But it's not really overall different with Windows.

Networking is like that. That's the way it is.

Once one does get those planets to aline and set up a state that can SAFELY also access the Internet then it's nice to have around.

Many use Samba to do GUI sharing among open or Windows computers.

Samba (smb) servers must be set right.
Samba client must be set right.
Shared folders must be set right.
Your firewall must be set right.
Your network must be set right (use ping).
You cables must be good, correct (crossover or not) and inserted right.
Any hubs or routers must not have any bad ports (it happens) and be set right.
Your user names must be set right.
All your Ethernet drivers must be working right.
Mars must be in retrograde or something.

What did I forget, net jockeys?

A USB flash drive you insert, click and drag. You'll need USB 2.0 for larger files. USB 2.0 is easy to add if you don't already have it.

If someone here can tell me how to set up * FAST*, Ubuntu Gusty; for scp, rcp or something, I'm all ears. 100BT (or Gigabit) LAN is much faster for big files.

Remember if you can't ping, don't forget the firewall. ...gets me everytime.

---

