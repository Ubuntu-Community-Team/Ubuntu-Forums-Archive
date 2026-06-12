---
title: "How do I configure apache so that I can use it on my lan but not be open to the net?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-07-30
I eventually want to use my Ubuntu machine as a web server on the internet. But for now, I want to access on my LAN and not have it available to the internet. 

I want to set up my web site and make sure all is working before I open it up to the web. 

So, how do I configure apache to do this?

---

### Post by Maxtorm on 2007-07-30
Here is a good page describing the changes you need to make to httpd.conf: [http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/](http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/)

However, if you have a LAN, would it not be better to lock down access at your point of connection to the Internet (i.e. the router)?

---

### Post by rich.bradshaw on 2007-07-30
I just don't forward port 80 on router as mentioned above.

Easy, and you know you haven't unwittingly broken anything else!

---

### Post by rsnow on 2007-07-30
Hmmm.....maybe I'm in over my head trying to do something like this while still such a noob.

I read and try to follow the instructions but do not seem to be able to get the expected results.

Of course it could also be that I have something screwed up already and that is why things don't work right. So, let me ask this question....if I uninstall say apached and/or samba and then reinstall them would that fix any bad settings I may induced?

---

### Post by p_quarles on 2007-07-30
What are the results you were expecting and what results are you getting? The more details, the more people can help.

A really easy test to run to find out if your router is blocking requests to your web page: Find out what your IP address is (your public one, not the LAN address; there are plenty of web sites you can go to for this info quickly); then, type that address in your browser, followed by a "/" and the name of a file in your web server's document directory.

This will send your http request outside of your local connection, and will be rerouted back to you through the address assigned to you by your ISP. If the file doesn't show up (usually it times out, or keeps trying to load the page indefinitely), then your page is invisible to the world outside your LAN.

If it does show up, you need to change the settings on your router.

---

### Post by rsnow on 2007-07-30
Here's an example: Apparently the person writing the instructions was using  something other than Ubuntu because the instructions were to type (as root) [I]/etc/httpd/conf/httpd.conf[I] and then look for the line containing 'ServerName [www.example.com:80](www.example.com:80)'.

When I type that line I get [B]No such file or directory[B]

The reason for trying to find the line mentioned above is because I am supposed to uncomment it and then change it to 'ServerName (my IP address):80. This is supposed to make the web server available to my LAN.[/B][/B][/I][/I]

---

### Post by p_quarles on 2007-07-30
Yep, you're exactly right. The Debian/Ubuntu version of Apache uses different filenames. 

The file you're looking for is:
/etc/apache2/apache2.conf

---

### Post by rsnow on 2007-07-30
Thank You. I was able to find the file using your info. I was also able to find out the line ServerName [www.example.com:80](www.example.com:80) does not exist in that file. So now, I am thinking that maybe I should quit referring to this book I have and try to find proper documentation for what I am using.

---

### Post by p_quarles on 2007-07-30
Yeah, I know what you're saying, but unfortunately there's not enough documentation out there for the Debian/Ubuntu version of Apache. This very same problem led me to reinstall Apache from the source code.

That said, I'm fairly certain that what you want to do is actually the default in your setup. 

You can doublecheck this by looking for all the lines in apache2.conf that begin with "include." The file name in the rest of that line is additional configuration info that is loaded into the the Apache setup. I can't remember which one has the "Listen" command (if I did, I would've have mentioned it in the last post), but by digging you should be able to find it. 

The other way of doublechecking is to run the test I mentioned in my first post in this thread; you could even have a friend try to access the site. If they can't, then your router is configured to block requests on port 80.

---

### Post by rsnow on 2007-07-31
O.K. you said look for all the lines in apache2.conf that begin with "include".  Here is what I found:

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf 
Include /etc/apache2/ports.conf
Include /etc/apache2/conf.d

I then checked httpd.conf and there was nothing in it.
I then checked ports.conf and Listen 80 was in it.

I also copied most of the lines that were uncommented but didn't know if they would be of any help. If you would like to see them, I will post them.

---

### Post by p_quarles on 2007-07-31
That's right, it's in ports.conf. 

Now, just change ```
Listen 80
```
to ```
Listen xx.xx.xx.xx:80
```
where the 'x's are the machine's internal IP address. This way, it will only listen to requests made using the local address. To keep it out of public view, you just need to make sure your router is not configured to forward requests to that machine (and unless you configured it manually, it's not).

---

### Post by rsnow on 2007-07-31
I made the change in /etc/apache2/ports.conf to read "Listen 192.168.1.102:80".

when I type that address into my browser I get a page that says:
Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 14:16 	-
Apache/2.2.3 (Ubuntu) Server at 192.168.1.102 Port 80

Now another question has come up. Before I started messing with this, I was able to see the other computers on my LAN. Now when I try, nothing happens. When I go to the network tools and do a lookup I get something referring to prisoner.iana.org.hostmaster for each of the other computers. 

When I do a Whois I get the following:

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    IANA-CBLK1
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    
RegDate:    1994-03-15
Updated:    2002-09-16

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

# ARIN WHOIS database, last updated 2007-07-30 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

Did I cause this or should I ask what/who caused this? What can I do about it?

---

### Post by p_quarles on 2007-07-31
Do you have an index.html file in /var/www ? If you do, then I really don't understand why it's not showing up when you point to the host. 

Changing ports.conf in Apache doesn't change any other LAN settings, just the Apache server. When you say you don't "see" the other devices on the LAN, what do you mean? Are you using a network browser, your router, or what? Is the network setup with NFS or Samba? 

As for the IANA page, that's just a default readout. IANA is the organization that reserved IP numbers like 192.x.x.x., 172.x.x.x and 10.x.x.x for internal networking use. If you want to see what your public "whois" profile looks like, you need to use your public IP address number.

---

### Post by rsnow on 2007-07-31
When I said I could not see the other computers I was talking about using Places>Network and clicking on the Windows Network icon. Also, I failed to tell that I had installed the Firestarter firewall. 

I am thinking at this point that it might be better for me to uninstall Firestarter, Apache and Samba and then start over.  That way I can work out one problem at a time. Do you think that will be helpful or should I just start from scratch and reinstall 7.04?

---

### Post by p_quarles on 2007-07-31
So you're network is Samba. To be quite frank, I've found it's a lot easier to connect to Samba folders from Windows than it is from Linux.  You can always try manually retyping the LAN IP into the connection dialogue. That works for me whenever I find that a shared folder has been disconnected.

While I do love Ubuntu's package management system, I've found that it's pretty bad at uninstalling stuff. If you have the time and backup media necessary to reinstall from scratch, I suggest it. I'm running Ubuntu on three separate boxes, and all of them are on their second installation. The first time through, you experiment. The second time, you have a much better idea what you're doing. That's my experience, anyway.

---

### Post by rsnow on 2007-08-01
I don't have much yet as far as data or media files. i have purposely held off on that just in case I had to do this. 

Oh, sorry I didn't answer earlier about the index.html. I do have one but it is in /var/www/apache2-default.

---

### Post by rsnow on 2007-08-01
I have just now noticed that samba and apache do a lot of the same things (according to the package descriptions) so I'm curious, is it better to just have one or the other installed instead of both?

---

### Post by p_quarles on 2007-08-01
I guess that depends on what you mean by similar . . . Samba allows you to share folders across a network, while Apache allows you to publish web pages. I currently have both installed on my home server, and have never found them to conflict with one another. 

What kind of function are you specifically looking for? Depending on what you want to do, there may be a better solution.

---

### Post by rsnow on 2007-08-01
Well, on a second look I see I was jumping to some conclusions that were not entirely accurate. (How's that for saying I failed to engage my brain before opening my mouth?)

Simply stated I guess I want to publish pages to a web site and also share folders (data) on my LAN with my Windows machines.... and learn as much as I can about using Linux so I won't be so dependent on MS.

I didn't want to switch from W2K to XP but it happened when I bought a new computer. I have drawn the line at Vista. If it comes to that, I will simply shut down my computers and find something else to do.

---

### Post by p_quarles on 2007-08-01
> I didn't want to switch from W2K to XP but it happened when I bought a new computer. I have drawn the line at Vista. If it comes to that, I will simply shut down my computers and find something else to do.
lol . . . Vista is pretty bloated. I keep it around for iTunes and a couple games, but if it weren't for that I'd be MS-free. 

Sounds like Samba and Apache are exactly what you want. Apache works really well out of the box, but Samba requires a good deal of configuration before it's fully up and running. The fact that your shared folders aren't showing up tells me it may be configured incorrectly. There are tutorials here in the forums, and on the Ubuntu wiki. 

Another application that might interest you is Webmin. It's basically an https interface to your server that allows you to do all sorts of things straight from your browser -- copy/transfer files, tweak server software, monitor resources, etc. And, because it's web-based, it's platform independent.

---

### Post by rsnow on 2007-08-01
Before I look at Webmin I'd like to put to this up and see if anything pops out at you:

As of now I can see all the windows machines when I go to Places>Network. I can access the windows desktop but not the windows laptop. I can see the linux desktop from the two windows machines but cannot access it. (Permission denied-see administrator)

With that info here is some of the settings in my smb.conf file. I tried to pick the ones that looked pertinent. I also tried reading the HOWTO-Samba3 but honestly didn't understand a lot of it.

[global]
   workgroup = HOME
   server string = %h server (Samba, Ubuntu)
   wins support = no
   wins server = w.x.y.z
   dns proxy = no
;  name resolve order = lmhosts host wins beast

####Networking####
;  interfaces = 127.0.0.0/8 eth0
;  bind interfaces only = true

######Authentication######
; security = user
   encrypt passwords = true
   obey pam restrictions = yes
;  guest account = nobody
   invalid users = root
;  unix password sync = no
; pam password change = no

##########Domains##########
; domain logons = yes
; logon path = \\%N\profiles\%U
; logon path = \\%N\%U\profile
; logon drive = H
; logon home = \\%N\%U
; logon script = logon.cmd
; add user script = /usr/sbin/adduser  --quiet  --disabled  -password-gecos""
%U

########Misc########
; include = /home/samba/etc/smb.conf.%m
; message command = /bin/sh -c'/usr/bin/linpopup %f" "%m" %5, rm &
; domain master = auto
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash

#---------------------------------Share Definitions-----------------------------
; [homes]
; comment = Home Directories
; browseable = no

; valid users = %S
; writeable = no
; create mask = 0600
; directory mask = 0700

; [netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writeable = no
; share modes = no

; [profiles]
; comment = User profiles
;path = /home/samba/profiles
; guest = no
; browseable = no
; create mask = 0600
; directory mask = 0700

wins support = no

---

### Post by p_quarles on 2007-08-01
The thing that immediately jumps out at me is that you have wins support set to "no." 

That said, instead of going through it line by line, I'll paste my smb.conf file below. Backup your current one, paste this one in, add your own network names, and restart Samba. This should give you a working setup. 

Also, I'm assuming that you have added a group and user for the Samba share, correct? If not, it might work in Windows, but not in *nix.

Anyway, here goes (I've italicized everything that needs to be personalized):
```
[global]
        workgroup = *windows network name*
        netbios name = *computer name*
        server string = %h server (Samba, Ubuntu)

        passdb backend = tdbsam
        security = user
        username map = /etc/samba/smbusers
        name resolve order = wins bcast hosts
        domain logons = yes
        preferred master = yes
        wins support = yes

        ## Use CUPS for printing

        printcap name = CUPS
        printing = CUPS

        ## Set default logon

        logon drive = N:
        #logon script = scripts/logon.bat
        logon path = \\fileserver\profile\%U

        ## User management scripts
        add user script = /usr/sbin/useradd -m %u
        delete user script = /usr/sbin/userdel -r %u
        add group script = /usr/sbin/groupadd %g
        delete group script = /usr/sbin/groupdel %g
        add user to group script = /usr/sbin/usermod -G %g %u
        add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
        idmap uid = 15000-20000
        idmap gid = 15000-20000

        ## Settings to sync Samba passwords with system passwords
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        passwd chat debug = yes
        unix password sync = yes

        ## Set the log verbosity level
        log level = 3

[homes]
        comment = Home
        valid users = %S
        read only = no
        browsable = no

[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = yes
        guest ok = yes
        browsable = no

[netlogon]
        comment = Network Logon Service
        path = /home/samba/netlogon
        admin users = Administrator
        valid users = %U
        read only = no

[profile]

        comment = User profiles
        path = /home/samba/profiles
        valid users = %U
        create mode = 0600
        directory mode = 0700
        writable = yes
        browsable = no

[public]
        comment = Public Share
        path = /home/shares/*~folder name~*
        valid users = *username*
        force group =  users
        create mask = 0660
        directory mask = 0771
        writable = yes
```


One more thing: for this to work, the user you create needs to be added to the "users" group. 

Hope this helps.

---

### Post by rsnow on 2007-08-02
No, I hadn't created another group or user. So I decided I would try that before swapping smb.conf files.

I created a group named 'languys'
I added a new user named 'lanron' , gave admin privileges and designated as 'users'.
I used the option to 'generate random password'.
When I go back and look properties for lanron it shows the option 'Set password by hand" is selected and there the black dots in both password and confirm password. ( assume these represent the password that was generated previously)

Now I can access both windows machines from the linux one. I can see linux from both windows but when I try to access linux from either windows I get "Connecting to" but it doesn't show a completed connection.

I have tried using both my regular login name and password and the lanron name and the generated password.

It looks like I'm on the verge of success but there must be some setting I have wrong or don't have. 

Oh, I did edit smb.conf and change wins support to yes.

Unless you can think of something else I need to check, I guess swapping files will be the next step.

---

### Post by rsnow on 2007-08-02
>[public]
>       comment = Public Share
>        path = /home/[COLOR="Red"]shares/~folder name~[/COLOR]
>        valid users = [COLOR="Red"]username[/COLOR]

I need a little clarification on the above. I do not have a /shares folder in my /home. I am not clear what folder name I should enter. Should it be the name of the user I created? There is a folder called lanron in  /home. It was put there when I added lanron as a user.

Would it be the same name for valid users?

---

### Post by p_quarles on 2007-08-02
Oh, I see the problem now. You haven't set permissions for the shared folder.

It can be whatever folder you want, just be sure to change the "path" setting to point to it.

Then (assuming you use the same folder you mentioned above):
```
sudo chmod 777 /home/lanron
```I had completely forgotten, too, that you need to use Samba's password setting utility:
```
sudo smbpasswd -a lanron
```You'll then be prompted to enter and verify the password you want to use with this account. 

You said you used a tutorial, but didn't find it very helpful. I'd suggest this one:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+setup](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+setup)
Lots of detail there, but once you wade through it you'll have a better understanding of how this program works.

EDIT: Btw, the fact that you can access Windows boxes remotely has nothing to do with Samba -- Samba has to be configured to share a folder on each Linux box you want available to the network. It's not the easiest way to share a folder, but it's the best way to setup and manage a filesystem that Windows machines can access.

---

### Post by rsnow on 2007-08-03
That did it! It works!! Thanks to you. Thank you for being so patient. I know sometimes you wonder if the light bulb is ever going to click on when trying to help others. I think part of the problem is having to switch out of the windows mode of thinking. As I work through these steps of learning Linux, I keep reminding myself that I had an equal amount of frustration when I first started with windows 95. 

At any rate you can blame all of this on my oldest son who kept telling I needed to learn how to use a computer. Even he didn't realize how this would come back to haunt him. He makes his living programming and I'm always bugging him about some computer problem I have. I usually cause the problems because I love to experiment. The problem with trying to get help from him is that he lives in Austin, Tx (about a 2 hour drive) and he doesn't want to fool with computers when he gets home from work. I sometimes think he wishes I would quit this computer stuff and age quietly.

Thanks again and I am going to take a break before going to next step - apache>web site.

Oh, if you ever need a damaged picture fixed up (no charge), that is my main love in computer work--that and editing home videos.

---

### Post by p_quarles on 2007-08-03
Hey, no problem. I'm relatively new to Linux myself, and I find that whenever I try to help others with things that I've done successfully, I end up understanding the whole process better (i.e., why it works). 

Linux is great for experimentation, I think. Pretty much every configuration setting is located in a human readable file, so while there are things you can do to break the system, most glitches are easy to undo.

---

