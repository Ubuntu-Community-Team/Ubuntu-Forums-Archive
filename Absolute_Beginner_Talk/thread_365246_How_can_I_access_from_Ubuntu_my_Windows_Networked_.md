---
title: "How can I access from Ubuntu my Windows Networked PCs?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-19
Hello!

I connected a Networked Windows OS (equipped) PC...
From the Menu, I selected "[color=blue]Places\Network Servers[/color]"

I saw my "[color=blue]Windows Network[/color]" icon & its subdirectories are the following:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/WindowsNetwork-MySnapshot.png[/IMG]

I am trying to connect to the Windows OS PC...
How can I do that?
What do I need to provide in the following fields:

```
Username:
Domain:
Password:
```

Is it the Ubuntu's user info, **or** the Windows user info?

On the Windows PC, I have created a _user_ "[color=blue]Remote[/color]" with Administrator Priviledges, with Password that belongs to the _Domain_ called "[color=blue]MSHOME[/color]".

_Questions_:
1. When typing these above, I can't get connected...
What is wrong?
Does the info has to be typed will all capital letters?
**OR** with the first letter in capital?
**OR** with all letters in small caps? :confused:

2. IF I can manage to access my Windows PCs through "[color=blue]Places\Network Servers[/color]", then where does "[color=red]samba[/color]" fit in & why do I need it?

Thanks.

---

### Post by louis_nichols on 2007-02-19
For some reason I can't see your screenshot...

However, the username and passwd are the ones of a user or admin on the windows computer. Now, why you can't access the shares after you type in a username and passwd depends on the type of error you get.

As for samba, it's pretty simple. Without samba you can access and use windows shares, but you need samba if you want windows to access files and folders from Ubuntu.

---

### Post by miseljt on 2007-02-19
1) is that Vista? one of my roomies has Vista and we all have issues getting to his computer, regardless of Windows/Linux.

2) Samba is a file sharing protocol that you need to be able to share files on a Windows network.

3) if you're trying to get directly to ShardDocs, or some other folder in particular, try mapping to the particular share through Places -> Connect to Server, change the service type to Windows Share, and add the 'server' (computer you're trying to connect to) and the share name (folder which you're trying to get into). i've found that this is typically the easiest way for me to map network drives, regardless of being in Windows or Ubuntu. hope some of this helps. :)

---

### Post by dvarsam on 2007-02-19
[QUOTE=louis_nichols]For some reason I can't see your screenshot...

However, the username and passwd are the ones of a user or admin on the windows computer. Now, why you can't access the shares after you type in a username and passwd depends on the type of error you get.[/quote]

Does the info have to be typed will all capital letters?
**OR** with the first letter in capital?
**OR** with all letters in small caps?

The problem is that I don't get any error... 
The only thing I get when clicking on the "[color=blue]Connect[/color]" button, is the window just flashing & appearing again...
As if I need to retype the access parameters again...!!! :-k

IF instead I click on the "[color=blue]Cancel[/color]" button, I get the following popup window:

```
**The folder contents could not be displayed.**
Sorry, couldn't display all the contents of "C$".

Button available: "OK"
```

I can't think of anything...
Am I missing any package...?
Is there a package that I need to install?

[quote=louis_nichols]As for samba, it's pretty simple. Without samba you can access and use windows shares, but you need samba if you want windows to access files and folders from Ubuntu.[/QUOTE]

So without "[color=red]samba[/color]", Ubuntu can access all Windows Files & perform copy&paste?
... but Windows can't access Ubuntu's Files?
Did I get it right?

Thanks.

---

### Post by louis_nichols on 2007-02-19
> **dvarsam said:**
> 

So without "[color=red]samba[/color]", Ubuntu can access all Windows Files & perform copy&paste?
... but Windows can't access Ubuntu's Files?
Did I get it right?

Thanks.

Yes, that is correct.

Now, the username and password... It may be the problem that miseljt said or it may be a typo indeed. Or it may be something else, that I'm missing.

I'm not sure about the username, but the password will certainly be case-sensitive. AFAIK, default installations of windows up to XP did not require the user to enter a password (I mean, the field is there but it will let you go on even if left blank), so I would try to leave either password or both username and password blank and then try to connect. I've never had this problem, so we're just using trial and error here. I actually don't know where to enable authentification for accessing files shared by windows.

---

### Post by dvarsam on 2007-02-19
[QUOTE=miseljt]1) is that Vista? one of my roomies has Vista and we all have issues getting to his computer, regardless of Windows/Linux.[/quote]

Sorry I did NOT mention this...
It is [color=blue]Windows XP SP2[/color].

[quote=miseljt]2) Samba is a file sharing protocol that you need to be able to share files on a Windows network.[/quote]

You mean share Ubuntu's files in Windows Pcs...
Cause I guess the opposite is possible without samba...?
Is that right?

[quote=miseljt]3) if you're trying to get directly to SharedDocs, or some other folder in particular, try mapping to the particular share through Places -> Connect to Server, change the _service_ _type_ to [color=blue]Windows Share[/color], and add the 'server' (computer you're trying to connect to) & the _share_ _name_ (folder which you're trying to get into). I've found that this is typically the easiest way for me to map network drives, regardless of being in Windows or Ubuntu. hope some of this helps. :)[/QUOTE]

In what syntax do you type the "share name"?
Can you provide a user case/example?

Thanks.

---

### Post by louis_nichols on 2007-02-19
Paths are not case sensitive. smb://test and smb://Test or smb://TEST are the same. Folder names are also not case sensitive.

I'm not sure about username, but passwords are definitely case sensitive.

---

### Post by dvarsam on 2007-02-19
[QUOTE=louis_nichols]Yes, that is correct.[/quote]

ok

[QUOTE=louis_nichols]Now, the username and password... It may be the problem that miseljt said or it may be a typo indeed. Or it may be something else, that I'm missing.

I'm not sure about the username, but the password will certainly be case-sensitive.
AFAIK, default installations of windows up to XP did not require the user to enter a password (I mean, the field is there but it will let you go on even if left blank), so I would try to leave either password or both username and password blank and then try to connect. I've never had this problem, so we're just using trial and error here.[/quote]

ok, I see!

[QUOTE=louis_nichols]I actually don't know where to enable authentification for accessing files shared by windows.[/QUOTE]

On the Windows PC, you will have to do the following:

**_Part A - Create some users_:**

1. Click on "[color=blue]Start\Control Panel[/color]"

2. Double click on "[color=blue]User Accounts[/color]"

3. Create some Users & assign Passwords to them

**_Part B - Allow users to connect Remotely to the WinXP PC_:**

1. Rght-click on the "[color=blue]My Computer[/color]" icon & select "[color=blue]Properties[/color]"

2. Select the **Tab** named "[color=blue]Remote[/color]"

3. Click on "[color=blue]Allow Remote assistance invitations to be sent from this computer[/color]"

4. Click on "[color=blue]Allow users to connect remotely to this computer[/color]"

5. Click on the button named "[color=blue]Select Remote Users...[/color]"

6. Click on the button named "[color=blue]Add...[/color]"

7. Under the field "[color=blue]Enter the object names to select (examples):[/color]", _type_ the user name you just added - e.g. "[color=blue]Remote[/color]" & then click on the button named "[color=blue]Check Names[/color]"

8. Click on the button named "[color=blue]OK[/color]" & your user names should be added to the list.

9. Click on the button named "[color=blue]ok[/color]" & again on "[color=blue]ok[/color]"

**_Part C - Enable Remote Access from your Windows Firewall_:**

1. Inside the Control Panel, double click on the icon named "[color=blue]Windows Firewall[/color]"

2. Click on the **Tab** named "[color=blue]Exceptions[/color]"

3. Under "[color=blue]Programs and Services:[/color]" make sure everything is selected

4. Click on the button named "[color=blue]ok[/color]"

You should now be ready to access your Windows PC Remotely, as long as your Network wires & drivers are working...

Is there anything that I am missing?

Thanks.

P.S.> Now you know how to do it ;)

---

### Post by dvarsam on 2007-02-19
[QUOTE=louis_nichols]Paths are not case sensitive. smb://test and smb://Test or smb://TEST are the same. Folder names are also not case sensitive.

I'm not sure about username, but passwords are definitely case sensitive.[/QUOTE]

What are you talking about? :confused:
I said that "[color=red]samba[/color]" is NOT installed in my PC!!!

Is the installation of "[color=red]samba[/color]" considered a **requirement**?
You said that samba is needed IF I want Windows to access my Ubuntu files...
I don't want that!!!
I want Ubuntu to be able to access the Windows files...

So why on earth should the path I am trying to access include "[color=red]smb://[/color]" when "samba" is NOT even installed?

Which is considered a correct path:

1. [color=blue]D:\Documents and Settings\Tony\Desktop[/color], **or**
2. [color=blue]\Desktop[/color], **or**
3. None of the above (please provide the appropriate path...)

Thanks.

---

### Post by dvarsam on 2007-02-19
Another Question:

**Does the [color=red]Ubuntu[/color] _Domain_ have to match the [color=red]Windows[/color] _Domain_?**

i.e. Windows uses the "[color=blue]MSHOME[/color]" _Domain_!

How can I find what _Domain_ my [color=red]Ubuntu[/color] uses?
Could that be the problem?

Thanks.

---

### Post by dvarsam on 2007-02-19
[QUOTE=miseljt]3) if you're trying to get directly to ShardDocs, or some other folder in particular, try mapping to the particular share through [color=blue]Places -> Connect to Server[/color], change the service type to Windows Share, and add the 'server' (computer you're trying to connect to) and the share name (folder which you're trying to get into). i've found that this is typically the easiest way for me to map network drives, regardless of being in Windows or Ubuntu. hope some of this helps. :)[/QUOTE]

I tried what you said & typed the following info:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/2-4.png[/IMG]

A "[color=blue]test[/color]" icon was created on my Desktop.
But when I double-click on it, I get the same "[color=blue]Authentification Window[/color]" I provided on the beginning post (see pic provided on Page 1 of this thread!)...

So, what could be wrong?
Thanks.

P.S.> The user name has to be typed as:
1. Tony, **or**
2. tony, **or**
3. TONY

The Domain name has to be typed as:

1. Mshome, **or**
2. MSHOME, **or**
3. mshome, **or**
4. WORKGROUP (if this is the Ubuntu's Domain?). **or**
5. Workgroup (if this is the Ubuntu's Domain?). **or**
6. workgroup (if this is the Ubuntu's Domain?)

And what about the folder path, does that look ok?
(I copied that from Windows...)

---

### Post by ktodac3298 on 2007-02-19
i too have the same problem srry i do not have an answer but i do have a question if u do get it working and u have a netwirked printer connected to the windows pc can u use that to print froml linux

---

### Post by jhenager on 2007-02-19
I haven't tried XP or Vista yet, but I am able to connect to my other Windows 98 computers through SAMBA, and yes, you need it installed if it isn't. (It probably is, unless you specifically turned it off during install.) The SMB icon on the share indicates Samba is running.
First of all, file sharing has to be enabled on the Windoze systems. Also, unless you have a domain controller (probably not) you are dealing with a workgroup, not a domain. 
Connecting to one of my other systems is as easy as typing in this: \\machinename\c$.

---

### Post by dvarsam on 2007-02-19
[QUOTE=jhenager]I haven't tried XP or Vista yet, but I am able to connect to my other Windows 98 computers through SAMBA, and yes, you need it installed if it isn't. (It probably is, unless you specifically turned it off during install).
The SMB icon on the share indicates Samba is running.
[/QUOTE]

Hello & thanks for your reply!
I have got "[color=blue]samba-common[/color]" & "[color=blue]smbclient[/color]" packages installed.
But **NOT** package "[color=red]samba[/color]" installed... (I checked this from "Synaptic")
So is that considered my _only_ option to be able to **copy & paste** files from [color=red]Ubuntu[/color] [color=blue]->[/color] [color=red]Windows[/color] & from [color=red]Windows[/color] [color=blue]->[/color] [color=red]Ubuntu[/color]?

An "smb" icon does NOT exist inside the "[color=blue]Places\Network Servers[/color]" window...

[quote=jhenager]First of all, file sharing has to be enabled on the Windoze systems. Also, unless you have a domain controller (probably not) you are dealing with a workgroup, not a domain. 
Connecting to one of my other systems is as easy as typing in this: \\machinename\c$.[/QUOTE]

On the Windows PC, File & Printer sharing is enabled.
I visited "[color=blue]Start\Control Panel\Windows Firewall\**Tab** Exceptions[/color]" & option "[color=blue]File and Printer Sharing[/color]" is checked!
I also re-runned "[color=blue]Start\Control Panel\Network Setup Wizard[/color]" to make sure "[color=blue]File and Printer Sharing[/color]" is enabled!
Then restarted the Windows PC...

Thanks.

---

### Post by louis_nichols on 2007-02-19
****OK. we are drifting here. I reaffirm:

NO, you do NOT need samba installled to access windows shares. smb:// is the name of the protocol and doesn't imply the installation of samba (just like having http:// in front of an URL when browsing the web doesn't mean you have a server installed, but a browser). The application that is the equivalent to a browser for samba is called smbclient and handles the smb protocol so you don't need samba unless you want to share.

Now, the path used to access a folder must not be absolute. As it is also with windows-to-windows, if you share folder C:\foo\foobar\test from machine *michael* and want to access that from machine *ralphie*, you use the path:

\\ralphie\test

To go on further, if you also share the folder C:\foo\foobar then that will also be in the root of the share, so you'll be able to access the subfolder *test* from 2 places. This is in fact THE EXACT WAY IT HAPPENS IN WINDOWS-TO-WINDOWS SHARING.

that is to say any shared folder from the computer will appear in the root of the shared folders. So, in the case from the screenshot, if you have shared folder D:\Documents and settings\tony\desktop then you access this by just writing **desktop** in the field "share" (I don't know what goes in field "folder" and what is the difference between them, but for accessing a folder, you write it under "share"). My recommendation is to not write anything, as you will access the root anyway and browse shared folders from there.

Of course, the thing that needs to be checked is whether the connection itself is sound. This can be easily tested by pinging the IP of the other computer. If it works, that's all good and you can go on accessing shares. If pinging doesn't work, than this part of the connection must be solved before trying to share.

---

### Post by dvarsam on 2007-02-19
[QUOTE=louis_nichol]****OK. we are drifting here. I reaffirm:

NO, you do NOT need samba installed to access windows shares. smb:// is the name of the protocol and doesn't imply the installation of samba (just like having http:// in front of an URL when browsing the web doesn't mean you have a server installed, but a browser). The application that is the equivalent to a browser for samba is called smbclient and handles the smb protocol so you don't need samba unless you want to share.[/quote]

So, it seems that the package "[color=blue]smbclient[/color] is installed here.
So this is good!

[quote=louis_nichol]...Of course, the thing that needs to be checked is whether the connection itself is sound. This can be easily tested by pinging the IP of the other computer. If it works, that's all good and you can go on accessing shares. If pinging doesn't work, than this part of the connection must be solved before trying to share.[/QUOTE]

I checked this & it works fine!
Output provided:

```
dimitris@dimitris-desktop:~$ [color=blue]ping 192.168.1.5[/color]
PING 192.168.1.5 (192.168.1.5) 56(84) bytes of data.
64 bytes from 192.168.1.5: icmp_seq=1 ttl=128 time=0.136 ms
64 bytes from 192.168.1.5: icmp_seq=2 ttl=128 time=0.134 ms
64 bytes from 192.168.1.5: icmp_seq=3 ttl=128 time=0.133 ms
64 bytes from 192.168.1.5: icmp_seq=4 ttl=128 time=0.133 ms
64 bytes from 192.168.1.5: icmp_seq=5 ttl=128 time=0.131 ms
64 bytes from 192.168.1.5: icmp_seq=6 ttl=128 time=0.133 ms
64 bytes from 192.168.1.5: icmp_seq=7 ttl=128 time=0.131 ms
64 bytes from 192.168.1.5: icmp_seq=8 ttl=128 time=0.135 ms
64 bytes from 192.168.1.5: icmp_seq=9 ttl=128 time=0.132 ms
64 bytes from 192.168.1.5: icmp_seq=10 ttl=128 time=0.131 ms
64 bytes from 192.168.1.5: icmp_seq=11 ttl=128 time=0.132 ms
64 bytes from 192.168.1.5: icmp_seq=12 ttl=128 time=0.135 ms
64 bytes from 192.168.1.5: icmp_seq=13 ttl=128 time=0.133 ms
64 bytes from 192.168.1.5: icmp_seq=14 ttl=128 time=0.130 ms
64 bytes from 192.168.1.5: icmp_seq=15 ttl=128 time=0.132 ms
64 bytes from 192.168.1.5: icmp_seq=16 ttl=128 time=0.133 ms
64 bytes from 192.168.1.5: icmp_seq=17 ttl=128 time=0.132 ms
64 bytes from 192.168.1.5: icmp_seq=18 ttl=128 time=0.133 ms

--- 192.168.1.5 ping statistics ---
18 packets transmitted, 18 received, 0% packet loss, time 17015ms
rtt min/avg/max/mdev = 0.130/0.132/0.136/0.013 ms
```

So, this looks good too!!!

[quote=louis_nichol]Now, the path used to access a folder must not be absolute. As it is also with windows-to-windows, if you share folder C:\foo\foobar\test from machine *michael* and want to access that from machine *ralphie*, you use the path:

\\ralphie\test

To go on further, if you also share the folder C:\foo\foobar then that will also be in the root of the share, so you'll be able to access the subfolder *test* from 2 places. This is in fact THE EXACT WAY IT HAPPENS IN WINDOWS-TO-WINDOWS SHARING.

that is to say any shared folder from the computer will appear in the root of the shared folders. So, in the case from the screenshot, if you have shared folder D:\Documents and settings\tony\desktop then you access this by just writing **desktop** in the field "share" (I don't know what goes in field "folder" and what is the difference between them, but for accessing a folder, you write it under "share"). My recommendation is to not write anything, as you will access the root anyway and browse shared folders from there.
[/QUOTE]

From the Menu, I selected "[color=blue]Places\Connect to Server...[/color]".
The following were typed:
```
Service type: Windows share
Server: [color=blue]192.168.1.5[/color]
Share:
Folder: [color=blue]desktop[/color]
User Name: [color=blue]Tony[/color]
Domain Name:
Name to use for connection: [color=blue]Trial[/color]

```

I then clicked on the button named "[color=blue]Connect[/color]".
A shortcut was created on my Ubuntu Desktop.
I double clicked the shortcut & got this window:

```
**The folder contents could not be displayed.**
"desktop" couldn't be found. [color=red]Perhaps it has recently been deleted.[/color]

Button available: "OK"
```

What does it mean it might have been deleted?
It is there & I can _see_ it!!!
Oh my Goodness, what is going on here?

Thanks.

---

### Post by dvarsam on 2007-02-19
I also tried this:

From the Menu, I selected "[color=blue]Places\Connect to Server...[/color]".
The following were typed:
```
Service type: Windows share
Server: [color=blue]192.168.1.5[/color]
Share:
Folder:
User Name:
Domain Name:
Name to use for connection: [color=blue]Trial[/color]

```

I then clicked on the button named "[color=blue]Connect[/color]".
A shortcut was created on my Ubuntu Desktop.
I double clicked the shortcut & got this window:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/3-5.png[/IMG]

So, I double click on the **2nd icon** & get here:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/4-3.png[/IMG]

I supply the following info:

```
Username: [color=blue]Tony[/color]
Domain: [color=blue]mshome[/color]
Passwork: [color=blue]I type this too![/color]

```

I then click on the button named "[color=blue]Connect[/color]" & get this pic:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/4-3.png[/IMG]

No matter what I type, whenever I click on the button named "[color=blue]Connect[/color]", I always get the same above picture...

How can I fix this?

Thanks.

P.S.> IF I double click on the **3rd icon**, called "[color=blue]SharedDocs[/color]" I have full access on those sub-folders & I can see/access Window's following folders:
1. My Music
2. My Pictures
3. My Videos
How can I access the remaining folders of the Windows machine [i.e. **1rst icon** & **2nd icon** above)?

---

### Post by louis_nichols on 2007-02-19
Well... For starters, you're obviously on the right track.

As for the username/password thing, that's just a detail. :D Really now. It's exactly what happens on windows: asks you for the darned password until you get it right. If it won't give you access, then the username and/or password are not right. Did you also try to leave those fields blank?

Another idea is to check folder permissions for access. Not many know this, but Windows has them too. Especially when it comes to sharing, depending on whether it is XP pro or home or whatever, there can be a button on the Properties>share screen that lets you set access rights. So you could set that to read for everyone and, at least in theory, you shouldn't have to enter the password again.

However, the option for advanced permissions might not be there. Which is not to say that they cannot be set (NTFS is the same for both XP home and pro), but they are not that easily accessible. Access to them can be given by tweaking some registry values or by using Total Commander with the NTFS for TC plugin. There may be other methods.

Anyways, the important thing is that, as far as ubuntu and networking are concerned, you are all set. The rest is really nothing that depends on Ubuntu, whatever the reason for failed access is, I assure you.

---

### Post by petermck on 2007-02-20
I had a bunch of problems getting access to a Windows XP SP2 machine until I went through the Samba documentation in detail.
In the /etc/samba/cmb.conf file under Authentication the default is
```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
   security = user
```
I found I could fix access problems like yours one of two ways;
1. Change to security=share.
2. Create an account on the Ubuntu machine with the same credentials as the Windows account. I found that ultimately, the best solution was just to change one machine account to match the other.
The second way seems more reliable.
There was also a bit in the documentation about 2000/XP needing encrypted password support, which I thing is the default in Samba. Have a look at [HTML]http://www.samba.org[/HTML]. There's a good how to there.
On the windows box all you should need to do is enable file sharing, enable netbios over TCP/IP (go to LAN Properties->Internet Protocol->Advanced and enable this at the bottom of the panel), and share the folder.
Finally, in Vista Microsoft decided to re-write the SMB code and call it SMB2. I have read some posts about problems with Vista and Samba, but I have not had a chance to check it out for myself yet.
I hope this is of some help.
I also found this link [HTML]http://ubuntuguide.org/wiki/Ubuntu_Edgy[/HTML] which has some pretty useful looking stuff.

---

### Post by Ginger The Cat on 2007-02-20
I just noticed louis_nichols said in post #15

...put desktop in field "share"

but in post #16 you said you put it in field "folder"

Worth trying?

Mike

---

### Post by dvarsam on 2007-02-20
[QUOTE=louis_nichols]Well... For starters, you're obviously on the right track.

As for the username/password thing, that's just a detail. :D Really now. It's exactly what happens on windows: asks you for the darned password until you get it right. If it won't give you access, then the username and/or password are not right. Did you also try to leave those fields blank?[/quote]

I tried & tried man...
I also tried leaving those fields blank...
All fields blank except the IP on the **1rst** window & on the **2nd** window, all those fields blank...
Nothing!!!

[quote=louis_nichols]Another idea is to check folder permissions for access. Not many know this, but Windows has them too. Especially when it comes to sharing, depending on whether it is XP pro or home or whatever, there can be a button on the [color=blue]Properties>share screen[/color] that lets you set access rights. So you could set that to read for everyone and, at least in theory, you shouldn't have to enter the password again.[/quote]

I right clicked on the "D" Hard Drive & selected "[color=blue]Sharing and Security[/color]"!
I then selected "[color=blue]Share this folder on a network[/color]" & "[color=blue]Allow network users to change my files[/color]".
I restarted the Windows PC & tried to access the NTFS Hard Drive...
I try to access "D:\Program Files" & get this:

```
**The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "Program Files".

Button available: OK
```

Basically, it seems that I can't access anything except "[color=blue]Documents\My Pictures, My Video & My Music[/color]"... :-k

[quote=louis_nichols]However, the option for advanced permissions might not be there. Which is not to say that they cannot be set (NTFS is the same for both XP home and pro), but they are not that easily accessible. Access to them can be given by tweaking some registry values or by using [color=blue]Total Commander with the NTFS for TC plugin[/color]. There may be other methods.[/quote]

Can you provide more info on this?

[quote=louis_nichols]Anyways, the important thing is that, as far as ubuntu and networking are concerned, you are all set. The rest is really nothing that depends on Ubuntu, whatever the reason for failed access is, I assure you.[/QUOTE]

I know...
But still it can't work...
Thanks.

---

### Post by dvarsam on 2007-02-20
[QUOTE=Ginger The Cat]I just noticed louis_nichols said in **post #15**

...put desktop in field "[color=blue]share[/color]"

but in **post #16** you said you put it in field "[color=blue]folder[/color]"
Worth trying?
Mike[/QUOTE]

Thanks for your reply!
I tried that & it did NOT work... :(

---

### Post by irish_flu on 2007-02-20
It looks to me like the user you're logging in as doesn't have permissions (on the Windows machine) to view those folders remotely.

The "shared docs" icon, I believe, lets anyone on the network look at it.

Any chance the user you're trying to use is not an administrator on your Windows XP box?

---

### Post by dvarsam on 2007-02-20
> **petermck]I had a bunch of problems getting access to a Windows XP SP2 machine until I went through the Samba documentation in detail.
In the "[color=blue]/etc/samba/cmb.conf[/color]" file under Authentication the default is
```
# "[color=blue]security = user[/color]" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
   security = user
```

I found I could fix access problems like yours one of two ways said:**
> security=share[/color]".
2. Create an account on the Ubuntu machine with the same credentials as the Windows account. I found that ultimately, the best solution was just to change one machine account to match the other.
The second way seems more reliable.


I tried using:

1. "[color=blue]security = user[/color]" & "[color=blue]/etc/init.d/samba restart[/color]"
Nothing man... nothing...

2. "[color=blue]security = share[/color]" & "[color=blue]/etc/init.d/samba restart[/color]"
Again nothing... :(

Of course your solution is proposing to find a way to Connect from [color=red]WinXP[/color] [color=blue]->[/color] [color=red]Ubuntu[/color] & accessing Ubuntu's files from a WinXP machine...
I would like to do this, but I am also interested for the opposite too!

[QUOTE=petermck]There was also a bit in the documentation about 2000/XP needing encrypted password support, which I thing is the default in Samba. Have a look at [HTML]http://www.samba.org[/HTML]. There's a good how to there.
On the [color=red]Windows[/color] box all you should need to do is "[color=blue]Enable File Sharing[/color]", "[color=blue]Enable Netbios over TCP/IP[/color]" (go to LAN Properties->Internet Protocol->Advanced & enable this at the bottom of the panel), and share the folder.[/quote]

From the Windows side, when I visit the "[color=blue]My Network Places\Entire Network\Microsoft Windows Network\Mshome\...[/color]", I can see an icon representing my Ubuntu PC!
But I can't connect to it...
I am getting this screen:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/5.jpg[/IMG]

[QUOTE=petermck]Finally, in Vista Microsoft decided to re-write the SMB code and call it SMB2. I have read some posts about problems with Vista and Samba, but I have not had a chance to check it out for myself yet.
I hope this is of some help.
I also found this link [HTML]http://ubuntuguide.org/wiki/Ubuntu_Edgy[/HTML] which has some pretty useful looking stuff.[/QUOTE]

I don't care about Vista...
I don't want to try them...
Everything is not working very well with Ubuntu...
i.e. the new MS Office Format does NOT work with Ubuntu's OOO format (from what I have heard)...

I feel so tired tonight.
I just came back from work...
Maybe I will try a little more tomorrow...

Thanks.

---

### Post by dvarsam on 2007-02-20
[QUOTE=irish_flu]It looks to me like the user you're logging in as doesn't have permissions (on the Windows machine) to view those folders remotely.[/quote]

Currently, the Windows PC has the following users listed:

1. **Tony**
Computer administrator
Password protected

2. **Remote**
Computer administrator
Password protected

I can't understand what else could be missing... :confused:

[quote=irish_flu]The "[color=blue]shared docs[/color]" icon, I believe, lets anyone on the network look at it.

Any chance the user you're trying to use is not an administrator on your Windows XP box?[/QUOTE]

For the "[color=blue]shared docs[/color]" icon, are you referring on the Windows side:

Opening the "[color=blue]My Computer[/color]" folder & right clicking on the "D" icon & selecting "[color=blue]Sharing and Security...[/color]"?
Is this what you are talking about?
OR are you referring on "[color=blue]security = share[/color]" on the "[color=blue]/etc/samba/smb.conf[/color]" file on the Ubuntu side?

Also, from what I provided, it seems that both users have administrating rights on the Windows side...

Anyway, this is what my "[color=blue]/etc/samba/smb.conf[/color]" contents look like:

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   [color=red]workgroup = MSHOME[/color]

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user

[color=blue]# I changed the above to:
; security = user
# But it did NOT work - then tried using:
security = share
# But it did NOT work either...!!![/color]

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de$
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spasswor$

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
# 
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration

# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)

# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes

  read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
# 
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


```

The above is what my **original** "[color=blue]/etc/samba/smb.conf[/color]" file looks like...
The blue parts are the ones I have changed...
I am NOT sure about this part: "[color=red]workgroup = MSHOME[/color]"...
How can I find what my "workgroup" is in Ubuntu?
Thanks.

P.S.> Sorry guys, as I said, I am very tired...
I got up at 06:30am today & got back from work at 22:00pm. :(
I am dead & need to sleep...
I will try to work on this more tomorrow...

---

### Post by BikerGeek on 2007-02-20
With Windows XP Home Edition you'll probably find it beneficial to turn off Simple File Sharing if you want access to folders other than SharedDocs.

I don't think you HAVE to though. But if you decide to do so, just open My Computer, click on Tools, then Folder options, then the View tab. Should be the second tab if you're not using an English code page on your Widnows machine. Scroll down until you see "use Simple File Sharing(recommended)" in the Advanced Setting box.

the C$ and D$ you see and can't access are what Windows refers to as "Administrative Shares". The $ makes them hidden from view if browsed using My Network Places or "net view" commands from the command line and they are not accessible by regular users without entering an admin password.

Also, being that you have a peer to peer workgroup setup instead of a domain with a domain controller, try using MACHINENAME\USERNAME where it asks for username.  Replace MACHINENAME with the machine's actual name and replace USERNAME with Remote I think you said you created. 

So the username will look like WINDOWSBOX\Remote. Use MSHOME for the wrokgroup and enter the correct password that you used when you created the user Remote on the Windows box.

Unless I've missed a few posts, I think that'll get you from the ubuntu box to the shares on the Windows box.

Also, I'm not sure there is but from looking at the screenshots and the text going along with them, there seems to be some confusion about Windows SHARES and Folder PATHs so forgive me if there's no actual confusion and I sound condescending, I'm only trying to help. 

Shares reference the PATH. I'll try to explain:

Share something on the Windows box. Let's say your machine is named WindowsBox and you shared the folder 
C:\MyFiles\ShareTheseFiles as MySharedFiles. The SHARE(MySharedFiles) you create refers to the PATH(C:\MyFiles\ShareTheseFiles). Actually it refers to the Universal Naming Convention (UNC) path but we'll leave that out for now.

So when you try to connect across a network to this share, you'd connect to (in the windows world) \\WindowsBox\MySharedFiles. 

That's it. No C:\MyFiles\ShareTheseFiles or anything else, just machinename\sharename.

Man. Hope I didn't just make it worse.<g> I'll be setting up my machines for the same thing, maybe tonight, so I'll check back and see if the post has been updated.

---

### Post by BikerGeek on 2007-02-20
Your WORKGROUP is whatever you chose to name it. You need to match the setting in SAMBA with the setting in Windows, which you have done with this line:

workgroup = MSHOME

---

### Post by dvarsam on 2007-02-21
[QUOTE=BikerGeek]With Windows XP Home Edition you'll probably find it beneficial to turn off Simple File Sharing if you want access to folders other than SharedDocs.

I don't think you HAVE to though. But if you decide to do so, just open My Computer, click on Tools, then Folder options, then the View tab. Should be the second tab if you're not using an English code page on your Widnows machine. Scroll down until you see "use Simple File Sharing(recommended)" in the Advanced Setting box.[/quote]

Thanks for your reply!
I currently want to connect an [color=red]Ubuntu v6.10[/color] PC with a [color=red]WinXP Pro SP2[/color] PC.
I performed what you suggested:

1. I double clicked on "[color=blue]My Computer[/color]" icon
2. From the Menu, I selected "[color=blue]Tools\Folder Options...[/color]"
3. I click on the **Tab** named "[color=blue]View[/color]"
4. Under "Advanced settings:", I scroll down to make sure "[color=blue]Use simple file sharing (Recommended)[/color]" is checked.

It was _already_ checked...

[quote=BikerGeek]the "[color=blue]C$[/color]" and "[color=blue]D$[/color]" you see and can't access are what Windows refers to as "[color=blue]Administrative Shares[/color]". The $ makes them hidden from view if browsed using "My Network Places" or "net view" commands from the command line and they are not accessible by regular users without entering an admin password.[/quote]

Thanks, I did NOT know that...
I thought that "[color=blue]C$[/color]" and "[color=blue]D$[/color]" referred to Hard Drives...
Does that mean that I can NOT double click on a "[color=blue]D$[/color]" icon to access its contents?

[quote=BikerGeek]Also, being that you have a peer to peer workgroup setup instead of a domain with a domain controller, try using "[color=blue]MACHINENAME\USERNAME[/color]" where it asks for username.  Replace MACHINENAME with the machine's actual name and replace USERNAME with "Remote" I think you said you created. 

So the username will look like "WINDOWSBOX\Remote". Use "[color=blue]MSHOME[/color]" for the workgroup and enter the correct password that you used when you created the user Remote on the Windows box.

Unless I've missed a few posts, I think that'll get you from the Ubuntu box to the shares on the Windows box.[/quote]

Ok
So, from the Menu I selected "[color=blue]Places\Connect to Server...[/color]".

The following were typed:

```
Service type: [color=blue]Windows share[/color]
Server: [color=blue]\\192.168.1.5\Remote[/color]
Share:[color=blue] desktop[/color]
Folder:
User Name: [color=blue]Remote[/color]
Domain Name:
Name to use for connection: [color=blue]Trial[/color]
```

And get this popup window:

```
**The folder contents could not be displayed.**
Sorry, couldn't display all the contents of "Trial".

Button available: "OK"

```

It seems that things are looking better...
But still, I can't seem to have any access! :-k

[quote=BikerGeek]Also, I'm not sure there is but from looking at the screenshots and the text going along with them, there seems to be some confusion about "[color=blue]Windows SHARES[/color]" and "[color=blue]Folder PATHs[/color]" so forgive me if there's no actual confusion and I sound condescending, I'm only trying to help. 

Shares reference the PATH. I'll try to explain:
Share something on the Windows box. Let's say your machine is named WindowsBox and you shared the folder 
C:\MyFiles\ShareTheseFiles as MySharedFiles. The SHARE (MySharedFiles) you create refers to the PATH(C:\MyFiles\ShareTheseFiles). Actually it refers to the Universal Naming Convention (UNC) path but we'll leave that out for now.

So when you try to connect across a network to this share, you'd connect to (in the windows world) \\WindowsBox\MySharedFiles. 

That's it. No C:\MyFiles\ShareTheseFiles or anything else, just machinename\sharename.

Man. Hope I didn't just make it worse.<g> I'll be setting up my machines for the same thing, maybe tonight, so I'll check back and see if the post has been updated.[/QUOTE]

I like to keep things practical...
So, when from the Menu I select "[color=blue]Places\Connect to Server...[/color]", what do I type in the field named "[color=blue]Server:[/color]"?

1. This: "[color=blue]\\192.168.1.5\Remote[/color]", **or**
2. This: "[color=blue]\\192.168.1.5\desktop[/color]"

Thanks.

---

### Post by BikerGeek on 2007-02-21
> 4. Under "Advanced settings:", I scroll down to make sure "Use simple file sharing (Recommended)" is checked.

Simple sharing should be UNchecked as we DO NOT want to use it. Feel free to try it with it enabled though. I only turn it off to enable sharing of folders that Simple Sharing doesn't allow and because with XP Home you can't set NTFS permissions without a hack. Turning it off is the first part of the hack.

> Server: \\192.168.1.5\Remote
Share: desktop
Folder:
User Name: Remote
Domain Name:
Name to use for connection: Trial

What name did you assign to the share you created? Or did you actually create one yet?

192.168.1.5 is the machine you created the user named Remote on, correct? 

Without having it tried it myself yet, I think you should be using \\192.168.1.5 for the Server field, desktop for the Share field assuming that's the sharename you're trying to connect to, leave the Folder field blank (I think), and \\192.168.1.5\Remote in the User Name field, and possibly MSHOME in the Domain Name field. 

> So, when from the Menu I select "Places\Connect to Server...", what do I type in the field named "Server:"?

1. This: "\\192.168.1.5\Remote", or
2. This: "\\192.168.1.5\desktop"

See above. I think you should only have the server's ip in the Server field.

---

### Post by BikerGeek on 2007-02-21
Ok, all done. I'll start from the very absolute beginning so this is gonna be long. Don't laugh at the names, my wife has a thing for Winnie the Pooh.<G> Also, this is just from the ubuntu box to the Windows box, not from Windows to ubuntu. 

It assumes Windows Simple File Sharing is enabled on the Windows machine, permissions of Everyone Read, and a default install of ubuntu with no name resolution other than broadcast setup yet, so we'll use ip addresses instead of hostnames for now.

Windows box:
Name: Tigger
IP: 192.168.1.102
WorkgroupName: 100AcreWood
SharePath: c:\DVD Tools
ShareName: DVD_Tools
UNCPathToShare: \\192.168.1.102\DVD_Tools
Account:BikerGeek
 
1) From ubuntu, click on Places and select Network Server. That should display a Windows Network icon.
2) Doubleclick that Windows Network icon.
3) Select File, Connect to Server
2) The Service type should already be Windows Share.
3) Type the ip address of the machine we want to connect TO in the Server field, in this case 192.168.1.102. Don't lead it with anything, type ONLY the ip address.
5) Put the ShareName in the Share field, in this case DVD_Tools
6) Leave the Folder field blank
7) Type in the unsername, BikerGeek
8) Type 100AcreWood for the Domain Name
9) Give it a name, Tigger
10) Since you gave it all the information it should create an icon on the desktop named Tigger.
11)Doubleclick Tigger and be prompted for a password. Type it in, decide if you want to save it and how, and now have access to the files in DVD_Temp.

---

### Post by dvarsam on 2007-02-23
[QUOTE=BikerGeek]Simple sharing should be UNchecked as we DO NOT want to use it. Feel free to try it with it enabled though. I only turn it off to enable sharing of folders that Simple Sharing doesn't allow and because with XP Home you can't set NTFS permissions without a hack. Turning it off is the first part of the hack.[/quote]

I _disabled_ [color=blue]Simple sharing[/color].


[QUOTE=BikerGeek]What name did you assign to the share you created? Or did you actually create one yet?[/quote]

What do you mean?
On the windows side?
Lets assume that I perform the following:

1. On the Windows desktop, I right-click & select "[color=blue]New\Folder[/color]".

2. I right-click on the folder & select "[color=blue]Sharing and Security...[/color]"

3. I click on the checkbox named "[color=blue]Share this folder on the network[/color]"

4. Under "[color=blue]Share name:[/color]", I type "[color=blue]Trial[/color]"

5. I click on the button named "[color=blue]Apply[/color]" & then on "[color=blue]OK[/color]".

[QUOTE=BikerGeek]192.168.1.5 is the machine you created the user named Remote on, correct?[/quote]

Yes, correct!

[QUOTE=BikerGeek]Without having it tried it myself yet, I think you should be using \\192.168.1.5 for the Server field, desktop for the Share field assuming that's the sharename you're trying to connect to, leave the Folder field blank (I think), and \\192.168.1.5\Remote in the User Name field, and possibly MSHOME in the Domain Name field. 

See above. I think you should only have the server's IP in the Server field.[/QUOTE]

So, I tried the following:

```
Service type: [color=blue]Windows share[/color]
Server: [color=blue]\\192.168.1.5[/color]
Share: [color=blue]Trial[/color]
Folder: 
User Name: [color=blue]\\192.168.1.5\Remote[/color]
Domain Name: [color=blue]MSHOME[/color]
Name to use for connection: [color=blue]Truly Hoping[/color]

```

And get this popup window:

```

**The folder contents could not be displayed.**
Sorry, couldn't display all the contents of "Trial".

Button available: "OK"
```

](*,)

---

### Post by dvarsam on 2007-02-23
[QUOTE=BikerGeek]Ok, all done. I'll start from the very absolute beginning so this is gonna be long. Don't laugh at the names, my wife has a thing for Winnie the Pooh.<G> Also, this is just from the Ubuntu box to the Windows box, not from Windows to Ubuntu.[/quote]

No problem... man...

[QUOTE=BikerGeek]It assumes [color=blue]Windows Simple File Sharing[/color] is [color=blue]enabled[/color] on the Windows machine, [color=blue]permissions of Everyone Read[/color], and a default install of Ubuntu with [color=blue]no Name Resolution[/color] other than broadcast setup yet, so we'll use IP addresses instead of hostnames for now.[/quote]

Ok man...
I re-enabled [color=blue]Windows Simple File Sharing[/color].
For the previously created Shared Folder, I checked its properties, and [color=blue]permissions of Everyone is Read[/color].
I _have_  [color=blue]no Name Resolution[/color]  other than broadcast.
What I don't have is patience man....
I am exhausted...
I worked a full 12 hours today! :(

[QUOTE=BikerGeek]Windows box:
Name: Tigger
IP: 192.168.1.102
WorkgroupName: 100AcreWood
SharePath: c:\DVD Tools
ShareName: DVD_Tools
UNCPathToShare: \\192.168.1.102\DVD_Tools
Account:BikerGeek
 
1) From Ubuntu, click on Places and select Network Server. That should display a Windows Network icon.
2) Double click that Windows Network icon.
3) Select File, Connect to Server
2) The Service type should already be Windows Share.
3) Type the ip address of the machine we want to connect TO in the Server field, in this case 192.168.1.102. Don't lead it with anything, type ONLY the ip address.
5) Put the ShareName in the Share field, in this case DVD_Tools
6) Leave the Folder field blank
7) Type in the unsername, BikerGeek
8) Type 100AcreWood for the Domain Name
9) Give it a name, Tigger
10) Since you gave it all the information it should create an icon on the desktop named Tigger.
11)Doubleclick Tigger and be prompted for a password. Type it in, decide if you want to save it and how, and now have access to the files in DVD_Temp.[/QUOTE]

I did as you said...

```
Service type: [color=blue]Windows share[/color]
Server: [color=blue]192.168.1.5[/color]
Share: [color=blue]D:\Documents and Settings\Tony\Desktop\Trial[/color]
Folder: [color=blue]D:\Documents and Settings\Tony\Desktop\New Folder[/color]
User Name: [color=blue]Remote[/color]
Domain Name: [color=blue]MSHOME[/color]
Name to use for connection: [color=blue]Getting Tired[/color]

```

Now I get a different error:
```
**Couldn't find "smb://Mshome%3BRemote@192.16...Tony%5CDesktop%5CNew%20Folder".**
Please check the spelling and try again.

Button available: "OK"
```

:confused:

---

### Post by BikerGeek on 2007-02-23
> **dvarsam said:**
> I did as you said...

```
Service type: [color=blue]Windows share[/color]
Server: [color=blue]192.168.1.5[/color]
Share: [color=blue]D:\Documents and Settings\Tony\Desktop\Trial[/color]
Folder: [color=blue]D:\Documents and Settings\Tony\Desktop\New Folder[/color]
User Name: [color=blue]Remote[/color]
Domain Name: [color=blue]MSHOME[/color]
Name to use for connection: [color=blue]Getting Tired[/color]

```


Almost did. :)

Server is correct.

Enter Trial in the Share field. Nothing else, just the word Trial. The SHARE name is Trial, what you actually entered is the PATH to the SHARE. And a LOCAL path at that.

Don't enter anything in the Folder field. It's supposedly used to open a particular folder within a SHARE. I didn't try it and until you get basic connectivity working there's no reason to.

Username is correct.

Domain name is correct.

Name to use for connection has GOT to be correct by now! :D

If it makes you feel any better I've been fighting with the ivtv drivers and a PVR150 for 3 weeks now so you're not the only one getting tired.

> Now I get a different error:
```
**Couldn't find "smb://Mshome%3BRemote@192.16...Tony%5CDesktop%5CNew%20Folder".**
Please check the spelling and try again.

Button available: "OK"
```

:confused:

You should get prompted for a password and connected once you enter it if you follow the above corrections, at the very LEAST you should get a different error. :) Remember to enter the password of the user named Remote, not the one you're using on the ubuntu box.

---

### Post by dvarsam on 2007-02-25
[QUOTE=BikerGeek]Almost did. :)

Server is correct.

Enter [color=blue]Trial[/color] in the Share field. Nothing else, just the word Trial. The SHARE name is Trial, what you actually entered is the PATH to the SHARE. And a LOCAL path at that.

Don't enter anything in the Folder field. It's supposedly used to open a particular folder within a SHARE. I didn't try it and until you get basic connectivity working there's no reason to.

Username is correct.

Domain name is correct.

Name to use for connection has GOT to be correct by now! :D[/quote]

I tried that & it did NOT work!!! :(
An icon is created on My Desktop - but things are worse!!!
I double click it to open, right click it, tried everything & get no Response or Error...
So, basically, that is NOT it either!!! :-k

[QUOTE=BikerGeek]If it makes you feel any better I've been fighting with the ivtv drivers and a PVR150 for 3 weeks now so you're not the only one getting tired.[/quote]

Oh my man...
Good luck!!!
I know the feeling man...
This is one of the reasons i don't buy a TV card yet - I want to wait until companies start supporting Ubuntu too!

[QUOTE=BikerGeek]You should get prompted for a password & connected once you enter it if you follow the above corrections, [color=blue]at the very LEAST you should get a different error.[/color] :) Remember to enter the password of the user named Remote, not the one you're using on the ubuntu box.[/QUOTE]

I guess I got the "least" of the "least" result, if you know what I mean... lol
**I can't get any output!!!**
It can't get worse, can it?

Thanks.

---

### Post by superm1 on 2007-02-26
> **BikerGeek said:**
> 
If it makes you feel any better I've been fighting with the ivtv drivers and a PVR150 for 3 weeks now so you're not the only one getting tired.

Do you have a thread opened about this?  If so point me at it, i'll try to give you a hand.

---

### Post by NJC on 2007-03-05
Bikergeek, have you seen this thread? 

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by BikerGeek on 2007-03-06
Nah I don't but thanks, it might come to that. <G>
> **superm1 said:**
> Do you have a thread opened about this?  If so point me at it, i'll try to give you a hand.

---

