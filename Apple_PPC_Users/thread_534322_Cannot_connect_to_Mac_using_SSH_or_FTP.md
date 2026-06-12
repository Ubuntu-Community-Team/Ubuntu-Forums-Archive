---
title: "Cannot connect to Mac using SSH or FTP?"
date: 2007-08-25
forum: Apple PPC Users
---

### Post by edanastas on 2007-08-25
Does anyone know how to connect to a mac from Ubuntu?

I see the computer in my Network but when I try and connect to it, it takes about 3-5 minutes and then it says that it can't connect.

I also tried using FTP to the local computer and still the same problem.

I was thinking it had something to do with Directory Access on the Mac. Does anyone have the procedure or the settings?

Thanks

---

### Post by cwskas on 2007-08-25
Assuming it is your Mac or you have admin privileges... check the System Preferences on the Mac.  Click on Sharing and then firewall and see if those services are blocked?

Willie

---

### Post by edanastas on 2007-08-25
Yeah it's my Mac and I have all the services activated and the Firewalls active too. I tried to connect over one of the open TCP ports but nothing. The funny thing to me is that I can connect using "ssh [email]username@host.loca[/email]l".

It seems like it is working now using rsync
```
sudo rsync -a [email]username@host.loca[/email]l:[SRC] [DST] 
```

Once I did the rsync connection, it gave me a message that
[INDENT]"The authenticity of host 'host.local (192.168.1.100)' Can't be established. RSA key fingerprint is [yada]. Are you sure you want to contineu connection (yes/no)?"[/INDENT]
so I said yes and then I got a Warning? [INDENT]"Permanently added 'host info' (RSA) to the list of known hosts".[/INDENT]

So maybe now it will work with the file browser too? ...nope just checked it's still not working.

---

### Post by edanastas on 2007-08-25
So, shutting the Firewall off for FTP on the Mac worked only with the FTP connection, but not File Sharing yet? I did specify which port it was on while the firewall was on and apparently it still did not let it pass through?

Maybe I need to setup an SSL on my Mac?

---

### Post by stmiller on 2007-08-25
In OS X System Prefs>Sharing> enable remote connections 

(I think that is what it is called) to enable ssh.

---

### Post by edanastas on 2007-08-25
Yes, I have "Remote Apple Events" active and "Remote Login - SSH" is that the same thing as Remote Connections? I have been able to access it via ftp which seems to work, but doesn't really seem like the right way to do it. I would also prefer to activate my firewall, rather than leave it open all the time.

---

### Post by walter_f on 2007-08-29
> **edanastas said:**
> Yes, I have "Remote Apple Events" active and "Remote Login - SSH" is that the same thing as Remote Connections? I have been able to access it via ftp which seems to work, but doesn't really seem like the right way to do it. I would also prefer to activate my firewall, rather than leave it open all the time.

I think "Remote Apple Events" is just applicable Mac-to-Mac (i.e., between computers running Mac OS), so you might turn it off if there is not another Mac-OS-Mac ;-) around...

Having "Remote Login" activated should be the Option you are looking for in order to get SSH access (platform- independent). 

On my Mac OS X, using German settings, it is called "Entfernte Anmeldung" - as close as a Babelfish translation can get to "Remote Login" ;-)

Regards,

Walter.

---

### Post by jltnol on 2007-09-20
Ok...

This works for me in connecting FROM Ubuntu TO Mac.

On the Mac end:

1. under the services tab of the sharing pane, check "Remote Login".  This will enable SSH connections.

2. It won't matter if your firewall is on or off, because checking the tab under services will enable that to pass thru the firewall regardless of whether its off...or on.


On the Ubuntu side:

Go to Places>Network.

Your Mac OSX box should show up as a folder with a little SSH on it. Double Click.. and you should see the contents of your Mac HD.  Navigate down to the Users Folders, then to your home folder.


Somewhere along the line, you'll need to log in with your Mac username and password... but I saved mine, so don't remember where in the process it happens




NOW... does anyone know how to do the reverse?  Connect to Ubuntu form Mac?

I've found the "Shared Folders" icon, and have enable a folder to share, named it, set up SMB sharing, can log in from the Mac, but can't authenticate into Ubuntu. 

Any ideas ?

---

