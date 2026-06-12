---
title: "Nooby trying to set up wifi net"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by NacIK on 2007-05-09
I am running Feisty on my desktop, and XP on my laptop.  I have my network card working in both computers and both connect to the internet.  The problem I am having is creating a network between the two to share media files.  I am new at setting up networks, so when I was reading the wiki's on Samba I was instantly lost.  Is there anyone that could help me out step by step to learn how this system works.  I love everything about Ubuntu and I believe it puts Windows to shame, but it is hard to so people that if I can't even set up a simple network between them.

Thanks for the help.

---

### Post by Martin on 2007-05-09
On the main dektop menu go Places - Connect toServer and you will be prompted to install the samba and or nfs networking software. After that it is very similar to accessing any other device on a windows network. You will not have to read anything about samba. Its pretty much all automagic. Just make sure you've shared the folders you're trying to access and you'll be away.

---

### Post by NacIK on 2007-05-10
Sorry, but that didnt help much.  I don't know anything about networks.

---

### Post by kragen on 2007-05-10
Don't worry too much about the wiki's for now - basically samba is a collection of tools that lets linux computers share folders that windows computers can access, and access shared folders on other windows computers. Most of the tools and command line tools, but thankfully however Ubuntu lets you do pretty much everything with graphical interfaces.

Firstly, goto "System > Administration > Shared Folders", it should either bring up a properties box, or it should prompt you to install either samba or nfs. Check the box saying you want to install samba, and follow the prompts - once it's done, you should be able to bring up the properties box.

The main reason I made you bring this box up is because its a simple way of checking that samba is installed, but this box has a couple of useful options - the first tab shows you a list of all the shared folders on your computer (folders that other computers over the network will be able to access), the second tab lets you change the windows workgroup you are in (if you are farmiliar with windows networking, you might be interested to know where the option to change this is, if you aren't, then don't worry about it).

Now, if you have a shared folder on a windows computer that you want to access, you should be able to goto "Places > Network", and either the computer you want to access will be listed, or you should be able to find it in one of the "subfolders" if you go into the "windows network" "folder". Once you've found the computer, you should be able to browse any shared files in the same way that you would on windows.

If you want to make a folder accessible to others via the network, simply find the folder you want to share, right click on it and select "share folder". In the "share through" drop down box select "Windows networks (SMB)", and press ok. Windows computers should now be able to read that folder in the same way they would be able to read other windows shares.

If you have any problems or find any / all of the above confusing, then just ask :) Networking can be confusing at first. If you aren't familiar with networking windows computers, it might be worth reading up a bit on that first. Once you are comfortable with networking windows computers, networking linux computers is a similar process, it's just that the buttons are in different places.

---

### Post by NacIK on 2007-05-10
ok, that was simple, but how do i create a network first, for some reason when i try to create a new network it wont connect to the other computer

---

### Post by NacIK on 2007-05-10
This is pathetic. I have built conputers for years, but never had to deal with networking until now.

---

### Post by kragen on 2007-05-10
How do you mean "create a new network"?

---

### Post by nickpaton on 2007-05-10
It will help if you disable the Firewall.

The firewall is called Iptables and is installed and enabled (i.e. the firewall is 'up') by default.

Make sure you have access to the Internet.

To control easily you need to install Firestarter which is done in Synaptic (System > Administration >Synaptic Package Manager).

From within Synaptic click on Search and type 'firestarter' (no '   ').
Synaptic will now find firestarter.  Hover over it and right click and click 'install'. 
The Install button will now be hightlighted - click and it will install firestarter.  Wait until the process is finished.

Close down Synaptic when you see 'All' appearing.

Firestarter is installed at System > Administation > Firestarter.

Follow the Firestarter wizard and at the end it will open.  Click on the Stop Firewall button and the top.

Minimise (Do not close) Firestarter.  Try now to see if you can access the other PC.

When you do get your network going it's best to configure Firestarter so that it's enabled but you can still see the other PC's. [This is a HOWTO]("http://ubuntuforums.org/showthread.php?t=202605&page=30#298")

---

### Post by NacIK on 2007-05-10
killing the firewall helped the two connect, but it still didnt allow me to see the files on either computer

---

### Post by NacIK on 2007-05-10
If I can ever figure this out I also need to find out how to enable my lan for the internet and my wireless at the same time.  Then I can keep the network on all the time.

---

### Post by nickpaton on 2007-05-10
Have you set up the XP PC to share files etc?  If not I'll find a HOWTO for that.

Also can you clarify your setup - do you have an ADSL modem router to which you have both PC's connected?

EDIT: If ADS mod rout - what is the make and model - we may need to make some simple changes to the configuration.

---

### Post by nickpaton on 2007-05-10
> **NacIK said:**
> If I can ever figure this out I also need to find out how to enable my lan for the internet and my wireless at the same time.  Then I can keep the network on all the time.

No worries about that - but one step at a time!

---

### Post by NacIK on 2007-05-10
No, it is a Linksys wifi-g pci router.  Model WMP300N

---

### Post by NacIK on 2007-05-10
I have XP and Feisty on my desktop, and XP on my laptop.  They share files just fine in Windows (that was the easy one to figure out) but I  don't if I have to do a special setup in XP in order to communicate to the Feisty computer.

---

### Post by nickpaton on 2007-05-10
Thanks for all that!

But can I assume that at the mo, you are 100% wire connected to a central ADSL modem router - if so what is the make and model of that.  The reason I ask is that we need to make one or two simple changes. 

'Fraid you cannot avoid setting up Samba, but it's like setting up Windows for networking - a bit of dabbling here and there!

The HOWTO I always use is[ Here]("http://ubuntuforums.org/showthread.php?t=202605"), and it does not 'interfere' with your windows networking.

I guess you will have Samba installed by now so if you sudo apt-get install samba it will say that it's already installed.

The stuff further down also goes into setting up the Windows bit.

I've also PM'd you

---

### Post by NacIK on 2007-05-10
Ok.  I am in the US Army currently deployed to Afgan.  I have a satellite connection, so I am not sure on the modem part.

After reading the tutorial I ran into some questions:

"Static IP" - how can I tell?

"-> force user = YOUR_USERNAME|"
"-> force group = YOUR_USERNAME"   -for windows or ubuntu?

"Time to add yourself as an samba user.

NOTE: You will be asked for a password - make sure you use the same as you use for login!

Code:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!"
  -same thing, windows or ubuntu

---

### Post by NacIK on 2007-05-12
ok, now im lost

---

### Post by nickpaton on 2007-05-12
Check your PM

---

