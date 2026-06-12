---
title: "printing from a mac to ubuntu"
date: 2009-10-28
forum: Apple Hardware Users
---

### Post by p2ranger on 2009-10-28
Howdy

Well, this was working up until I upgraded to Ubuntu desktop 9.10. No more.

I'm a new with Linux. I just did a complete reinstall of Ubuntu desktop 9.10. I want to make it a print and file server. I've currently got samba installed and running. I'm not sure if I installed cups onto. I'm assuming by default it was installed. Currently, my XP computer is interacting with it the way I want. Getting XP to work, by the way, wasn't hard. Cant' say the same about the mac.

My wife's mac will not print. I just updated it to snow leopard and it has all the updates to it. I can't get it to see the printer when I try to add it as a Windows pritner. It sees the linux computer, asks for a username/pass or use as a guest account, and it will never show the printer now for me to choose from. 

The printer is connected by USB to the linux box right now. When I tell it to print, it asks for me to authenticate. I've tried the main user/pass that I use when I use linux, and that doesn't work. I've tried accessing it as a guest, and that doesn't work. I don't know much about mac's as it's my wife's. What ever happened to "Macs just work"?

When I go to System->Admin->Printing, the printer is there. When I right click, the shared box is checked. When I go to Server->Settings, Publish Shared printers connected to this system is checked as well as Allow remote admin

I've tried editing my smb.conf file the way the online documentation has said to do and that doesn't work. I commented out what it showed first and added what the online documentation said to do below that:
```

#[printers]
#   comment = All Printers
#   browseable = no
#   path = /var/spool/samba
#   printable = yes
#   guest ok = yes
#   read only = yes
#   create mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
   printcap name = /etc/printcap
   print command = /usr/bin/lpr -P%p -r %s
   printing = cups

```

On the Mac, I've tried adding the printer two ways:

1. add as a windows pritner. The workgroup and the computer show up, but not the actual printer. Once I click the computer name, it asks for a usuer/pass. My ubuntu user/pass doesn't work nor does guest.

2. Add as an IP printer using IPP. I can get the printer to add, but it won't print. When I try to print, the printer jobs show it as being paused and its reason says because the printer doesn't exist.

I've been reading around the Internet and can't find a solution. Any help would be greatly appreciated.

Thanks

Jason

---

### Post by p2ranger on 2009-11-05
bump

---

### Post by linuxopjemac on 2009-11-05
Is it an idea to post this also under "Networking & Wireless" ? I guess more general people who know more about samba can be found there.

---

### Post by linuxopjemac on 2009-11-05
if CUPS is running on the Ubuntu machine, and the printer is visible, you can set the printer with:
[http://local_address:631](http://local_address:631)
this is the internal CUPS site. Add the new printer and add that printer (with an address like: [http://local_address/printers/HP](http://local_address/printers/HP) for example) as a network printer in MacOSX. Should be straightforward.

---

### Post by p2ranger on 2009-11-05
I must be missing some fundamental understanding here.

When I go to that address, my printer is already sitting there, so I'm guessing I don't need to add it again.

I tried adding from the mac using the system preferences, add printer, IPP using this address, which I got from the internal CUPS site
[https://192.168.1.123:631/printers/HP-LaserJet-1022](https://192.168.1.123:631/printers/HP-LaserJet-1022)

It said "client-error-not-possible"

I have no clue.....

---

### Post by KeLa on 2009-11-05
have you tried to change the setting
[FONT=monospace]
browseable = no
to
browseable = yes

That's the thing that hides the printer if you try to browse it.

[/FONT]

---

### Post by p2ranger on 2009-11-05
Just tried changing it, restarted the samba server, still doesn't show up

---

### Post by linuxopjemac on 2009-11-05
post it in the other thread, I don't know to be honest.

---

### Post by p2ranger on 2009-11-05
So get this, I ran through trying to set it up again, went through the CUPS web page interface, nothing seemed to work. Then I pulled a windows and rebooted the mac. Now I tried adding the printer through the system preferences as a windows printer (this would be through samba) and it let me add the printer (using as a guest). I have done that dozens of times, and it wouldn't work. I have no idea what changed. I guess when they say "Macs just work", its because there's no explanation as to why it worked.

Thanks for all your input.

Jason
):P

---

### Post by mediamind on 2009-11-16
Jason's method worked for me with a Macbook Pro (10.6.2) printing to an HP Laserjet 1012 connected via USB to my Ubuntu 9.10 machine. Like Jason, I added the printer to the MBP as a guest (System Preferences > Print & Fax > "+" Add a Printer > Windows > workgroup > My_Ubuntu_Computer_Name > Guest > Connect) but had to provide a Samba Username and Password the first time I tried to print a file from the MBP. I set these up on the Ubuntu end using: sudo smbpasswd -a USERNAME

Thanks!
David

---

