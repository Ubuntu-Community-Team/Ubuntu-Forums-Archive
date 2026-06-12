---
title: "2 days asking for help with samba."
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by deethree on 2006-11-04
ok I'm :confused: .

Tired to use Stormbringers HOW-TO, checked out a few links etc. (oh yeah I'm new to ubuntu btw. ;) )

I can "see" the drive I'd like to share on my laptop but it keeps saying that "network path is not found" I thought I laid it out properly in the config *sigh* but I've messed something up somewhere. 

(I've tried to set up an ftp, and that did work out either.) 

(I enter a wrong username (other then the ones I set in samba and it pukes out a login box again (can't be too much wrong then could it? )))

I'm gonna go re-read the how-to again and see if I missed something. 

d3.

---

### Post by deethree on 2006-11-04
That's a horrible title. Sounded ok in my head. not the intention I wanted to get across.

"2 days can't get it to work, now asking for help with samba"

"Tried for 2 days, asking for help with samba"

](*,) 

d3.

---

### Post by Irony on 2006-11-04
These are my notes on Samba;

Samba doesn't need to be installed for a shared Windows folder to be visible on the Network to a Linux machine.

However for the Windows machine to see the shared Linux folder Samba is necessary.

Set a network password for each user;

[PHP]sudo smbpasswd -a username[/PHP]

System > Administration > Shared Folders

This adds entries to;

[PHP]gksudo gedit /etc/samba/smb.conf[/PHP]

Which can also be manually configured &#8211; once configured do;

[PHP]sudo /etc/init.d/samba reload[/PHP]

which reloads the smb.conf file.

[PHP]sudo /etc/init.d/samba restart[/PHP]

which restarts samba.

Then check the editing with;

[PHP]testparm[/PHP]

Places > Network Servers

Here's my config file;

[PHP]log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

encrypt passwords = true
passdb backend = tdbsam guest
obey pam restrictions = yes
invalid users = root
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

socket options = TCP_NODELAY

wins support = no

[global]
   workgroup = MSHOME
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

[homes]
   comment = Home Directories
   browseable = no
   writable = no
   create mask = 0700
   directory mask = 0700

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

[storage]
   path = /mnt/fat32/fatshare
   comment = fat32_partition
   available = yes
   browseable = yes
   public = yes
   writable = yes[/PHP]

Even although I'm the only one who uses my computer, I set up another user (so when I boot up I see myself and another person) - I did this because I didn't want the other person to see my home folder; thus they have there own password which allows them to see the shared folder but not my home folder.

---

### Post by deethree on 2006-11-04
ok, I'll go thru it. 

](*,) 

Hopefully I can get it. No music is driving me insane. :-k

---

### Post by deethree on 2006-11-04
w0ot!

damn firewall on the laptop was killing me.

Copying files now, at least I'll have background music to figure out 100% the issues between ubuntu and XP. 

Thanks for the prompt response Irony.

Greatly appreciated.

d3

---

### Post by RudolfMDLT on 2006-11-04
Deethree,

I had troubles with samba and ftp but i cracked both. I'll be happy to help. Too much help is a bad thing so Irony's help is good. Just to expand on what he/she said:


1) Have you added the windows users to to your samba server?
If you don't what i'm talking about:


i) "sudo smbpasswd -e yourname" (you're user name)
ii)Type and retype new Samba password
iii)"sudo smbpasswd -a XP windowsusername" (kitchenpc)
(the usernames of your network users)
iv)Type and retype their passwords

2) Are you running a firewall? If so switch it off and try again.


Setting up ftp is really easy! :)

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Is a really good guide, but please use the GUI method! 
then on the windows machine's download and install
NetFileServer from tucows.

[http://www.tucows.com/start_dl/296978_111881_1020](http://www.tucows.com/start_dl/296978_111881_1020)

It's really an awsome little app. 

Anyway, I'll check back later to see of you won! If you do get you network working try the ftp anyway! :-D 

Goodluck!

Cheers!

---

### Post by RudolfMDLT on 2006-11-04
I have a machine on the network that when I put it on all browsing on my network goes down! to check whether the nework is working, try this:

On the windows machine, click start, run: "CMD" or "Command"(Win98&Me)

in cmd type ipconfig.

Take the ip address of the windows machine and in linux's "Explorer" press CTRL+L and copy and paste:

smb://10.0.0.6/

where 10.0.0.6 is the IP address of the mahcine, 192.168.10.1 or whatever.

Cheers!

---

### Post by deethree on 2006-11-04
1) yes I did, twice in fact. I'm sure that after I get everything working I'll reinstall the whole mess and do it over again. Just to make sure it wasn't a fluke.

2) a firewall on the other machine ( XP? )  I was, but I've got a computer I'm going to turn into a fire wall and put it before my router to stem any issues.

3) I'll have to check into that thread, just saw that nautalis was eating 93% of my CPU (gonna look into that.) 

Thanks for the time and I'll reply later about the proress (if any ;) )

d3.

---

### Post by Eric Boring on 2006-11-05
Irony, 

Your Config file and instructions worked great for me. After days of trying, I could finally browse to the Ubuntu machine from my XP laptop and map the shares I wanter, etc.

But when I restarted Windows, everything was broken again. 

I tried restarting samba on the Ubuntu machine. Does anyone have any ideas for me? Even if I try to map the network drive after the restart, it's liket he Ubuntu maching is just turned off.

Could it be the screensaver that is kicking in on the Ubuntu machine?

Any advice you have will be greatly appreciated!

-Eric

---

