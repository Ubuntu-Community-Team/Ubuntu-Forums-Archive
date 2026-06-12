---
title: "SAMBA and Edgy. Any HowTos?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-02-03
I just got Edgy running, and when I was on Dapper I tried to get SAMBA running but never did. This time I'm trying it again.

Using the ubuntu guide, I tried to install Edgy. But I got an error.


jason@jason:~$ sudo smbpasswd -a system_jason
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user system_jason. Does this user exist in the UNIX password database ?
Failed to modify password entry for user system_jason
jason@jason:~$ 


How can I get around this? I couldn't find any how-to guides, maybe someone can link me to one?

---

### Post by phossal on 2007-02-03
You might find it's easier to simply *reinstall* edgy over your previous installation. I know it isn't ideal, but it's probably the best way.

Then you can grab samba pretty easily using the package manager:
```
sudo apt-get install samba
```

The default configuration is useful right away (depending on what you want to do with it of course). On 32Bit Ubuntu, you'll almost immediately be able to access Windows shares out of the box. 

Once installed, you can refer directly to the samba site (or your local bookstore)  for decent documentation.

---

### Post by Roasted on 2007-02-03
Dude... *cries* I just installed Edgy on Wednesday!! :( :mad:

---

### Post by phossal on 2007-02-03
I'm sure someone out there knows better than I do, maybe the thread activity will bring them in. However, I've read similar threads a couple times, and I was surprised to see the mods say the same thing. It's often just *better* to install a new version of Ubuntu than to try an Upgrade.

---

### Post by Roasted on 2007-02-03
Oh no no. I didn't upgrade anything. I fresh formatted my hard drive, redid windows, and put edgy in.

The thing is I TRIED to get samba running with dapper, but due to a heavy schedule and lack of knowledge I was unable to get it running. Now that I have the weekend off I wanted to get samba running.

So this is a fresh install of edgy.

---

### Post by Dritzen on 2007-02-03
[Samba Guide]("http://www.ubuntuforums.org/showthread.php?t=202605")

Stormbringer wrote a pretty big guide.  Perhaps it will help you out with getting it running.

---

### Post by Roasted on 2007-02-03
What's the first thing I should look for when I get an error saying "The network path \\workgroup\myfiles could not be found."

For the record, we have 4 machines at this house. Three are dual boot, one is strictly windows. Two are XP home, the other two are 2k Pro. All four machines belong to the workgroup named "workgroup." My computer name and host name is "jason" and the IP is set right.

I also went to my /media folder, right clicked on hdd1 (the folder I want to share) and clicked share. I looked and it was checked to be shared through WINS. When I checked my sambaconfig file, my path had changed to /media/hdd1. I assume that's good?? 

I went back over the how-to guide posted above about 6 times, and I seriously can't see anything that I did wrong, however I'm sure it's something simple that I'm overlooking. I wish I could provide more info, but unless you folks ask me for more I wouldn't know what more to tell you guys.

Help. :(

---

### Post by Dritzen on 2007-02-04
Click on Places up top, then "Connect to Server..."

For Service Type: select Windows Share

For Server, type the name of the computer

For Share, type the share name.  For instance, one of the shares on my network is named External, so I just type External in this box.

Type in your username or just make one up, even if your windows shares allow anyone access

Click connect and enjoy.

---

### Post by Roasted on 2007-02-04
I still get network path not found on the windows machines.

Also, was anything supposed to happen on my ubuntu rig? Nothing happened, no new window or error or anything. It just disappeared when I hit okay. The windows machien though wouldn't detect the network path. The network path I am using when I try to map the drive is \\workgroup\myfiles, which I assume is right, if it's something else I don't understand why. *shrug*

---

### Post by phossal on 2007-02-04
You have samba installed on 32 Bit Ubuntu, and you're trying to access a Windows share *from* the Ubuntu machine?

---

### Post by Roasted on 2007-02-04
I want the other 3 computers, whether they be linux or windows, to have the ability to access my 200 gig drive that I have in my computer. If I need to, I'll partition the hard drive half in NTFS half in EXT3. But right now I can't even get it to see the drive or even make a connection. Why? :(

---

### Post by Milt888 on 2007-02-04
One thing I noticed in trying to get my lan working was #1 get the file sharing set up right and #2 shut down the Windows firewalls, any firewall for that matter. At least they didn't play well with my setup.
I still have to restart samba periodicly to get things to work.
Good luck.

---

### Post by Roasted on 2007-02-04
How do you restart samba? By using those commands to stop/start it?

---

### Post by Milt888 on 2007-02-04
> **Roasted said:**
> How do you restart samba? By using those commands to stop/start it?

sudo /etc/init.d/samba restart

---

### Post by Roasted on 2007-02-04
If my workgroup name on all 4 computers is workgroup, what should I map the drives to? \\workgroup\myfiles? Cause it's not working. *shrug*

---

### Post by Falcorian on 2007-02-04
> **Roasted said:**
> I just got Edgy running, and when I was on Dapper I tried to get SAMBA running but never did. This time I'm trying it again.

Using the ubuntu guide, I tried to install Edgy. But I got an error.


jason@jason:~$ sudo smbpasswd -a system_jason
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user system_jason. Does this user exist in the UNIX password database ?
Failed to modify password entry for user system_jason
jason@jason:~$ 


How can I get around this? I couldn't find any how-to guides, maybe someone can link me to one?

This may have been covered, but I think you should do:

```
jason@jason:~$ sudo smbpasswd -a jason
```

As far as I know, it should be a user that's already on the Linux system.

---

### Post by Roasted on 2007-02-04
Okay. Done. Now should I try mapping the drive?

Should I use \\workgroup\jason, or what?

---

### Post by Roasted on 2007-02-04
All right. I'm getting a little aggrivated.

"MyFiles on jason" randomly appeared on my desktop. I double click, and it wants me to log in, with workgroup already sitting in the "domain" section. Besides that, it requires a password. I put my password in, no entry. I tried putting my username (jason) in, and using that password. No entry there either.

I went to the windows machine, and tried to map the network drive to \\jason\myfiles, and it prompted me to log in. Yet, the information was rejected.

I only set up one username and one password. Besides that, I set up one workgroup. Why is it rejecting the ONLY information I put in? :confused:

---

### Post by Falcorian on 2007-02-04
It should be the username and password that you set up with: ```
sudo smbpasswd -a jason
```

I suppose that's what you've been trying though...


What's your smb.conf?

---

### Post by Roasted on 2007-02-04
jason@jason:~$ sudo smbpasswd -a jason
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
jason@jason:~$ 


For the record, I am 100% positive I am putting this password in. Caps lock is off and I have it written down right here next to me. Maybe I should redo everything, something's not right. If I uninstall everything (complete removal) via synaptic, will it get rid of my settings too so I don't have to worry about anything? This is just getting a little ridiculous.


My smb.conf:




[global]
    ; General server settings
    netbios name = jason
    
    workgroup = workgroup
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
    ;path = /home/samba
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
    path = /media/hdd1
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = jason
    force group = workgroup
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by Falcorian on 2007-02-05
> **Roasted said:**
> jason@jason:~$ sudo smbpasswd -a jason
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
jason@jason:~$ 


For the record, I am 100% positive I am putting this password in. Caps lock is off and I have it written down right here next to me. Maybe I should redo everything, something's not right. If I uninstall everything (complete removal) via synaptic, will it get rid of my settings too so I don't have to worry about anything? This is just getting a little ridiculous.

I don't know about that... I just learned how to Samba a week ago. ;) Worth a shot I suppose...

> **Roasted said:**
> My smb.conf:




[global]
    ; General server settings
    netbios name = jason
    
    workgroup = workgroup
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
    ;path = /home/samba
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
    path = /media/hdd1
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = jason
    force group = workgroup
available = yes
browsable = yes
public = yes
writable = yes

I don't see anything obviously wrong... Sorry. :(

---

