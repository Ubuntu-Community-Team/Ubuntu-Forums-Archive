---
title: "Samba + Home Networking"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Jaydos on 2007-01-14
Hello all again xD!
I am on a home network and was wondering if anyone could possibly point me in the right direction to resolve my samba issues.
I tried to follow the HOWTO at [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)
I handled it all right up until configuring the windows box (Sort of, lol). 
```
netbios name = YOUR_HOSTNAME
```Does this refer to my login/username? I am unsure what it means by "what I configured upon installation"
```
 wins support = yes
```How do I know whether to use yes/no option? Is there a utility to find out if my IP is static? Or is there some more information that I could possibly give you?

Seeing as I was unsure of the whole WINS support thing, it all fell apart after that. I** think** it's only that issue that's stopping me at the moment. Although in regards to the latter part of the HOWTO;
For the [MyFiles] section, I created a folder in my home/jayden called xfer, so would the path = /home/jayden/xfer?

With setting up accounts, I blundered a bit, I accidentally copy and pasted the guide, so I'm guessing I have a user login named mark somewhere around, what file/database/command would I use to refresh/delete and/or clear the users?
Hrm, in relation to users, the windows box has the same login as me (Only difference is a capital first letter), will this cause conflictions? Should I reconfigure the default user on the windows box?

Last query (Thank god!); when mapping the network drive on the windows box (location), would it read like this;
WINS Support version: \\***nocluewhatgoeshere***\home\jayden\xfer
WINS Not Supported:  \\10.1.1.4\home\jayden\xfer

Just as a bit of additional information;
Two computers (Ubuntu and windows box) connected to a hub with my modem/router as uplink (Should I be configuring anything in my router?).

Thanks in advance for any tidbits of advice/help you can give me :).

---

### Post by jvc26 on 2007-01-14
Hio there as to the netbios name, it is the name you want the computer to have on the windows network (like the name you give to your windows pc) so you can choose technically whatever you want - no spaces or odd characters though.
Static IP - go to System->Administration->Networking then select the ethernet/whatever connector you use, then go to properties and you can set up a static IP in there.

Theres a couple of things to help you :)
Il

---

### Post by Jaydos on 2007-01-15
Hrm, well I found out where my netbios name is (Networking -> General). But the rest is eluding me as of yet.

---

### Post by Fitzy_oz on 2007-01-15
> **Jaydos said:**
> Hello all again xD!
I am on a home network and was wondering if anyone could possibly point me in the right direction to resolve my samba issues.
I tried to follow the HOWTO at [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)
I handled it all right up until configuring the windows box (Sort of, lol). 
```
netbios name = YOUR_HOSTNAME
```Does this refer to my login/username? I am unsure what it means by "what I configured upon installation" - [COLOR="Blue"]This is the name of your Linux Box - What the rest of the network will see[/COLOR]
```
 wins support = yes
```How do I know whether to use yes/no option? Is there a utility to find out if my IP is static? Or is there some more information that I could possibly give you? [COLOR="blue"]Use WINS, it will not hurt it to be turned on[/COLOR]

Seeing as I was unsure of the whole WINS support thing, it all fell apart after that. I** think** it's only that issue that's stopping me at the moment. Although in regards to the latter part of the HOWTO;
For the [MyFiles] section, I created a folder in my home/jayden called xfer, so would the path = /home/jayden/xfer?

With setting up accounts, I blundered a bit, I accidentally copy and pasted the guide, so I'm guessing I have a user login named mark somewhere around, what file/database/command would I use to refresh/delete and/or clear the users?
Hrm, in relation to users, the windows box has the same login as me (Only difference is a capital first letter), will this cause conflictions? Should I reconfigure the default user on the windows box?

Last query (Thank god!); when mapping the network drive on the windows box (location), would it read like this;
WINS Support version: \\***nocluewhatgoeshere***\home\jayden\xfer
WINS Not Supported:  \\10.1.1.4\home\jayden\xfer

Just as a bit of additional information;
Two computers (Ubuntu and windows box) connected to a hub with my modem/router as uplink (Should I be configuring anything in my router?).

Thanks in advance for any tidbits of advice/help you can give me :).


OK - Accessing your windows box from Ubuntu should be very straigt forward.  Instead of using \\<computername> or \\<Ip Address> you simply use smb://<computer Name> or smb://<ip address>.  

Accessing your ubuntu box from windows will require a few additional steps.  Firstly.
Setup a windows user account for you Ubuntu box.  jump to the command line and type the following:
smbpasswd -a <your username on the ubuntu box>

This will ask you to type and verify a password.

Once this is done, the next time you try to access the ubuntu box via windows it will ask you for a username and password, it will be the same as the username and password you use to login to ubuntu.  You can configure your shared directories by opening the Settings -> administration (i think if not it's preferences) -> sharing and simply add the folders you wish to share to the list and voila` it's ready to go.

---

### Post by Jaydos on 2007-01-15
> **Fitzy_oz said:**
> OK - Accessing your windows box from Ubuntu should be very straigt forward.  Instead of using \\<computername> or \\<Ip Address> you simply use smb://<computer Name> or smb://<ip address>.  

Accessing your ubuntu box from windows will require a few additional steps.  Firstly.
Setup a windows user account for you Ubuntu box.  jump to the command line and type the following:
smbpasswd -a <your username on the ubuntu box>

This will ask you to type and verify a password.

Once this is done, the next time you try to access the ubuntu box via windows it will ask you for a username and password, it will be the same as the username and password you use to login to ubuntu.  You can configure your shared directories by opening the Settings -> administration (i think if not it's preferences) -> sharing and simply add the folders you wish to share to the list and voila` it's ready to go.
OMG Thank you!
smb://<Computer Name> is basically what I was looking for (I transfered all my pers data to windows box pre format). Thank you very much!

---

### Post by Fitzy_oz on 2007-01-15
> **Jaydos said:**
> OMG Thank you!
smb://<Computer Name> is basically what I was looking for (I transfered all my pers data to windows box pre format). Thank you very much!

No worries mate.  ;)

---

### Post by demandred87 on 2007-01-15
I have tried the How-To [COLOR=Blue][here]("http://www.ubuntuforums.org/showthread.php?t=202605")[/COLOR] and I could never get the Network Drive to be mapped in the last step. I tried the method you described and sadly it still doesn't work I get [COLOR=Blue][this error]("http://www.ubuntuforums.org/attachment.php?attachmentid=23162&stc=1&d=1168919475")[/COLOR].

---

### Post by Fitzy_oz on 2007-01-15
> **demandred87 said:**
> I have tried the How-To [COLOR=Blue][here]("http://www.ubuntuforums.org/showthread.php?t=202605")[/COLOR] and I could never get the Network Drive to be mapped in the last step. I tried the method you described and sadly it still doesn't work I get [COLOR=Blue][this error]("http://www.ubuntuforums.org/attachment.php?attachmentid=23162&stc=1&d=1168919475")[/COLOR].

Have you tried smb://<ip_address>?
This may sound really stupid but I assure I caught out a few times trying to access a windows box that isn't sharing anything, this can cause problems...  Also, check and see if there is a user account on your windows box that corresponds to you ubuntu username (It shouldn't matter but I always made a habbit of having an account there for it", give it the same password also.  And last but not least, check make sure that the file and printer sharing isn't eing blocked by your firewall.  If your using windows firewall, it should under the exceptions and ticked.  

Try this after you've accessed the box successfully.
Mapping a drive using samba is a little different - you have to run a command to mount it to a folder - sudo mount -t smbfs //<computer name>/'share name' /<the folder you would like to mount the share to>

---

### Post by demandred87 on 2007-01-17
> **Fitzy_oz said:**
> Have you tried smb://<ip_address>?
This may sound really stupid but I assure I caught out a few times trying to access a windows box that isn't sharing anything, this can cause problems...  Also, check and see if there is a user account on your windows box that corresponds to you ubuntu username (It shouldn't matter but I always made a habbit of having an account there for it", give it the same password also.  And last but not least, check make sure that the file and printer sharing isn't eing blocked by your firewall.  If your using windows firewall, it should under the exceptions and ticked.  

Try this after you've accessed the box successfully.
Mapping a drive using samba is a little different - you have to run a command to mount it to a folder - sudo mount -t smbfs //<computer name>/'share name' /<the folder you would like to mount the share to>Yeah I did try the smb://[IP Address] as well [with no luck]("http://www.ubuntuforums.org/attachment.php?attachmentid=23244&stc=1&d=1169010040").

I do have an account on my Windows box with the same username and password as my Ubuntu user. Also "File and Printer Sharing" was ticked under the "Exceptions" tab of the Windows Firewall.

It's getting really confusing because I've checked and double checked and triple checked all instructions.

Thanks for the help so far anyways. I greatly appreciate it.

---

### Post by featherking on 2007-01-17
@demandred87

could you run 'smbtree' and post its output?

---

### Post by featherking on 2007-01-17
@Jaydos

> WINS Support version: \\nocluewhatgoeshere\home\jayden\xfer
WINS Not Supported: \\10.1.1.4\home\jayden\xfer

Dont know if you got this yet but the 'nocluewhatgoeshere' would be the netbios name of the computer. The path that you have written there looks more like a linux path, if you are mapping a drive on your windows box it would be written like \\BILLY\windows\system32 or \\BILLY\Program Files\Messenger, just trying to clarify that

as an example, if you wanted to mount an itunes music folder on your windows machine to your ubuntu machine, you would type this into a terminal on ubuntu:
```

mount -t smbfs -o username=<user>,password=<pass> "//RON/iTunes Music" /mount/path
```

---

### Post by Fitzy_oz on 2007-01-17
> **demandred87 said:**
> Yeah I did try the smb://[IP Address] as well [with no luck]("http://www.ubuntuforums.org/attachment.php?attachmentid=23244&stc=1&d=1169010040").

I do have an account on my Windows box with the same username and password as my Ubuntu user. Also "File and Printer Sharing" was ticked under the "Exceptions" tab of the Windows Firewall.

It's getting really confusing because I've checked and double checked and triple checked all instructions.

Thanks for the help so far anyways. I greatly appreciate it.

Hmmm,
Let's go back to basics, it's usually the best way.  goto the system menu ---->  Administration  --------->  Shared Folders.

If not it will ask you to enable file sharing via NFS or Samba. 

After this is complete check the general properties tab and make sure that the This computer is a wins server is ticked.  After that it should be ok.....

Are the IP addresses handed out by your ADSL router via DHCP? Can you ping the windows box?

---

### Post by demandred87 on 2007-01-17
@featherking:

I tried that in the terminal and got no output :???:

@Fitzy:

I enabled "This computer is a WINS server". My IP address' are handled by the router (my router acts as a DHCP server. And yes, I can ping the Windows box from Ubuntu and vice versa.

EDIT: Thanks for the help guys/girls, especially Fitzy! I can finally access my shared folder on the Windows box. But I can't access my shared folder on my Ubuntu box. I'll just go through and look around for the culprit.

Cheers.

---

### Post by Fitzy_oz on 2007-01-18
> **demandred87 said:**
> @featherking:

I tried that in the terminal and got no output :???:

@Fitzy:

I enabled "This computer is a WINS server". My IP address' are handled by the router (my router acts as a DHCP server. And yes, I can ping the Windows box from Ubuntu and vice versa.

EDIT: Thanks for the help guys/girls, especially Fitzy! I can finally access my shared folder on the Windows box. But I can't access my shared folder on my Ubuntu box. I'll just go through and look around for the culprit.


Cheers.

No problem:) As for accessing the Ubuntu share - try this: 

Open a terminal - type sudo smbpasswd -a <your ubuntu username>, give it a password and use it when you try to access your shares from windows - Samba accounts aren't created by default in ubuntu.

---

### Post by Barney on 2007-01-25
Fitsy_oz,

Your [smbpasswd -a <your username on the ubuntu box>] worked great for me.

Thank you.

Barney

---

### Post by Fitzy_oz on 2007-01-26
> **Barney said:**
> Fitsy_oz,

Your [smbpasswd -a <your username on the ubuntu box>] worked great for me.

Thank you.

Barney

No worries ;)

---

