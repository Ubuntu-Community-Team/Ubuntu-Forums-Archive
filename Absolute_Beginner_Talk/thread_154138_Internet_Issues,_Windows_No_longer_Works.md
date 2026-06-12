---
title: "Internet Issues, Windows No longer Works"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by WSTGangsta on 2006-04-02
My first problem, is that Ubuntu cannot connect to the internet, at least not very easily, Im posting this using Firefox in ubuntu though, it can only connect to the various ubuntu websites! (IRC doesnt work either) But Synaptic Package Manager works fine! Help!
PS: My dads computer also says that another systems IP on the network is conflicting or something, (little help bubble)

Second ( more serious problem) 

My Windows installation no longer works properly, I installed Ubuntu with Grub, but when I try starting up windows, I get this blue error screen, that basically tells me nothing, just that my configurations is screwy, and to start in safe mode, then some tech info at the bottom that basically looks like (x75y175106) over and over. So that sucks.

Any help please! Normally I would just say, oh...well I guess Ill just use Ubuntu now but thats not easy without proper internet.

---

### Post by davidmoore83 on 2006-04-02
[QUOTE=WSTGangsta]My first problem, is that Ubuntu cannot connect to the internet, at least not very easily, Im posting this using Firefox in ubuntu though, it can only connect to the various ubuntu websites! (IRC doesnt work either) But Synaptic Package Manager works fine! Help!
PS: My dads computer also says that another systems IP on the network is conflicting or something, (little help bubble)

Second ( more serious problem) 

My Windows installation no longer works properly, I installed Ubuntu with Grub, but when I try starting up windows, I get this blue error screen, that basically tells me nothing, just that my configurations is fucked, and to start in safe mode, then some tech info at the bottom that basically looks like (x75y175106) over and over. So that sucks.

Any help please! Normally I would just say, oh...well I guess Ill just use Ubuntu now but thats not easy without proper internet.[/QUOTE]

Firstly, please refrain from bad language.

Now to your problem. Your internet connection appears fine given that you can use synaptic. I would assume from your network error the problem is one of the following:

1. Your network at home is set to assign I.Ps to the clients via DHCP and your linux install has one set manually.

2. Your home network has static I.Ps (192.168.0.xxx) and your Linux install is set to go by DHCP or has a static IP the same as another client. 

If you can tell me if your home network is static or dynamic then i can help you solve that issue.

As for your windows install no idea without more info of the error you get and the setup of your machine. ie partition setup etc.

Dave

---

### Post by WSTGangsta on 2006-04-02
What bad language?

And my internet is really screwy, and I hope to change it soon, I have Qwest DSL, my dad has like 2 routers connected to eachother (one linksys and an actiontec) 

As my partitioning, i used the ubuntu installers guided partitioning thing, with a 30 gb linux installation and another swap something. (sorry for the poor descriptions, Im new to linux) I will boot up windows and attempt to take a photo of the error screen.

---

### Post by WSTGangsta on 2006-04-02
Sorry for the double post, here is the error I get when trying to boot windows.

---

### Post by WSTGangsta on 2006-04-02
I assure you ive never triple posted before, but this is urgent, I need to make a birthday card, but I dont have access to photoshop, or the internet to get some good photos! And Dave, I use dynamic IP's, I think, would the ipconfig on another computer answer this?

---

### Post by davidmoore83 on 2006-04-02
[QUOTE=WSTGangsta]I assure you ive never triple posted before, but this is urgent, I need to make a birthday card, but I dont have access to photoshop, or the internet to get some good photos! And Dave, I use dynamic IP's, I think, would the ipconfig on another computer answer this?[/QUOTE]

Firstly your bad language can be seen in my quote of your first post - you have now edited it in the original thankyou.

I have seen that windows error before - you could try fixing the master boot record. Instructions here:

[http://www.tech-recipes.com/windows_installation_tips483.html](http://www.tech-recipes.com/windows_installation_tips483.html)

This will mean that you can't use the Ubuntu install without going back and reconfiging Grub but at the moment that would be wise given your situ.

Yes IP config on each of your home machines would identify if its dynamic or static. Post the IPs here and i will see if i can tell.

---

### Post by WSTGangsta on 2006-04-02
Thanks, yeah I edited it out, took me a while to even notice it, lol.

And Ill edit the rest of the IP's in here later.

Im using my dads computer right now, so heres his:
192.168.1.101
EDIT: Ok
Heres the other computer, my moms laptop.
192.168.0.2

---

### Post by davidmoore83 on 2006-04-02
[QUOTE=WSTGangsta]Thanks, yeah I edited it out, took me a while to even notice it, lol.

And Ill edit the rest of the IP's in here later.

Im using my dads computer right now, so heres his:
192.168.1.101
EDIT: Ok
Heres the other computer, my moms laptop.
192.168.0.2[/QUOTE]

Well this is confusing as you mums looks to be set static and your dads dynamic. Whichever is the pc with ubuntu just pick a random IP 192.168.0.xxx where you choose 'xxx'

See if that helps - any luck with fixing the master boot record?

---

### Post by WSTGangsta on 2006-04-02
The MBR did not work, so I wasted a long time finding the win XP disc! And now Ubuntu is gone, and my Computer is unusable! Gosh darnit! (I gotta watch my language ^_^)  So...I now have to reinstall windows or what? (Im still getting that error)

---

### Post by catlett on 2006-04-02
What is happening now? Can you log in anywhere? I assume you went into recovery and typed fixmbr. What happened the next time you started your computer? Do you have a Live CD you can boot into? How are you posting now? Do you have accrss to another computer that can download a Live CD of Ubuntu?

---

### Post by WSTGangsta on 2006-04-02
Right now I am posting with my pop's computer, and I have plenty of live CD's, I am currently re-installing windows, as that is the my only choice left.
I did the fixmbr and that error I posted earlier still showed up, so yeah. I wish internet worked on Ubuntu for me, its a great distro! Haha, I told my mom that Ill go to bed as soon as I format my hard disk, install 2 operating systems, she didnt think that was a good idea, but whatever. And I found this [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) so that I dont do anything stupid.
EDIT: What does the user title Spilled The Beans mean?
EDIT2: What the hell, my windows XP install disc does the install thing, says when you reboot the computer set up will continue, then tries starting the set up all over again, any help? I might end up having to use linux permanatley, I really dont want to do that, I mean Gimp does not even compare to photoshop, and I would have to leave Flash behind! Aghh! Why Do I use computers? ALl they do is piss me off!!!
EDIT3: Okay now my computer is saying that my partitions are invalid when I try to boot, so I am using Damn Small linux live CD, whats a good stable linux distro to install permanatley on this computer, because I may never use windows again, or how do I just totally wipe my computer clean and start from scratch?

---

### Post by catlett on 2006-04-02
If you have a live cd  try starting the program gparted or qtparted. I don't know about other distros but in Ubuntu it's gparted and in Kubuntu it's qtparted. These are programs that partition your hard drive. You can delete and reformat your hard drive from that program. 
But back to windows for one minute. Did you take the install disc out after the initial install. If you don't take the disc out after restarting it will boot to the install disk again.
Believe it or nor Ubuntu is very stable. I would get a good nights sleep and start tomorrow. Re-install your XP. Let windows reformat the hard drive and install. You should still have the partitions that Ubuntu created after XP is installed. 
Boot your Ubuntu disk and let the install run. The guide you have is very good. As long as both your CDs are made correctly, you shouldn't have any problems

Do you have the Ubuntu live cd? Use that to run gparted. Delete your partitions. Format your drive for Fat32. Then split your drive into 2 partitions. Boot windows and let it create C on the first half. Boot to the Ubuntu disk and let it install to the open half. Let it install Grub the boot loader to the first partition. Once that is done you should have XP and Ubuntu dual booting. Linux is tough until you get used to it. But once you get it there is alot you can do. You don't have to go all or nothing. Keep your choices open. If a program works good for you and it is windows based, boot to windows. If you find  one that runs on linux, boot to Ubuntu.
Linux expands your mind. Once you are dual booting you will have accomplished something. You worked your mind, problem solved and expanded your knowledge. What did your friends do today? Play Doom all day long? Keep pushing yourself and try new things. It might be frustrating at times but it is habits like those that get you ahead in life. People who quit or don't even try something new never get anywhere.

---

### Post by darkwarrior0404 on 2006-04-03
We had the same problem in a computer course on one of the Dell's in class, where it kept flashing the same blue screen, we eventually just troubleshooted it down to where all we could do was a reformat, tried repairing XP and didn't work, try repairing it (didnt read all the way through so I dont know if you tried it) but if you didnt, try that, and if it don't work, my second best guest is to if you don't have any files you need backed up, reformat..:-k

---

### Post by WSTGangsta on 2006-04-03
Thanks catlett! I cant post much Im on my PSP, I'll post an update tomorrow.

---

### Post by Jason_25 on 2006-04-03
Hey, it sounds like you may be having master boot record troubles.  I think windows might not be able to rewrite on to the master boot record for some reason.  To reinstall windows, you'll probably need to boot from the windows cd, then run the recovery console when prompted.  In the recovery console type 'map' , which will list your drives.  Then you need to do the fixmbr command on the drive you want to install windows to.  It will probably look something like this
'fixmbr \Device\HardDisk0'

After you reboot from the recovery console, you should be able to reinstall windows.       Make sure to leave some space for ubuntu!

---

### Post by davidmoore83 on 2006-04-03
[QUOTE=Jason_25]Hey, it sounds like you may be having master boot record troubles.  I think windows might not be able to rewrite on to the master boot record for some reason.  To reinstall windows, you'll probably need to boot from the windows cd, then run the recovery console when prompted.  In the recovery console type 'map' , which will list your drives.  Then you need to do the fixmbr command on the drive you want to install windows to.  It will probably look something like this
'fixmbr \Device\HardDisk0'

After you reboot from the recovery console, you should be able to reinstall windows.       Make sure to leave some space for ubuntu![/QUOTE]

I already told him to fix the MBR on page 1

---

### Post by Buffalo Soldier on 2006-04-03
I try not to link to any Microsoft/Windows site, but at this moment this is the best information that I can find.

[http://support.microsoft.com/?kbid=297185](http://support.microsoft.com/?kbid=297185)

Any additional information about your computer? (brand, model, processor, harddisk size & type, how many partitions you've got, the details on those partitions)

When you were setting up Windows XP using the install CD, did you manage to succesfully create NTFS partitions? Did you used the whole disk? Did you use a part of the harddisk and create some other partitions?

---

### Post by WSTGangsta on 2006-04-03
Okay, I will use one of the gparted or qtparted programs to delete my partitions, and then try installing windows, see, what was happening, it would make the NTFS partition, copy all the windows files, and tell me to restart my computer, leaving the disc IN the drive so that setup could continue. I have to go to school Im not getting started on that yet.

---

### Post by WSTGangsta on 2006-04-03
Yeah! Thanks for your help everyone,  have reinstalled WinXp, and now I want to know, have I any chance of my DSL working with Ubuntu? Because I tried some configurations with the Live CD and it wasnt working, and I like gnome, what is another gnome distro that I can try out?

---

### Post by Jason_25 on 2006-04-03
Use ethernet instead of USB.

---

### Post by Desert Linuxwannabee on 2006-04-03
[QUOTE=WSTGangsta]Yeah! Thanks for your help everyone,  have reinstalled WinXp, and now I want to know, have I any chance of my DSL working with Ubuntu? Because I tried some configurations with the Live CD and it wasnt working, and I like gnome, what is another gnome distro that I can try out?[/QUOTE]


I used the Live cd for the first time yesterday to try it out.
Everything worked just fine for me, and got internetconnection full auto, without changing one thing in the settings.
So, i can say one thing: Live cd is=D>

---

### Post by Buffalo Soldier on 2006-04-04
[QUOTE=WSTGangsta]Yeah! Thanks for your help everyone,  have reinstalled WinXp, and now I want to know, have I any chance of my DSL working with Ubuntu? Because I tried some configurations with the Live CD and it wasnt working, and I like gnome, what is another gnome distro that I can try out?[/QUOTE]
That depends on your DSL modem. Is the modem connected to your PC thru a USB cable or ethernet cable (to your network card)? USB modems are very GNU/Linux friendly. For ethernet modems, if you set it up correctly it will work flawlessly.

Perhaps you would like to check if your [wired](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards) / [wireless](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) card is supported.

Another GNOME distro that I would suggest is [Fedora Core](http://fedora.redhat.com/).

---

### Post by WSTGangsta on 2006-04-04
Okay, Ill try it, and its connected by ethernet, my dad has two routers together so everythings screwy, and my phone line is screwy also

---

