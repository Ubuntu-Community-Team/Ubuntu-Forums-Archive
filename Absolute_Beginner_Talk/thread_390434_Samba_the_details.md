---
title: "Samba: the details"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-03-21
Hi,

Nothing like a new OS to highlight a total lack of fundamental knowledge with regards to file systems, IP addresses, ports, protocols and the daunting command line. So, okay, I'm going to do it anyway, and then, I want to put together a "For Compleat Morons Like Me" page so that the budding Linux community - trembling, dry-mouthed n00bies like me - don't lose heart and go back to the other OS. 

When you look at the common computer user (WindowsXP, mostly) you will see someone who has nil interest in the workings of an operating system and protocols, and if such an interest did fleetingly emerge, it would be summarily blown away by the language and volume of the man manuals.

I've been reading the man for smb.conf. Toothsome. For the most part, it made no sense to me, so I read up on the history of Samba, which turns out to be a sort of means by which Unix-types can gain access to SMB file-systems... SMB (Server Message Block) being a Windows protocol for accessing files, printers and such. If I understand it correctly, it's a little like TCP/IP. So, it's a protocol to allow direct access to the Windows filesystem by Linux, right? So, how does that compare (and live in harmony with) mounting an ntfs drive with the ntfs-3g? Is that a mix-and-match thing? Or shouldn't you do one with the other? On my laptop, for instance, in Windoze, I set a drive letter to a network drive on my desktop, making it like a local drive, except through the network. Is it possible to do this? Is it through a mount command?

Here's what I want to do, for the moment. I've got a desktop machine and a laptop which are part of a Windows2000 Professional-based peer-to-peer network. I say Win2K, because that is the system that actually connects to the internet, and then performs ICS for the rest of our little home network via a couple of smart switches. In this class I took at TAFE a couple of years ago I found out the ICS actually includes a mini-version of dhcp... so all the systems on our network are assigned 192.168.xxx.xxx addresses dynamically by the ICS box when they boot up (after the 'NetServer' box has been booted and formed a connection to the internet). I actually tried static IP addresses on the 'workstations', but the box with a static address didn't seem to be recognised by the ICS box suddenly, and couldn't get online anymore.

Anyone have any idea why?

I'd love to fix that, and here's why:
> 
 Re: Samba configuration help
Here is a link to a procedure that I used and it worked wonderfully. Hope it helps.
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)


took me to:
> 
HOWTO: Setup Samba peer-to-peer with Windows
As many fellow Ubuntu users seem to have trouble setting up samba peer-to-peer with Windows I decided to write a small howto on this matter.
...
<block of text here--good stuff, by the way>

1. Prerequisites
- Your Linux box should have ***a static ip-address***.
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.


So far, I've installed Samba using:

```

sudo apt-get install samba
sudo /etc/init.d/samba stop
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.template
sudo touch /etc/samba/smb.conf

```

and with sudo gedit /etc/samba/smb.conf set my /etc/samba/samba.conf file to look kinda like:

```

[global]
    ; General server settings - [B][COLOR="Red"]that netbios name has me confused - 
    ; would that be the name of my connect-to-the-Internet machine or the name of 
    ; the machine that this particular installation is on?[/COLOR][/B]
    netbios name = flight ; name of my desktop with Ubuntu 6.10
    server string =
    workgroup = WORKGROUP  ; **[COLOR="Red"]yes, kept the name it was originally given[/COLOR]**
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

   ; **[COLOR="Red"]Probably need static IP address for WINS support[/COLOR]**
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

**[COLOR="Red"]Didn't uncomment the bit about primary domain controller [/COLOR]**
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

[UbuntuFolderName]
    path = /media/foldername/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = moron
    force group = morons

```

In the [] brackets I put the actual name of the Ext3 folder I'm trying to share with Windows in mixed case, and in lower case in the path.

So far, so good. Samba starts... then I booted up my laptop to WinXP... in the Workgroup (My Network Places) I can see my desktop and the shared drive, but I can't access it.

Any idea what I'm doing wrong?

Cheers,
Robyn

---

### Post by scxtt on 2007-03-21
sudo smbpasswd -a $USERNAME

$USERNAME should just be yours, but it has to be valid in /etc/passwd

---

### Post by Robynsveil on 2007-03-22
Don't ask me what I did, but it works now.  \\:D/

I started with your advice, scxtt, and and then read more of the advice of Stormbringer

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

... further down that huge thread, he discusses passwords, and so I set the user password for Samba to be the same as what I use to log on to the Windows 2K drive, and now it works! - rebooted Windows and lo-and-behold, my shared folder on my Linux box is like a local drive in Windows. Here are my settings in /etc/samba/smb.conf:

```

[homes]
comment = Home Directories
path = /home/robyn
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = no
printable = no
share modes = no
locking = no

```

and took out (commented) the folder entry (the one I wanted to share):

```

;[content]
;path = /media/content
;available = yes
;browsable = yes
;public = yes
;writable = yes

```

and hey, it worked... :-o  so I *didn't* have to disable dhcp and set static IP addresses, which would have (because of my lack of knowledge) buggered the rest of the network.

I'll have a bit of a play more with this and let you know how I go.

Cheers,
Robyn

What's really weird is that the password I entered with...

```

 sudo smbpasswd -L -a robyn

```

...is the one used to log on to the NetServer box (the ICS box), not the laptop. However, on the laptop I don't even have to do any logging on now - the drive is just there! 'Course, I *did* have a mapped drive to Flight (a folder on my Windows desktop) at one point - it must assume this is that folder or drive.

---

### Post by cowlip on 2007-03-22
check out this bug if Samba's configuration bugs you like it bugs me.  I think the lack of a GUI for smbpassword is a big issue: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067)

---

### Post by Robynsveil on 2007-04-07
> **cowlip said:**
> check out this bug if Samba's configuration bugs you like it bugs me.  I think the lack of a GUI for smbpassword is a big issue: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067)

I'm kinda new at all this, and - I must say - have been experiencing my share of frustration with getting things to work: Samba being no exception. Whilst perhaps a GUI might be a good solution, I think a straight-forward, do-this,-then-do-that type of tutorial - unencumbered by the history of SMB and the future of Microsoft or the vagaries of the whole OSI thingie - would make me happy enough to  where I could forgo the GUI. Give me one really good example, some sample lines of code to copy and paste into a file or into the terminal that actually works... hey, that would work for ME!

I certainly don't expect - or even *want* - Linux to be like Windows... I just want it to work, and I realize that in order for it to work, there's some stuff I need to understand... so I want explanations that make sense to me. I feel that in that way, it will help me become better acquainted with this brilliant piece of work called Linux.

---

