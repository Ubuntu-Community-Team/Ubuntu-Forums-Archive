---
title: "Samba Help Required"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-18
Hello,
I have (apart from this laptop) a laptop running Windows XP Pro, with all my music, movies and other files. I installed Kubuntu on this laptop yesterday. So just for convience let me call my windows laptop as Wlap and kubunt laptop as Klap. 

So I installed samba on my Klap and went to the remote places from the system menu on the task bar. There I saw 'Samba Shares'. So I went inside that and there was a folder called MSHOME. Inside MSHOME I saw that my Wlap was listed. When I tried to go into that I got this error:

Could not connect to host for smb://lucky/

(Lucky is my Wlap's computer name)

So what to do from here? I would like to access my stuff on Wlap from my Klap so that I could slowly migrate to linux completly. Do I need to setup something on my Wlap so that my Klap can access stuff on the Wlap?

Help much appreciated.
Thanks.

---

### Post by Sand Lee on 2007-06-18
um, did you share the folders in your wlap?

---

### Post by linuxnovice on 2007-06-18
Well thats the deal.

I did but nothing happened.

---

### Post by linuxnovice on 2007-06-18
I can access the internet from my Klap without any trouble. I ping the router and no problem there. But I ping my Wlap and there is no answer. Packets only get sent but not recieved. But when I ping the Klap from the Wlap it gets pinged fine. That means, I am guessing the Wlap can see the Klap and not the other way round.

---

### Post by stalker145 on 2007-06-18
> **linuxnovice said:**
> Hello,
I have (apart from this laptop) a laptop running Windows XP Pro, with all my music, movies and other files. I installed Kubuntu on this laptop yesterday. So just for convience let me call my windows laptop as Wlap and kubunt laptop as Klap. 

So I installed samba on my Klap and went to the remote places from the system menu on the task bar. There I saw 'Samba Shares'. So I went inside that and there was a folder called MSHOME. Inside MSHOME I saw that my Wlap was listed. When I tried to go into that I got this error:

Could not connect to host for smb://lucky/

(Lucky is my Wlap's computer name)

So what to do from here? I would like to access my stuff on Wlap from my Klap so that I could slowly migrate to linux completly. Do I need to setup something on my Wlap so that my Klap can access stuff on the Wlap?

Help much appreciated.
Thanks.

I'm not sure if this is any part of the issue, but do you have the same username and password combination for your Windows laptop as for the Kubuntu Laptop? I know that I've always had issues getting my Wife's Win2K laptop connecting to my shares because she refuses to use anything but the Administrator account and I refuse to make a user named administrator on my Linux boxes...

Also check the domain/workgroup settings... that *might* be a problem.

---

### Post by dannyboy79 on 2007-06-18
what does this return

smbclient -L WLAP
(NOTE: put either the IP of your Wlap or the Netbios name, then hit enter. If my machine was dans, then I would enter, "smbclient -L dans")
this should return the shares that are available on the Wlap machine, if you get NT status error, then you need to authenicate yourself to that machine. OR are your Wlap shares open to the public? If not,  you'll have to create a user on the Klap machine that's the same as the naem your trying to authenticate on the Wlap machine OR have you added a username.map file within your smb.conf that says that the Wlap usersname is the same as the Klap machine, then you'll also need to add teh Klap username to the smbpasswd file. Have you done all that?

---

### Post by linuxnovice on 2007-06-18
It says it couldnt connect to the Wlap. Here is the exact details:

sudarshan@Lucky-Linux:~$ smbclient -L 192.168.2.2
timeout connecting to 192.168.2.2:445
timeout connecting to 192.168.2.2:139
Error connecting to 192.168.2.2 (Operation already in progress)
Connection to 192.168.2.2 failed
sudarshan@Lucky-Linux:~$ sudo smbclient -L 192.168.2.2
Password:
timeout connecting to 192.168.2.2:445
timeout connecting to 192.168.2.2:139
Error connecting to 192.168.2.2 (Operation already in progress)
Connection to 192.168.2.2 failed

I made sure the IP matches that on the Wlap.

---

### Post by dannyboy79 on 2007-06-18
firewall on winbloz blocking ya!

---

### Post by linuxnovice on 2007-06-18
I thought so. I am using Zonealarm on my Wlap. How do I make it allow this connection? If its a program I know how to do it. But I thing it automatically blocks any unauthorized connection. So do I have to disable the firewall completly to connect to my Wlap?

---

### Post by linuxnovice on 2007-06-18
Ok I added the Klap to the trusted zone of zonealarm. Here is what I get when I run smbclient now:

Password:
Domain=[LUCKY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Default share
        IPC$            IPC       Remote IPC
        D$              Disk      Default share
        print$          Disk      Printer Drivers
        SharedDocs      Disk
        Music           Disk
        ADMIN$          Disk      Remote Admin
        PDF Print       Printer   eDoc Printer
        C$              Disk      Default share
session request to 192.168.2.2 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[LUCKY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
But when I go to my windows folder under the remote place on system menu and thro the samba shares, I still get the error saying that it couldnt connect to the said network.

What do I do next?

---

### Post by linuxnovice on 2007-06-18
Hi I added the Klap to the trusted zone of zonealarm. Here is the run of smbclient now:

Password:
Domain=[LUCKY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Default share
        IPC$            IPC       Remote IPC
        D$              Disk      Default share
        print$          Disk      Printer Drivers
        SharedDocs      Disk
        Music           Disk
        ADMIN$          Disk      Remote Admin
        PDF Print       Printer   eDoc Printer
        C$              Disk      Default share
session request to 192.168.2.2 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[LUCKY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
But I still cant connect to my Wlap. What now?

---

### Post by dannyboy79 on 2007-06-18
instead of going thru the Windows Network, try to do it manually. Choose to connect to network, then enter the Wlap name within the server, then enter the share name, tehn hit Connect. this will put a icon on your desktop, then double click that, this should bring up the Username and password box, enter the windows username and password, and hit ok, this should get you into that folder. 

The browsing thru places windows network is very flaky. It's because of Gnome-VFS and it's been a problem since Dapper for me. For some reason though it works now for me. But I didn't think that it worked until I did what I described above first. Don't know why, it just worked. It must have somethig to do with the Gnome-VFS not using the correct authentification credentials and then it times out and says it could be displayed.

---

### Post by dannyboy79 on 2007-06-18
I copied and pasted this which was originally written by Dedoimedo (I know all this but didn't feel like writing it all out)

Hello,


First, make sure you have shared folders on Windows ...

You can see this for more details:
[http://ubuntuforums.org/showthread.php?t=465896](http://ubuntuforums.org/showthread.php?t=465896)

Try this:

First, install Samba:

apt-get install samba

After the Samba server is installed, you will need to edit a few options in the configuration file to allow sharing privileges.

cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
gedit /etc/samba/smb.conf

In the configuration file, you will need to setup a number of parameters:

* workgroup = workgroup_name - the name of the Workgroup for your LAN (e.g. HOME)
* netbios name = netbios_name - without spaces; computer alias by which you will be able to call it across the network
* security = user

After saving the configuration file, you will have to restart the Samba server:

/etc/init.d/samba restart

Now, via home folder, select a folder that you wish to share. If you have ticked the option Writable, you will be able to modify the contents of this folder.

Finally, to be able to connect to this share from Windows, you will have to create a Samba user:

smbpasswd -a 'name'

Under 'name' you should specify an existing UNIX user. Do not forget the apostrophes! You will be asked to create a password. And finally, restart the Samba server again, for the changes to take effect.

Now, the sharing itself. Very simple.

Windows > Linux

Start > Run > \\xxx.xxx.xxx.xxx OR \\netbios_name


When asked for username and password, provide the Samba user name and the relevant password. And that's it. Browse to the shared folder. If the shared folder is writable, you will be able to modify the contents.

Linux > Windows

Press Alt + F2.

This will bring up the Run Command window. In the Command line, specify the IP address or the name of the computer that you wish to connect.

---

### Post by linuxnovice on 2007-06-18
Ok I dont exactly know how but now when I go into samba shares and into my Wlap, I can see my partitions and my shared folders. i followed the instructions given here and did something more too (i guess):
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Now I have a few questions:
1) I had set up the music folder (not my music but a separate one that I use) in windows as shared. So when I went inside it didnt ask my for any password or anything. I think this is dangerous. So how to change it so that it asks me for a password. 

2) When I tried going in to my non-shared folders it did ask me for a username and password. But whatever relavent username and password I tried entering it wouldnt go through. Which username and password do I need to enter for accessing these folders. (My windows machine doesnt have a password).

3) I played some music on amarok which I accessed from my windows machine thro share. I just want to know one thing. when i play a song on amarok, does that file get downloaded into my Klap from my Wlap or does it just stream wirelessly? Suppose I build a collection on amarok will all my music be transfered to my Klap or will they just be 'indexed' so that they could just stream?

Thanks.

---

### Post by dannyboy79 on 2007-06-18
> **stalker145 said:**
> I'm not sure if this is any part of the issue, but do you have the same username and password combination for your Windows laptop as for the Kubuntu Laptop? I know that I've always had issues getting my Wife's Win2K laptop connecting to my shares because she refuses to use anything but the Administrator account and I refuse to make a user named administrator on my Linux boxes...

Also check the domain/workgroup settings... that *might* be a problem.

> **linuxnovice said:**
> Ok I dont exactly know how but now when I go into samba shares and into my Wlap, I can see my partitions and my shared folders. i followed the instructions given here and did something more too (i guess):
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Now I have a few questions:
1) I had set up the music folder (not my music but a separate one that I use) in windows as shared. So when I went inside it didnt ask my for any password or anything. I think this is dangerous. So how to change it so that it asks me for a password. 

2) When I tried going in to my non-shared folders it did ask me for a username and password. But whatever relavent username and password I tried entering it wouldnt go through. Which username and password do I need to enter for accessing these folders. (My windows machine doesnt have a password).

3) I played some music on amarok which I accessed from my windows machine thro share. I just want to know one thing. when i play a song on amarok, does that file get downloaded into my Klap from my Wlap or does it just stream wirelessly? Suppose I build a collection on amarok will all my music be transfered to my Klap or will they just be 'indexed' so that they could just stream?

Thanks.


Just so you know, everytime you change stuff, you need to restart samba or even wait a couple minutes before the changes take effect.

1.) this obviously depends on who is on your network? how ever you shared your Wlap shares that are hidden, then make it the same if you want to have them only accessible by a username and password.

2) You need to set them up with a username and password then. that's how all my computers are so I don't know what to tell you if you don't want to use a username and password. haev you tried to just leave the password blank? have you added the windows user to your machien and hten to the smbpassword file? If you don't want your wlap user to have his own folder within the klap /home/ folder, than use a username.map file and map the wlap user to the klap user within that and then add the file location within your smb.conf.

3) if you browse any network shares and play a song from that location, it doesn't download that file, it's streaming it. it's indexed I believe but I don't do this. BUT I can tell you for sure it surely doesn't download them, that I know for sure.

---

