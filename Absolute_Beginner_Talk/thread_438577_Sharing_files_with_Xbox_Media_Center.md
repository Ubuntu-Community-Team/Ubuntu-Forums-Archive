---
title: "Sharing files with Xbox Media Center"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by dustyken on 2007-05-09
Okay.  I'm a newbie here.  I used to use Windows (still do to a certain extent).  I also have an Xbox that I have modded to be a Media Center.  I currently run Xbox Media Center on it.  When I had Windows running on my PC, all I had to do was select a folder I wanted to share, right-click, Properties, and Share it.  My Xbox would automatically detect the network and the shared files.  Now, I have no idea what to do.  I need to know how to share a folder across the network.  I installed Samba, but don't really know how to or to what degree to configure it.  Any help would be appreciated.  Thanks in advance.

---

### Post by mckryptyk on 2007-05-09
Have I got the answer for you! I've done this 30+ times now for various xbox owners. :)

I'm glad you are using samba it is much better than the alternatives in my opinion.

Here is the howto:

Install samba
"sudo apt-get install samba"

Now we stop samba
"sudo /etc/init.d/samba stop"

Now we copy the old config for backup
"sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup"

Now we edit the samba config
"sudo gedit /etc/samba/smb.conf"

Now copy what I have written below:

[global]
    ; General server settings
    netbios name = yourcomputername
    server string =  (leavethisblank)
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    
    ;interfaces = 127.0.0.1, 192.168.2.1/24
    interfaces = lo, eth1 (put you ethX here ,eth0 or 1 etc.) 
    bind interfaces only = true
    
    hosts allow = 127.0.0.1, 192.168.2.12 (the ip of your xbox goes here)
    hosts deny = 0.0.0.0/0    

    passdb backend = tdbsam
    security = user
    encrypt passwords = true
    username map = /etc/samba/smbusers
    obey pam restrictions = yes    
    invalid users = root

    name resolve order = hosts wins bcast

    wins support = no

;    printing = CUPS
;    printcap name = CUPS

    syslog = 1
    syslog only = yes

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0700
    ;browseable = no
    ;read only = yes
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = yes

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = no
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
    ;path = /var/lib/samba/printers
    ;browseable = no
    ;guest ok = no
    ;read only = yes
    ;write list = root
    ;create mask = 0644
    ;directory mask = 0755

;[printers]
    ;path = /tmp
    ;printable = no
    ;guest ok = no
    ;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = no
    ;read only = yes
    ;guest ok = no

[MyFiles]
    path = /path/to/your/share/folder/or/partition/
    browseable = no
    read only = yes
    guest ok = no
    create mask = 0600
    directory mask = 0700
    force user = yourusername
    force group = yourusername

Now we add a user
"sudo smbpasswd -a yourusername"
enter you samba passwd

Now we enable samba
"sudo smbpasswd -e yourusername"

Now start samba
"sudo /etc/init.d/samba start"

Now if you have firestarter, the firewall

go to the policy tab and select "allow service port for"
now add your xbox ip address and select samba from the "type of connection" tab.

Now on XBMC 
go to your video menu
hightlight "SMB Network share"
select "edit source"
(on my remote it is tile button)
remove previous connections if any
add this
"smb://yourusername:yourpassword@yourcomputerIPaddress/MyFiles/"

for example only
"smb://smiley:face@172.131.100.200/MyFiles/"

Now highlight "SMB Network share" again
select "Make Default"

Now when you reboot the xbox and select "video"
from the start up

Hope that helps :)

If you have any trouble let me know here and I'll help you

Cheers.

Edit: BTW are you using the latest T3CH release? it now supports wide icons and more.
A definite must have :) 

check out the official XBMC forums here for more XBMC info if you are stuck:
[http://forums.xbox-scene.com/index.php?showforum=180](http://forums.xbox-scene.com/index.php?showforum=180)

---

### Post by dustyken on 2007-05-11
Do I use this to replace the existing code in the Samba file, or just add it to the end of the file?

---

### Post by dustyken on 2007-05-12
How do I find my netbios name?

---

### Post by Phantom784 on 2007-05-12
Samba uses (by default, at least) your computer's hostname as a netbios name.  Just type "hostname" at the command line to see what it is.

---

### Post by mckryptyk on 2007-05-23
Sorry for the long delay,
After you copy the smb.conf for backup, you edit the original smb.conf and replace it with what I have written.
hope that helps :)

---

### Post by conorharris on 2007-05-31
Thanks alot! It works great!

The only catch for me was that my XBox default workgroup was WORKGROUP rather than MSHOME.

---

### Post by grate on 2007-07-07
Hi,

Sorry to bump this old post, I have followed the directions supplied here and believe I almost have everything working.

My xbox is able to connect to the share or at least acts like it is, however once it connects I am left with an empty directory list ..\

My workgroup was also set to 'WORKGROUP' rather than 'MSHOME', however making this change didn't have any effect.

Can anyone offer any insight as to what I may have done wrong?

Thanks so much.

---

### Post by quattroman on 2007-07-11
I will be doing this tonight when I get home from work, I will let you know what happened. My Workgroup is also something different from MSHOME or WORKGROUP.

what is force workgroup....

---

### Post by quattroman on 2007-07-13
Ok. I got all running, I can see the internet from XBOX.

BUT....I can't see SAMBA shares, I get the following error:

"Remote Share
Could not connect to network server"

I tried both IPs, this computer has for the shared internet connection, added samba to the allow policy in firestarter, I also tried in xbox with the name of the computer. 

Please advice in what else can I do to reach my files in xbmc


EDIT: I get the following error while accessing My Videos on XBMC after xbox boot, I got samba as default in My Videos like instructed; here it is:
"Error ~1073741772:Share not available"

EDIT #2: I got into my SAMBA from XP machine. 

EDIT 3: After playing around, I figured out it was the path that was wrong. I did not realized that after IP/MyFIles is actualy the title used for that command in SMB.CONF and not the real path.

THanks

---

### Post by ontario1984 on 2007-08-06
I'm new to forums, ubuntu, and networking.  I figured out that all those commands are supposed to be typed into the "Terminal" program and copied the script in this forum to just above the "" # Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d""  line.  did I stop to early, and what should the xbox settings be at.  please just tell me what to use for usernames and passwords and IP addresses, don't use words like "recieving IP address" or" sending IP address"  use "192.68.0.4"  Pictures would be fantastic, and also what do you do in the xbox settings.  I have a modded xbox with the xecuter 3 mod chip in it.  I have a 5 port network hub, and 3 ethernet cords going from hub to wall, hub to xbox, and hub to computer.  Do I need anything else?  I would love pictures, or a video on youtube woulb be fantastical.  

So far what I've been trying is install samba with synaptic package manager.  share a folder over the smb network, then make the ip address static, and set it to 192.168.0.2.  my xbox is i think where i get confused.  i set my ip address to 192.168.0.3 and my wins server to 192.168.0.3  all usernames and passwords are xbox.  what am I doing wrong??  please help.

---

### Post by soldave on 2007-09-03
That's awesome!  Worked first time with no problems at all.

Much kudos to you:)

---

### Post by johnny9794 on 2007-10-30
I did everything accordingly and this is just not happening for me,
My xbox is 192.168.2.17 and my ubuntu box is 192.168.2.14
my hostname is ubuntu.
I created smba pw's just like in the howto ect.
My ethernet interface is eth0, is there something in the cfg that i missed or did not do right?
screenshots below of xbmc, first one is the addy, second and third shows cannot connect and the fourth one is after i reboot the xbmc and navigate to Videos.

Thanx.
> 
[global]
; General server settings
netbios name = ubuntu
server string =
workgroup = MSHOME
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;interfaces = 127.0.0.1, 192.168.2.1/24
interfaces = lo, eth1 (eth0)
bind interfaces only = true

hosts allow = 127.0.0.1, 192.168.2.17
hosts deny = 0.0.0.0/0

passdb backend = tdbsam
security = user
encrypt passwords = true
username map = /etc/samba/smbusers
obey pam restrictions = yes
invalid users = root

name resolve order = hosts wins bcast

wins support = no

; printing = CUPS
; printcap name = CUPS

syslog = 1
syslog only = yes

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0700
;browseable = no
;read only = yes
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = yes

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = no
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;path = /var/lib/samba/printers
;browseable = no
;guest ok = no
;read only = yes
;write list = root
;create mask = 0644
;directory mask = 0755

;[printers]
;path = /tmp
;printable = no
;guest ok = no
;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = no
;read only = yes
;guest ok = no

[Share]
path = /home/johnny/Share
browseable = yes
read only = yes
guest ok = no
create mask = 0600
directory mask = 0700
force user = johnny	
force group = johnny


---

### Post by il-luzhin on 2007-12-09
I have had zero success on an xbox 360.  Other posts on ubuntu forums and google suggest that the need for WMP11 or WMConnect for the 360 interface may make my desire a pipe dream.

Any advice on the topic?

BTW:  I can go from 360 -> vista laptop -> ubuntu 7.10 running Samba if that's of any consulation to anyone.  Pretty bloody annoying though.

---

### Post by mckryptyk on 2007-12-13
My tutorial was really only intended for the original xbox, not the xbox360. If you can make use of it though than thats excellent!

Here are a few links to things that may help you with sharing data to your xbox 360:

[http://forums.xbox-scene.com/index.php?showtopic=406958&st=105](http://forums.xbox-scene.com/index.php?showtopic=406958&st=105) (VLC360?)

[http://www.youtube.com/watch?v=2YRel0VxQyk](http://www.youtube.com/watch?v=2YRel0VxQyk) (starts at the 15.00 minute mark) (xbox 360 streaming)

* The above one may require wine if not using a windows pc, I've never tried it but the video speaks for itself *

[http://forums.xbox-scene.com/index.php?showtopic=461128](http://forums.xbox-scene.com/index.php?showtopic=461128)

[http://forums.xbox-scene.com/index.php?showtopic=632660](http://forums.xbox-scene.com/index.php?showtopic=632660)

These should get you on to the right track, If there is enough intrest I may create a xbox360 tutorial for linux to make it easier on xbox owners in the community.

Also for everyone who has trouble with my xbox/samba tutorial, have you tried this command after folling the instructions to the letter?

"sudo /etc/init.d/networking restart && sudo /etc/init.d/samba restart"
*Just copy/paste and remove the quotations arount the command*

What it does is restart your networking subsystem and restart the samba daemon so that it uses the new config. 
It also ensures that the samba daemon is running. 

I have noticed on ubuntu for some reason, it will not always start on every boot and doesn't seem to affect all samba/ubuntu installs. Very weird.

---

### Post by dustyken on 2007-12-13
The easiest way for me to remedy this was to buy a file share and store all of my files on it.  Which works out better anyway because if my computer is ever down, I can access all of my files on my share from my Xbox.  I got a D-Link DSM-600.  Really good.  I highly recommend it.  I have no problems connecting to it from Ubuntu and I'm running 7.10.  

I also use the T3CH builds so that it is really easy to set up a bookmark of your files for XBMC.

---

### Post by dustyken on 2007-12-13
On a related note, I am very close to getting a 360, so I greatly appreciate the links that were posted!

---

### Post by yonyhagadol on 2008-04-16
i dunno wat i did wrong
xbmc just keeps telling me to enter username and password after every time i enter it

---

### Post by jackal242 on 2008-04-16
I would not do any of what was posted here.

XBOX uses uPNP to view media files NOT SAMBA, so all the above instructions are pretty much wrong.

I set up ushare on my ubuntu box and run the following command to kick it off:
/usr/bin/ushare -n Hazard -t -p 49153 -D -x -c /data/ushare

Where /data/ushare is the directory with all my media files.  ushare streams them to the xbox.

Again, use ushare NOT samba for streaming media files to your xbox360.

---

