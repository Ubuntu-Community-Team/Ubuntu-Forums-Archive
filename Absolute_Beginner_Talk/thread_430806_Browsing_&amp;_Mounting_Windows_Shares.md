---
title: "Browsing &amp; Mounting Windows Shares"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-05-02
Something is screwy on my network and I can't quite figure it out.

If I click on Places-->Network Servers, Nautilus opens showing "Windows Network".  Clicking on that shows nothing even though I know there are 5 computers with windows shares (including one Fedora Machine with Samba sharing).  

I can ping all of the other computers.  All of my network NFS folders properly mounted at startup.

If I click on Places-->Connect to Server..., I can manually enter the computer name and the computer mounts (showing a folder on my desktop that I can browse and see all the shares for that computer).

Any clues for troubleshooting?  I checked System-->Administration-->Networking, and made sure my computer is in the right workgroup (domain name).

---

### Post by lamalex on 2007-05-02
can you post your smb.conf? something is probably going on inside there.

---

### Post by l951b951 on 2007-05-02
One question:  Doesn't samba affect how other computers see me?  Does it affect how I see other windows shares?


> [global]
    ; General server settings
    netbios name = LINUX-LAPTOP
    
    workgroup = LINKSYS
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
server string = tuxtop
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

[levishare]
    path = /levishare
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = levi
    force group = levi
comment = linux laptop share
available = yes
public = yes
writable = yes


---

### Post by Fitzcarraldo on 2007-05-03
I have the same problem as *I951b951*. If I click on Places > Network Servers and double-click on the Windows Network icon in the main part of the window, the window that opens has nothing in it. However, it used to display the icons of the other PCs on my home network. Fortunately, some time ago I 'instanced' some of the shared folders ("shares") in the Side Pane of the window, so I can still access the shares on some of the other PCs by double-clicking on the small folder icons in the window's Side Panel, but I would like to be able to see all the PCs in the main window.

---

### Post by Fitzcarraldo on 2007-05-04
It appears that this is a known bug in Ubuntu Dapper, first reported a year ago:

[Bug #47386 in samba (Ubuntu)](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/47386)

Is there any chance that the developers will fix this?

---

### Post by Fitzcarraldo on 2007-05-04
Here's another thread that may be related to the problem we are seeing:

[Can't Browse Windows Network](http://ubuntuforums.org/showthread.php?t=298909)

where some people report being able to see the other PCs in the window while others see a 'white sheet' icon or nothing.

---

### Post by l951b951 on 2007-05-07
Thanks for your response.  I figured I had broken it (since it worked before) and didn't look for a bug.  But it does seem to be a bug.

---

### Post by Fitzcarraldo on 2007-07-02
Just an update on my latest finding regarding the annoying Nautilus bug that does not allow us to browse Windows Network samba shares.

I happened to read again the following thread today -- I've read it before but discounted it because a reboot did not solve the problem in my case -- and decided to actually try running Nautilus as root. Have you tried it?

[http://ubuntuforums.org/showthread.php?t=382847](http://ubuntuforums.org/showthread.php?t=382847)

I typed the following command into a Terminal window:

```
sudo nautilus --browser
```

and then selected **Go > Network** from the pull-down menu in the Nautilus browser window that popped up. What do you know, the icons for my BT HomeHub and Windows Network (named MSHOME in my case) appeared, I could click the MSHOME icon and see the icons for the other PCs on the Windows Network and click on them to get to the shared folders on each PC.

So it works if I am running Nautilus as root, but not if I am running Nautilus when I'm logged in under my usual username. Very strange. I wonder if the problem is related to file permissions? :???:

EDIT: As a workaround I've added a shortcut to my Desktop to launch a Nautilus browser window as root, so that I can again browse all the PCs on my network with ease. I added the shortcut by right-clicking on my Desktop and selecting 'Create Launcher...', and then entering the command "sudo nautilus --browser" (without the quotes) in the Command box and ticked the 'Run in terminal' box. I gave the launcher a suitable name and selected a suitable icon for it. Now, if I want to browse the samba shares on any of my networked PCs, I double-click on the launcher icon on the Desktop, enter my password in the Terminal window that pops-up, and a Nautilus window running under root pops up. This is not ideal, but is better than nothing.

---

### Post by jaime256 on 2007-07-17
Hi guys. Well, I'm getting a similar problem. I'm only using windows under vmware and my problem is that I can't browse from the vmware under ubuntu or anything else to my infrant nas. If I click on browse nothing shows up, but I can open the folder icon with the ip for that nas and see my shares. Does anyone have any ideas on what's going on. I even reinstalled my whole ubuntu in order to clean things up and just to make sure things are on a new install. I'm also getting the same thing on my desktop using Ubuntu. Again, I can connect directly, but not when I'm browsing. I got a screenshot here to show you guys...let me see if I can post it...any help is appreciated, thanks.

---

### Post by sailtoad on 2007-07-24
I also had the same problem - Places > Network > Windows Network > Workgroup 

Opening the icon for the my workgroup yielded the following error:

Couldn't display "smb://workgroup"
The location is not a folder

Of course, "Workgroup" would be whatever you call your Windows workgroup.  After following all the directions for WINS,  DNS, Winbind, etc.  I had no luck.  I could not browse the windows network.  I could ping all the workgroup computers by ip addess or computer name but still no luck.

Finally after 2 days of frustration I found the solution.

System > Administration > Shared Folders  After being prompted for my password I was notified that the file and I believe the printer sharing modules were not loaded and I was prompted to load two modules (One for Windows  and one for Linux).  And I set up my Home folder for sharing.  After that, all the workgroup computers were visible and fully accessable.  Go figure - the same thing happens in Windows when file sharing isn't enabled.

Hope this helps others who are also green to Ubuntu.

---

### Post by jaime256 on 2007-08-02
Thanks for the info sailtoad, but your solution is only good if I want to share a folder from my computer. I want to browse a network shared from inside vmware.  I did install the support for the shared folders then realized that didn't do anything for me. I then wanted to uninstall that since it made no difference to me, but I couldn't find what I needed to uninstall, so that's that. I just left it alone for now, since I'm not sharing any folders anyway. I have found that I can browse the network drives from within open office, so I think the problem just has to do with vmware since that one will not let me browse the nas shared. It's odd because I remember being able to do that when I first installed it, but then we got all the updates and who knows.

Now my problem is the sound, sometimes it works and sometimes it just doesn't which is very annoying because I haven't made any changes myself to the sound files other than the usual ubuntu updates. Other than that, things seem to work okay plus my new 22" inch lcd makes things look really nice now. :) So I can live without this other stuff for now, but I hope they clean this stuff up once and for all. Soooo close, but not quite there just yet...:)

---

### Post by seb_renaud on 2007-08-02
Hi,

I have not had the "invisible shares when browsing with Nautilus" problem, but what I was trying to do is in the title of *this thread, so here it is:

How can I mount ( no GUI needed here ) a Windows share to be able to access it in a shell script? I tried a lot of smbclient and mount invocations with no success. I always get a "5428: session setup failed: ERRDOS - ERRnoaccess (Access denied.)" error .Nautilus is able to see these shares, so I KNEW it was possible, but how? 

This [thread]("http://ubuntuforums.org/showthread.php?t=280473") seems to show the right method, since I got it to work. My problem seemed releated to my password that has many characters that needs to be escaped from the shell. Even if the shell does not complain, changing my password to alphanum values solved my problem.

---

### Post by klytu on 2007-08-04
> **l951b951 said:**
> Something is screwy on my network and I can't quite figure it out.

If I click on Places-->Network Servers, Nautilus opens showing "Windows Network".  Clicking on that shows nothing even though I know there are 5 computers with windows shares (including one Fedora Machine with Samba sharing).  

I can ping all of the other computers.  All of my network NFS folders properly mounted at startup.

If I click on Places-->Connect to Server..., I can manually enter the computer name and the computer mounts (showing a folder on my desktop that I can browse and see all the shares for that computer).

Any clues for troubleshooting?  I checked System-->Administration-->Networking, and made sure my computer is in the right workgroup (domain name).

Did you ever find a solution for your issue? If you haven´t, I don´t think my story will give you an answer but at least you will know that you are not alone!

I built a new computer last weekend that had this same issue for a couple of days. After I did a fresh installation of Feisty and installed all the latest updates, when I would click Places>Network Servers I got exactly the same behaviour you got. Going to Places>Connect to Server also gave the same behaviour. The only way I could connect to a Windows share was to manually enter the IP address of the computer I wanted to connect to. I also tried using a Fiesty LiveCD on the newly built machine, but had the same issue.

A side effect of this behaviour was that I couldn´t connect to a shared printer that is physically attached to one of the networked Windows machines. This was really frustrating because I never had these issues on my older machines that ran either Fiesty or Dapper. On those I could connect automatically to my Windows shares through either Places>Network or Places>Connect to Server. On the old machines I could do this without installing any additional packages or changing any settings after a fresh, default installation. For a couple of frustrating days I tried all sorts of troubleshooting (including many of the things you tried) and searched the forums and online for a solution. I also re-connected the old boxes that worked and meticulously wrote down their network settings to see if I could find any differences, other than hardware, between the settings on the old machines vs. those on the new one that might be causing the problem on the new box. I couldn´t find an answer. 

One night, I happened to leave a Nautilus window open where I had been browsing a shared folder on a Windows machine by using Go>Location and then typing in the IP address of the Windows machine. I had accidentally left this window open all night long when I went to sleep. When I got up the next morning I closed it and tried Places>Network again - I could now see and access all of my Windows shares! The problem had gone away! I confirmed this by shutting down and rebooting - I could still connect to the shares through either Places>Network or Places>Connect to Server.  I could also now connect to the shared printer attached to the networked Windows machine.

 I tried using a LiveCD to see if the problem was corrected there now as well, but it wasn´t. It´s great that the new computer connects as expected now, but I haven´t been able to figure out what caused the problem or why the behaviour went away. Incidentally, on the older boxes that never demonstrated the faulty behaviour, the LiveCD connects to Windows shares through Places>Network and Places>Connect to Server without issue. This leads me to theorize that the odd behaviour is due to a hardware compatiblilty issue. I have been thinking about this for a while and it occurred to me that the new computer I built has an ethernet adapter built-in to the motherboard, while the older boxes that didn´t demonstrate this issue all have PCI card ethernet adapters. This may not mean anything, but I still think the faulty behaviour is  most likely due to a hardware interaction issue of some kind. 

Anyway, that´s more than enough rambling about this for now!

---

### Post by funkadelic on 2007-08-07
I am having this problem in feisty as well...

---

### Post by michaelzap on 2007-08-07
I've also had this problem, and what I do is to disable the Firestarter firewall and then the shares appear normally in Nautilus. I imagine that if I were to spend some time learning how to set up firewall rules I could make this work without needing to do that, but so far I've been too busy/had more important things to do.

If anyone figures out how to set this up so that it's not necessary to disable the firewall to see SMB shares in Nautilus, I'd love to know how.

---

### Post by funkadelic on 2007-08-07
Thanks!

I removed firestarter, rebooted, and things are back to normal. I didn't realize that firestarter (or parts of it) were running in the background.

---

### Post by jaime256 on 2007-08-08
> **klytu said:**
> Did you ever find a solution for your issue? If you haven´t, I don´t think my story will give you an answer but at least you will know that you are not alone!

I built a new computer last weekend that had this same issue for a couple of days. After I did a fresh installation of Feisty and installed all the latest updates, when I would click Places>Network Servers I got exactly the same behaviour you got. Going to Places>Connect to Server also gave the same behaviour. The only way I could connect to a Windows share was to manually enter the IP address of the computer I wanted to connect to. I also tried using a Fiesty LiveCD on the newly built machine, but had the same issue.

A side effect of this behaviour was that I couldn´t connect to a shared printer that is physically attached to one of the networked Windows machines. This was really frustrating because I never had these issues on my older machines that ran either Fiesty or Dapper. On those I could connect automatically to my Windows shares through either Places>Network or Places>Connect to Server. On the old machines I could do this without installing any additional packages or changing any settings after a fresh, default installation. For a couple of frustrating days I tried all sorts of troubleshooting (including many of the things you tried) and searched the forums and online for a solution. I also re-connected the old boxes that worked and meticulously wrote down their network settings to see if I could find any differences, other than hardware, between the settings on the old machines vs. those on the new one that might be causing the problem on the new box. I couldn´t find an answer. 

One night, I happened to leave a Nautilus window open where I had been browsing a shared folder on a Windows machine by using Go>Location and then typing in the IP address of the Windows machine. I had accidentally left this window open all night long when I went to sleep. When I got up the next morning I closed it and tried Places>Network again - I could now see and access all of my Windows shares! The problem had gone away! I confirmed this by shutting down and rebooting - I could still connect to the shares through either Places>Network or Places>Connect to Server.  I could also now connect to the shared printer attached to the networked Windows machine.

 I tried using a LiveCD to see if the problem was corrected there now as well, but it wasn´t. It´s great that the new computer connects as expected now, but I haven´t been able to figure out what caused the problem or why the behaviour went away. Incidentally, on the older boxes that never demonstrated the faulty behaviour, the LiveCD connects to Windows shares through Places>Network and Places>Connect to Server without issue. This leads me to theorize that the odd behaviour is due to a hardware compatiblilty issue. I have been thinking about this for a while and it occurred to me that the new computer I built has an ethernet adapter built-in to the motherboard, while the older boxes that didn´t demonstrate this issue all have PCI card ethernet adapters. This may not mean anything, but I still think the faulty behaviour is  most likely due to a hardware interaction issue of some kind. 

Anyway, that´s more than enough rambling about this for now!

Well, I can assure you, it's not hardware. I'm very sure about that. I've just tested amaya to try an edit my website, but I can't save anything. I am able to use the ip address and go to my share under amaya like you mentioned, but I still can't do that under vmware, so I'm now very certain it's all software related. All the hardware is working fine. I'm attaching the screenshot of this. The program tells me I can't save though. So there you go. I also can browse the network shares under places and network without any problems or leaving my system on all night, so I can see everything fine. Just remember when you first turn on your machine, it takes a moment to see things on the network. I have also checked to make sure I'm not running a firewall and that's not installed either. At the moment, I'm not sure what other firewalls to look for since that's the one thing that makes a bit of sense, but other than that, I'm still running into this annoying problem. So I'm narrowing it down to Ubuntu or Firewall for now...since I got two programs that won't let me do that. Open Office shows my share ip and shares fine. So it's a program issue not hardware related. Hope that helps. I still haven't heard from anyone from ubuntu or the rest of the community so my guess is as good as yours for now. Oh yeah, as for the printers, you gotta use cups and the line you need to type is picky, you need the word printers in there. Just put your mouse over the line and look at the example, but I'm sending you a screenshot so you can see what I mean. You add printers just as you do in windows too. It's just this line that gets picky, I had to reinstall my network printer again yesterday and forgot about that so it took me a bit to get it working again. That is fine now. Last but not least, I don't know why we can't see the screenshots when you're not logged in. It sucks because people can't see what you mean...guys what's going on with that?

---

