---
title: "Access Windows Shares Via a Samba Web Share"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-11-12
Hey All,

I have been trying to get Webdav working with my W3K file servers , but there seems to be a massive overhead, which means if more than about 25 users use it at once it runs very slow... so I tried accessing them Via a samba share and wow the speed increased was about 10 fold!

Now I'm wondering if it's possible to setup a Samba Web Client to access Windows Shares... From my Ubuntu Server?

I have tried smbwebclient.php, which is good but realised it doesn’t map to home directories!
   
I would like to be able to get samba to map to a share like: domain/fileserver/users$/%username% over the web...
  Any Ideas???

---

### Post by robinlennox on 2007-11-23
Any Ideas??

---

### Post by popch on 2007-11-23
Not quite sure if I can follow you here.  Let us take this step by tiny step.

You have a server which offers files to your users. I have never heard of a W3k server. Would that be a W2k server, by any chance? 

You say that you are using webdav for those file shares, and that this was pretty slow. 

If you are really using a Windows server, why use webdav at all, and not the native SMB protocol which is the default for Windows shares?

Any Ubuntu client (as installed off the liveCD) can access SMB shares. The SAMBA client is already installed. Use the Places/Network menu to browse your Windows network and to find and attach file servers.

The term Samba Web client appears to be a contradiction in terms. Webdav is a web protocol, i.e. an extension to http. SMB is an ancient file sharing protocol initially invented by IBM, I believe, it is now used by Windows file servers and by other computers offering file shares to Windows clients. It is not used in the Web at all, I shall hope.

You are speaking about a Ubuntu server needing access to files shared by a Windows server. If it is not already installed, your server needs the samba client installed. Use synaptics. Sorry, I don't know the name of the package to use from off the top of my head.

By the way, why does the Ubuntu server have to access those directories on the Windows server?  Why not place them on the Ubuntu server?

Now comes another part of your quest which I do not understand: the home directory bit. Does a 'home directory' in this context mean the home directory of a user logging onto your Ubuntu server?

If so, your problem can be dissected into several parts.

Firstly, you create the home directory on the Windows server and create a hidden share for that directory. A share is hidden if its name ends with a dollar sign.

Next, you have to attach each of those directories to the server. Use SMBMOUNT to do that. If you do not find out how to use SMBMOUNT, start a new thread. I know the command name but I do not know how to use it, either.

As an alternative, you could create a directory on the Windows server holding all the 'home directories' for all users. Create a share for that directory only, and attach the share to the Ubuntu server (using SMBMOUNT, again). Create user's home directories within this share from within Ubuntu.

---

### Post by robinlennox on 2007-11-23
I have a Windows 2003 Server with Active Directory setup...  I have set home drives for all users.

The homedirectory are: \\fileserver.mydomain.org\shares$\%username%

I have an Ubuntu Server running 6.06, which i user as my web server. I want the users to access there home drives via a web interface on the website which runs on this server.


I.E
[LIST]
[*]User goes to [https://www.mydomain.org/homedir.php](https://www.mydomain.org/homedir.php)
[*]The user will be asked for their Username/Password (Their A/D Username/Password)
[*]Once the user is authenticated with the DC, they are present wth a web interface showing there file and folders in there homedirectory on the fileserver.[/LIST]I want them to have an interface simlair to that of webdav.

Hope this is a bit more clear.

---

### Post by popch on 2007-11-23
Now it's much clearer to me.

The problem can be divided into parts.

Part1: mount the share \\fileserver.mydomain.org\shares$ on your ubuntu server (using the smb client and smbmount) on some mountpoint convenient for the task. That's the easy part.

Part 2: find some web server or plug in which does webdav. I do not know if such exist, but it is reasonable to assume since webdav is an extension to http. Without knowing, I would speculate that chances are good that apache already does webdav. Perhaps others in this forum know. However, I would suggest taking that particular question to another subforum. It probably does not qualify as an absolute beginner's question.

Part 3: Find out if your clients (presumably the browser)  can actually use webdav. 

Part 4: If your clients can not use webdav, there's no point in offering it from your web server. Rather look for some product which lets users browse their directories and let them up- and download files using a 'normal' browser window.

I realize that I have not actually solved your problem. Still, I hope that I could contribute so that you can find parts of your solution on your own.

---

### Post by robinlennox on 2007-11-24
Thanks for the help popch... I have some fresh ideas, to think about now :)

---

