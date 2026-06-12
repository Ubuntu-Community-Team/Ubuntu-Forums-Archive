---
title: "How does FTP work ?"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-09-14
I'm interested in setting up an FTP server using proftpd. Do you need a domain or something ? How does it all work ?

Regards,
grofaz

---

### Post by frodon on 2005-09-14
If you have a dynamic IP (it change each time you turn on your computer), you can create a domain name which will always make the link to your current IP see : [http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip).
If you don't use a domain name you will need to give each time your current IP to people who want to access your FTP server.
Have you seen my [HOWTO](http://www.ubuntuforums.org/showthread.php?t=51611) about proftpd ?

Good luck  ;-)

---

### Post by grofaz on 2005-09-14
Hi frodon!

Yes I did, very helpful too. Thanks! So I don't need to have a domain name ? All I need do is provide my IP address ? Whoever wants to access my ftp would then, for example, type in my IP address in gFTP and they're good to go ? What do I enter for server name in the proftpd.conf file ?

regards,
grofaz

---

### Post by frodon on 2005-09-14
Yes you can only put your IP in gftp (with good username, pwd and port). You don't need to change anything to get a domain name, just go to the dyndns.org website an open an account and create a domain name and follow the ubuntuguide.org link above. Then your friend will enter the domain name instead of your IP, the connection will ask to dyndns.org to get your current IP therefore your friend will never have to ask you your IP again (he will use the domain name) and the crontab script will update your IP for you each hour.
For server name in proftpd.conf choose what you want, this text will appear on loggin in gftp (or in any other ftp client), it's just like a welcome message, choose something funny  ;-)

---

### Post by grofaz on 2005-09-14
Cool, thanks for the help!

Regards,
grofaz

---

### Post by grofaz on 2005-09-14
frodon,

Im still having trouble with this. I've followed your how-to and created an account at dyndns. Also followed the dyndns how-to above. However, I can't seem to be able to connect to my new site. When I try gFTP just keeps trying to connect...forever. Help!

grofaz

---

### Post by grofaz on 2005-09-15
OK...I've got everything set up where it should work, but it don't. I believe I have a static IP, not dynamic. Also I believe my network connection is configured for DHCP.
I also go through a linksys router. Do I need to adjust my proFTPD configuration differently ??

Right now, I try to connect to my server with gFTP and it finds my host name at dyndns.org, and then keeps "trying" to connect ad infinitum.

Regards,
grofaz

---

### Post by frodon on 2005-09-15
You should know that dynndns database is not updated each minute (maybe every 15 minutes) so if you have just created your account an test before the dyndns database update gftp is unable to get your correct IP (remember that it's a free account). Are you able to connect yourself to your server with your IP number ?

---

### Post by grofaz on 2005-09-15
No. This is the status message:

Cannot look up hostname xxx-xxx-xxx-xx: Name or service not known
Waiting 30 seconds until trying to connect again

I x'd out my actual IP number, but you get the gist.

And here's what I get when I use my host name through dyndns:

Looking up myhostname.dyndns.org
Trying xxx-xxx-xxx-xx-cdsl-rb1.sol.acsalaska.net:21

What's wrong ??

---

### Post by frodon on 2005-09-15
Give me your domain name and what you type exactly in gftp, maybe it's just a small problem or maybe your dyndns account is not well created.
you can use PM if you don't want people in this forum to see your domain name, up to you.

---

### Post by grofaz on 2005-09-15
Makes no difference, I can always change it if I need to.

Host: rmftp.kicks-ass.net
Port: 21

Need anything else ??

---

### Post by frodon on 2005-09-15
If you have set your server following my howto you need to add username and password. To check if your domain name link to the good IP go on the dyndns.org website then login and see what IP is linked to your domain name, then compare it to your current IP (use "ifconfig" command to see it quickly).

---

### Post by grofaz on 2005-09-15
OK Monsiuer Frodon,

When I type "ifconfig" it shows me an "inet addr:" which is the number I use to access my Linksys settings. When I access my Linksys settings it lists my "Internet IP" as the same number I get at dyndns.org. "ifconfig" also lists a "Bcast:" number which is slightly different from the "inet addr:" number.

grofaz

---

### Post by frodon on 2005-09-15
So the IP is the same on your computer and dyndns.org and you still can't access your ftpserver with the domain name. Look at the bottom of gftp when you try to login, the log will tell which address is read from dyndns.org, therefore if the IP here is the same as your current IP it's sure that the probblem don't come from dyndns.org. i'd like to be sure of that before thinking about any other problems.

Don't worry it will work  ;-)

are you french ?

---

### Post by grofaz on 2005-09-15
Yes the number at dyndns.org is the same as the number at bottom of gFTP. gFTP seems to get the host name/IP number from dyndns.org just fine. But when it tries to connect using the IP number the wheel keeps spinning round and round forever. Nothing happens, it just keeps trying to connect.

---

### Post by lao_V on 2005-09-15
I'm not sure but it could be something to do with PASV mode. You may need to disable it in your gFTP/connection settings.

---

### Post by frodon on 2005-09-15
[QUOTE=grofaz]Yes the number at dyndns.org is the same as the number at bottom of gFTP. gFTP seems to get the host name/IP number from dyndns.org just fine. But when it tries to connect using the IP number the wheel keeps spinning round and round forever. Nothing happens, it just keeps trying to connect.[/QUOTE]Do you run a firewall or a router ? Sometimes it could bring about 30seconds to connect, or something really stupid i know but have you start your server ? Because at this step gftp acts like if your FTP server don't answer to its requests, what you should search for is why your server don't answer to ftp request.

---

### Post by grofaz on 2005-09-15
I run Firestarter, but it doesn't work with the firewall on or off. I also have a Linksys router as I said before. Also I let it try to connect for several minutes but it made no difference. So I should look at gFTP site to figure out why it's not answering FTP requests ?? Actually, I can access other FTP sites with gFTP so I think it works OK in that department. I'll look at the PASV mode thing.

---

### Post by grofaz on 2005-09-15
I tried messing with different gFTP PASV settings but they had no effect. I have a strong feeling my problem has something to do with my Linksys router settings.

Who is saavy with Linksys routers ?? There's a MAC filter setting that blocks anonymous Internet requests. Could it be...??? I have no idea what a MAC filter is.

grofaz

---

### Post by frodon on 2005-09-15
I think the problem come from your router, because i also run firestarter and it don't block access if you try to connect yourself, but for external access you might need to open the port or allow the IP of your friend.
You should also read this [HOWTO](http://www.ubuntuforums.org/showthread.php?t=39566&highlight=proftpd+nat).
Also check if you can access the server using directly your IP instead of your domain name.

---

### Post by grofaz on 2005-09-15
frodon,

This HOW-TO looks promising. But before I try it I have one question. I removed proFTP and I need to reinstall a fresh copy. My question is should I run proFTP STANDALONE or INETD ?? I noticed that even though I typed at the command line: "sudo /etc/init.d/proftpd stop" that at shut down ubuntu still lists proFTPD deamon as running!? That bugs me. I don't want the thing constantly running in the background. How do you properly stop the server ?

grofaz

---

### Post by ds[de] on 2005-09-15
This might be a dumb answer, but wouldn't it be easy and sufficient to just kill the proftpd daemon process after typing "sudo /etc/init.d/proftpd stop"?

$ ps -e | grep proftpd (or whatever the daemon is listed as), then
"kill *PID*".

Or would that cause any inconviniences?

Regards,
ds[de]

---

### Post by frodon on 2005-09-15
[QUOTE=grofaz]frodon,

This HOW-TO looks promising. But before I try it I have one question. I removed proFTP and I need to reinstall a fresh copy. My question is should I run proFTP STANDALONE or INETD ?? I noticed that even though I typed at the command line: "sudo /etc/init.d/proftpd stop" that at shut down ubuntu still lists proFTPD deamon as running!? That bugs me. I don't want the thing constantly running in the background. How do you properly stop the server ?

grofaz[/QUOTE]You should run it as standalone server, see proftpd website for more informations.
If the daemon isn't stop with the "sudo /etc/init.d/proftpd stop" it sound like a bug, i never got this behaviour.
Also you should know that ubuntu run all the services on startup (firestarter, samba, proftpd, ...).
I'm still working with the help of some ubuntu users on small useful scripts to handle that in a easiest way.

---

### Post by grofaz on 2005-09-16
frodon,

I give up on this for the time being, I have too many projects going at the moment. But I want to thank you for all your help. I'll try again when I'm not so busy. :)

Regards,
grofaz

---

