---
title: "Where is the windows network in terminal?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-20
how do you navigate to the windows network in the terminal?
i've tried many things, like:
```
cd Network
```
```
cd network
```
```
cd network:///
```
```
cd Network:///
```
and all kinds of other stuff, but nothing works!!!](*,)

---

### Post by user1397 on 2006-05-20
bump!

---

### Post by Jagot on 2006-05-20
```
smbclient //sharename/folder
```

So when I want to access my iTunes folder on my desktop, cunning called 'desktop', the code I write is:

```
smbclient //desktop/iTunes
```

---

### Post by user1397 on 2006-05-20
i meant more like how would you go to the windows network directory (places->network servers->windows network) in a terminal???

---

### Post by mostwanted on 2006-05-20
[QUOTE=erik1397]i meant more like how would you go to the windows network directory (places->network servers->windows network) in a terminal???[/QUOTE]

Can't you just drag and drop? I'm able to do that with my FTP sites.

---

### Post by Jagot on 2006-05-20
[QUOTE=erik1397]i meant more like how would you go to the windows network directory (places->network servers->windows network) in a terminal???[/QUOTE]

I don't think you'd be able to do it without mounting the drive:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by user1397 on 2006-05-20
[quote=mostwanted]Can't you just drag and drop? I'm able to do that with my FTP sites.[/quote]
i dragged and dropped the windows network icon into a terminal, and it turned out to be : network:///smblink-root
so i did:
```
sudo chmod 755 network:///smblink-root
```
but i got " No such file or directory"
???

---

### Post by IYY on 2006-05-20
Your Windows network is not a physical place on your file system unless you mount it there. Read up on smbmount. The command is of the form:

mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test

---

### Post by DSn0wMan on 2006-05-20
I just use
```
 smbmount //sharename/folder /home/somelocalfile 
```

This way samba isn't trying to mount the share when I am on the go with my computer.

jagot's advice seems to be the best option if your computer is not mobile.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by dmizer on 2006-05-20
[QUOTE=IYY]Your Windows network is not a physical place on your file system unless you mount it there. Read up on smbmount. The command is of the form:

mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test[/QUOTE]
if you want to browse to your share via terminal, you have to create a place for your share on your local machine.  ie, you have to do more than just mount it.

i added an entry to fstab so i get an icon appear on my desktop.  the fstab entry is called /media/sentra ... so in the terminal i go to cd /media/sentra, and my shared files will be shown with ls.

but using the smbfs mount method, you can place your shared folder anywhere on your system, like so: mount -t smbfs -o username=tridge,password=foobar //fjall/test /home/tridge/samba

now, i can use the cli to "cd /home/tridge/samba" and view my shares via command line.

---

### Post by user1397 on 2006-05-20
in the wiki guide, i followed [SIZE=2]the "Mounting unprotected network folders" part.
then i did "sudo mount -a" and i got:
Error connecting to <IPaddress> (Connection refused)
18082: Connection to <IPaddress> failed
SMB connection failed

BTW, in the wiki guide in the part where it says:
[/SIZE]"Then edit your /etc/fstab file", i did "sudo gedit /etc/fstab" to write those lines at the end. is that the correct procedure?

---

### Post by user1397 on 2006-05-20
bump bump bump!

---

### Post by user1397 on 2006-05-21
anybody?....................................:(

---

### Post by DSn0wMan on 2006-05-21
I think I am a little lost with this thread, but I'd like to help if I can.

Tell me if my assumptions are correct.

1) You have a share on your windows machine
2) You are trying to connect to it with your ubuntu machine
3) You want to be able to browse it from the terminal

---

### Post by user1397 on 2006-05-21
[quote=DSn0wMan]I think I am a little lost with this thread, but I'd like to help if I can.

Tell me if my assumptions are correct.

1) You have a share on your windows machine
2) You are trying to connect to it with your ubuntu machine
3) You want to be able to browse it from the terminal[/quote]

1) yes
2) yes
3) yes im trying to connect to it thru a terminal, since the gui way (places->network servers->windows network) doesn't work for me (nothing shows up inside windows network)

---

### Post by DSn0wMan on 2006-05-21
Ok then here is what worked for me.

Install smbfs
    sudo apt-get update 
    sudo apt-get install smbfs

Allow non root users to mount shares
     sudo chmod u+s /usr/bin/smbmnt   

Mount the share
     smbmount //myserver/myshare /home/yourusrname/mnt

*note /home/yourusrname/mnt needs to be created first, and you might need to adjust permissions

After running the smbmount command you will then authenticate with your windows share, and then you are in like flyn.

---

### Post by user1397 on 2006-05-21
[quote=DSn0wMan]Ok then here is what worked for me.

Install smbfs
    sudo apt-get update 
    sudo apt-get install smbfs

Allow non root users to mount shares
     sudo chmod u+s /usr/bin/smbmnt   

Mount the share
     smbmount //myserver/myshare /home/yourusrname/mnt

*note /home/yourusrname/mnt needs to be created first, and you might need to adjust permissions

After running the smbmount command you will then authenticate with your windows share, and then you are in like flyn.[/quote] thanks for stcking with me here,
when i tried the smbmount command, i got:
Error connecting to <IPaddress> (Connection refused)
3942: Connection to <IPaddress> failed
SMB connection failed

btw, my /etc/fstab file ends like this (correct it if you think its wrong):
//<IPaddress>/SHARE  /media/winmount  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=erik1397]thanks for stcking with me here,
when i tried the smbmount command, i got:
Error connecting to <IPaddress> (Connection refused)
3942: Connection to <IPaddress> failed
SMB connection failed

btw, my /etc/fstab file ends like this (correct it if you think its wrong):
//<IPaddress>/SHARE  /media/winmount  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0[/QUOTE]

Ok, So its telling you either that it dosn't like the //servername, or the windows share dosn't want to talk to you (firewall or share permissions)

Did you try using your windows hostname instead of ip address?

Your fstab looks fine, but I would probably try to get it working just using smbmount at first. When that works, then add it to fstab to mount on startup.

---

### Post by user1397 on 2006-05-21
[quote=DSn0wMan]Ok, So its telling you either that it dosn't like the //servername, or the windows share dosn't want to talk to you (firewall or share permissions)

Did you try using your windows hostname instead of ip address?

Your fstab looks fine, but I would probably try to get it working just using smbmount at first. When that works, then add it to fstab to mount on startup.[/quote]
i tried both the IP address and the server name, but neither works.
on my windows pc, i have the windows firewall set to allow file and printer sharing, and it can see and open my ubuntu share.  
i temporarily took out the fstab crap i put in, and tried smbmount, but it didn't work.
what now?!!!!!!!:confused:
(thanks again for staying with me on this one)

---

### Post by catlett on 2006-05-21
Why don't you post in "Server Talk" instead of "Absolute Beginner"? Did you already try and got no response? I don't know anything about this buit isn't this "server talk"? Might be better than bumping for replies in the beginner section, Wish I could help.

---

### Post by DSn0wMan on 2006-05-21
I am running out of ideas.

The part about "Error connecting to <IPaddress> (Connection refused)" really looks like a firewall issue if the windows part of the sharing is working.

Typically that error means that the service isn't running, or a firewall is blocking it.

I would try disableing windows firewall, and see if that works (temporarily of course).

If it doesn't, then I  would redo the file sharing on the windows end.

---

### Post by user1397 on 2006-05-21
[quote=catlett]Why don't you post in "Server Talk" instead of "Absolute Beginner"? Did you already try and got no response? I don't know anything about this buit isn't this "server talk"? Might be better than bumping for replies in the beginner section, Wish I could help.[/quote]
well actually, "server talk" is about the server edition of ubuntu, not about samba or windows shares........

---

### Post by it.henrik on 2006-05-21
can you brows your share through nautilus?

Places-Network Servers-Windows Network?

if yes

then this should work.

In your System-preferences menu  you might have something called xSMBrowser. With this tool you can brows your samba network and mount folders by rightclikcking on them.
If you dont find it there .. install it with synaptics.

Happy samba-share hunting.

---

### Post by dmizer on 2006-05-21
can you even ping the windows box?

also, what's the output of smbtree?

---

### Post by user1397 on 2006-05-21
[quote=it.henrik]can you brows your share through nautilus?[/quote]
no.

[quote=it.henrik] Places-Network Servers-Windows Network?[/quote]
no.

[quote=it.henrik] In your System-preferences menu  you might have something called xSMBrowser. With this tool you can brows your samba network and mount folders by rightclikcking on them.
If you dont find it there .. install it with synaptics.

Happy samba-share hunting.[/quote]
i installed it, but it does not appear in system->preferences

---

### Post by user1397 on 2006-05-21
[quote=dmizer]can you even ping the windows box?[/quote]
no, it just says "unknown host"

[quote=dmizer] also, what's the output of smbtree?[/quote]
$ smbtree
Password:
Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted
Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted
Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted

---

### Post by user1397 on 2006-05-21
[quote=DSn0wMan]I am running out of ideas.

The part about "Error connecting to <IPaddress> (Connection refused)" really looks like a firewall issue if the windows part of the sharing is working.

Typically that error means that the service isn't running, or a firewall is blocking it.

I would try disableing windows firewall, and see if that works (temporarily of course).

If it doesn't, then I  would redo the file sharing on the windows end.[/quote]
i disabled win firewall temporarily, and redid file sharing, and yet its a no-go :(

---

### Post by dmizer on 2006-05-21
[QUOTE=erik1397]no, it just says "unknown host"


$ smbtree
Password:
Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted
Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted
Packet send failed to 192.168.1.255(137) ERRNO=Operation not permitted[/QUOTE]
well, that's your problem.  something is blocking the connection between ubuntu and windows.  do you have a router between them?  how about checking firewall settings on your ubuntu box?

if you have a router between the two, i suggest rebooting your router to see if that fixes your problem.

---

### Post by user1397 on 2006-05-21
[quote=dmizer]well, that's your problem.  something is blocking the connection between ubuntu and windows.  do you have a router between them?  how about checking firewall settings on your ubuntu box?

if you have a router between the two, i suggest rebooting your router to see if that fixes your problem.[/quote]
i reset my router, but to no avail. i guess i have to manually open ports in my router, but i'm not really sure how! :(

---

### Post by user1397 on 2006-05-21
does it have to do with port forwading at all?
what category would this fall under?

---

### Post by dmizer on 2006-05-21
well, since windows can see ubuntu (is that still the case?) i was suspecting that there may have just been some sort of glitch in the router preventing ubuntu from seeing your windows box.  most often, a simple power off/power on will fix these kind of problems.

you said you reset the router, so that should have also done a power cycle.

how exactly is your network physically configured?  ie, what is where?
mine goes like this ... modem > knoppix firewall/router > hub > networked machines.

---

### Post by user1397 on 2006-05-21
[quote=dmizer]well, since windows can see ubuntu (is that still the case?)[/quote] yes that is still the case
[quote=dmizer] i was suspecting that there may have just been some sort of glitch in the router preventing ubuntu from seeing your windows box.  most often, a simple power off/power on will fix these kind of problems.

you said you reset the router, so that should have also done a power cycle.[/quote] well i reset it, so i guess it powered on/off, but still no change with my problem

[quote=dmizer] how exactly is your network physically configured?  ie, what is where?
mine goes like this ... modem > knoppix firewall/router > hub > networked machines.[/quote] mine is: cable modem > router > ubuntu box 
and router > windows pc (connected wirelessly)

---

### Post by user1397 on 2006-05-21
For a clearer picture of my setup, i have made this with KolourPaint:

---

### Post by dmizer on 2006-05-22
lol ... i'm in love with your wireless signal ;)

few more questions ... what brand/model of router, and what version of windows are you running.

you should be able to completely disable the router firewall to see if that helps.  also, if you're running win xp, that stinkin norton has a tendency to interfere even if it's turned off ... and especially if norton has expired.

if you have norton still on your machine and it's not paid for and not up to date, uninstall it from add/remove programs.  same goes for mcafee if you also have that but it's out of date.

what do you use for your firewall/av solution in windows?

---

### Post by user1397 on 2006-05-22
> **dmizer]lol ... i'm in love with your wireless signal  said:**
> 
windows is XP home, and router is linksys BEFW11S4 wireless-B broadband router

[quote=dmizer] you should be able to completely disable the router firewall to see if that helps.
im not sure how to disable the router firewall, but isn't that a huge security risk anyway?  

[quote=dmizer] what do you use for your firewall/av solution in windows?[/quote]
all i have is the windows firewall turned on but w/ file sharing as an exception, and then i have norton av, but im not sure how to access its firewall settings (if it even has one? i don't see one!)

---

### Post by DSn0wMan on 2006-05-22
Still at it huh?

You should be able to point your browser to [https://192.168.0.1](https://192.168.0.1) to access your router, and use some GUI to look at the firewall settings. It might be helpfull to post the rule set on your router firewall, if you can find them.

---

### Post by user1397 on 2006-05-22
[quote=DSn0wMan]Still at it huh?

You should be able to point your browser to [https://192.168.0.1]("https://192.168.0.1") to access your router, and use some GUI to look at the firewall settings. It might be helpfull to post the rule set on your router firewall, if you can find them.[/quote]
again, thanks so much everybody that has been helping me with this.
i'm able to go into my router settings using 192.168.1.1
here are all of my router settings' menus:
setup, password, status, DHCP, log, help, advanced (advanced includes:
filters, forwarding, dynamic routing, static routing, dmz host, mac address clone, wireless)
i don't see "firewall" anywhere :???:

---

### Post by DSn0wMan on 2006-05-22
My guess is that "filters" is your firewall, since a firewall in many cases is just a packet filter.

---

### Post by user1397 on 2006-05-22
here's what my "filters" section looks like:

---

### Post by catlett on 2006-05-22
Hey erik, I don't know anything about this (as you can tell by my server question that has nothing to do with networks/shares) but, I have experience with norton messing things up.
Norton can get in your system and not let go. 
I'll give you an example about norton and windows. My father has XP and Norton AV because a trial of Norton was on the computer when he bought it. He bought a subscription and when the next time came around I told him to switch to McAfee AntiVirus because Comcast gives you a McAfee subscription for free.
Anyways I shut down Norton. Uninstalled it through add/remove programs. Ran a utility I have to clean up traces of uninstalled programs on XP and installed McAfee. Once McAfee was installed his browser was blocked from the internet. I went crazy trying to figure it out. I power cycled evrything. The modem, router, even the voip box. I disabled Mcafee as well and nothing. I called comcast and they said everything is fine, it is on my end. Something, somehow had his computer totally blocked from the internet.
Totally exasperated and with no other thought, I reinstalled Norton. And go figure everything was fine. Once Norton was reinstalled the connection was back. Somehow norton shut down the computer even though I disabled it and then uninstalled it. I don't know if this affected you but I thought I'd throw it out there.

P.S. This might not help at all but when you scroll down to responses the guy solved his problem. It sounded pretty similar to you. Plus this was solved on the windows side which seems to be your issue. [http://www.experts-exchange.com/Networking/Microsoft_Network/Q_20965078.html](http://www.experts-exchange.com/Networking/Microsoft_Network/Q_20965078.html) Wish I could be of more help. I keep seeing you bump and wish I had an answer for you. Good luck. When you graduate you're  going to make a great administrator.:-D

---

### Post by dmizer on 2006-05-22
yes, this is a windows issue, i don't think your router is causing it.  especially since your windows box can see your linux box.  it really has to be something on the windows machine blocking your ubuntu.

do you have norton security center, or just norton antivirus?  and again, is it up to date and current?

also, in network connections, local area connection/properties, what's listed and checked under "this connection uses the following items:"?

also check under local area connection/properties > advanced > firewall > windows firewall settings > advanced tab ...
this will list all of your adapters/modems installed in windows, and allow you to select each one individually for firewall protection.  see, in windows if you have a dial up modem and a network adapter installed, but the firewall is turned on for the network adapter but not for the dial up modem, windows reports that the firewall is off for everything, so always check the advanced tab to make sure that the firewall is completley off.

if you're worried about security, simply disconnect the wan side from your router.  your local network will still be in place and you can still troubleshoot it.

but i'm going with a windows issue at this point.

---

### Post by user1397 on 2006-05-22
[quote=catlett]Hey erik, I don't know anything about this (as you can tell by my server question that has nothing to do with networks/shares) but, I have experience with norton messing things up.
Norton can get in your system and not let go. 
I'll give you an example about norton and windows. My father has XP and Norton AV because a trial of Norton was on the computer when he bought it. He bought a subscription and when the next time came around I told him to switch to McAfee AntiVirus because Comcast gives you a McAfee subscription for free.
Anyways I shut down Norton. Uninstalled it through add/remove programs. Ran a utility I have to clean up traces of uninstalled programs on XP and installed McAfee. Once McAfee was installed his browser was blocked from the internet. I went crazy trying to figure it out. I power cycled evrything. The modem, router, even the voip box. I disabled Mcafee as well and nothing. I called comcast and they said everything is fine, it is on my end. Something, somehow had his computer totally blocked from the internet.
Totally exasperated and with no other thought, I reinstalled Norton. And go figure everything was fine. Once Norton was reinstalled the connection was back. Somehow norton shut down the computer even though I disabled it and then uninstalled it. I don't know if this affected you but I thought I'd throw it out there.[/quote] well i guess this might be my problem then...:(

[quote=catlett] P.S. This might not help at all but when you scroll down to responses the guy solved his problem. It sounded pretty similar to you. Plus this was solved on the windows side which seems to be your issue. [http://www.experts-exchange.com/Networking/Microsoft_Network/Q_20965078.html]("http://www.experts-exchange.com/Networking/Microsoft_Network/Q_20965078.html") [/quote] ummm...it says to view the solution you have to be a member and pay $$$?
are you a member or something?
[quote=catlett] Wish I could be of more help. I keep seeing you bump and wish I had an answer for you. Good luck. When you graduate you're  going to make a great administrator.:-D[/quote]  Thanks! but i don't know if im ever going to graduate! :D (it...takes....sooo.....long.....:))

---

### Post by user1397 on 2006-05-22
[quote=dmizer]yes, this is a windows issue, i don't think your router is causing it.  especially since your windows box can see your linux box.  it really has to be something on the windows machine blocking your ubuntu.

do you have norton security center, or just norton antivirus?  and again, is it up to date and current?

also, in network connections, local area connection/properties, what's listed and checked under "this connection uses the following items:"?

also check under advanced > firewall > windows firewall settings > advanced tab ...
this will list all of your adapters/modems installed in windows, and allow you to select each one individually for firewall protection.  see, in windows if you have a dial up modem and a network adapter installed, but the firewall is turned on for the network adapter but not for the dial up modem, windows reports that the firewall is off for everything, so always check the advanced tab to make sure that the firewall is completley off.

if you're worried about security, simply disconnect the wan side from your router.  your local network will still be in place and you can still troubleshoot it.

but i'm going with a windows issue at this point.[/quote]
i'll try your various methods, dmizer :D

---

### Post by catlett on 2006-05-22
> ummm...it says to view the solution you have to be a meber and pay $$$?
are you a member or something?
Scroll past that stuff and there are replies. The guy got an answer that worked but I don't know if it relates. The title just struck me as similar to yours.

---

### Post by user1397 on 2006-05-22
[quote=dmizer]do you have norton security center, or just norton antivirus?  and again, is it up to date and current?[/quote]
i have norton av 2006, just updated it with liveupdate, and i don't have security center (though in the system tray there is an icon called "Norton Protection Center"
[quote=dmizer] also, in network connections, local area connection/properties, what's listed and checked under "this connection uses the following items:"?[/quote] ummm...client for microsoft networks, file and printer sharing for microsoft networks, QoS packet scheduler, network monitor driver, internet protocol (TCP/IP). i don't know why you want this info tho, cause this pc is connected wirelessly, so shouldn't i be listing the wireless connection properties?

[quote=dmizer] if you're worried about security, simply disconnect the wan side from your router.  your local network will still be in place and you can still troubleshoot it.[/quote]i dont know what this means

[quote=dmizer] but i'm going with a windows issue at this point.[/quote]me too

---

### Post by dmizer on 2006-05-22
[QUOTE=erik1397]i don't know why you want this info tho, cause this pc is connected wirelessly, so shouldn't i be listing the wireless connection properties?
[/QUOTE]
quite ... #-o sorry, post the same about wireless networks please.  what items are listed and which have checks.

as for disconnecting the wan (stands for wide area network ... ie, the internet) for testing purposes, disconnect the cable between your router and your modem ... that way, no security issues. ;)

---

### Post by user1397 on 2006-05-25
WOW..........YOU WON'T BELIEVE HOW EASY THIS ACTUALLY WAS.........
I had my firestarter outbound as "deny service: samba"
so..........that's the only reason i couldn't see my windows PC's on ubuntu......
i feel sooooooooooooooo STUPID!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :)
I didn't have to do that whole mount thing or anything, now i can just go to places->network servers->windows network!!!!!!!!!!

BTW, how can i improve my samba security? (do i need to add something like "psswrd" in  /etc/samba/smb.conf?

---

### Post by DSn0wMan on 2006-05-26
[QUOTE=erik1397]WOW..........YOU WON'T BELIEVE HOW EASY THIS ACTUALLY WAS.........
I had my firestarter outbound as "deny service: samba"
so..........that's the only reason i couldn't see my windows PC's on ubuntu......
i feel sooooooooooooooo STUPID!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :)
I didn't have to do that whole mount thing or anything, now i can just go to places->network servers->windows network!!!!!!!!!!

BTW, how can i improve my samba security? (do i need to add something like "psswrd" in  /etc/samba/smb.conf?[/QUOTE]

Now I feel dumb too. It's pretty obvious now that you say it.

---

