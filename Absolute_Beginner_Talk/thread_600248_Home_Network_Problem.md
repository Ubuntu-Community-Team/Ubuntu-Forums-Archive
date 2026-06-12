---
title: "Home Network Problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by john262 on 2007-11-02
When I open my network file browser I can see the icons for the two XP machines that share my home network with my Ubuntu Gutsy machine. But when I click on either icon I get a message that says that the folder contents cannot be displayed.

I didn't have this problem with earlier versions of Ubuntu. Also, I can browse my Ubuntu machine's shared folders from either XP machine but it won't work in reverse.

Also, I can put smb://192.168.0.3 etc. in my browser's address bar and get to the shared folders on the Windows machines that way.

I don't think it's a problem with the Windows machines since as I said before I upgraded it worked fine and I have not changed either Windows machine since. BTW, I tried turning off the Windows firewall but it didn't help.

Can anyone help with this? Thanks a lot.

---

### Post by john262 on 2007-11-02
Nobody has an answer to this? Is it a bug that I can't do anything about? Thanks.

---

### Post by john262 on 2007-11-02
I am bumping this message again in hopes that some kind soul will decide to help me. If I cannot network my Ubuntu machine with my Windows machines then it's worthless to me.

Thanks.

---

### Post by jba6511 on 2007-11-02
same issue here. Successfully used samba to share a folder that can be seen by xbox and windows xp clients. Can not browse xp clients even though they have shares.

---

### Post by john262 on 2007-11-02
Thank you for your reply. If this is happening to you too then perhaps we need someone to look into this. Does anyone know if it's a bug and if so when will it be fixed? I looked through the list of known bugs and couldn't find it listed there.

---

### Post by jba6511 on 2007-11-03
any one have some suggestions????

---

### Post by tact on 2007-11-03
tell us some more about your home network....

For example.   I had a similar problem (folder cannot be displayed) when accessing shares on my wife's WinXP laptop from my Feisty/Gutsy laptop.

Frustrated the hell out of me as i could ping the machines and get to them via IP addresses (as some here seem to be able to do also).

Then I found something...  My home network has one router with wifi AND wired ports..  and I have another wifi AP set up on the LAN to give good signal all thru the house.  The problem ONLY occurred if:
1.  I was connected via one wifi AP and she the other or....
2.  if one of us was on wired and the other wifi connection.

i.e.  if we were both on the same wifi access point...  or both on the same wired hub...  then the problem disappeared.

Does that give you all any leads?

---

### Post by antony11 on 2007-11-03
I too am having network problems similar to this thread. I have a small network at home as follow:

pc1 dual boot vista/ubuntu (this pc is the one with this issue)
pc 2 Vista
pc 3 + 4 xp
pc 5 Ubuntu server (will be anyway when working - different issue)

When I go to places > Network I get the icon for the Windows network double clicking on this varies from giving me an empty window to showing me my network icon (called startrek).
When I double click this icon it thinks about it for a few seconds and then gives the following message:

[B]The folder contents could not be displayed.
Sorry, couldn't display all the contents of "Windows Network: startrek".[/B]

pc1 connects direct to the router. 2,3,4,5 connect to the router via a switch (not enough ports on router to connect direct). All are running DHCP. I cannot get any further than this so I cannot see any of the other boxes or their shared folders. I dont even get an icon for this box either as I would expect to get on a windows network.

---

### Post by afeasfaerw23231233 on 2007-11-03
i have the same problem here too. although i set my windows box to share a folder, this popup appears
[[img]http://img3.freeimagehosting.net/uploads/c03c1ea6de.png[/img]](http://www.freeimagehosting.net/)

---

### Post by carlosjuero on 2007-11-03
I have noticed this too - I cannot browse the SAMBA shares on my local network (with all Samba/NFS/etc drivers installed on the local machine) via the network panel; I can type in the IP address of my file server (smb://192.168.1.xxx) but browsing through network:/// or smb:/// doesn't allow anything to be opened.

Today I decided to change my file server over to Ubuntu (another story in itself, bloody old AGP ATI card has compiz enabled from the get-go with no issues; where as my X1650 on this machine has to jump through hoops and deal with performance degredation if I enable compiz :() - I set up the new ubuntu system to share some folders via Samba (I tried NFS, but it didn't show up that way either) - same thing happened. I could browse to it with the IP Address, but it won't open/show up in the network browser.

It seems to be something with name resolution or what not - the crazy thing? My windows boot can see the shares and open them perfectly normal. This is something to do with Ubuntu (likely Gutsy to be precise).

---

### Post by dvase on 2007-11-03
I also have this problem.  I would go submit a bug report right now, but my upgrade from Feisty to Gutsy left me with more serious issues to fix first.

---

### Post by jba6511 on 2007-11-03
My network setup is just a router with 3 hosts wired in and 1 wireless. Windows can see linux machines, linux can see windows but can not access them. 

copy of smb.conf

[PHP][global]
    ; General server settings
    netbios name = UbuntuDesktop
    
    workgroup = NETWORK
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
    path = /home/blake/Videos
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = blake
    force group = blake
available = yes
browsable = yes
public = yes
writable = no[/PHP]

---

### Post by OsakaWilson on 2007-11-03
Same problem here connecting two Ubuntu systems, both on Gutsy.

---

### Post by tact on 2007-11-03
My guess is that it is something to do with the windows network protocols (that smb mimics) cannot make the jump across different physical lan segments (wifi to different wifi AP, or wifi to wired) even if the logical segment is the same (i.e. all ip addresses are in the same subnet).

dont know enough to say more tho.

I gave up researching months ago.  I got as far as finding some comment about making the ubuntu box a WINS server and use winbind that way smb packets get retransmitted properly...  but I dont know if it would have worked.

---

### Post by john262 on 2007-11-03
Well, it looks like I'm not the only one with this problem. I have a D-Link DI-504 wired router. I don't have wireless.

---

### Post by tact on 2007-11-03
> **john262 said:**
> Well, it looks like I'm not the only one with this problem. I have a D-Link DI-504 wired router. I don't have wireless.

So all the machines in your home LAN are attached to the same router, all wired?   Hmmm...  then my problem is different.

When I had my wife's and my laptops connected via the same wired hub or same wifi AP then I could open shares no problems.  

e.g. Lets say we were both on the same wifi AP.  I can get into her shared folders.  If I plug in an ethernet cable ubuntu auto switches over... now she is on wifi and I am on wired.  Cannot get into her shares.

EDIT:  it had been so long since I tried this and I have gone from feisty to gutsy since then.   Thought I better check its still an issue.  *blush*  No its not an issue any more.  I can get into her shared folders easily and fast regardless which AP or router we are connected to.   So for me - problem is solved.

I did install winbind and set my gutsy box as a WINS server anyway (so I can browse corporate WAN windows shares that are on different subnets) ...  dont know if that makes a difference.

---

### Post by Jerry N on 2007-11-03
Is there a chance that your Windows machines and your Linux machines have different workgroup identifications?  I have found that to be necessary with Ubuntu 7.10 although I am not sure it was a requirement with Freespire (which is based on Ubuntu 7.04).

Jerry

---

### Post by carlosjuero on 2007-11-03
> **Jerry N said:**
> Is there a chance that your Windows machines and your Linux machines have different workgroup identifications?  I have found that to be necessary with Ubuntu 7.10 although I am not sure it was a requirement with Freespire (which is based on Ubuntu 7.04).

Jerry
I know my machines all share Workgroup ID's (first thing I checked); that also wouldn't explain why my windows box can see and access the shares normally.

---

### Post by jba6511 on 2007-11-04
my defined workgroup name is the same for all clients, xp and linux

---

### Post by carlosjuero on 2007-11-04
Ok, out of a spur of the moment thing I added my file server IP & Host name to my Hosts file.. and bingo. I could open it up and browse the SAMBA shares just fine.

I had already set up the server in my hosts file, but I had it set up as SERVER.WORKGROUP - I added another alias to just SERVER for the IP address, and the network places opened up and showed the server there, I could open it and browse the shares just fine.

So, if you are having trouble browsing your windows share (or SAMBA share on another linux box) with the network browser, try adding the IP address(es) and computer name(s) to your host file (System -< Administration -> Network -> Hosts tab). This works best, of course, if the computer(s) to be browsed has(have) a static IP address(es).

I can't believe this little thing slipped me by so easily, the reason my Windows boot could see it is that I didn't do anything to the Host file, on my Ubuntu box I added the server IP while trying to see the shares when the server ran Win XP; so this idea might help others in this thread with a similar issue.

---

### Post by jba6511 on 2007-11-04
that did it. I added the ip and hostname and now I can browse the windows shares. Thanks.

---

### Post by JayvJay on 2007-11-04
This may not be too helpful, but when I installed ubuntu I gave it my workgroup name and it had .net to at end of it.  It must have defaulted to that and I did not notice.  Check your workgroup name on the linux machine.   Everything works perfectly here...today. :guitar:

Luck!

---

### Post by carlosjuero on 2007-11-04
> **jba6511 said:**
> that did it. I added the ip and hostname and now I can browse the windows shares. Thanks.
yep :)

---

### Post by Peter09 on 2007-11-04
I am sure that this is an on-going bug which has been identified but nobody seems to be actioning it. General symptoms are that machines get an IP address from the DHCP server but cannot register their name, or get other machines names from the server. Allocating a static IP seems to work, but  my case is not satisfactory.

You can normally ping the other machines and mount shares by using IP addresses etc.

Unfortunately to a general 'windows' user this problem would stop them using Ubuntu. I use Ubuntu a lot and like it, however at present it would be difficult to recommend someone who does not know much about Linux to use it. To my mind this, and several other on-going bugs are BASIC flaws and should not appear in a functional OS.

---

### Post by antony11 on 2007-11-05
I tend to agree with many of the comments made above and Peter09 seems to sum it up nicely. Im a newbee to linux but not to computers in general and networking this is driving me mad with frustration.
If I open the network setting window and click on the general tab - I presume Im right in expecting to see my host name and domain name filled in with the information I supplied on earler attempts to set it up . However the domain name is always blank. Same if I go to the DNS tab and add a name in the search domain window. Every time I restart linux those windows are empty.
Ive started looking into the settings for the smb.conf file and have noticed there that its so full of things I am finding it difficult to know what should be there and what is not needed.
Unfortunately I think that many of the things in the documentation and the Howto files expect some understanding in the first place. That is frustrating in itself as you cant edit a file to you know what to edit it with and that requires antoher search for help.

Dont get me wrong, I can see many advantages to linux. But coming from a very MS windows domintated bakground Im finding it very frustrating to do the most simple of tasks. But give me a month or 2.... oh and a lot of help and support :) which seems to be far more freely available than any Ive seen in MS.

---

### Post by nikkkko on 2007-11-08
Hi,

I'm coming to this late but have the same problem.  I'm trying to share a directory on one Gutsy box with another Gusty box using samba.

I've shared the appropriate directory, and on the other machine can see the directory by typing smb://xxx.x.x.x but can't open it.  Here's where I show the depth of my ignorance - on which machine do I enter the host information, the server, (that sharing the directory), or the client, (that trying to see it)?  And do I add the ip/host name of the server or the client?

Thanks

---

### Post by carlosjuero on 2007-11-08
> **nikkkko said:**
> Hi,

I'm coming to this late but have the same problem.  I'm trying to share a directory on one Gutsy box with another Gusty box using samba.

I've shared the appropriate directory, and on the other machine can see the directory by typing smb://xxx.x.x.x but can't open it.  Here's where I show the depth of my ignorance - on which machine do I enter the host information, the server, (that sharing the directory), or the client, (that trying to see it)?  And do I add the ip/host name of the server or the client?

Thanks
The first key is to make sure that either one or both of the machines has a static IP address (rather than a dynamic one - which would require constant editing of the Hosts file). I suggest setting the Server to be static at the minimum, but if you share between the 2 alot then set both to static.

To set a static IP (I am using GNOME for an example as thats what I use) go to System -> Administration -> Network

Enter your password for access.

Depending on if you are connecting via cable/wireless select the appropriate network connection (Wired / Wireless in other words) and then click the Properties button.

Uncheck 'Enable Roaming Mode'

Select 'Static IP' from the drop down box

Enter a static IP in the first text box (Depending on your router/LAN configuration it will be in the format of 192.168.1.xxx or 192.168.0.xxx where xxx = the computer address)

The second box will be filled in automatically, don't bother changing it unless you have custom Subnets on your LAN

In the last box enter the IP address of your gateway (router - typically 192.168.1.1 or 192.168.0.1)

Click OK

Next click on the HOSTS tab

Click the Add button

Enter the IP address for the Server/Client [edit: not the computer you are on, the one you want to be able to see]
In the box below the IP entry, type in the name(s) of the Client/Server computer (I.e. Server, Workstation, DANSPC, etc)

Repeat as necessary on the other machine(s).

Click Close - it should update quick, you can stop and restart the networking daemon + SAMBA - I just restart the computer cause its easier for me :)

---

### Post by nikkkko on 2007-11-08
Thanks for the reply but still no joy.

To keep it simple, I am trying to see my shares from the same computer.  In my network settings I have added under 'hosts' my ip address, (from ifconfig), which happens to be 192.0.2.5 (static) plus my host name, 'whitecube'.  I save these settings then restart samba.

If I then go to the share, (from the same computer), smb://192.0.2.5 I see the folder, but when I try to enter I get the 'folder contents could not be displayed message'. 

Could you tell me where the 'hosts' information is stored so that I can check it?  I have two network connections, (one wired, one wireless), and am not at all convinced that the dialogue box saves the right information in the right place.

Thanks

---

### Post by nikkkko on 2007-11-09
For anyone else with Gutsy to Gutsy sharing problems, I solved this by uninstalling and removing everything samba and installing NFS instead.  Turns out that in this environment - i.e., no Windows - NFS is a lot easier to get to grips with.  From System>Administration>Shared Folders, download NFS when prompted, share the folder you want and add the users you want to be able to see the share, (I did that by entering their ip addresses). Remember that every time you add/change a share you need to restart NFS. 

sudo /etc/init.d/nfs-kernel-server restart

From the client end you need to create a directory to which you are going to mount the share as if it is a hard disk.  E.g., create a directory on the Desktop called 'See' and mount the directory 'Shared' (which is on the computer doing the sharing), thus:

sudo mount xxx.xxx.xxx.xxx:/path/to/Shared /path/to/See

where xxx.xxx.xxx.xxx is the ip address of the sharing computer.

You can set Gutsy to mount this drive automatically when you start it up, but I haven't done this yet so I'm not goint to post how to.  (But it doesn't look very difficult).

Hope this helps someone.

---

### Post by john262 on 2007-11-09
Thank you very much  Carlosjuero. I followed your instructions and I finally got it to work after banging my head on the wall about this for the past two weeks.

I have to say that we newbies shouldn't have to go through all of this just to get our network going, especially since it worked right out of the box without going through all of this configuration in previous releases.

I think that your tutorial should be placed in a sticky post at the top of this forum and/or it should be added to the  wiki.

Thanks again.

---

### Post by carlosjuero on 2007-11-09
> **john262 said:**
> Thank you very much  Carlosjuero. I followed your instructions and I finally got it to work after banging my head on the wall about this for the past two weeks.

I have to say that we newbies shouldn't have to go through all of this just to get our network going, especially since it worked right out of the box without going through all of this configuration in previous releases.

I think that your tutorial should be placed in a sticky post at the top of this forum and/or it should be added to the  wiki.

Thanks again.
No problem :) - I had to figure it out the hard way, had the exact same problems. I don't know why it is like this, but I have a suspicion it has to do with the local server name resolution in this SAMBA version (or something with Ubuntu's networking).

Just remember to pass things you learn along to someone else who may need help :)

---

### Post by cottonslurpy on 2007-11-09
**The Scene**
Shared Files on the XP machine.
I want to access my XP files from the UBuntu machine.
I can see the workgroup
I can see the computer(host) name.

**The Result**
Can't view the contents of the folder.

**The Fix**
I placed the IP of my shared machine in the host file as suggested, and that didn't do it for me.

My ubuntu machine and XP machine had the same Host(computer)  name  , so I changed my ubuntu Host(computer) name, restarted, BAM!!!  It works now.

I would recommend adding the ip of the shared machine to the host file anyway, and double , triple check you dont have the same Host(computer) name on both machines. 

Hope that helps someone, it drove me nuts for weeks.

---

### Post by carlosjuero on 2007-11-09
> **cottonslurpy said:**
> **The Scene**
Shared Files on the XP machine.
I want to access my XP files from the UBuntu machine.
I can see the workgroup
I can see the computer(host) name.

**The Result**
Can't view the contents of the folder.

**The Fix**
I placed the IP of my shared machine in the host file as suggested, and that didn't do it for me.

My ubuntu machine and XP machine had the same Host(computer)  name  , so I changed my ubuntu Host(computer) name, restarted, BAM!!!  It works now.

I would recommend adding the ip of the shared machine to the host file anyway, and double , triple check you dont have the same Host(computer) name on both machines. 

Hope that helps someone, it drove me nuts for weeks.
Oh yeah - thats a pretty important thing too. Even Windows will throw up if two host names are alike on the same network and trying to share. Always name each computer (or Virtual Machine) something unique, or face the headaches ;).

---

### Post by dgholmes59 on 2007-11-20
I added the IP address of the Linksys router, 192.168.1.1, to the hosts tab of the 'Network Settings'.  All of my computers are connected through the router.  2 wireless and 1 wired.  Using Ubuntu 7.10 on the laptop and Windows 2000 on the wired computer.  Worked great after that.

System>>Administration>>Network>>Hosts  'Add' - 192.168.1.1

Edit:
Spoke too soon.  This only allowed my computers to finally show up.  I still could not access the files.  Had to add the IP address of the computer with the shared files before they would display.  This is going to be a problem though, because my network uses DHCP.

---

### Post by jonandrews on 2007-11-21
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

### Post by markham999 on 2007-12-01
Just wanted to say many thanks to jonandrews for your networking guide - after hours of fruitless stumbling newbie-searching it was your guide that finally got windows to access my ubuntu shares!

I now have a network of several windows PC + one ubuntu machine!

Only one minor problem is that to access the shares on the ubuntu box I have to re-enter the password on the windows boxes after every reboot and this is a problem because there are a number of automatic scripts that I use to syncronise files across the network - is there a way round this I wonder?

Thanks again for saving my sanity!
Mark.

---

### Post by jonandrews on 2007-12-02
I glad the guide worked so well for you.  I have to say, I can't replicate the issue you have with being forced to re-enter the passwords every time you re-boot windows. I've had about 12 or so different Windows pc's on my network, XP & Vista, and only ever had to do it once, on the first time of access. I know that there are issues with Win98 & Win2000 - do you have either of these OS's on your network?

---

### Post by markham999 on 2007-12-03
> **jonandrews said:**
> I can't replicate the issue you have with being forced to re-enter the passwords every time you re-boot windows. ... I know that there are issues with Win98 & Win2000 - do you have either of these OS's on your network?

Its odd - there are three windows and one ubuntu machine on the network. All the windows machines are XP home and  fully updated. Of these two insist on the password to access the shares on the ubuntu machine after every reboot. The only one that does not is my own desktop machine and on that, coincidentaly, I use the same username and password as I've set up on the ubuntu machine.

Hmmm...

Mark.

---

### Post by jonandrews on 2007-12-05
Mmm... indeed.  It is coincidence, though, I think, as all my machines have different passwords and only force a login once, on the first time of connecting.  I'm afraid I'm out of ideas, but I think if I were you, I'd be researching the Windows end of things now. Good luck

---

### Post by rmalouin on 2007-12-05
Instead of trying to browse to the share, try linking to it (just got to know the name). That worked for me. Once the link is established an icon will appear on your desktop click that and there you be.

Hope this helps.

---

