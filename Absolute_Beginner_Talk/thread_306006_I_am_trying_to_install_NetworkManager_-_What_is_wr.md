---
title: "I am trying to install NetworkManager - What is wrong?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-11-24
Hello All!

I have installed the program/package "networkmanager", from Synaptic Package Manager.

I followed this article:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Unfortunately, there is NO program shortcut created on the Applications Menu.

I decided to create it by myself!

Steps:

1. I launched a Terminal window & typed "which networkmanager". No path was found & I had to quit the method of creating a "launcher" & adding it to the "Applications" Menu.

2. From the Menu, I selected "Applications\Add/Remove...".

a. Under "Internet", I selected the application "Network Manager" & clicked on the button named "ok" & the application was installed!

(...and I thought that the application was installed by Synaptic... Shouldn't this be already checked inside the "Applications\Add/Remove..."?
Cause it gave me the impression that it is installing the application twice!)

3. From the Terminal window, I decided to "restart" the networking application.

And got the following:

> root@dimitris-desktop:/# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
root@dimitris-desktop:/#

Can somebody explain what is going on?

Why do I get these:

1. > ...There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416

And

2. > SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416

And then the same for:

> 
eth2: ERROR ...
...Failed to bring up eth2.
...ath0: ERROR ...
Failed to bring up ath0.


I don't have a clue!

Thanks.

---

### Post by NiklasV on 2006-11-24
Make a backup of your /etc/network/interfaces
```
sudo mv /etc/network/interfaces /etc/network/interfaces.old
```
Create a new file
```
gksudo gedit /etc/network/interfaces
```
Paste this, and save
```
auto lo
iface lo inet loopback
```
This is assuming you want network managaer to control all your interfaces.
Now reboot.
Done.

If it doesn't work after this, restore your old /etc/network/interfaces
```
sudo cp /etc/network/interfaces.old /etc/network/interfaces
```

---

### Post by dvarsam on 2006-11-24
Dear "NiklasV",

Thanks for your reply!

I performed all you said & Rebooted my Ubuntu.

I launched a Terminal window & performed a "/etc/init.d/networking restart"

Everything restarted fine!

However, I don't know how can I run the Program NetworkManager!

In a Terminal window, I type "networkmanager" & get:

> root@dimitris-desktop:/# networkmanager
-bash: networkmanager: command not found

In the Menus there is NO shortcut of Network Manager either!

And, when in a Terminal window I type: "which networkmanager", I get:

> root@dimitris-desktop:/# which networkmanger
root@dimitris-desktop:/#

How do I run the program?

Sorry, but it seems that I am missing the "magic" command or "magic" word!

Thanks.

---

### Post by jleigh on 2006-11-24
It should show up automatically in the notification area after logging in.  If you don't see it, you may need to add the notification area to the panel.

---

### Post by dvarsam on 2006-11-24
Dear "jleigh",

thanks for your reply!

> **jleigh said:**
> It should show up automatically in the notification area after logging in.  If you don't see it, you may need to add the notification area to the panel.

After a couple of restarts, I noticed a "launcher" for it in the Top Panel.
And that launcher looks exactly like the "Network Monitor" icon.

It is very hard to distinguish... between those 2 icons!

At the same time, there is no "launcher" for "Network Monitor" in the Menus.

Also, the functionality of the program is strange!

> You are only provided with 2 options:

1. "Enable/Disable Networking"

AND

2. Show-up of "Connection Information"

Is that all?

And all the Ubuntu Programmers are going to embed, is _this_ in the coming Feisty Version?
(Oh my God: @#$!%#&*%*)

When I was thinking of Networking, I was thinking of the following:

From the Menu, I select "Places\Network Servers" & see 2 icons:

1. Windows Network (this exists!)

2. Ubuntu/Linux Network (does NOT exist!)

And what I NEED is the following:

Being able to double-click on the "Ubuntu/Linux Network" icon, to open its window & being able to _actually_ see one icon for each computer connected in my Ubuntu/Linux Network.

Example (contents of "Ubuntu/Linux Network" icon):

1. Icon for: Linux Networked user Dimitris

2. Icon for: Linux Networked user Maria

3. Icon for: Linux Networked user Mark

4. Icon for: Linux Networked user Tony

5. etc. etc.

I want to be able to have a quick picture of what my Network is comprised of...!

The User Rights for being able to access/enter a User's PC is a different issue!

It is something that you deal with, _after_ you get to know what your Network consists of...

And then, you can "issue" a rule saying:

Attention to all Networked PCs, this Networked PC (e.g. above user "Mark") is going to be the Administrative Computer!

And this Networked PC (e.g. "Mark") is going to administer who has access to whose computers & what Networked Folders are to be shared across all the Network...

> But being able to have a quick representation of what your Network consists of, is the MOST IMPORTANT THING!!!
Its where all things start from...
AND we don't _even_ have this!!!

Thanks.

---

### Post by Papa-san on 2006-11-24
By the sounds of it, you have quite the list of needs! I guess you have your work cut out for you! Personally I wouldn't want to be the one writing all that code.  This is Open Source, so knock yerself out!
Oh BTW... when you put in the code for your "which networkmanager" You actually had "networkmanger" which was prolly what made the difference.

You should be able to get the starting point of your list from your router, or whatever network hub you use. If you access it, most of them have a pretty informative and complete interface that contains the 'data' you need (IP's, computer names, network names, permissions, etc... That is just a start, though, Good luck. I know you aren't the only one looking for something like this!

---

### Post by dvarsam on 2006-11-24
Dear "Papa-san",

thanks for your reply!

Long time to hear from you!

> **Papa-san said:**
> By the sounds of it, you have quite the list of needs! I guess you have your work cut out for you! Personally I wouldn't want to be the one writing all that code.  This is Open Source, so knock yerself out!

Users have needs!
You can't tell them to NOT expect to ever see this being implemented...!
What you can say to them is:

Hopefully in the next Coming Versions we might get there...

That is better!

> Oh BTW... when you put in the code for your "which networkmanager" You actually had "networkmanger" which was prolly what made the difference.

You should be able to get the starting point of your list from your router, or whatever network hub you use. If you access it, most of them have a pretty informative and complete interface that contains the 'data' you need (IP's, computer names, network names, permissions, etc... That is just a start, though, Good luck. I know you aren't the only one looking for something like this!

If Somebody could get all that info from the Router, then why can't Ubuntu programmers write a simple program that grabs all info from the Router & represents info for each user into the "Places\Network Servers", with a separate icon for each user identified from the Router?

BUT AGAIN:

You can't ask/enforce all Ubuntu users to go & buy a Router, can you?

I think that I am not asking for too much...

I bet that there are other who would like to see this implemented!

Besides, it is ridiculous to open, from the Menu, "Places\Network Servers" & all to _actually_ find is an icon with name "Windows Network"...!!!

**HELLO, IS ANYBODY THERE???**!!!

> What happened to the "Ubuntu Network" icon?

I thought we were oriented towards Linux, NOT Windows...???

Thanks.

---

### Post by Papa-san on 2006-11-24
You can catch more flies with honey than you can with vinegar...

;)

---

### Post by junglepeanut on 2006-11-24
If I recall correctly networkmanager is a daemon not an application, so you should try calling its gui application network-admin.

Does this help?

I often use the command line. If you are using edgy I had an issue with the my internet service at certain locations creating the symptoms you descibe with pid already existing, if you delete the file, next time it is run you wont get the error but probably will the time after that. I actually think it has to do with the provider as I only experience this issue at one location. It did not really cause any real issue for me, other than the complaint.

---

### Post by dvarsam on 2006-11-25
Dear "junglepeanut",

Thanks for your reply!

> **junglepeanut said:**
> If I recall correctly networkmanager is a daemon not an application, so you should try calling its gui application network-admin.

Does this help?

I pressed Alt+F2 on the keyboard & typed "network-admin", as you suggested.

This is NOT what I am looking for!

> I often use the command line. If you are using edgy I had an issue with the my internet service at certain locations creating the symptoms you descibe with pid already existing, if you delete the file, next time it is run you wont get the error but probably will the time after that. I actually think it has to do with the provider as I only experience this issue at one location. It did not really cause any real issue for me, other than the complaint.

I do not understand what you are talking about...

Can you please explain...?

What I want to really see in Ubuntu Networking, is the following:

From the Menu, select "Places\Network Servers" & see this:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/3-1.png[/IMG]

I then want to be able to double-click on the icon named "Linux Network" & see this:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/5-1.png[/IMG]

Now, as I said before, the Next step is to be able to SET UP access rights in the "Linux" Network"!

In the picture above, lets assume that _my computer_ is represented by the icon named "Linux Networked User - Dimitris" & all the other icons are representing other users connected to the Linux Network.

To be able to double-click to the icon named "Linux Networked User - Tony", means I am entering into user "Tony's" computer in the Network!

IF I perform a double-click, to be able to see user "Tony's" Desktop, I must have the appropriate **USER RIGHTS** to do so!!!

So, a Window could come up saying that I do NOT have priviledges to access user "Tony's Desktop!

A Window, like this:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/11.png[/IMG]

And IF all priviledges are setup OK (e.g. read/write/execute), and User "Dimitris" is allowed to access the Computer of user "Tony", he will be able to see what the User "Tony's" Desktop looks like!

Am I asking too much?

Is something like this, coming up in the Ubuntu Feisty Fawn?

Thanks.

P.S.> Currently, the Menu "Places\Network Servers" looks _too_ PRIMITIVE!!!

Is this considered a logical "Places\Network Servers" window?

This:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/1-1.png[/IMG]


And even worse, after I managed to install the program/package "Network Manager"...

I realized that _all_ the program was about/provided was this:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/2.png[/IMG]

Is this what a "Network Manager" is supposed to do?

This is ridiculous!!!

And somebody decides to "**Share a Folder**"r across the Network, that "Shared" Folder's icon should be shown inside the "Places\Network Servers" window!
_ALL_ "Shared Folders" should be listed in there!!!

---

### Post by junglepeanut on 2006-11-25
Quote:
I often use the command line. If you are using edgy I had an issue with the my Internet service at certain locations creating the symptoms you describe with pid already existing, if you delete the file, next time it is run you wont get the error but probably will the time after that. I actually think it has to do with the provider as I only experience this issue at one location. It did not really cause any real issue for me, other than the complaint.
I do not understand what you are talking about...

What I mean is when I use the Internet provider at my university I get this complaint, a lot. When I am at home, or at my friends, the same things does not occur. Also it does not occur for me ever when I am connected via wireless, no matter where I am, but I think that is because the router I use at school probably gets that complaint and just works around it or ignores it like I do. 

Sorry I did not get what you were asking. I can see now that network-admin is not what you are looking for. I do have to say though even when I had dapper I had what your picture looks like in Nautilus for connecting to servers.

How are you connecting to your servers? I used ssh, and thus I had a link I could click on (similar to your picture) and then I would just be on those computers (if you have nautilus store your password) otherwise you need to type in a password everytime. Give me a bit, I will log out of IceWm and and log into gnome and take a pic,...if nautilus is working, its been a little buggy for me with the feisty upgrades.

---

### Post by junglepeanut on 2006-11-25
OK so I am going to try putting a pic in the forums never done it before but here goes, I think this is what you are saying where if you go into Network from the top it should take you to a folder with windows and linux guys, then go inside those and it shows individuals. I am pretty sure you could create it as you are asking as this shows my school server here with my user name, then just throw it inside one of the things you want like windows network or linux network.


Sorry if you don't like the blue but Feisty is blue right now for some reason.

Also maybe you are trying to do something more like Samba? 
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

---

### Post by dvarsam on 2006-11-25
Dear "junglepeanut",

thanks for your reply!

> **junglepeanut said:**
> Quote:
I often use the command line. If you are using edgy I had an issue with the my Internet service at certain locations creating the symptoms you describe with pid already existing, if you delete the file, next time it is run you wont get the error but probably will the time after that. I actually think it has to do with the provider as I only experience this issue at one location. It did not really cause any real issue for me, other than the complaint.
I do not understand what you are talking about...

I am talking about a LAN - a local Network with NO Servers involved!

Just 4-5 Ubuntu Desktop PCs.

I have added many pictures in my previous post, with what I want, can you please go back & see the post again (I finally finished editing it)?


> What I mean is when I use the Internet provider at my university I get this complaint, a lot. When I am at home, or at my friends, the same things does not occur. Also it does not occur for me ever when I am connected via wireless, no matter where I am, but I think that is because the router I use at school probably gets that complaint and just works around it or ignores it like I do.

> Sorry I did not get what you were asking. I can see now that network-admin is not what you are looking for.

Is there some package/program that can show My Ubuntu Network the way I would like it?

> I do have to say though even when I had dapper I had what your picture looks like in Nautilus for connecting to servers.

How are you connecting to your servers? I used ssh, and thus I had a link I could click on (similar to your picture) and then I would just be on those computers (if you have nautilus store your password) otherwise you need to type in a password everytime. Give me a bit, I will log out of IceWm and and log into gnome and take a pic,...if nautilus is working, its been a little buggy for me with the feisty upgrades.

I am NOT connecting to any Servers!
I want to connect from an Ubuntu Desktop to another Ubuntu Desktop on a Local LAN!
And, YES, I have used SSH, but I don't like it as much...

Looks very primitive!

Even though SSH could be implemented for connecting on the Local LAN, there is NO representation of what my LAN is comprised of...

And it would be nice if there was such a representation - like the pictures I provided!

Thanks.

---

### Post by dvarsam on 2006-11-25
Dear "junglepeanut",

Thanks for your reply!

> **junglepeanut said:**
> OK so I am going to try putting a pic in the forums never done it before but here goes, I think this is what you are saying where if you go into Network from the top it should take you to a folder with windows and linux guys, then go inside those and it shows individuals. I am pretty sure you could create it as you are asking as this shows my school server here with my user name, then just throw it inside one of the things you want like windows network or linux network.

What you are showing me is the "Places\Network Servers", after you have created an SSH connection!

What I really would like to _see_ is what my Linux Network is comprised of, from **before** I start up creating the SSH connections!

There is NO representation of that, is there?

Example:

Lets suppose that YOUR Network is consisted of:

1. Your Computer
2. User "ahyder" (as depicted in the SSH connection in your provided picture)
3. User "Maria"

> **Before** you even have created _ANY_ SSH connections, shouldn't your "Places\Network Servers" show what Your Network is comprised of?

This is what I am talking about!!!

SUPPOSE that your job is an IT Network Administrator Support Freelancer & a company with 50 employees invites you to help them with their Network Problems...

You visit the company & you know Nothing about what their Network is comprised of...

IF you had launched "Places\Network Servers" & you found NO SSH connections, how could you tell how many computers was their Network comprised of?

You would be "pulling your hairs" out, wouldn't you?

Am I asking too much?

This is what I would like to see in the coming Ubuntu "Feisty Fawn"!

> Sorry if you don't like the blue but Feisty is blue right now for some reason.

Also maybe you are trying to do something more like Samba? 
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

No problem with the blue background, don't worry!

I don't care about Samba, I am talking about an **Ubuntu 100% pure Network**!

Forget about Windows...

Windows suck!

(But, unfortunately their Networking is better....@#$%#$&#@)

Thanks.

---

### Post by junglepeanut on 2006-11-25
OK, I guess I will have to give up, ssh does everything for me that you are doing. i.e. I use ssh even for computers all connected via an ethernet cord and a router, and can just log in to them via nautilus, or safari etc. of course I know the names so I just set them up then they are all connected. 

If nobody solves your problem, give me a day to research it, I know it is not hard to configure what you want, and I am sure it must be out there, shoot it must be simple.

---

### Post by junglepeanut on 2006-11-25
> I don't care about Samba, I am talking about an Ubuntu 100% pure Network!
I dont understand just because you install gedit does not mean it is not ubuntu. Ubuntu is a distribution, samba is a program that runs on the distribution. And there is a ubuntu wrapper for it so you dont need to use the source, just install it. So I think you have a serious flaw in your argument. (or you have changed requirement from seeing windows and linux computers) winbnd is used I think to add windows compatibilty to samba.

The linux philosophy is create one program to do a job well, then if more features are needed merge the applications that do something well.

---

### Post by dvarsam on 2006-11-25
> **junglepeanut said:**
> OK, I guess I will have to give up, ssh does everything for me that you are doing. i.e. I use ssh even for computers all connected via an ethernet cord and a router, and can just log in to them via nautilus, or safari etc.

I know!

SSH can create a connection & I know how to do it...

I have created SSH connections in my Local LAN, in the past!

[quote=junglepeanut]... Of course I know the names so I just set them up then they are all connected.[/quote]

That is what I talking about!!!

**You _know_ everything about your LAN, because _you_ have created it by yourself!!!**

You _know_ what your LAN is comprised of, because you have _personally_ connected all computers in your LAN!

But if you go & visit a company & try out to help them with their LAN & you want to see what their LAN is comprised off, IF you open "Places\Network Servers" & see NO SSH connections,...

**How do you know how many computers are connected to the LAN?**

There is NO representation of the Local Linux LAN provided by "Places\Network Servers", even though _all_ the PCs are TRULY connected to a Hub or Router!!!

That is why, in my opinion, the "Places\Network Servers" **must** improve!!!

> If nobody solves your problem, give me a day to research it, I know it is not hard to configure what you want, and I am sure it must be out there, shoot it must be simple.

Can you understand now what I am talking about?

Thanks.

---

### Post by junglepeanut on 2006-11-25
I think I understand it... The issue is just figuring out who is connected, then it should allow you to set-up. The main reason this may not work so well is we may need to let each computer be seen. I have to do a lot of reading.

Right now I am reading this to see if it will help.

[http://www-128.ibm.com/developerworks/linux/library/l-lan.html](http://www-128.ibm.com/developerworks/linux/library/l-lan.html)

---

### Post by junglepeanut on 2006-11-25
Now this

[http://www.debuntu.org/2006/08/05/85-how-to-setting-up-a-dns-zone-with-bind9](http://www.debuntu.org/2006/08/05/85-how-to-setting-up-a-dns-zone-with-bind9)

---

### Post by junglepeanut on 2006-11-25
Maybe these help?
[https://wiki.ubuntu.com/FeistyNetworkAuthentication?highlight=%28network%29](https://wiki.ubuntu.com/FeistyNetworkAuthentication?highlight=%28network%29)

[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#WHAT](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#WHAT)


I am looking, but I have to say even when I used windows if all the boxes are not saying connect me, then I did not see them. i.e. Windows lan was not easy, you probably have just done enough times that it is easy now, I found linux connecting to be simple, but then I have never tried to discover computers that may not want to be discovered. 

I think the bind9 post seems like it might work, but I think I will need more than a day. I will discuss this with our I.T. guy.

Hope you can resolve your issue.

---

### Post by junglepeanut on 2006-11-25
I will still talk with the I.T. guy but from reading it seems to me that NFS is the way to go if you don't want Samba. (it even says you can use both as they are very alike but NFS does not support windows.)

Still though you need to set up each computer to look in the right place. Which makes sense as normally you want to hide, and this will let the main computer no where to look.

---

### Post by junglepeanut on 2006-11-25
[https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28network%29%7C%28company%29](https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28network%29%7C%28company%29)

---

### Post by dvarsam on 2006-11-26
Dear "junglepeanut",

thanks for your reply!

Also, thanks for supplying all those links!

So, it seems to me that, for someone to see what his network is comprised of in a GUI environment (i.e. a window with icons of what is auto-detected after a boot), it is impossible!

Everything you have suggested, is requiring that a user messes with network config files & setting them up from the Terminal!

Nothing done in a GUI like environment...

OR

...a "Wizard" (like in Windows), that helps you setup your Network in a step-by-step process...

I think that I have read, in the past, something that looks/sounds like what I am looking for:

> 
Ubuntu Feature Specification: Sharing Information over a Network

Users want to be able to share information and hardware between each other over a network as easily as possible; this **requires network discovery of what is available.**

This spec should outline how to take advantage of the new default-network-services policy to enable information to be shared over a computer network.

Such information should include directories, rhythmbox library, presence, etc.

[https://blueprints.launchpad.net/distros/ubuntu/+spec/network-information](https://blueprints.launchpad.net/distros/ubuntu/+spec/network-information)

I am also not sure whether this is also what I am looking for:

Ubuntu Feature Specification: Zero-configuration networking

[https://blueprints.launchpad.net/distros/ubuntu/+spec/zero-configuration-networking](https://blueprints.launchpad.net/distros/ubuntu/+spec/zero-configuration-networking)



I think that when somebody makes a fresh install of a Desktop version of Ubuntu in 2-3 PCs, when he selects from the Menu "Places\Network Servers", he needs to see:

> Icons that represent the output of: **An auto-network discovery of what is available.**

Then, when you double-click those icons to open them, the "Connect to a Remote Server" could launch! 

But the connected PCs in the network must be auto-discovered at every boot/refresh & each machine identified connected to the network, being represented by an icon as I have shown in my pictures!

And when I double-click on a icon, a window should be launched with contents what I have entered in the "Connect to a Remote Server's" "Folder:" inputbox. 

Thanks.

P.S.> I hope you understand now of what I talking about...
From what you have suggested, something like this seems NOT to exist.

---

### Post by junglepeanut on 2006-11-26
Please keep in mind with everything I say, I am new to Linux, very new, I just saw that not much was going on in this thread and decided to try my best to learn something.

I think I understand and I think it is that most of ubuntu does not announce itself to the world, I think that is why you have to use a config file to tell each one to say hey I am here, you can call me at this number. Writing a gui for editing the config files should not be to hard, I suspect if it has not been done yet it is because the majority of users who do this are system admins and they are more comfortable with files than the gui. I am not a system admin and I quite often prefer editing a file to the correct variables. 

So yes it is possible and it appears nobody has written a gui yet (but there may be one out there we just didn't look hard enough). 

I think it sounds like you have lots of skills, if it turns out after I talk with my I.T. guy that the only ways is config files, then maybe after you get it worked out, you could write a gui? I might be able to write one after I finish my thesis, so completion would not be quick.

---

### Post by junglepeanut on 2006-11-29
He is going to make a list of programs for you, he says they are all simple, although he says he normally does it just by editing files. (He runs rpm based and deb based similar to many individuals so you might have to alien some of them.)

---

### Post by dvarsam on 2006-11-29
I have created a Visual Representation.

Please go ahead & visit the following thread:

[http://ubuntuforums.org/showthread.php?t=309226](http://ubuntuforums.org/showthread.php?t=309226)

Thanks.

---

### Post by junglepeanut on 2006-12-01
I know this isnt what you wanted, but I plugged in my computer to a network I had never visited before and this is what I got. The reason this works is these computers are on a network and they all say hey look at me. None of these computers were able to see me as I have not edited my files to say look at me. I could see computers, ftp servers, ssh servers, etc etc.

In fact I later walked outside to connect wireless and just wanted to see what happened...again I was connected to many many many more networks than I realized.

Here are some pics I took later. I did not know any of these computers names before hand, they were just recognized because they said I am here. Although this does not show many linux computers, I can say when I was plugged in with the linux boxes on the network all of them were visible to me, again I was not visible to them though. 

I did not have to install NFS or Samba to see these computers either. First shows the windows network with some other junk as usual, the next has me clicked on the windows network and shows what is in there. You can continue inside those as well. Just as in the other networks I went into with linux boxes.

---

### Post by dvarsam on 2006-12-01
> **junglepeanut said:**
> I know this isnt what you wanted...

On the contrary, THIS IS WHAT I WANT!!!

OR:

THIS IS THE FIRST STEP OF WHAT I WANT!!!

Well, I have a Network of 2 Ubuntu Desktop PC's connected, but they don't see each other...

No icon representations on the "Places\Network Servers", like the pictures you provided...

How is it possible that it works for you, but NOT for me?

I don't get it!!!

Is this some kind of Picture Editing (like I did), or is this plain reality, you are talking about?


> but I plugged in my computer to a network I had never visited before and this is what I got. The reason this works is these computers are on a network and they all say hey look at me. None of these computers were able to see me as I have not edited my files to say look at me. I could see computers, ftp servers, ssh servers, etc etc.

What do I have to edit in my PC's (or what settings do I change), to send the same signal to the whole Network?

I want _all_ my Ubuntu PCs to say too:

[quote=dvarsam]**Hey look at me!!!**[/quote]

How do I do this?

What packages do I have to install?

OR:

What Network Settings do I have to change?

> In fact I later walked outside to connect wireless and just wanted to see what happened...again I was connected to many many many more networks than I realized.

Here are some pics I took later. I did not know any of these computers names before hand, they were just recognized because they said I am here. Although this does not show many linux computers, I can say when I was plugged in with the linux boxes on the network all of them were visible to me, again I was not visible to them though. 

I did not have to install NFS or Samba to see these computers either. First shows the windows network with some other junk as usual, the next has me clicked on the windows network and shows what is in there. You can continue inside those as well. Just as in the other networks I went into with linux boxes.

I WANT TO SAY:

> I AM HERE TOO!!!

How do I do it?

Thanks.

---

