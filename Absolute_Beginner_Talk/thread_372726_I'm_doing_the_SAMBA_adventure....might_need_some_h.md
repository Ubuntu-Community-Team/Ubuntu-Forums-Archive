---
title: "I'm doing the SAMBA adventure....might need some help!"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-28
I'm finally doing the SAMBA adventure....might need some help understanding what I'm manipulating in  /etc/samba/smb.conf
Since the Ubuntu SAMBA tutorials and guides out there don't seem to cover everything that one needs to know I'm following a generic Linux SAMBA tutorial.  That's why I need help understanding if things mean the same when they are written and typed differently in the tutorials instructions.
[CENTER]**[COLOR="Purple"]Question no. 1[/COLOR]**[/CENTER]
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = My_Work_Group

# server string is the equivalent of the NT Description field
[COLOR="Sienna"]   server string = Alice[/COLOR]
```
Is **"server string"** the same as **"netbios name"** or are they 2 different things?
[http://www.samba.netfirms.com/sambconf.htm#global](http://www.samba.netfirms.com/sambconf.htm#global)
> 
[COLOR="Sienna"]netbios name = Samba[/COLOR]: netbios name is what you will see in your Windows pc "Network Neighborhood" for your Samba server.You can name this anything you wish. If you leave it blank, it will default to your host name.

---

### Post by jingo811 on 2007-02-28
How do I add users correctly?
My only source and clue [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add.2Fedit.2Fdelete_network_users)
[CENTER]**[COLOR="Purple"]Question no. 2[/COLOR]**[/CENTER]
```

mike@sanka:/etc/samba$ **sudo smbpasswd -a einstein**
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user einstein. Does this user exist in the UNIX password database ?
Failed to modify password entry for user einstein
mike@sanka:/etc/samba$ **sudo smbpasswd -a antec**
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user antec. Does this user exist in the UNIX password database ?
Failed to modify password entry for user antec
mike@sanka:/etc/samba$ **sudo smbpasswd -a Einstein**
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user Einstein. Does this user exist in the UNIX password database ?
Failed to modify password entry for user Einstein
mike@sanka:/etc/samba$

```
What am I doing wrong, my Windows XP has user login Einstein?
When I did this add user command for myself that is the root account I'm using right now, by typing this line:
```
sudo smbpasswd -a `whoami`
```
I don't get error messages as above.  Why :confused:
[CENTER]**[COLOR="Purple"]Question no. 2.1[/COLOR]**[/CENTER]
OK i skipped some chapters on that tutorial and found one page describing how to add a Win machine on the network, the thing is the commands below doesn't seem to work for Ubuntu :( 
Do you know what the equivalent commands for Ubuntu are in this case?
[http://www.samba.netfirms.com/addmachine.htm](http://www.samba.netfirms.com/addmachine.htm)
```
useradd -s /bin/false -d /dev/null windows_machine\$
smbpasswd - -m windows_machine
```

---

### Post by raja on 2007-03-01
Sorry, I dont know too much about this. However, I think the error you encounter when trying to add a user to the network is because that user is not yet added as a system user. If that is the case, then add that person as a system user (GUI or sudo useradd in the terminal) and then try this again.

---

### Post by dannyboy79 on 2007-03-01
you don't have to add system users if it's only because these users are users on your windows computer. you can create a username.map file and refer to it in your smb.conf file. that way, user fred on windows can be user al on ubuntu so that fred can be authenticated and will be able to access shares. there is a great guide here for ubuntu and samba. [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=share](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=share)

your netbios name is what the server is called (same as computer name in windows), the server string is what shows up in the description field in network neighborhood. I just went thru and read all of man smb.conf and learned a lot. I was sick of reading guide after after guide and getting no where so I looked at what the guide used for smb.conf options, then read he man page and made my own decision based on sometimes on logic and sometimes based on what ALL the guides had in common. the thing that will screw you up possibly is which computer will be the local master browser for your samba network. cause windows xp pro will almost always win but then when I shut off winxp pro and want samba to work between my xubuntu laptop and my ubuntu desktop, it wouldn't work so I added the proper stuff so that my ubuntu desktop was always gonna wein and going to be the local master browser. it took me a LONG time to get my 2 xbox's, xubuntu dapper, ubuntu dapper, and winxp pro to all talk to each other and whatnot. printing works also. i used the real cups web interface, not the gnome one.he trick there is you have to enable to admin user for it to work otherwise you don't have access to the configurations pages.i can help ya igf you;d like but please please make sure your computers can ping each other and ping the router if you have one. (ping by ip at least, netbios name can come later) then use the guide, then if you still need help, let me know. i am gonna take a nap though, I am exhausted.

---

### Post by Detonate on 2007-03-01
Samba is not as complicated as it appears.  I think what throws people off, is they don't think of Samba for what it is, a separate server which happens to be running on your machine.

Once you have installed Samba, the first thing you need to do, is establish yourself as a user.  Just because you are already a user on your machine does not make you a Samba user.

To do this, enter sudo smbpasswd -a username at the prompt.  Use the same username you use for your Ubuntu username.  It will ask you to enter a password twice.  It can be the same as your Ubuntu password, or different.  Different would be more secure, of course.

Now open your smb.conf file.  sudo gedit  /etc/samba/smb.conf

The file that opens is full of a lot of commented instructions that are confusing.  Don't read them.
Under edit, click on "Save As" and save the file as smb.conf.old are something like that.

Now delete everything in the file.  Yes, I said everything.

Then enter the bare minimum to get things working.

This is my smb.conf file.  It works.  The only thing you should have to change is the name of your windows workgroup.  Mine is "HOME".  Many times it is "MSHOME" as this is the windows default.  Anyway, make it whatever it's called on the windows machine.

[global]


   workgroup = HOME
   security = user
   encrypt passwords = true
   guest account = nobody

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

Save this file as /etc/samba/smb.conf

Now stop and restart Samba

sudo /etc/init.d/samba stop
 
then

sudo /etc/init.d/samba start

If you want to access files in your home directory from your windows machine, go to your home directory and select the folders you want to share.  Change the permissions to allow access and read write as you see fit.  Then right click on the folder and click on share folder.  Enter your password, then select Windows Network (SMB) from the pull down menu.  Click OK.

If you go back and look at your smb.conf file now, you will see that this information has been automatically entered.

Go to your windows machine, and open the network browser and you should see your Ubuntu computer listed.  Open it.  It will ask for a user name and password.  Enter the SMB user name and password we created earlier.  As long as you don't reboot either machine you should stay logged in and it won't ask again for the user name and password until you reboot.

As you progress in your knowledge of Samba, you can try different settings and parameters in that smb.conf file.  But this one should get you up and running.

Floyd

---

### Post by jingo811 on 2007-03-02
> Samba is not as complicated as it appears. I think what throws people off, is they don't think of Samba for what it is, a separate server........
Nah that wasn't the first thing I thought of when trying to SAMBA.  It's the infinite amount of ways to solve the same thing that throws me off.  Right now I haven't been able to follow just one guide/tutorial/thread to do what I need, I'm picking bit and pieces from different tutorials all the time.  Even at this stage :( 

So like I already managed to share files in previous attempts by logging in with my Linux login/pass account on the Win XP machine.  But I consider that a risk by logging in with your root login/pass on some other machine, especially Windows, there might be keyloggers in there that I haven't found yet.

**This is what I want to do:  I want to add the Win XP user into my Ubuntu Share PC but making it so that he can choose a different password compared to his regular login/pass when he starts Windows.**

---

### Post by dannyboy79 on 2007-03-02
> **jingo811 said:**
>   by logging in with my Linux login/pass account on the Win XP machine. But I consider that a risk by logging in with your root login/pass on some other machine, especially Windows......

the only way you could possibly do this is if you had that user (ubuntu user as you stated)already defined on winxp or if you were using active directory authentification, I think? so I am not sure what you mean here. I wouldn't suggest logging into ubuntu using your root account ever. It's better to use sudo.

> **jingo811 said:**
>  
**This is what I want to do:  I want to add the Win XP user into my Ubuntu Share PC but making it so that he can choose a different password compared to his regular login/pass when he starts Windows.** 
You can map windows users to ubuntu users using username.map file within your smb.conf, so you don't need to create anymore users on ubuntu if you don't want. also, your samba password IS different than your normal password already. your normal password is controlled by ```
sudo passwd user
```
if you want to change your samba password you would do ```
sudo smbpasswd user
```.

---

### Post by steve101101 on 2007-03-02
here is a good walkthrough specific to Ubuntu

[http://ubuntuforums.org/showthread.php?t=202605&highlight=set+up+samba+peer-to-peer]("Samba HOW TO")

---

### Post by dannyboy79 on 2007-03-02
> **steve101101 said:**
> here is a good walkthrough specific to Ubuntu

[http://ubuntuforums.org/showthread.php?t=202605&highlight=set+up+samba+peer-to-peer]("Samba HOW TO")


your link is broken and I have already posted that back in my first post.

---

### Post by jingo811 on 2007-03-02
That tutorial was for static routers I'm using DHCP so I couldn't implement all the suggested steps.  But there was some good security stuff I could implement into my smb.conf file.
> 
You can map windows users to ubuntu users using username.map file within your smb.conf, so you don't need to create anymore users on ubuntu if you don't want. also, your samba password IS different than your normal password already. your normal password is controlled by  I didn't know how to use your username.map file suggestion so I followed your tutorial's section describing how to add users manually.
```

sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark
```
But how can I check which users I have registered in the SAMBA database thingy?
Now that I have removed the smbusers file that your tutorial didn't bring up?
I created smbusers file from a previous tutorial which didn't do much......:)

---

### Post by jingo811 on 2007-03-02
I think the above trick enabled my Win XP user to access my Ubuntu shares.  At least I can browse and listen to some mp3s, but there are some folders where I can't even open up text files and jpg's.  Must be some permissions settings that are whack!
[IMG]http://i2.tinypic.com/48n9dgn.jpg[/IMG]
How can I know what permission category my WIn XP user belong to,
and how do I make my newly created Win XP user on SAMBA belong to OWNER, GROUP or OTHERS?  

What does this do in the smb.conf file?
```

force user = stormbringer
force group = stormbringer
```
Is that the same as the below which I got from some other tutorial?
```
write list = mike, einstein
```

---

### Post by dannyboy79 on 2007-03-02
for 1 thing all you had to do was do man smb.conf and you can read about every smb.conf option that exists and the username.map option is really easy. as far as the smbpasswd database it depends, are you using the default passwd database, which is smbpasswd or are you using the passwd.tbd. Per the man pages for smb.conf:
smbpasswd - The default smbpasswd backend. Takes a path to
                 the smbpasswd file as an optional argument.

tdbsam - The TDB based password storage backend.  Takes  a
                 path  to  the  TDB  as  an  optional argument (defaults to
                 passdb.tdb in the private dir directory.

so if you want to know who you added to the samba passwd file you can do a sudo cat /etc/samba/private/passdb.tbd (note: if it's not located here, you'll have to search for it because I don't use it so I can't tell you where it is other than what the smb.conf man pages states, I use smbpasswd file. i read that the smbpasswd database isn't as secure) or /etc/samba/smbpasswd and you should see usernames in the begining of each line followed by their user id but the password is encrypted.

here is my smb.conf file.
NOTE: anything that has a pound symbol is not used, i left there so I knew it didn't work when I tried it.

[global]
    netbios name = UBUNTU
    server string = Dans Linux Desktop
    workgroup = LINUX
    encrypt passwords = yes
#    guest ok = yes
    smb passwd file = /etc/samba/smbpasswd
    domain master = yes
    local master = yes
    preferred master = yes
    os level = 99
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 $#   passdb backend = tdbsam
    null passwords = true
    username map = /etc/samba/username.map
#   name resolve order = wins lmhosts host bcast
    hosts allow = 127.0.0.1 127.0.1.1 192.168. EXCEPT 192.168.0.20
    hosts deny = 0.0.0.0/0
#   hostname lookups = yes
#   hosts equiv = /etc/samba/lmhosts
#   map to guest = Bad User
#   guest account = nobody
#   wins support = yes
#   smb ports = 139
    browse list = yes
    mangled names = yes
    default case = lower
    case sensitive = no
    preserve case = yes
    short preserve case = yes

#global logging
    syslog = 1
    syslog only = yes

#global printing settings
    printing = CUPS
    printcap name = CUPS

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
wins support = no

[homes]
    valid users = xxxxxx root
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    ;veto files = /*.{*}/.*/mail/bin/

---

### Post by dannyboy79 on 2007-03-02
> **jingo811 said:**
> I think the above trick enabled my Win XP user to access my Ubuntu shares.  At least I can browse and listen to some mp3s, but there are some folders where I can't even open up text files and jpg's.  Must be some permissions settings that are whack!

How can I know what permission category my WIn XP user belong to,
and how do I make my newly created Win XP user on SAMBA belong to OWNER, GROUP or OTHERS?  

What does this do in the smb.conf file?
```

force user = stormbringer
force group = stormbringer
```
Is that the same as the below which I got from some other tutorial?
```
write list = mike, einstein
```

the force user and force group will force the user who is accessing the share basically be viewed as the user and group that you set this option to. this is NOT the same as the write list. you can find out what groups your user belongs to by typing ```
groups username 
``` you;re making this too hard, if you want your winxp user to be the same as your ubuntu user, than you needed to just map the winxp username to the username you want him to be in ubuntu and samba. for any options you want to know about, read the man page for smb.conf

---

### Post by jingo811 on 2007-03-03
> man smb.conf I'm afraid of Linux terminal manuals, it's so technical written I'm having trouble following them and seeing the overall perspective :confused: ....but I'll try.

> you;re making this too hard, if you want your winxp user to be the same as your ubuntu user, than you needed to just map the winxp username to the username you want him to be in ubuntu and samba. for any options you want to know about, read the man page for smb.confThe thing is I don't want WinXP username to have the same permission as my Ubuntu user, I want WinXP to be a low level permission user....I'll try to look for it in the man, but I doubt I'll understand it.

---

### Post by jingo811 on 2007-03-03
Hmm...maybe the things I want to manage would be easier if I used a GUI type SAMBA.
Is there any that you can recommend?  I'm really bad at reading technical manuals and troubleshooting things that way.
[http://us3.samba.org/samba/GUI/](http://us3.samba.org/samba/GUI/)

Never mind the GUI swat I was recommended seemed like a hassle to learn, so I'm back at manually editing smb.con file.  And I'm starting to understand what the man smb.con are saying :-)

---

### Post by dannyboy79 on 2007-03-03
> **jingo811 said:**
> I'm afraid of Linux terminal manuals, it's so technical written I'm having trouble following them and seeing the overall perspective :confused: ....but I'll try.

The thing is I don't want WinXP username to have the same permission as my Ubuntu user, I want WinXP to be a low level permission user....I'll try to look for it in the man, but I doubt I'll understand it.

i agree some of the man pages are very technical but I just starting reading the smb.conf and it rreally isn't that hard to follow. you simply scroll down to the option you want to learn about and read it. It makes sense after you read it.

As far as wanting your winxp user to have low level permissions, you;'re looking at it al;l wrong. It's not like you're opening up your entire box just for a samba service. you need to think of a share as a service. so if you don't want t a user to have access to it, then exclude him from it with an smb.conf option. I think there may be a users option or something like that. you can make shares read only etc etc. BUT you are right about not mapping the winxp user to your ubuntu user IF you don't want that user to have access to the shares that YOU have access to. almost the easiest thing to do if you just want most people to have read access you can add an option that will map a bad user (some1 who isn't in the samba username and password database) to a guest. that way they'll only have rewad access to the services (shares or printers) of that samba server. which copmputer in your network is your local master browser? turn on all your compouters and type in findsmb. does it return anything? it should return your local mastewr browser. this is what is used to set the ip address to the netbios names (i think, i could be wrong.)  good luck. i have plenty of machines on my samba network BUT I  am the onyl user so thats why it might be easier for me to setup. i just made sure all usernames and password on all my computer were the same and wala, it works. and for my roommate, if I want to let her access my shares, I just enable the map bad user to guest which then lets her have guest access, which is read only.

---

### Post by jingo811 on 2007-03-03
tnx I experimented a little on my own and I think I got a handle on the basic stuff now.

---

### Post by craftbrewer on 2007-03-03
Spent the last two freakin' days trying to see my ubuntu server samba share from my ubuntu desktops to absolutely no avail.   I had tried every howto google offered me and still I could not see this share.

After trying the barebones method in this thread, restarting samba yet again and retrying the connection from my desktop again without success, I grabbed a beer and headed down to the basement to blow off some steam and bash some chords on my guitar.

An hour later and as I sit down I click 'Reload' on nautilus just for shits'n'giggles.  Lo and behold there's my share!  I don't know whether its the client or the server, but this is not something I recall dealing with in the past in setting up samba. 

Just thought I'd share this tale of impatience in case others may be having problems because they expect to see their changes to the server take effect immediately on the client side.

(why is it the faster computers get the more time I spend waiting on them?)

---

### Post by LucasLinard on 2007-03-07
Man your post it really good
it solved most of my samba problems in one minute!
do your know how can I share my printer with a windows comuter???

---

### Post by jingo811 on 2007-03-07
I made an alternate tutorial on how to install SAMBA with DHCP contrary to that STATIC ip tutorial that was suggested :KS It took 6 pages in Open Office.
Now I need to learn how to make a website and setup the tutorial the way I want it :)

> do your know how can I share my printer with a windows comuter???
I dunno how, I prefer using:
System > Admin > _Printing_
Add printer > Network Printer > _LPD_
then probably type the ip in HOST.  Where my router were connected to the printer port.

(UNIX) Line Printer Daemon, worked under Windows XP so I just continued using that trick when I switched to Linux.
.....
.....sorry now I understand your question, you should lookit up in your router manual about how to install (UNIX) LPD/LPR printing drivers for Windows it's easy peasy!

---

### Post by gutterballk7 on 2007-04-24
I was following the Samba tutorial and it made sense, but every time I try to go to /etc/init.d/samba start it says that the file doesn't exist. How can I remedy this? Thanks.

Edit: nevermind, the server went crazy (user error?) and samba wasn't really installed, though the samba software existed. I dunno, but it works now.

---

### Post by BLTicklemonster on 2007-12-01
I've been trying for two years, and I still have window xp boxes that can't connect to me. (read: none of them can)

they can see me fine, but they can't connect.

I set a password, but it doesn't work when I go to a windows machine and try to log on.

Two years.

---

