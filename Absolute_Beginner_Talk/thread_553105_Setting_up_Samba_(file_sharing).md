---
title: "Setting up Samba (file sharing)"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-17
Hi,  Just would like to know If I have Setup Samba correctly or if there is something
else I need to do.

1. I went to the Synaptic Packet Manager and installed Samba.
2. I went into System --- Share Folders  ( In Xubuntu )
3. I choose "Add" and in Path choose the folder I wanted to Share.
4. I choose" SMB" in the Share WIth box.
5. Under "Share properties", I typed in the name of my share folder
6. I also added a little comment to let me know what computer the share is located on.
7. In the "General Windows Sharing Settings" box I typed in the name of my Workgroup.
   I left the HOST description as defalut,
8. I hit ok and it should all be set up, I guess.

I haven't added any more PC's to my network yet but I plan to.

Do I need to do anything thing else or am I ready to go on this.
Does Samba need to be set to auto start or be told to run?

Thanks.....

---

### Post by SteveHillier on 2007-09-17
Just a thought.  Have you set up the workgroup in smb.conf to match the Windows workgroups?

---

### Post by Orbital75 on 2007-09-17
I haven't messed with the smb.conf directly. I was thinking that
In the "General Windows Sharing Settings" box, would do it for me.... 
This is a setting in the Share folders options in Xubuntu.

---

### Post by Ian-on-the-Trent on 2007-09-17
I have several computers attached to my network. I had Samba working prior to upgrading to 7.04 and now I can't seem to get everything up and running. My XP boxes can see the Ubuntu box--and vise versa--but the XP box can't access any files on the Ubuntu box.

I need to use some Windows-only applications but I stored all of the files on the Ubuntu box.  I don't use my su login name for these apps, just a regular user.

I have used the various "how to" guides but still no luck. This is what I've done so far:
[LIST]
[*]XP & Linux boxes have same users and passwords.
[*]On XP, Zonealarm set to allow access from the static IP Ubuntu box.
[*]I created a samba users to match Ubuntu users:  sudo gedit /etc/samba/smbusers:
                user1 = "user1"
                user2 = "user2"
[/LIST]

And using the various guides (this one in particular(, [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)), my smb.conf looks like the following:

[global]
    ; General server settings
    netbios name = Linux_Box
    server string =
    workgroup = MY_LAN
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

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
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/

[MyFiles]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = user2
    force group = user2

[user2]
    path = /home/user2/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = user2
    force group = user2

**Does anyone have a suggestion as to why this doesn't work for me?**

---

### Post by BLTicklemonster on 2007-09-17
Been using ubuntu for a couple years, and I still don't know how you are supposed to get windows computers to see a linux box's folders and access them, nor do I know why this has yet to be addressed and fixed with a simple user interface. I've followed instructions and how tos and tutorials from here to Timbuktu, and still, to this day, cannot get a windows machine to access a shared folder on a linux box.

By the way, for anyone who agrees, please make your voice heard (like it will matter) [http://ubuntuforums.org/showthread.php?t=553169](http://ubuntuforums.org/showthread.php?t=553169)

---

### Post by Orbital75 on 2007-09-17
I'm sure you guys meant well explaining your experiences but
mine doesn't work and I'd like to know how to get mine to
work right now.  However I did enjoy reading your experiences,
seems a little tougher to get file sharing going in linux.
I didn't think it would be that hard since Linux is a Networking
OS.  :-)

---

### Post by BLTicklemonster on 2007-09-17
I would be my last penny that the problem lies in the way how tos are presented, and the fact that there is this insane "security" mindset prevalent. I'm behind a hardware firewall, so I really couldn't give a flying rat's patootie about security. I just want to right click on a folder, click share, then walk over to any machine I have on my network, and see the folder, and have access to it. No passwords, no user names, just let me at it, already.

The how tos I have seen have all been confusing, and tech oriented, as if the people reading them understand what the author is saying. Well, I don't catch on, so they are basically useless for me.

It's extremely frustrating. Sorry about hijacking your thread.

---

### Post by Ian-on-the-Trent on 2007-09-17
Orbital....mine doesn't work either.  I'm trying to get it going since I have a client breathing down my neck.

BLTicklemonster: I agree with your last post.  I'll add that some of the ones I've read may be well written but they don't always work for my scenario.  And then the neo-techies slag the writer to death.  Sometimes I feel that that the uber-linux-techies are even more blinded to the linux-speak/CLI gods way of thinking than when DOS techies lost control of boxes when Windows first appeared. (To think I was one of those DOS control freaks...well, a minor version anyway.)

Sorry for being a post hog.

---

### Post by porcorosso on 2007-09-19
I'm used to doing things the hard way. And not because I'm smart. It's because the easy way usually doesn't work for me.

But I saw this thread, and I happened to have a fresh installation of Linux Mint Cassandra (based upon Ubuntu Feisty Fawn) just installed. And I needed to be able to set up shares on it to be accessed over a "public network" from a Vista machine. So I thought I would try the GUI way.

It appears that Linux Mint comes with the basic parts of samba already installed, so I didn't have to mess with that. I had already installed Firestarter and had it running on the eth0 (hardwired) network connection because this puppy is connected to a work network (where I also have my Vista machine).

On the Linux Mint system I went into Administration -> Shared Folders and told the thing to share my "username" folder, which works out to /home/username via SMB. I unchecked the read only feature. On the General Properties tab of that applet I also stipulated that this system was a member of WORKGROUP (the workgroup to which the Vista box belongs) and that the Linux box was also a WINS server. I okayed my way out.

On the Windows Vista system I left this network connection set as a Public network (with discovery turned off, in other words). I changed the TCP/IP properties for the connection to include the IP address of the Linux box as a WINS server.

When I opened Windows Explorer in Vista I was able to connect to the Linux share by typing \\Linux-Box-Name\username in the "breadcrumbs" field, and I was instantly connected to the share on the Linux box! I created a text file in the share just to test my ability to create new files. Didn't do any other testing.

Trying to get to the already established shares on the Vista box from the Linux box, however, isn't happening just yet.

But this was a pretty promising beginning, no? It was GUI all the way. No manual editing of smb.conf or any other terminal / cli stuff.

I just turned on network discovery for a few moments to see if I could browse the Linux box's share, and it showed up -- along with its printers.

There aren't many steps in there. Did you get the bit about enabling the Linux box as a WINS server and then telling the Windows box(es) to use it as a WINS server? I think that might be pretty crucial.

----

Added Point: Uh, I forgot to add that I created a rule in the firewall allowing Samba for the Windows Vista box's IP addy. That way my Samba box is not discoverable (in the Windows network browsing sense) on this work network. Firewall stays up, and I breathe a little easier.

---

### Post by bobbocanfly on 2007-09-19
Have you made sure you have setup the SMB passwords for your users?

```
sudo smbpasswd <username>
```

Then type in the new password twice so users can log in remotely.

---

### Post by porcorosso on 2007-09-19
> **bobbocanfly said:**
> Have you made sure you have setup the SMB passwords for your users?

```
sudo smbpasswd <username>
```

Then type in the new password twice so users can log in remotely.

Oh, good grief! I KNEW I had left something else out of my little write-up! Yes, I did have to issue that command in Terminal.

Well, I warned that I am a dummy!
:lolflag:

But it is a pretty minimal command line requirement.

---

### Post by the_nite_owl on 2007-09-19
Hi Guys,
I just setup Samba and managed to make my share visible to my Windows boxes after reading this thread and finding the smbpasswd command.

I have questions on privledges for the shares though.
How do I make the resource read/write accessible to users on the network and set privledges for different users?
When you issue the smbpasswd command does it have to relate to a local account on the linux box?  Or in other words do I have to create accounts on the box first then issue the smbpasswd command using the newly created accounts?

The drive I am trying to share out is of course owned by root.  How do I set folder privledges for the accounts I setup for access in Samba?  

I am a relative newbie but making progress.  Using Feisty x64 LAMP server and building up everything step by step.  Getting close to what I need and getting rid of my Windows server once I figure out the share space stuff.

Thanks.

---

### Post by BLTicklemonster on 2007-09-19
> **bobbocanfly said:**
> Have you made sure you have setup the SMB passwords for your users?

```
sudo smbpasswd <username>
```

Then type in the new password twice so users can log in remotely.

Did it, and you know what? I used to could see the windows machine when I used earlier versions, but now in gutsy, I don't even see the box across the room. Argh!

---

### Post by HermanAB on 2007-09-19
Here is a samba debug guide: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

H.

---

### Post by BLTicklemonster on 2007-09-19
I'm seeing something troublesome here. I have to go doing user name and password stuff on the windows machine? 

Good God all mighty.

I'll take the old HP in the other room and set it up as a server removing all the unnecessary stuff on it before I'll go doing all that. I wanted to use this machine to store pictures and other files so we could get to them from other computers in the house, but if I have to go getting all that wierded out, forget it. I have a freaking hardware firewall for crying out loud, and we aren't "gee, let's do all our financial stuff on the computer" morons. It's the 21st century, financial stuff and computers don't mix, I don't care how good you are.

---

### Post by porcorosso on 2007-09-20
> **BLTicklemonster said:**
> I'm seeing something troublesome here. I have to go doing user name and password stuff on the windows machine? 

Good God all mighty.

I'll take the old HP in the other room and set it up as a server removing all the unnecessary stuff on it before I'll go doing all that. I wanted to use this machine to store pictures and other files so we could get to them from other computers in the house, but if I have to go getting all that wierded out, forget it. I have a freaking hardware firewall for crying out loud, and we aren't "gee, let's do all our financial stuff on the computer" morons. It's the 21st century, financial stuff and computers don't mix, I don't care how good you are.

I don't know where to begin. I could be mistaken, but it seems as though you're depending very heavily upon the NAT/PAT and SPI of a peripheral firewall to protect some very wide open systems. Such networks are often compromised as the result of innocent behavior on the part of an end user -- clicking on the wrong link, insertion of co-opted media, etc. If the users aren't running under limited accounts, and if those accounts and higher level ones on the systems don't require credentials...

Besides, someone getting to your financial data is not the only worry here. There might be all sorts of information on one of those hard drives (like names and addresses) that you wouldn't want the wrong person to own. And then there's the risk of having one or more systems used for nefarious purposes by someone on the outside.

It's not as though setting up password-protected accounts is that inconvenient. If you're worried about end users being prompted for passwords when they connect to shares on the Linux box, that isn't going to happen if you use the save password setting when you first establish the connection to the share.

There are, of course, lots of ways to skin this particular cat. All of them require some work up front, but everything works very easily once the initial setup has been performed. For instance, I saw mention of use of openssh-server (on Linux) and WinSCP (on Windows) mentioned somewhere around here as a possible alternative to Samba.

As for me, I guess I'm a moron. (And I'd bet that there are a lot of us here on this forum.) I do virtually all of my financial record-keeping and perform most financial transactions using our computers. But I also use password-protected and restricted accounts, data and communications encryption, remote storage of encrypted backups, and various forms of malware detection (real-time and on demand, on some operating systems) as well as address translation and SPI at the periphery. Am I 100% safe? No. But it would be hard enough to get to our data that it couldn't possibly be worth the effort to anyone who was bent on getting it.

Hope you get these wrinkles ironed out to suit you!

---

### Post by TaTaE on 2007-09-20
If you are using gutsy gibbon, file sharing is very easy: Just right click your folder, select SHARE and follow that wizard. In the end you must write this in terminal:
    sudo smbpasswd -a *yourubuntuboxusername*

After that, you must provide that username and password to connect remotely to your shared folder.

---

### Post by HereInOz on 2007-09-20
The one thing that everybody seems to miss is the firewall (iptables).  The easiest way to configure iptables is with Firestarter.

Install Firestarter and make sure that you allow the other machines on the LAN to access the linux machine (in the Policy tab).

THEN (sorry for shouting but this is important) go to Preferences > Advanced Options and uncheck the option to "block broadcasts from the external network".

If you don't do this in the firewall, Windows machines will not be able to access the Samba share.

---

### Post by porcorosso on 2007-09-20
> **HereInOz said:**
> The one thing that everybody seems to miss is the firewall (iptables).  The easiest way to configure iptables is with Firestarter.

Install Firestarter and make sure that you allow the other machines on the LAN to access the linux machine (in the Policy tab).

THEN (sorry for shouting but this is important) go to Preferences > Advanced Options and uncheck the option to "block broadcasts from the external network".

If you don't do this in the firewall, Windows machines will not be able to access the Samba share.

That's not what I'm seeing here at all. The only thing I had to do was to provide an inbound policy allowing service Samba (SMBP for ports 137-139 and 445 for the IP addresses of the systems I wanted to allow access to the shares. Unchecking the "block broadcasts from the external network" was not necessary. Probably not dangerous if behind a peripheral firewall, but not necessary anyway. Also, no policies to allow connections from hosts were needed.

---

### Post by porcorosso on 2007-09-20
BTW, I just tried using openssh-server on a Linux Mint Cassandra box and WinSCP on a Vista box. I just installed the two applications, created an inbound policy in Firestarter on the Linux box to allow SSH connections from the Vista box, cranked up WinSCP on the Vista box, and connected to the Linux share. Unbelievably simple. I can customize connection sections to look just the way I want them and save them. About as easy as it gets. And tremendously controllable.

---

### Post by BLTicklemonster on 2007-09-29
> **TaTaE said:**
> If you are using gutsy gibbon, file sharing is very easy: Just right click your folder, select SHARE and follow that wizard. In the end you must write this in terminal:
    sudo smbpasswd -a *yourubuntuboxusername*

After that, you must provide that username and password to connect remotely to your shared folder.

I installed gutsy beta on a storage drive (now I have an entire gutsy to use if the other one tanks) and shared, then did what you said, and I finally have totally shared files.

Thank you!!! :guitar:

---

### Post by BLTicklemonster on 2007-11-13
Dangit! Just tried that again, and it doesn't work now. Says I don't have permission to even see it. I never get a login window or anything.

---

### Post by TaTaE on 2007-11-13
Maybe you should check the file permissions. Maybe they should be world readable.
Or you could purge samba and reinstall. I hope these will help..

---

### Post by BLTicklemonster on 2007-11-13
After playing around with Ubuntu for around 2 years now, and never getting networking down rock solid (as in: once I get it working, it invariably stops working at next upgrade, or for no apparent reason. Case in point: I could connect to the network and see other computers, then I couldn't, then last night I could, then I couldn't. *all since last Friday*), and now having problems getting a "this one works for Ubuntu" printer to work (as in it doesn't work at all), I'm pretty much burned out on this all. Period.

Look, if ubuntu were ready for the masses, then anyone could install it, then share a folder, fill in a few blank spaces (user name, password), then click okay/close, and the networking would work. Period. Same with a printer. But that doesn't happen, and after putting up with a "it's really neat, but all I can really do with it is get online and read emails, chat in a less than stellar functioning chat program, make some really neat graphics, etc." operating system for 2 years, I really don't feel that it's been worth the hassle at all. Not one bit. 

Ubuntu severely inhibits my PCs functionality.

There's no other way of looking at it.

So I'll leave it installed, but I'm going back to the functional OS for now, as much as I hate to. I'm sure that Ubuntu will one day be ready, and that the developers will **_*quit*_** **wasting time on eye candy**, and **work on the nuts and bolts**:

auto grub: I ought to be able to drop a slave HD in, and boot to the desktop without having to reconfigure grub from a live cd.
Networking Wizard: I ought to be able to use a gui that asks me what I want to share, what user name, and password, and if it's windows share, and be done with it.
Printer: I think you're getting the idea now.

And this really pains me because I've been going around telling everyone about how good ubuntu is. Now I'm a bit of a laughing stock with 5 of my friends who couldn't get (ubuntu ready) printers or networking going either.

See you all around.

---

### Post by TaTaE on 2007-11-15
Maybe you should have pulled your finger off your nose while sharing the driver. It could be a bug, who knows... :(

---

### Post by BLTicklemonster on 2007-11-17
lmao, I thought it was a bugger but it's snot.

I'm back trying it again. This is really eating me up. I can see the XP boxes now, and can get to the login on an XP box, but I can't use my username and password (from other instructions) so I'm back to this thread to try the no password trick.

---

### Post by yortski on 2007-12-14
Thanks to all the info in this thread I'm sharing Vista over my network now. On Feisty Fawn.

Used apt-get  to install samba, right clicked folder I wanted to share, set to share, set my read and write access then did the sudo smbpasswd -a yourubuntuboxusername , refreshed the Vista network and there it was, logged in, transferring files.

I Think the sudo smbpasswd -a yourubuntuboxusername is what did the trick for me.

Thank you people.:)

 I was getting sick of having to files into my mounted drive, then booting to XP to network.

---

### Post by iharrold on 2008-04-08
> **bobbocanfly said:**
> Have you made sure you have setup the SMB passwords for your users?

```
sudo smbpasswd <username>
```

Then type in the new password twice so users can log in remotely.

Old post... but this solved my Samaba issues aswell.  Thought I would bring it to the top for posterity.

---

### Post by Delta5 on 2008-04-08
> **BLTicklemonster said:**
> Dangit! Just tried that again, and it doesn't work now. Says I don't have permission to even see it. I never get a login window or anything.


Total newbie here.... 

Have you tried connecting to those shares while you're logged in on the Ubuntu machine?  I've got an external USB drive that I'm sharing on my home network.  It works perfectly (can see, can access, read/write, etc) from XP & Vista *so long as I'm logged in* on the Ubuntu machine.  As soon as I log out, the USB drive is unmounted or something and the shares immediately stop working.

For me anyway, the most useful resource I found on setting up Samba was here...
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

But also with a little help from here, since I was (initially) having problems with username/passwords.  This at least got me started with a share that worked without having to tweak logins.
[http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/]("http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/")

But yes, the smbpasswd command was a big part of getting it to work for me as well.  IMHO, that process ought to be part of the file sharing GUI.

---

### Post by BLTicklemonster on 2008-04-10
Thanks Delta5!

---

### Post by BLTicklemonster on 2008-04-11
Lmao, I can get into the other machines (XPs) now, but they don't see my machine. Probably something simple. I'll just have to go back over it slowly and look everything over. Thanks for the no password link. that totally simplifies things.

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

