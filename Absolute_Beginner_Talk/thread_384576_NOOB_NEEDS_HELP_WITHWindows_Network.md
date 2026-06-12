---
title: "NOOB NEEDS HELP WITH:Windows Network"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by arang on 2007-03-14
ok, i tried to explain my ideas fully last time but seems noone understood so lets try something even simpler.

I have installed Ubuntu 6.10 everything default, on my PC, (i also tried it in other pc's i own) when i go to check the windows network ubuntu finds the workgroup (the name appears and all) but when i click on it , it says it cant show the contents, i tried this in different machines the same result, also tried Feisty too, the machines are getting ip's from my local router thru dhcp, all are able to go to the internet and browse easily without problems, only problem is no access to windows shares.

I've read some say that they just install ubuntu and the windows networking just works i dont know whats the problem here, im flying with defaults or even with the liveCD thing.

If i cant fix this i'll say byebye to ubuntu till it's at least on the 8 or 9 release i guess

---

### Post by ferg on 2007-03-14
It sounds like you have the same problem I have had for quite some time now - I cannot access Windows shares from my Ubuntu box by the method you describe. However - if you launch nautilus and in the "Location:" box (sometimes to get this to show you have to click the little pad and paper) and type...

smb://192.168.1.15/

Replace the IP address with the IP address of your Windows box, and you will get a list of shares. Remember it's forward slashes not backslashes (this caught me out for ages when I first switched!). Be patient, it can take a few seconds to populate. If you want to mount shares permanently then you will need to assign a static IP to the Windows computer. 

This is how I access shares at home and it works great, I just can't browse them by hostname. Maybe someone else can suggest a fix for this? I've tried quite a few things myself to no avail. This is a bit a of a dirty workaround, but I hope it works for you! :)

Fergus.

---

### Post by arang on 2007-03-14
i havent been able to try with nautilus cos im using normal ubuntu and i think it comes with Kubuntu? (KDE?) anyways i'm still stuck in this problem anyone care to give me a hand, i tried the irc channels but nothing noone wanna help/nor knows how to help

---

### Post by albs on 2007-03-14
Thanks mate!  That cleared up a few issues for a walk-in like me.

What about the other way around?  I'd like to get access to my Edubuntu box from Windows and grab files.

Thanks!

---

### Post by kelbizzle on 2007-03-14
edit "/etc/samba/smb.conf" and change this line:
```
 workgroup = MSHOME
```

to your workgroup (domain)

then restart samba (I think its "sudo /etc/init.d/samba restart")

---

### Post by swoskow on 2007-03-14
I just finished setting up Ubuntu for the first time on my Home Network (all other computers are XP) so I thought some of my experiences might help.  

1.  Shut off all firewalls in all your network (or at least the Ubuntu and 1 other).  IN Ubuntu this is done through system>administration>Firestarter.  In Windows make sure all virus programs with Firewalls are shut off.  This includes Windows firewall.  You can do this in the control panel.  I shut mine down completely by going to Control Panel>Performance & Maintenance>Administrative tools>Services>Windows Firewall Internet Connection   double click on the Windows Firewall and disable.    Once you establish your connections you can go back and set up your firewalls but this way at least you will find out if you can get a connection.

2.  Permissions Ubuntu - this is a Ubuntu feature that is a bit obnoxious but I understand the added safety of doing it this way.  Make sure all your file permissions are set up (you have to use Nautilus to do this - in terminal sudo nautilus).  Go to the share folders and right click on the folder then click on the permission tab.  Set the owner as you (whatever you set up in install).  Set the group to your group name.  Set the folder access to whatever level of access you want to grant.  Apply the permissions - also in the dialog box when I make a share I unmark the Read Only box - I want full access to all the files this may be redundant with Permissions set up (I am not sure) but it works.  

3.  Windows - mark your folders as shared and make sure they are all set up as shares (I will assume you know how to do that).

After spending hours searching forums etc I did the steps above and everything worked great.  Keep trying because once you get set up it really is slick and I really like how Ubuntu works as a Network server.  I was even able to set up a share on a 3 disc Raid on LVM and everything is working great so far.

Good luck and hang in there it is worth it.

---

### Post by albs on 2007-03-14
> **kelbizzle said:**
> edit "/etc/samba/smb.conf" and change this line:
```
 workgroup = MSHOME
```

to your workgroup (domain)

then restart samba (I think its "sudo /etc/init.d/samba restart")

I've opened the document, and my workgroup is already written in there...

What I get on my windows side is, it keeps prompting me for my username/password, as if I mistyped.  So I'd first type:

- *my username*
- password

and then windows will come back with 

- EDUBUNTU/*my username*
- password

Is there some user setting I haven't done?

---

### Post by ferg on 2007-03-14
Instead of Nautilus use whatever windows manager KDE uses, the principle will carry. :)

Some good suggestions as to fixes here too - I shall be trying these later! :P Thanks guys.

---

### Post by swoskow on 2007-03-14
One other item I did - once I had everything set up on Ubuntu (samba) I re-set up my network on the Windows computer  control panel>network & internet connections>set up or change your home or small office network.  Like you I tried to just add the Ubuntu to the network but I never could get it to work.  Once I just re- set up the network it worked fine.  When you do that give it some time to establish the network.

---

### Post by arang on 2007-03-14
> **ferg said:**
> It sounds like you have the same problem I have had for quite some time now - I cannot access Windows shares from my Ubuntu box by the method you describe. However - if you launch nautilus and in the "Location:" box (sometimes to get this to show you have to click the little pad and paper) and type...

smb://192.168.1.15/

Replace the IP address with the IP address of your Windows box, and you will get a list of shares. Remember it's forward slashes not backslashes (this caught me out for ages when I first switched!). Be patient, it can take a few seconds to populate. If you want to mount shares permanently then you will need to assign a static IP to the Windows computer. 

This is how I access shares at home and it works great, I just can't browse them by hostname. Maybe someone else can suggest a fix for this? I've tried quite a few things myself to no avail. This is a bit a of a dirty workaround, but I hope it works for you! :)

Fergus.

hey fergus, it really worked for me, but sadly i dont have the luxury to do that given the fact that my computers get ips dynamically from the dhcp server in my router, so i dont know their ip's all the time, so i cant input that in nautilus, thats why i need the browsing capabilities to work :(

anyone care to help for the love of god!

arang

---

### Post by dstew on 2007-03-14
Hi arang. I have Xubuntu 6.06, so some things might be different between your system and mine, but I have to use Samba to connect to Windows shares. Is Samba already installed on your system? If not, you have to install it. Once it is installed, you use it to mount your shares to your Linux file system.

---

### Post by arang on 2007-03-14
hi, it depends on what u mean to connect, the nautilus thing lets u explore the share and also lets u use apps on the files on it (some not all), samba is used to "mount" the share into the filesystem, in something like /mnt/windowsshare so other apps dont need to be "windows networking share" aware to use the files.

---

### Post by seshomaru samma on 2007-03-15
you should read [this ]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba")

---

### Post by albs on 2007-03-15
Are you able to log into your router, check which connected device has which IP address, and use the smb://x.x.x.x command?

I'd still like someone to show me how to grab files from a Ubuntu box to a Windows box, either from Ubuntu or Windows.

I'm getting authentication problems from the Windows side (even though I can see the Ubuntu box in "my network places", and I simply can't display my Windows files Ubuntu, except as web links.

---

### Post by arang on 2007-03-15
> **seshomaru samma said:**
> you should read [this ]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba")

i already read that, thank you still no answer to my problem, as someone said i could log into the router and check what computer got what ip but sincerely thats a dirty solution, i should be able to browse the net normally not start checking the dhcp leases

arang

---

### Post by glxyjones on 2007-03-31
I have a similar problem with Ubuntu.  Whenever I try to connect to my Vista machine I type in my username and password but after hitting enter, it thinks for a second and then asks for them again.  As if I'm mistyping something, but I've tried it multiple times with multiple username/pw combinations.  I don't think it's my Vista machine because I can access its shared folders via my parents (windows xp) laptop.  Also, I can access files on my ubuntu machine via vista.  

I'm sure it's something stupid, like i haven't set something up in samba, but I cannot figure it out.  Any help would be appreciated, thanks!!

---

### Post by brownknight on 2007-03-31
hi. i am a noob too. i am able to share my ubuntu folder(s) with my windows xp laptop and vice versa using samba. i just followed the guide here in [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy").
 
i always go to this site first for the howtos i need. i hope this helps. :)

---

