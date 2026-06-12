---
title: "How to create an FTP/SSH server (for dummies)?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Bou on 2007-05-19
Hi, I'd like to create an FTP or SSH server to share some folders over the Internet with some friends of mine. The thing is, I have ABSOLUTELY no idea how to make that. I don't know how to set up the shared folders, or how to get an address, or even what programs to use.

Could you guys give me some basic advice (think you are explaining it to your granny or a 3-year-old) or point me to a similar guide?

Thanks in advance.

---

### Post by Najand on 2007-05-19
Check: 
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Bou on 2007-05-19
Thanks, but I can't see anything there about creating an SSH server. What's the part you refer to?

---

### Post by chamberlain2006 on 2007-05-19
FTP would probably be easier, I use Proftpd, which requires little configuration for a base install.

---

### Post by Najand on 2007-05-19
Sorry I sent you a wrong link. The Server one is:
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by Bou on 2007-05-19
Well, I've given gproftp a try but I don't have a clue what 95% of the options it gives even mean.

Let's suppose I want to share ~/videos to anyone on the Internet, with only read permissions; what's the simplest way to get it running?

---

### Post by rich.bradshaw on 2007-05-19
For ssh:
```

sudo apt-get install openssh-server
```

now you have an ssh server. To test, 

```
ssh localhost
```

on that computer, you should get a login prompt and can log in. Type exit to logout again.

Other computers on your LAN should now be able to SSH in. Windows tools WinSCP and Putty are useful here.

If all that works, you probably want to set it up so you can access your server from anywhere on the internet. If you have a router, in it's set up, forward port 22 to your PC. That's it.

See how you get on with that!

You might want to 

```
sudo apt-get install fail2ban
```

so that people who get the password wrong 5 times get banned for 5 mins, this is a good idea as you will get random people trying to guess the password all the time!

---

### Post by Bou on 2007-05-19
> **rich.bradshaw said:**
> now you have an ssh server.

I think we'd better leave SSH aside for the time being, since I'm totally lost about it. Can an FTP server provide an easy way to share a specific folder over the internet? Cause that's everything I need.

---

### Post by chamberlain2006 on 2007-05-19
Here's a link: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server)

---

### Post by chamberlain2006 on 2007-05-19
You should have a look at the " How to map anonymous FTP user to folders outside /home/ftp/" section.

---

### Post by Bou on 2007-05-19
> **chamberlain2006 said:**
> Here's a link: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server)

So, I'd just have to install proftpd and add this:

> <Anonymous /home/david/videos/>
 User            ftp
 Group            nogroup
 UserAlias          anonymous ftp
 DirFakeUser on ftp
 DirFakeGroup on ftp
 RequireValidShell      off
 MaxClients         10
 DisplayLogin        welcome.msg
 DisplayFirstChdir      .message
 <Directory *>
  <Limit WRITE>
   DenyAll
  </Limit>
 </Directory>
</Anonymous>

and type sudo /etc/init.d/proftpd restart, right?

The problem is, then I get this:

> * Starting ftp server proftpd
- IPv6 getaddrinfo 'david-laptop' error: No address associated with hostname

What's wrong there? How can I solve it?

---

### Post by xpod on 2007-05-19
I`d second the vote for "ssh" i think.

I`m no expert either Bou but setting it up was really easy.(wether I`VE set it up correctly is another mater mabey):)
My sons machine is on a completely seperate internet connection to our main one so all i had to do was install the ssh server on his machine then i can use "connect to server" from the menus on mine and just pop in his ip address etc.....or from the terminal "ssh son@ip address".Both ask for his password of course and i`m in:).
I also used firestarter on his machine to allow access from mine only.

As i said i really dont know much about this kinda stuff but it is more secure from what i understand.
My son would mabey disagree mind you:twisted:

---

### Post by Bou on 2007-05-19
No doubt, but I'm so clueless right now that I just wanna go for the simplest thing possible and ftp is already halfway there, I think.

Besides, I don't want my friends to access "my computer", I want them to access one single folder in it.

---

### Post by Acglaphotis on 2007-05-19
Pure-ftpd rocks! i use it to connect to my vm and it works great. just do a :

```
sudo aptitude install pure-ftpd
```

then run

```
pure-ftpd
```

Its that easy.

-Acgla

---

### Post by Bou on 2007-05-19
> **Acglaphotis said:**
> Pure-ftpd rocks! i use it to connect to my vm and it works great. just do a :

```
sudo aptitude install pure-ftpd
```

then run

```
pure-ftpd
```

Its that easy.

-Acgla

So, how do I configure the folder I want to share?

---

### Post by Acglaphotis on 2007-05-19
The folder is /home/ftp. You can change that but i dont know how. But you can just move/copy the files there.

-Acgla

---

### Post by Bou on 2007-05-19
> **Acglaphotis said:**
> The folder is /home/ftp. You can change that but i dont know how. But you can just move/copy the files there.

Hm... No, I want to share one of my folders, forget about it and just let my friends copy stuff from it as I add it.

Kind of like a samba share, but not over the same LAN.

---

### Post by xpod on 2007-05-19
> No doubt, but I'm so clueless right now that I just wanna go for the simplest thing possible and ftp is already halfway there, I think.

Besides, I don't want my friends to access "my computer", I want them to access one single folder in it.
Reply With Quote

Your probably right if your halfway there with ftp i suppose.
Of course,with ssh you would also only allow access to any  folders you wanted accessed on your computer and not the whole pc:)

Good luck with whatever your trying anyway

---

### Post by Acglaphotis on 2007-05-19
Maybe you can create a link from the folder at /home/ftp to the folder you wanna share

-Acgla

---

### Post by rich.bradshaw on 2007-05-19
In Kubuntu there is an applet that sets up a webserver, you just drag files you want to share to it, and it works.

Very simple. Maybe there is something like that for Ubuntu?

You could just use apache...

sudo apt-get install apache2

then anything in /var/www is shared. Read only though.

---

### Post by Bou on 2007-05-19
> **rich.bradshaw said:**
> You could just use apache...

sudo apt-get install apache2

Thanks, but I'd rather explore the options I have now before considering any new ones. I'm trying pure-ftpd; so... sudo aptitude'd install pure-ftpd, then sudo pure-ftpd.

I got: Unable to start a standalone server: Address already in use

Does that mean the server is already working? If so, how can I find out its address and access it myself?

---

### Post by rich.bradshaw on 2007-05-19
I had a look at pure-ftpd for you, you can chroot people into only their home, so you could make  a user called say ftp, then the users can only access things in that folder.

If you want that, 

sudo apt-get pure-ftpd

then

cd /etc/pure-ftpd/conf
sudo touch ChrootEveryone
sudo nano ChrootEveryone

type yes in the file and save. Control O, Control X.

sudo pure-ftpd-control restart  

Now users only can see their home directory. If you make a user using the GUI in admin menu then that will work.

use

ftp localhost 

to check it works.

---

### Post by rich.bradshaw on 2007-05-19
Yeah I had that, it's already running.... Confusing message isn't it!

---

### Post by Bou on 2007-05-19
> **rich.bradshaw said:**
> Yeah I had that, it's already running.... Confusing message isn't it!

It is indeed. So, how do I find out the server's address? Do I need my public  IP address? That and the port?

---

### Post by rich.bradshaw on 2007-05-19
Port for FTP is 21.

If you want to find your external IP go to [http://whatsmyip.org/](http://whatsmyip.org/), if you type ftp then that IP e.g.

ftp IPADDRESS

and it works, then you are offically a server on the internet!

If not, you need to forward 21 on your router (if you have one...)

---

### Post by rich.bradshaw on 2007-05-19
In case you didn't realise, the username and password, willl be same as your normal one - it uses normal user accounts.

I'm just going to make some orange juice, be back in a bit!

---

### Post by Bou on 2007-05-19
Hm, I think I'm starting to get it, thanks man. 

Seems that I'm in fact on the Internet!

> david@david-laptop:~$ ftp 84.126.254.xx
Connected to 84.126.254.xx.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 18:19. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.

But for some reason I cannot connect graphically:

[IMG]http://img525.imageshack.us/img525/4164/pantallazoconectarconeldl5.png[/IMG]

[IMG]http://img237.imageshack.us/img237/7787/pantallazonautilusconnett2.png[/IMG]

I don't think I'm doing anything wrong there, am I?

---

### Post by rich.bradshaw on 2007-05-19
You aren't allowed anonymous login, as you saw from the text based login welcome message.

You should specify a port (21) and a user (your username) in the graphical login. That should work. Alternatively you can type

[ftp://YOURUSERNAME@YOURIPADDRESS](ftp://YOURUSERNAME@YOURIPADDRESS) 

in the address bar in Nautilus, this way you don't have to save the location.

---

### Post by Bou on 2007-05-19
> **rich.bradshaw said:**
> You aren't allowed anonymous login, as you saw from the text based login welcome message.

You should specify a port (21) and a user (your username) in the graphical login. That should work. Alternatively you can type

[ftp://YOURUSERNAME@YOURIPADDRESS](ftp://YOURUSERNAME@YOURIPADDRESS) 

in the address bar in Nautilus, this way you don't have to save the location.

Alright, it worked! ^^ That was so simple.

The only thing is, it opened my / folder instead of /home/ftp for some reason. Any file that I can edit to fix that?




Also, as a curiosity, seems that entering the port is not necessary.

---

### Post by kh4nh on 2007-05-19
have you tried **[_ftpd_]("http://packages.ubuntu.com/warty/net/ftpd")** yet.

---

### Post by rich.bradshaw on 2007-05-19
Port 21 is the standard one for FTP so it will assume that anyway.

Were you really in /, or did it just think that?

Did you add the ChrootEveryone file I mentioned earlier and restart the server?

If you do that, it Chroots (CHanges the root) to /home/user where user is the user you log in as to /, this means you can't go back into the file system.

I would recommend doing that, as it will make it easier for you.

---

### Post by rich.bradshaw on 2007-05-19
I gotta go now for a bit,

if you have that working, register for free at [www.dyndns.org](www.dyndns.org), and get a name linked with your IP.

If you go here [http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/) and make an account, you can link a name so that you can just tell people that instead of an IP. 

If your IP always changes, you can apt-get install ddclient, which let's you update the IP at that site automatically. I can't remember how to set ddclient up, but you can look in this forum as you know, and I'm sure it's been mentioned more than a few times.

Good Luck!

---

### Post by Bou on 2007-05-19
Not really, I'm gonna try:

> **rich.bradshaw said:**
> then

cd /etc/pure-ftpd/conf
sudo touch ChrootEveryone
sudo nano ChrootEveryone

type yes in the file and save. Control O, Control X.

sudo pure-ftpd-control restart  

david@david-laptop:/etc/pure-ftpd/conf$ sudo pure-ftpd-control restart 
Restarting ftp server: /usr/sbin/pure-ftpd-wrapper: Invalid configuration file /etc/pure-ftpd/conf/ChrootEveryone~: No corresponding directive

and even if I delete /etc/pure-ftpd/conf/ChrootEveryone I still get the same error!

---

### Post by rich.bradshaw on 2007-05-19
so you have a ChrootEveryone file, with just the word "yes" in it, nothing else, no speechmarks or anything?

That should work...

I did that on mine, and it works fine... maybe you should try again?

when you have made the file, read it out using cat and check that it just has yes in it.

If you do ls -l in that directory (/etc/pure-ftpd/conf) then they should all have same permissions.

---

### Post by Bou on 2007-05-19
I found the problem :)

> -rw-r--r-- 1 root root 36 2007-05-19 16:51 AltLog
-rw-r--r-- 1 root root  4 2007-05-19 21:20 ChrootEveryone
-rw-r--r-- 1 root root  0 2007-05-19 21:19 ChrootEveryone~
-rw-r--r-- 1 root root  5 2007-05-19 16:51 MinUID
-rw-r--r-- 1 root root  4 2007-05-19 16:51 NoAnonymous
-rw-r--r-- 1 root root  4 2007-05-19 16:51 PAMAuthentication
-rw-r--r-- 1 root root 28 2007-05-19 16:51 PureDB
-rw-r--r-- 1 root root  3 2007-05-19 16:51 UnixAuthentication


See that ChrootEveryone~ file? That was causing it.


So, anyone can login to /home/invitado now, and copy or paste stuff. Is there any way that people can access /home/david/videos too?

---

### Post by rich.bradshaw on 2007-05-19
You could try symlinking it into that dir. Make a symlink from a videos file in that dir to the directory you want:

ln -s /home/invitado/videos /home/david/videos


you might have to sudo that, try it without first though.

and see if the ftp server resolves the link. If it doesn't you need to find out how to make pure-ftpd follow symlinks. It probably will do it automatically though...

---

### Post by ryanVickers on 2007-05-23
Thanks, all of this has been really helpful.  I'm trying to get some way to be able to network in to my computer from others on the LAN, and hopefully anywhere in the world eventually.

A few question though.  How would you...
1. Turn off/toggle the ability, or possibly just change the password for, the sharing through the SSH?
2. Choose permissions for certain folders (like read and/or write on/off)
3. Change the root folder like you said earlier (just so you know, I'm using the ssh, not ftp)

---

### Post by Bou on 2007-05-24
> **ryanVickers said:**
> A few question though.  How would you...
1. Turn off/toggle the ability, or possibly just change the password for, the sharing through the SSH?
2. Choose permissions for certain folders (like read and/or write on/off)
3. Change the root folder like you said earlier (just so you know, I'm using the ssh, not ftp)

After a lot of fiddling I managed to do all of that using Gproftpd; It's too complex for a gnome app, true: but also quite complete, and it lets you do everything you asked for. Just get your server working in the "server" section,  then you can set up the password, permissions and root folder in the users sections.

Thanks a LOT to rich, because I could have never got it working without his help; the man had lots of patience with me, and that's unusual today.

---

### Post by AZzKikR on 2007-05-24
Did you manage to get SSH working yet though?

---

### Post by ryanVickers on 2007-05-24
Yes, I got the SSH working *perfectly quite easy actually.  First try and every thing was great.  *A little too good though, and that gproftpd thing looks like it would provide excellent customizability, but for now, and I guess now that I look back I didn't make this very clear, but I'm using the SSH sharing and would like to know if there is something like that package for *it*?

I have another discussion about this continued [here]("http://ubuntuforums.org/showthread.php?t=454615").

---

### Post by Bou on 2007-06-23
Hey, just in case someone with the same doubts checks this thread - I recommend using [PureAdmin]("http://purify.sourceforge.net/index.php?page=about"), very complete and MUCH easier to use than Gproftd (easier to pronounce, too).

---

