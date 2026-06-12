---
title: "Network Problems"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by xthund3rh3adx on 2007-05-12
hey, i have successfully configured SAMBA, so now i can view Ubuntu shares on my XP machine. 

Only problem is that I cannot see my XP machine in Ubuntu.

I go to places>network, and all it is there is a "Windows Network" icon.

When i click on that, nothing is inside.

HELP!!!

---

### Post by jtraub on 2007-05-12
Open Explorer and type into address bar
```
\\<ip adress of Ubuntu machine>
```

Have you installed samba server?

---

### Post by xthund3rh3adx on 2007-05-12
>_< i can do that, but i cannot connect FROM my Ubuntu machine TO my XP computer

yes i have installed SAMBA....

---

### Post by xthund3rh3adx on 2007-05-13
bump

---

### Post by nickpaton on 2007-05-13
Hi

Try this first of all.

Disable firewall using Firestarter - if you need more information about this get back to me.

Then

Places >  Connect to Server

Service Type: windows share

Server:  Whatever you call your windows PC - mine is home for instance.  If you don't know how to find this on your Windows PC, get back to me.

If this doesn't work please would you post the full results of 

```
sudo gedit /etc/samba/smb.conf
```

---

### Post by xthund3rh3adx on 2007-05-13
here is my smb.conf file:

```

[global]

workgroup = MSHOME
server string = %h server (Samba, Ubuntu)
dns proxy = no
interfaces = lo eth0
bind interfaces only = true
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = share
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
guest account = nobody
invalid users = root
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

[Ubuntu Root]
comment = Full Access Root Share
path = /
browseable = yes
read only = no
guest ok = yes

[Peter Home]
comment = Peter's Home Folder
path = /home/peter
browseable = yes
read only = no
guest ok = yes

```

my computers name is "Windows XP computer" ....i named it this for network clarity....it doesnt work

---

### Post by xthund3rh3adx on 2007-05-13
nevermind i connected to my PC using its IP address....


but how can i make it so it does this at startup? so i dont have to Connect To server?

usually it should just show up with my Ubuntu machine and my XP machine under Places>Network, no?

i need it to connect to my whole network, not just 1 PC.......if that makes it a little clearer

---

### Post by xthund3rh3adx on 2007-05-13
bump to get to first page ;) lol

---

### Post by nickpaton on 2007-05-13
What has worked for me from Dapper:

First go to[ this post]("http://ubuntuforums.org/showthread.php?t=202605").

Note that Stormbringer the author recommends the use of netbios in Windows, so you will need to reconfigure your Windows IP settings.
He also recommends that your PC's have static IP addresses, and this can be done via your router by reserving IP addresses for each PC.

I have tweaked the smb.conf file to look this this:

```
[global]
    ; General server settings
    netbios name = YOUR_UBUNTU_PC_NAME
    
    workgroup = YOUR_WINDOWS_WORKGROUP_NAME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share 
    ;  (change to "user" if want to login to windows PC)
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
    path = /home/nick/samba
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = 
    force group = 
available = yes
browsable = yes
public = yes
writable = no
```

If you then try using the "Connect to Server" option under Places, it should work.

Again I cannot emphasise enough that initially to disable the firewall.  If you need information on setting up Firstarter have a look at [this post]("http://ubuntuforums.org/showthread.php?t=442188#4").

---

### Post by xthund3rh3adx on 2007-05-13
ok so...

FireStarter is disabled, thank you!

Everything is set up perfectly thanks to you, you have my graditute..


only thing is that I would like to go to Places>Network and see all PCs connected to my network....any help??

---

### Post by nickpaton on 2007-05-13
Glad it's working - I need to go to bed now, but I'll try to post tomorrow around 10pm UK time.

Nick

---

### Post by nickpaton on 2007-05-14
Have you set up ALL of your Samba according to [THIS]("http://ubuntuforums.org/showthread.php?t=202605") excellent post, which I recommended earlier?

Also it mentions about adding user accounts, and setting up user permissions.  
Your network will not work without doing this.

Have you set up your Windows PC according to Section 2 of the HOWTO?  Again you MUST do this.

Setting up Ubuntu to see your Windows shares:

When, and only when you have done all of the above, including setting up the TCP IP Netbios stuff in the XP PC, and rebooted all PCs

To place a link on your desktop to your XP PC:

Places > Network > Connect To Server

Server Type: "Windows Share" 

Server: "The_name_of_your_XP_PC".  (May I suggest you make it one word like "HOME", and the domain something like "MSHOME" - in other words a single word.)

To make this alteration in XP read [this]("http://support.microsoft.com/kb/295017") from Microsoft.

And finally left click the Connect button.

An icon will appear on your Ubuntu desktop which you can click to access your XP PC.

To view your XP files:

P)laces > Network > Windows Network > Mshome (in my case) > Home (in my case - the name of your XP PC) > Your XP files.

As a general comment, it seems that your smb.conf file is missing a lot of vital stuff, and while it may work to a certain extent, I do know that the one I use based on Stormbringers post has worked for me on many UbuntuPC's from Dapper onwards, together with the simple setting up of the netbios part of the XP networking section.

If you feel for whatever reason that you dont want to change your smb.conf file, thats 100% fine, but I will not be able to help you further since I am not familiar with the version you are using.

Good luck anyway and get back to me with your progress!

Nick

---

### Post by xthund3rh3adx on 2007-05-14
thank you very much. your nice tut made my life a whole lot easier. I cannot use wins, since i use a wireless router. 

BUT, everything is working now thanks to you ;)

i can connect to my XP PC now, thanks a lot!

But yet, one question remains unanswered:

Is there anyway I can go to "Go>Network" and have all the connections on my network listed there?? this worked before i reinstalled Ubuntu. Then i reinstalled it and now i cant figure out why it doesnt do it now...

---

### Post by nickpaton on 2007-05-15
My stupid - didn't read your other post properly - apologies and pleased it's mostly working.

I know exactly what you mean....and I don't know the answer.  Mine, unfortunately for you, displays all the PC's on the network.

I'll have a play around over the next few days and see if I can make it go off and will PM you.

Sorry I can't me more help, but HTH for the time being.

Nick

---

### Post by xthund3rh3adx on 2007-05-15
Not a problem at all, thank you so much

---

