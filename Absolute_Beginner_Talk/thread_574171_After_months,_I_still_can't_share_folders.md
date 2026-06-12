---
title: "After months, I still can't share folders"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-10-12
Hi all,

Now, after a long time of this, I have been trying to share one little folder between my son's pc and mine, both running Ubuntu Fiesty. 

I have tried basic sharing and have samba and nfs installed, have tried sharing using both smb and nfs. No love. I have been through the forum from one end to the other, nothing has worked. 

I have tried that supposed easy share network manager and got nowhere. Upon finishing even in root, for the etc/samba/smb.conf  <permission denied. Even modified it directly and got nowhere. Someone stated what a wonderful easy tool yet it takes you in more circles just trying to find out how to install the package. Bah humbug. 

If my son boots into Windows, BAM , instant sharing, Fedora, instant sharing, Ubuntu to Ubuntu, nothing. I have been with Ubuntu for some time now but I need to share files and folders across my network and honestly, I hate this to be the downfall of using Ubuntu for me. I have since learned how to do everything else and personalize my Ubuntu over the months but this is one problem that I can't conquer. 

It shared last month for a day and then my son reinstalled Ubuntu and we haven't gotten it to work since. I made sure he has everything installed properly. Also, there is no share icon on the folder and I can keep setting it to share, seems settings may not stick. 

So, is there anyone that thinks they can get two Ubuntu computers to share? I would be very grateful. I run through Linksys wired 4 port router but as stated, every other combo of OS I've had works great, just not Ub to Ub. 

Thanks,

Paul

---

### Post by Old *ix Geek on 2007-10-12
I know it's frustrating when something, especially something important, fails to work.  But rest assured it definitely *IS* possible to share folders in a Ubuntu-to-Ubuntu scenario--that's how my entire home network is set up. You're probably just missing a step--which I've done many times!--but once you figure out what step that is, and fix it, you'll be fine.

If possible, please post a summary of what you've done.  That way someone will probably spot what you HAVEN'T done, and then you'll be on your way. :)

---

### Post by samb0057 on 2007-10-12
> **gimpguy2000 said:**
> Hi all,

Now, after a long time of this, I have been trying to share one little folder between my son's pc and mine, both running Ubuntu Fiesty. 

I have tried basic sharing and have samba and nfs installed, have tried sharing using both smb and nfs. No love. I have been through the forum from one end to the other, nothing has worked. 

I have tried that supposed easy share network manager and got nowhere. Upon finishing even in root, for the etc/samba/smb.conf  <permission denied. Even modified it directly and got nowhere. Someone stated what a wonderful easy tool yet it takes you in more circles just trying to find out how to install the package. Bah humbug. 

If my son boots into Windows, BAM , instant sharing, Fedora, instant sharing, Ubuntu to Ubuntu, nothing. I have been with Ubuntu for some time now but I need to share files and folders across my network and honestly, I hate this to be the downfall of using Ubuntu for me. I have since learned how to do everything else and personalize my Ubuntu over the months but this is one problem that I can't conquer. 

It shared last month for a day and then my son reinstalled Ubuntu and we haven't gotten it to work since. I made sure he has everything installed properly. Also, there is no share icon on the folder and I can keep setting it to share, seems settings may not stick. 

So, is there anyone that thinks they can get two Ubuntu computers to share? I would be very grateful. I run through Linksys wired 4 port router but as stated, every other combo of OS I've had works great, just not Ub to Ub. 

Thanks,

Paul

Are you running a firewall? Try turning it off on both machines if you are.

---

### Post by gimpguy2000 on 2007-10-12
Thanks for the replies. 

I will try to do the best I can at explaining. 

I have a home network, two computers, Athlon and HP. I have them wired through Linksys 4 port wired router. Both run Ubuntu Feisty. 

Now, the two computers can recognize each other with Windows network easily, even Fedora running, I can recognize the Athlon Ubuntu , Athlon Windows and vice versa with HP. I can't share if both using Ubuntu at the same time. 

I have since did away with Fedora and only have Ubuntu and XP pro, so does the Athlon <my son's computer> HP is mine. 

So what I first did was went to **System\Administration\Shared folders ** which of course needs Samba or NFS so I did install both, and then added a folder I created as a share, chose properties, first choosing smb. I also allowed 192.168.XXX my son's ip. I changed permissions of the folder so there was access without restriction. I am the owner with all permission, group all permission and other all permission. I mainly did this so I could tell if it would work or not. 
I also tried to right click the folder and set sharing that way which of course was already set. I tried the same with NFS which yielded little results, well, none actually. 

So, I tried setting up a share file on my son's pc , same thing, I can't see or access it. The only network on my pc is Windows under ///smb  which doesn't show any shared folders on either machine. 

I can't create a folder under the network either, says operation not permitted. Even in root.  Maybe that's normal, I don't know. 

So I tried that network manager and couldn't even set that up and won't go there again. I downloaded the tar file yet couldn't find on thing on installation. Either way, as stated, I don't want to go there again. 

I do not have a firewall running. 

So that's where I stand currently. 

Thanks,

Paul

---

### Post by thelegionnaire on 2007-10-12
maybe [http://who.hasfiles.com/](http://who.hasfiles.com/) would help? just a quick suggestion.

---

### Post by gimpguy2000 on 2007-10-12
> **thelegionnaire said:**
> maybe [http://who.hasfiles.com/](http://who.hasfiles.com/) would help? just a quick suggestion.

Thanks for the suggestion but I have plenty of storage locally, I do a lot of graphics work and other as well does my son and sharing across the network would just be much easier. 

 That is a pretty good idea though for other backups in case of failure so I may still use it. :) Unfortunately I still would like to share on my network. 

Thanks for the info. 

Paul

---

### Post by gimpguy2000 on 2007-10-12
UPDATE:

I just tried setting the samba user password but it changed nothing. I have been browsing and trying other things but so far nothing has worked. I can't see his pc and he can't see mine it seems. 

Thanks,

Paul

---

### Post by gimpguy2000 on 2007-10-12
Anyone have any ideas? :(

TX

Paul

---

### Post by shaft350x on 2007-10-13
Are they setup on the same "workgroup" (or equivalent)???  I had some similar issues when trying to share a printer, which I've got working now no matter what OS either any systems are running.

I had some problems with sharing before, and basically I just gave up on it.  With Gutsy I'll probably try to give it another go, so I'll be interested to see how you get yours working.

---

### Post by dmizer on 2007-10-13
you will have to set up both ubuntu boxes as both a server and a client.

nfs will give you your best option for sharing files between two linux boxes.  follow the last link in my sig to configure nfs.  configure both computers both a server and a client.

---

### Post by gimpguy2000 on 2007-10-13
> **shaft350x said:**
> Are they setup on the same "workgroup" (or equivalent)???  I had some similar issues when trying to share a printer, which I've got working now no matter what OS either any systems are running.

I had some problems with sharing before, and basically I just gave up on it.  With Gutsy I'll probably try to give it another go, so I'll be interested to see how you get yours working.

Thanks. I can't seem to get a specific work group setup. I just named it my login name and my son's as my login name. There is no work group per se. This is where I'm confused as well, I can't find anywhere to set up a work group.

Thanks,

Paul

---

### Post by gimpguy2000 on 2007-10-13
> **dmizer said:**
> you will have to set up both ubuntu boxes as both a server and a client.

nfs will give you your best option for sharing files between two linux boxes.  follow the last link in my sig to configure nfs.  configure both computers both a server and a client.

Thanks I am giving this a go right now. 

Paul

---

### Post by dmizer on 2007-10-13
good.  i'm running to the computer store :-D but i'll check back in a couple hours when i get home.  i want to make sure things are working for you.

---

### Post by la3875 on 2007-10-13
Have you entered a workgroup name in the shared folder menu in Administration? And if you have, like Windows are they identical? I have been successfully sharing with both Ubuntu and Windows over my home network as a trial to building a network storage box for photos and music for all to share. I think you are close. Hang in there...

---

### Post by gimpguy2000 on 2007-10-13
> **la3875 said:**
> Have you entered a workgroup name in the shared folder menu in Administration? And if you have, like Windows are they identical? I have been successfully sharing with both Ubuntu and Windows over my home network as a trial to building a network storage box for photos and music for all to share. I think you are close. Hang in there...


@dmizer:Thanks again, but no go on my part :( didn't change a thing but i'm not giving up yet. 


@la3875: Yep, I did that just a few minutes ago, even restarted the computers, no go. It's as if I have no network at all. If I boot to Windows or my son does, instant sharing between Windows boxes or Ubuntu and Windows but no Ub v.s Ub. :confused: 

What concerns me as well, all these tries can't be good for my configuration, if not a problem, great , but I keep thinking that i'm digging  a hole like last time and sinking. I keep hearing how easy it is so not sure what's going on. Every other network configuration i've tried, worked, just not Ub to Ub. :confused:

Thanks,

Paul

---

### Post by la3875 on 2007-10-13
I feel your frustration...

It might be time to try to deconstruct a few things. If you have both samba and NFS running there may be a conflict with both trying to access the same resources. I had to edit the samba conf file to get my shares seen by the windows machine which it seems you must have done too?

I'd be inclined to uninstall samba or stop it on both machines for a moment and try to isolate sharing via NFS.

---

### Post by kvonb on 2007-10-13
I don't understand why you would be having problems, but I'll try to go through it with you:

1. Run synaptic from the main menu->system->admin->synaptic package manager

2. Change the search box to "Name" and search for **samba**

3. Click on the box next to **Samba** and **Samba common** and select **Mark for Complete Removal**, this will delete the messed up config files.  Click on **Apply**.

4. Do the same for **nfs** (nfs-common I believe), remove it, it's rubbish (from a normal desktop user's pov).

5. OK, re-install samba through synaptic, just search for samba again and select (mark for installation) **samba** and **samba-common**, apply, and close synaptic once it has finished.

6. Now on your main menu, goto **places->home folder** and right click on the folder you want to share (or create one for this purpose).  Select share folder then in the box that pops up select **Share through-> Windows Network (SMB)**.  Deselect **read-only** then click on OK.

7. On the main menu, goto **system->administration->shared folders**.  You should see the folder you just shared in there, now click on the **general properties** tab along the top and put in a workgroup name, as you can see from the included screenshot, mine is called **WAMRFIXIT**.  Do not select **this computer is a WINS server**.

8. Reboot, and do the exact same thing on the other computer.

9. All should be rosy in fileshareland!

Oh, you might want to give the folder you shared the 777 treatment, right click on it and select **properties**.  Now select the **permissions** tab from along the top there and change all the folder accesses to **create and delete**, and all the file accesses to **read and write**.  Chang all three categories: Owner/Group/Others.

Also maybe select **execute** as well for good measure :).

PS.  Oh and to access the other computer, simply run Nautilus (the file manager), and in the address box at the top left (click on the little notepad and pencil icon if you are in icon mode), and type in: smb://other.computers.ip.address and it should appear as if by magic ;)

---

### Post by gimpguy2000 on 2007-10-13
Hi all, 

Well it's a new day but nothing new with the sharing, I tried all the steps posted but unfortunately I knew it was for nothing as those are pretty much exactly what I did prior.  I just don't understand where it's going wrong, even if I type in the network address in net or smb network addy, nothing. It states it's not a folder. Now, I know there are folders since I made them. So basically I tried typing in the folder share name, the ip addy, the workgroup, nothing. I restart, still no sign of a shared folder. My network is empty. Now, I had my son boot to Windows for good measure and sure enough I had the network without a problem. 

 This is beginning to look like one of those never work situations but I will continue on until I figure where I'm going wrong. I tried to set up a share on my son's pc too and I still can't see a shared folder either way. 

Thanks,

Paul

---

### Post by la3875 on 2007-10-14
I'm thinking there's got to be some setting that's not playing well with your network router... :confused:

Hang in there! I think this OS is worth it.

---

### Post by gimpguy2000 on 2007-10-14
> **la3875 said:**
> I'm thinking there's got to be some setting that's not playing well with your network router... :confused:

Hang in there! I think this OS is worth it.

I am man, I am , lol. Just barely though. ;)

TX

Paul

---

### Post by kvonb on 2007-10-14
Can you ping each machine from the other?

Did you install a firewall on the Ubuntu computer? (Firestarter)

Try booting one comp with the liveCD, and try enabling sharing on that.

On each system, open a terminal from the applications->accessories menu and type:

```
ifconfig
```

Copy the output and paste here

also type:

```
route
sudo iptables -L
```

---

### Post by gimpguy2000 on 2007-10-14
Morning to those it's morning in, 

Well, dmizer has helped solve, rather, he solved my issue, and to my embarrassment, I had no idea that even when you stop firestarter from processes and stop it in any other way, it still likes to keep your ports closed. In other words, the only way to open up my sharing was to uninstall the bugger. Which I did. Now I can share just fine. :)  I thought it was a basic firewall, not being used to some Linux apps, and of course why should it block when shut off? Well it sure thinks it should. So anyway, that was my issue and I thank everyone who gave a hand. I am sort of laughing while kicking myself at the same time. But at least it's over, the nightmare is finally over. 

Cheers,

mr. embarrassed.

---

### Post by Soarer on 2007-10-14
Excellent news! Firestarter is often described as a firewall, but it isn't. It's a GUI for setting firewall configuration using IPtables.

As you now know. Networking can be a biatch, can't it. :)

---

### Post by gimpguy2000 on 2007-10-14
NOOOOOOOOO !

I did a restart and now have no network again! Why me??? It's all gone again and I know there is no firestarter.  This is a nightmare, that's it...I'll pinch myself....ouch! nope. :( 


Paul

---

### Post by gimpguy2000 on 2007-10-14
Ok, this is weird. I have to keep setting the folder to shared else after every restart, it's gone :confused:  Oy, any ideas? If so, I have to get to bed, i'll be back tomorrow, or later today I should say. Thanks in advance. 

Paul

---

### Post by gimpguy2000 on 2007-10-14
Ok , after a few restarts and setting it to share, it seems to be stable now. I have no idea what happened, lol, oh well, even in Linux it's only binary and things happen. So far, all is good. :)


Cheers!!

Paul

---

### Post by gimpguy2000 on 2007-10-14
> 

As you now know. Networking can be a biatch, can't it. :)


Boy do I ever! Well, I was used to Windows networking and knew how to set everything easily, but with a Linux OS, getting used to the workings is quite a "as you put"  a biatch. I had no idea firestarter did what it did. I am still confused on the firewall thing. I assume Linux\Ubuntu has some built in firewall\IP tables or is it simply a port controller? Which I would think since by default the ports are closed. I am probably wrong. 

Thanks again,

Paul

---

### Post by Soarer on 2007-10-14
IPTables is installed by default. All Firestarter does is give you a GUI to change the rules, as IPTables on it's own is not very friendly. 

I find ALL networking a biatch, Windows or Linux. Nature of the beast I guess.

---

### Post by la3875 on 2007-10-15
Congratulations! If its any consolation, your pain is the community's gain. I agree networking can be a biatch, even in windows. 

All the best.

---

### Post by jnorris235 on 2008-01-10
Kvonb is the man (or whatever).
For me it was down to the sharing.
I didn't see that anywhere (maybe I missed it). And I don't see why they got UNshared from before - but each new version of Ubuntu does seem to cause a few problems (which they shouldn't!!).

I don't care how wonderful Ubuntu is - if someone doesn't collect some of these answers/guides that dedicated helpers on this forum produce and add them to THE guide - what is the point in ever assuming the world and his wife will leave Windows?
I appreciate every set up is different but of all the problems I've had, and the many many hours wasted searching endless threads (and there are always dozens of long threads for each problem) the answer is always a straightforward one, or series of commands.
Cheers everyone.

Surely that is as important as inventing new versions of Ubuntu every six months?
Seal up the holes!!

PS I thought this would solve Apache suddenly not having permission to see the web folder, but no ...

---

