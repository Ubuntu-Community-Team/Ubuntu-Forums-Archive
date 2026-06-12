---
title: "Wireless at a university"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by shickidyshade on 2006-02-22
ok I am a engineer at a college were i have to use windows for all of my classes and i cant get the wireless to work on campus with ubuntu, i am at a university that reguires a secure connection and user login over the wireless any ideas if anyone has ideas i would greatly appreciate it 

Thanks

---

### Post by nalmeth on 2006-02-22
does your wireless work elsewhere?

---

### Post by jchau on 2006-02-22
Do they use something like Cisco VPN? If  they do, you need to get a VPN client for that.  Your school would probably have a link to the client on their website (chances are, there is a linux version avaliable (I know Cisco has a linux version of their VPN client).  If the client is unavailable, there are alternatives like vpnc (avaliable through apt-get or synaptic).  

If it is just WEP, you can use iwconfig.  

Hope this helps.  I'd probably be able to help you more if you posted what a Windows user would do to connect.  

(My school uses the Cisco VPN. I didn't want to install the client, so I just bring a CAT5 cable with me.  But then again, wireless coverage is quite shabby here.  Wired network access is more common here than wireless.)

---

### Post by shickidyshade on 2006-02-22
This is what it gives as requirements

All of the requirements below must be met in order for your wireless connection to properly work. Click Here for Wireless Support Information.

1. Windows XP Service Pack 1

      Windows XP Service Pack 1 provides the latest security and reliability updates to the Windows XP family of operating systems. Windows XP SP1a is designed to ensure Windows XP platform compatibility with newly released software and hardware, and includes updates that resolve issues discovered by customers or by Microsoft's internal testing team. Note: Please make sure your machine is in good working order before installing Window XP SP1. is not responsible for any malfunction of Windows XP Sp1.

Click here for Windows XP SP1

2. Wireless Secure W2 Client
    - Click here to learn more about SecureW2 and its download

3. 802.1x (A or B) Wireless Network Card or Dell D600/D800 internal network card.
    - Click here for more information on the supported network card @.

4. Zero Wireless Configuration Service , Started
    - Click here Instructions for checking and enabling if not available.

 5. Windows Pop-ups Must be EnableD
If pop-ups are not enabled, follow the instructions below.

Note: Editing the registry is a risky operation. Please call for assistance. User Support is not responsible for problems created due to registry editing.
To turn on balloon tips in applications that support XP Themes:

Method 1

   1. Go to Start, Run, type &#8220;gpedit.msc&#8221; and click OK
   2. Under User Configuration\Administrative Templates\Start Menu and Taskbar\
   3. Double click Remove Balloon Tips on Start Menu items
   4. Click Disabled, click OK, and Reboot

Method 2 (If Balloon Pop-ups are already turned OFF)

To turn on balloon pop-ups in applications that support XP Themes&#8230;
   1. Go to Start, Run, type &#8220;regedit&#8221; and click OK
   2. Go to HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced
   3. Delete the DWORD value EnableBalloonTips and Reboot

---

### Post by BoyOfDestiny on 2006-02-22
Geez, they might as well append MS to the name of the school network. Anyway, try step #2 in wine and see if that does the trick?


EDIT: Link removed per request. :)

---

### Post by shickidyshade on 2006-02-22
i also believe for non-university bought comp which i have 

they give out a cd so idk if ubuntu will be able to get it u must also have microsoft antispyware and a virus check i think

---

### Post by shickidyshade on 2006-02-22
what is wine and how does it work i found it on automatix and have no idea what it does

---

### Post by jchau on 2006-02-22
wine sets up an enviroment for windows programs in linux so that the windows programs can run.  

I would suggest contacting your school helpdesk or IT.  They will probably have more info.

---

### Post by Brunellus on 2006-02-22
[QUOTE=jchau]wine sets up an enviroment for windows programs in linux so that the windows programs can run.  

I would suggest contacting your school helpdesk or IT.  They will probably have more info.[/QUOTE]
...and in the event that your helpdesk is manned by drones who know nothing more than "click next, next, next, finish" and wouldn't know the difference between an operating system and an operating theatre....

Seek out your local Linux Users' Group.  There is probably one on campus.  Failing that, talk to the usual suspects for Linux use:  The engineering school, the mathematics department, the physical sciences.

---

### Post by shickidyshade on 2006-02-22
ok well heres the thing the idiots at our help desk are idiots they know dell and windows and just enought to fix them but they tend to just ghost a comp at any sign of error idiots i tell u 

i have tried the engineers that actually use linux which is few since we have so many programs in windows aka excel matlab mathcad autocad solidworks icepack etc.... therefore it is a small amount that use linux..  I am working on trying to get other people to make people turn or at least try linux..

I have not tried wine yet so if anybody wants to give a good qualtiy description of what it can doo i now understand it works windows programs but we have to have so many programs to make it work i am unsure if this will be possible 

thanks for any help in the past and in the future

---

### Post by shickidyshade on 2006-02-23
ok so i talked to a friend with an apple and this is what works for her. 

they have something called internet connect this is what she recieved

Wireless setup for Macs 
Even though "we don't support Macs," here's how to setup wireless for an Apple computer. 
They have aiport wireless card-Mac as 10.3 or later 
The Internet Connect application is needed to setup wireless. Open up Internet Connect, Go to File / New 802.1X connection (shift-open apple-X) and enter configuration. 
The user needs to enter LDAP usernarne/password. Under Edit Configurations, check TTLS for Authentication, click configure with TTLS highlighted to select PAP with 'anonymous' for inner authentication. 
See attached .jpeg for what I'm talking about. 
After that, all the user has to do is open up Safari/Firefox/MSIE and accept the security certificate and now they have wireless internet access. 

 I have a picture of it to but i dont know how to post it it is saved on my computer

---

### Post by shickidyshade on 2006-02-24
does anybody have any ideas abou this

Shade

---

