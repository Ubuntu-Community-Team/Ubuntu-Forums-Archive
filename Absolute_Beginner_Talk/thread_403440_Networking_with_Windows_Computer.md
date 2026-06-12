---
title: "Networking with Windows Computer"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by adamgram on 2007-04-07
Is it possible to share files over a network with windows xp?  How?

---

### Post by zvacet on 2007-04-07
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by swey on 2007-04-08
> **zvacet said:**
> [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

This page is far too complicated. All I want is to be able to browse and access files on my Ubuntu PC from by Laptop and Windows XP PC - I can already browse them from Ubuntu but its just one way. I can see my Ubuntu PC on the Windows network as was able to setup a Shared Folder but can't access it as it asks for a password but I was never asked to create one! On Knoppix there was a "Start Samba Server" item in the application menu which then asked you to set a password. That's what I call easy - it just worked. I don't want to have to mess around with lots of confusing console commands.

Oh and the Network settings screenshot looks nothing like mine (on 6.10) - mine doesn't say "ethernet lan card" - it has "Wired connection" in the connections window (with DHCP enabled whatever that is) and in the general tab there's no "enable windows networking" tickbox - just a box for name and domain (how do you know your domain anyway?? - this is my home network not a business)

---

### Post by msfisher on 2007-04-08
You will probably get a better answer than this from some of the local gurus, but your post piqued my curiosity.  I googled on "access linux "from windows"" (quotes only around "from windows") and came up with the following, for whatever they are worth.  I'm sorry there aren't any actual links, 'cause I don't know how to do that here yet.

Access Linux from Windows XP system | Frequently Asked Questions
[www.cyberciti.biz/faq/access-linux-from-windows-xp-system/](www.cyberciti.biz/faq/access-linux-from-windows-xp-system/)

How to access linux from windows - ITtoolbox Groups
linux.ittoolbox.com/groups/technical-functional/linuxadmin-l/how-to-access-linux-from-windows-920852

Access Linux Partitions/Files under Windows - Read and write on ...
news.softpedia.com/news/Access-Linux-partitions-files-under-Windows-48292.shtml

And don't forget Samba: 
Sharing Resources with Samba - Samba for Linux UNIX Windows Networking
compnetworking.about.com/od/softwareapplicationstools/l/aa062499.htm

And LOTS of others.  Many of the hits I saw were guides to doing what you want, not just pointing to a particular software solution.

Good Luck!

---

### Post by Austin_KW on 2007-04-08
the samba server defaults to security = user settings so it is asking for you linux account (username & password)

You can add your linux shares using the GUI menu; system->administration->shared folders

---

### Post by swey on 2007-04-08
> **Austin_KW said:**
> the samba server defaults to security = user settings so it is asking for you linux account (username & password)

You can add your linux shares using the GUI menu; system->administration->shared folders

Yes that's how I set up a shared folder but the username/password combo I have for Ubuntu itself isn't working - it won't accept it.

---

### Post by Austin_KW on 2007-04-08
try restarting/reloading samba config
```

sudo /etc/init.d/samba restart
or
sudo /etc/init.d/samba reload

```

Also look at the log file for the client PC at /var/log/samba/log.*IPaddrress*
or log.*netbiosname*

If that does not work post the output of your config file "grep -v [\;\#] /etc/samba/smb.conf"

---

### Post by Austin_KW on 2007-04-08
Also not usually recomended but I think if you add "security = share" and remove "security = user" in /etc/samba/smb.conf, windows will use the guest account, you can then map the guest account to some user with r/w access with " guest account = *yourUserNameHere*". Again if you do this you will have to restart/reload samba, and any user on your network would have access with the rights of whatever username you mapped to the guest account.

---

### Post by swey on 2007-04-09
> **Austin_KW said:**
> try restarting/reloading samba config
```

sudo /etc/init.d/samba restart
or
sudo /etc/init.d/samba reload

```

Also look at the log file for the client PC at /var/log/samba/log.*IPaddrress*
or log.*netbiosname*

If that does not work post the output of your config file "grep -v [\;\#] /etc/samba/smb.conf"

```
[global]


   workgroup = Workgroup

   server string = %h server (Samba, Ubuntu)



   dns proxy = no








   log file = /var/log/samba/log.%m

   max log size = 1000


   syslog = 0

   panic action = /usr/share/samba/panic-action %d




   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   invalid users = root


   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .















   socket options = TCP_NODELAY












wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no






[hda5]
path = /media/hda5
available = yes
browsable = yes
public = yes
writable = yes
myname@myname-ubuntu:~$ 


```

---

### Post by Austin_KW on 2007-04-09
That looks ok, but your linux and smb passwords are not synced

Try "smbpasswd" to set the password, from a terminal for the linux user account you are using to access the shares.  The is also an option in the smb.conf to sync the samba and linux passwords

---

### Post by meomike2000 on 2007-04-09
when i first started using ubuntu and had the same problem i followed this how to.
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
helped me lots. hope it helps u with ur problem. is a copy and paste. explains how to set users and permissions/passwords. and a general windows share. good luck

---

### Post by FITorion on 2007-04-10
anyone know how to set up a log file that will tell me 

What username connects 
what username uploaded
what username downloaded
when username did the above

I got samba all set up and have multiple users... Now I need to keep track of what they do so I can punish any that do anything nefarious.

---

### Post by Austin_KW on 2007-04-10
Try increasing your log level but it will produce much larger log files
You set/pick the log file in smb.conf under [global]
   log file = /var/log/samba/log.%m      ;To log per client machine connecting
   log file = /var/log/samba/samba.log      ;To log to a single log file
   syslog = 1      ;To log to the linux system log Logging level

and set how verbose you want the logging (1-3) (4+ for debug)
   log level = 3

and how many KB you want the max log to be
  max log size = 1000

---

### Post by swey on 2007-04-10
> **Austin_KW said:**
> That looks ok, but your linux and smb passwords are not synced

Try "smbpasswd" to set the password, from a terminal for the linux user account you are using to access the shares.  The is also an option in the smb.conf to sync the samba and linux passwords

Problem is I don't know what password samba is set to - all I know is my user password but it asks me to enter my original password before it will change it.

I've looked at the conf file but it won't let me edit it - read only - and I'm not sure where to change it either.

thanks

---

### Post by Austin_KW on 2007-04-10
if you run as root you can set anyone's samba password, and I think I remember that it gives an error the first time ( i dont remember if you need to add -a for add or -e for enable but I dont think so)

try 
sudo smbpasswd swey (or whatever username)
but remember the first password it ask may be you sudo password!

---

### Post by FITorion on 2007-04-10
to add users to the computer

sudo useradd -s /bin/true username

it will prompt for your pass word since sudo gives root powers
The -s makes it so the user can not have root control... useful if you don't fully trust people.

you already have an account on the computer so you don't need to do that.

adding users to shared list

sudo smbpasswd -L -a username
since you didn't need to "useradd"  it will prompt for your main pass word
then prompt for the pass word for the account you are creating
then prompt again to conferm the pass word

sudo smbpasswd -L -e username
this will enable the account you just made

---

### Post by FITorion on 2007-04-10
> **swey said:**
> Problem is I don't know what password samba is set to - all I know is my user password but it asks me to enter my original password before it will change it.

I've looked at the conf file but it won't let me edit it - read only - and I'm not sure where to change it either.

thanks


Sudo asks for the password you use to get into Ubuntu that you set up at the beginning.

smbpasswd -L -a username is setting up an account in samba so it's all new sort of... you can set it's password to what ever you want.  The username has to be one that is set up in user and groups in the system>administration tab or by useing useradd.  since this is for you I'd say use your current username since that is already set up.

---

### Post by swey on 2007-04-11
> **FITorion said:**
> The username has to be one that is set up in user and groups in the system>administration tab or by useing useradd.  since this is for you I'd say use your current username since that is already set up.

Thanks - I opened this and there were two accounts - the one I set up and one called root. I tried using root as the username but it still wouldn't open so then i just changed the root password to the same one as my username password and now it opens.

---

### Post by Austin_KW on 2007-04-11
the root (super user) account on ubuntu is normally disabled s.t. you cannot login as root but rater use sudo to gain root privileges. You do not want to use the root account as a samba user, it has too many access rights. 

Either use your own or another existing  username to access samba shares or create a new user like 'sambauser' you can then control what rights you give it.

---

