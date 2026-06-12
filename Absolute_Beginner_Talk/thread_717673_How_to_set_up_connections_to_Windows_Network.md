---
title: "How to set up connections to Windows Network?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2008-03-07
I've installed Samba and smbfs (and set up a share with the correct workgroup), and I get the message that "the folder contents could not be displayed" when trying to access my laptop (on my laptop) for about a minute before it finally appears. Why does it take so long to allow access? Also,  there's no sign of any other PCs on the network... Help?

:(

---

### Post by dwanders on 2008-03-07
Guessing that your running 7.10? And your trying to connect to another Windows Computer in a home LAN? All are connected with Network cables and switches etc..? Also guessing you can reach them from a lower networking level like PING other computer, what are your settings for System -> Admin -> Shares -> General?

---

### Post by oedha on 2008-03-07
1. can you ping......
2. did the windows firewall on ? (turn it off)

---

### Post by Mazza558 on 2008-03-07
Yes, I can ping all PCs on the network... I'll check the firewall now...

---

### Post by dwanders on 2008-03-07
Sorry - I also noticed your specs are in your Sig ;) ;) not trying to be a wanker or anything! :)

---

### Post by dwanders on 2008-03-07
If you could - whats your /etc/samba/smb.conf look like (this might be kinda big, if you could jut remove everything that #'ed out.

---

### Post by Mazza558 on 2008-03-07
> [global]
    ; General server settings
    netbios name = james-laptop
    
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes




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


[JamesLaptopFiles]
    path = /home/james/Shared Files
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = james
    force group = james
available = yes
browsable = yes
public = yes
writable = yes

That's my config file...

EDIT: My Windows PC now sees my laptop, but tells me that it is "not accessable". Now Samba (labelled as Windows Network) shows no folders at all. I changed security in the config file from user to share.

---

### Post by oedha on 2008-03-07
what if..you open places - home folder
then change the address bar (by click on paper pencil icon) type :==> smb:///
did you see others ?

---

### Post by dwanders on 2008-03-07
This is kind of a standard config I use. I don't get into all the security or AD participation, password sync etc - and it has worked for me in a private LAN/domain for many years through varying versions of Samba and Ubuntu:

[global]
   workgroup = (Domain or Workgroup name other PC is in)
   server string = (Your Samba PC Comment)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

security = share
#hosts allow = (IP or host name of PC you want to allow)

socket options = TCP_NODELAY
wins support = no
wins server = (If you have one IP or host Name of server)

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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

#Then I add shares off my PC like this
[work]
path = /home/danderso/Back_up
comment = David Anderson
read only = no
locking = no
guest ok = yes
available = yes
browseable = yes
public = yes
writable = yes

With this config, for every share I want to connect to on remote computers, I have to enter a Uname/Password/Domain until Ubuntu learns it and stores it in the password wallet thing. But It works for me. 

When I build a new PC, I always use the Admin -> Share to install Samba and smbfs, then I put this config in /etc/samba/  (saving my old one) and then I restart samba with  
sudo /etc/init.d/samba restart

As I said it works well enough for me :)

---

### Post by Mazza558 on 2008-03-07
I've added a few options to my config file but still no luck :(

---

### Post by oedha on 2008-03-07
mm.....
1. from linux...can you browse windows shares ?
2. from windows.....can you browse linux shares ?

for no.2
go to system - administration - shared folder
click add button
choose the folder that you would share
pay attention on read only box

then....open terminal
type :==> sudo smbpasswd -L -a username ( make a username and password )
try to see from windows now.....

---

### Post by dwanders on 2008-03-07
I think your biggest hold up is that:

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

instead of:
security = share

I am sure those other approaches are more fitted for a true Domain and all the other great features of Samba, of which the Official Samba HowTo and Reference guide is very useful - but I gave up on that stuff a bit ago and just wanted it to work. 

Try dropping that config I posted earlier, change it for your network and restart samba. For mine, I can even see computers in Places -> Network it is very useful. I also use this same set up at home and can store all my photos etc on a Linux server for backup. 

Hope it helps.

---

### Post by syntheticgoo on 2008-03-07
changing security=user to security=share worked for me. thanks

---

### Post by Mazza558 on 2008-03-09
It's working now :)

Just tried again today... funnily enough, simply restarting samba wasn't enough.

---

### Post by Mazza558 on 2008-03-09
Okay... now it's not... got a timeout after copying about 400 files and haven't been able to get back on since... "the folder contents could not be displayed"...

---

### Post by An_Dynas on 2008-03-09
which changes did you make that had it working?  I'm late to this thread but have exactly the same problem, a wireless laptop that used to share nicely with Windows, but now (despite being able to ping all the other machines) can neither send, receive, nor see anything on the network.

---

### Post by dwanders on 2008-03-09
Whats your new smb.conf look like?

---

### Post by dwanders on 2008-03-09
Although, that does not really sound like the problem (the conf) - is there any way you can re-create the problem? Like after a reboot does it work for a bit then fail? [If so which PC do you need to rebbot Win or Lin or both] And if it works, is there a time frame we are looking at how much time? or is after a specific number (amount) of data? We are not filling up the drive or share? I'm still pondering - but those are a few the first thoughts.

---

### Post by jon1965 on 2008-03-09
I am also having a similar problem. I can see the linux share from the windows machine and am able to transfer files but can only see the window share, cannot access it. I am also using a laptop connected to my network wireless. 
I have a second windows machine connected wired and I can see all the shares and their contents, same with my MacBook Pro which is wireless. The problem just seems to be on the one windows laptop.

---

### Post by dwanders on 2008-03-10
If the problem is that you can see the share on the Linux box (e.g. the Samba share) but cannot access the files, it may be permissions. Make sure the files in the share are read and write (if you want) from others. 

I don't think that is the same problem Mazza558 is experiencing though.

---

### Post by Mazza558 on 2008-03-10
> **dwanders said:**
> Whats your new smb.conf look like?

I never changed it completely (e.g using your config) - I was going to, and it simply started working... now it's not.

---

### Post by dwanders on 2008-03-10
Lets see what your current one looks like.

---

### Post by Mazza558 on 2008-03-11
> **dwanders said:**
> Lets see what your current one looks like.

Here it is:

> [global]
    ; General server settings
    netbios name = james-laptop
    server string = James's Laptop
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no
    dns proxy = no

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

[shared]
    path = /home/james/Shared Files
    comment = James's Shared Files 
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = james
    force group = james
    available = yes
    browsable = yes
    public = yes
    writable = yes
    locking = no

---

### Post by dwanders on 2008-03-11
I would suggest changing/trying 

remove:
passdb backend = tdbsam
security = share
null passwords = true
username map = /etc/samba/smbusers

add:
security = share

then restart samba with sudo /etc/init.d/samba restart

If you want to try that - cool let me know how it turns out.
:)

---

### Post by Mazza558 on 2008-03-11
> **dwanders said:**
> I would suggest changing/trying 

remove:
passdb backend = tdbsam
security = share
null passwords = true
username map = /etc/samba/smbusers

add:
security = share

then restart samba with sudo /etc/init.d/samba restart

If you want to try that - cool let me know how it turns out.
:)

No luck - now even my laptop itself won't appear in "Network". hmmm...

---

### Post by dwanders on 2008-03-11
Lets see the new one

---

### Post by siroche on 2008-03-14
how do I get the samba config file to show - says permission denied

---

### Post by dwanders on 2008-03-14
To just display it, you should be able to open it with the text editor (accessories) and it should let you read it. If you need to edit it (to make changes) you may need to open a Terminal (or console) and type sudo gedit /etc/samba/smb.conf [return]

This will open the file in the editor with root user permissions and allow you to edit it.

---

### Post by njparton on 2008-03-14
Mazza558, try this instead:

```

[global]
workgroup = HOME
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

security = share
username map = /etc/samba/smbusers

[shared]
path = /home/james/Shared Files
read only = no
guest ok = yes
create mask = 0644
directory mask = 0755
available = yes
browsable = yes
public = yes
writable = yes

```

see if you can get the share up and running with that simplified version before you add the printers bit back in.  If that doesn't work you're problem isn't with samba it's elsewhere.

---

### Post by Mazza558 on 2008-03-16
Gah, it's still not working. It must be an issue with the other PC.

---

### Post by njparton on 2008-03-16
> **Mazza558 said:**
> Gah, it's still not working. It must be an issue with the other PC.

most probably

---

### Post by Mazza558 on 2008-03-16
Right, my WIndows PC can see the Ubuntu Laptop and my other PC but can't access them, telling me that "the network path cannot be found". My Laptop still can't see any other PCs.

---

