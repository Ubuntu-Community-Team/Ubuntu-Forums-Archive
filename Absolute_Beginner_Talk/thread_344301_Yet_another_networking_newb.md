---
title: "Yet another networking newb"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Stranger678 on 2007-01-22
I have read through what seems to be a thousand posts in here on how to do this, and still haven't gotten it right. Can someone help me out with some plain english?

I have five machines on my home network all runnding WinXP my workgroup is Cpo mess. I have a machine running Edgy, I have started samba and configured the file to read Cpo mess and restarted samba. Now under networks I have an icon for Cpo mess, but when clicked, I can view no other machines. I am trying to access all the hard drives that are currently shared across my home network and use my shared printer. 

This problem has driven me to drink...and purchase two books on Ubuntu operation, (they both roundly ignored the possiblity that an ubuntu user might still need to talk to windows from time to time) 

Can this procedure even be done? If so, can one of you nix geniuses help me out, cause I am feeling pretty dumb right now.

---

### Post by carverj on 2007-01-22
From memory, I think what I did back when I had a share with windows was to create share folders and a mapped network drive on the winbox. Sorry, winbox no longer here so can't test for you.

---

### Post by freebeer on 2007-01-22
> **Stranger678 said:**
> my workgroup is Cpo mess.  


Does the workgroup name permit a space character in it?  Seems to me that it isn't allowed.  Just a thought.  *shrugs*

---

### Post by jimrz on 2007-01-22
> **freebeer said:**
> Does the workgroup name permit a space character in it?  Seems to me that it isn't allowed.  Just a thought.  *shrugs*

i think you can get around this by listing it as either "Cpo mess" (using the quotes) or Cpo\mess (or that may be forward slash, not sure)

---

### Post by Threbus5 on 2007-01-22
Hi well, you should really be OK, the network concept really works. Smile.

Anyway, I have seven machines on the home LAN. One Mac, three windows, and three Ubuntu Linux.

One of the Linux machines is a file server it uses Samba share for access from all of the network - that is accessible from a mapped windows drive.

The other machines are accessible from the Ubuntu "go to server" or "go to computer" selection via fixed IP addressing. I believe that DNS addressing would have been sufficient for the network. Also, the other Linux computers (I believe) are reachable via the windows add network place function - the one that goes something like "\\192.168.1.x\sharedfolder"

I am going to attempt to paste some of the help files that I used (I have only copied them from their authors - the work is NOT mine)

First - Sharing  afterwards a post about printer sharing.

I am NOT the "I" in this howto you may find it advantageous to read the full original posting. I believe it is under SAMBA or HOWTO the author is  	
Stormbringer and   [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+to](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+to)    may link.

**Sharing**

"HOWTO: Setup Samba peer-to-peer with Windows 

As many fellow Ubuntu users seem to have trouble setting up samba peer-to-peer with Windows I decided to write a small howto on this matter.

NOTE: I am aware that there's a wiki-page as well as several other howto's around - but by looking at the constant "how do I setup samba" posts that are floating around in the forum I simply see the need for a more thourough guide on this matter.

Feel free to contribute and suggest - it'll only help to make this howto a better guide.

The goal of this howto is to have samba act like a Windows Workstation in the LAN. As a "value added bonus" we will use samba to do netbios name resolution so that you can use the names of the workstations for network drive mapping instead of their ip-addresses (i.e.: \MY_WINDOWS_BOX\SHARE) - but only for as long as your Linux box has an static ip-address and is up and running.

This guide is based on Ubuntu 6.06 LTS and intended for all architectures (i386, AMD64, ...) - if you are still using Breezy it's safe to follow this guide as there should be no differencies.

A second guide on how to setup samba as Primary Domain Controller along with several other services such as DHCP, DNS and NTP will follow later on as this topic will be a little more thourough.


1. Prerequisites

- Your Linux box should have an static ip-address.
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.

- You need to have samba installed.
If you haven't done so already open a terminal and type:
Code:
sudo apt-get install samba
Don't close the terminal upon installation - we still need the commandline to get several tasks done!


2. Getting samba configured

First, let us make sure samba isn't running:
Code:
sudo /etc/init.d/samba stop
As a starting point I included an smb.conf below, and there are only a few simple things you may need to tweak.

Since the installation of samba just installed a rather useless template file we're going to rename it - we keep the file just in case.
Code:
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.template
Next we create a new empty file
Code:
sudo touch /etc/samba/smb.conf
And finally we need to open the file inside an editor
Code:
sudo gedit /etc/samba/smb.conf
NOTE: If you're on KDE replace "gedit" with "kate"

Copy / Paste the contents of the code-section below into your editor and read on ...
Code:
[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP
Ok, I already mentioned that there are a few simple things you may need to tweak; so here they are:

-> netbios name = YOUR_HOSTNAME

Replace "YOUR_HOSTNAME" with your desired hostname (don't use spaces!). Best pratice would be to use the same name you configured upon installation.

Example:

netbios name = DAPPER

-> workgroup = YOUR_WORKGROUP

Replace "YOUR_WORKGROUP" with the name of your workgroup, but make sure you're using the same as configured in Windows.

To find out the Workgroup name in Windows follow these steps:

- Click "START"
- Click "Control Panel"
- Click "System"
- Click the 2nd Tab entitled "Computername" and find the name of the Workgroup there.

Example:

workgroup = MSHOME

-> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS.

-> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...
Code:
sudo mkdir /home/samba
... and adjust "path =" to read ...

path = /home/samba/

Remember that this is just an example - you are free to put things wherever you like.

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer

Now we completed the part of editing smb.conf

Save the file and close gedit.

Since we are going to share the folder with other users we should now make sure that the permissions are set. Type:
Code:
sudo chmod 0777 /media/samba
NOTE: Don't forget to correct the path to the location you chose above!

That's it - now we need to start samba ...


1.1 Starting samba and setting up user accounts

Let us fire up samba for the first time. Type:
Code:
sudo /etc/init.d/samba start
There shouldn't be any errors - if you are presented with an error message make sure everything is correct (search for typos and/or invalid paths).

Time to add yourself as an samba user.

NOTE: You will be asked for a password - make sure you use the same as you use for login!
Code:
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

In the following example we will add an user called "mark" ...

Example:
Code:
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark
The "-s /bin/true" in the first line prevents the users from being able to access the commandline of your linux box ("-s" stands for "shell"). I strongly advise you to follow this recommendation! Don't change that setting to a valid login-shell unless you really know what you are doing!

Repeat this step until you configured all user accounts!

Now that we configured samba and created the user accounts we are done with the Linux-part - there's one more thing to do in Windows.


2. Changing network settings in Windows

Now we should let Windows know that there's a WINS server active in the network. 

If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows

Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
NOTE: Adjust this to the hostname and sharename you chose above!
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

That's it - samba is up and running now.


3. Security consideration

This is the right time to think about security right away.

In case your computer has more than one network connection (i.e. wired and wireless ethernet) you may want to restrict access to samba.

If not especially configured samba will bind its service to all available network interfaces.

So, let us assume you only want your wired network to have access and that the network card is called eth0.

Add the following lines to the [general] section of your smb.conf to achieve that goal:
Code:
interfaces = lo, eth0
bind interfaces only = true
If you did it correctly it should look similar to this:
Code:
[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true
Now only the local loopback interface (dubbed "lo") and eth0 are able to access samba - there's no need to fear that someone might break into your system by wireless as the interface isn't bound to the service.


4. Final words

If you happen to have any questions feel free to ask - I'll try to help as soon as possible.

If you find any mistakes in this howto please let me know so that I can fix them.

Feel free to contribute and suggest - help to make this howto a better guide.


5. Addendum: Useful links

Here are some links you may find useful.

The onsite links refer to other samba-guides and to ubuntu_daemon's "Important Links" thread.

- Onsite
Ubuntu Help: Windows Networkworking
Ubuntu Documentation: Setting up Samba

READ THIS FIRST prior to posting - IMPORTANT links (by ubuntu_daemon)


The offsite links refer to the offical Samba homepage and to a selected choice of their official documentation; these links are useful if you like to dig yourself into the mysteries of samba's configuration and usage as well as troubleshooting problems.

- Offsite
Samba Homepage

Practical Exercises in Successful Samba Deployment
The Official Samba-3 HOWTO and Reference Guide
Using Samba, 2nd Edition"


**Re: sharing printer to windows clients **
________________________________________
Quote:
Originally Posted by dbrum  
I have a HP printer on my Ubuntu works fine locally. I shared it and my user home directory with samba.

From my windows box, I can see my ubuntu machine in the same workgroup no problems. Problem is, when I try and access the Ubuntu from win, it asks me for a user/pw, which I typed in the user combo, the root, tried everything. Can't "log in". What have I done wrong? What login information is it authenticating against and how do I set it properly?

thanks.
Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(Dapper: /etc/cups/cups.d/ports.conf; Edgy: /etc/cups/cupsd.conf)
Code:
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
Restart the cups daemon:
Code:
sudo /etc/init.d/cupsys restart
On the Windows box: 
1.	Start the Add Printer wizard 
2.	Click Next 
3.	Select A network printer, or a printer attached to another computer 
4.	Select Connect to a printer on the Internet or on a home or office network 
5.	Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the URL box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. Don't forget the port number! 
6.	Click Next and run through the driver installation to complete

Good luck.

---

### Post by jonandrews on 2007-01-23
I was in a very similar position last year, and eventually got where I wanted to be.  The thread that gave me the clues was 

[www.ubuntuforums.org/showthread.php?t=224458](www.ubuntuforums.org/showthread.php?t=224458).

This also centred around 'stormbringer's article, and may be helpful,

Since that time, I have done a dozen or so installations that work fine on my hybrid network, and simplified the process considerably. I have nearly finished documenting it in detail - let me know if you would like to see the current draft.

---

### Post by Stranger678 on 2007-01-23
I'd love to see the current draft, I am starting over, reinstalling everything in case I gooned the Samba install the first time around. Thanks for all your help guys.

---

### Post by jonandrews on 2007-01-23
OK - give me a few hours to make it more useable, and then I'll e-mail it to you. 
In the meantime, I hope you are installing 6.06 (Dapper Drake), because that's the version my guide definitely works with. (I have found definite networking differences with 6.10). Finally, someone else in the thread picked up on the Windows network name you mentioned.
I am pretty sure that spaces are not allowed - I recall having to use underscore in the past.

---

### Post by jonandrews on 2007-01-23
OK. The draft of my guide is ready, and I've tested the procedure by doing a fresh installation. If you want to give it a try, you'll need to email me with your email address. If it works for you, I would like to put it on the forum somehow and see if it can help others.

---

