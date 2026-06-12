---
title: "SSH and FTP connect crazy slow"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by moofdaddy on 2006-09-10
Greetings,
I set my Ubuntu box as a file/web/etc server recently but I have noticed an annoying problem.  SSH and FTP connection times are incredibly slow.  When I SSH or FTP in it takes a minute or more before I get a password prompt or a connection.  

Once I am connected things are as speedy as you'd expect them to be but the connection time is slower then I have ever experienced.

I'm wondering if it is a problem with the port listening.  I don't know enough about this to really speculate but the only real thought I have is that it doesn't listen for a connection as often as it should.

Anyone have any ideas how to fix this or what the problem might be?  If I am on the right track with the listening, is it something I can fix in the config file and where would that file be located?  I believe I am using openssh and I have no idea what my ftp dameon is, I actually don't remember installing any.

---

### Post by ProjectGod on 2006-09-10
are you trying to FTP over ssh? as in SFTP? 

i've noticed that when i try put in the full SSH string the password prompt takes an age to load. e.g. 

a@b:/$ **ssh user@<ipaddr> **

however when i do the following, its pretty fast: a@b:/$**ssh <ipaddr> **

if you want to create a windows based SFTP site it's quite simple. all you need are the following tools which are free, much more secure than IIS enabled FTP site:
* [FreeSSHD]("http://freesshd.com/?ctt=download") Open SSH for windows
* [WinSCP]("http://winscp.net/eng/download.php#download2") SFTP client equivalent

Its very hard to find the server and client that works well together. most of the time you get free implementations and also commercial tools that do not work well when combined. saying this these two tools work so well together i use them on normal desktop computers whenever someone wants to host an "ftp" site. so much faster and so much more secure than normal ftp. pssss keep it a secret ;) :biggrin: 

hope this helps!

---

### Post by steve.horsley on 2006-09-10
This sounds like it may be a DNS problem. Maybe the server is trying and failing to lookup the identity of the caller using DNS IP->name. Make sure the server either gets a quick reply from a working DNS server (even if it's a lookup failure) or the caller is in the /etc/hosts file.

---

### Post by ProjectGod on 2006-09-10
Steve,

if its a dns problem wouldn't it reply with an "unknown host" message? and refuse connection? 

Moofdaddy, 

could you be more specific as to the type of network setup? is it intranet? or over the internet? dialup or broadband? behind what router? firewall? this too... however firewalls and blocked ports too will only either refuse or accept connection. 

slow connection establishment. hmmm. try and connect to another ssh server. that way you can find out whether it's your client or server that's slowing things down. although it seems its the server.

cheers.

---

### Post by steve.horsley on 2006-09-10
No,you get an "Unknown host" type message if the client tries to connect to a server ucing an unknown name. This is because the clinet doesn't know what addres to connect to.

It's different if the **server** is having DNS problems. I have seen a server accept a connection and then try several times to contact a non-responsive DNS server asking "what name is this IP addreess that's calling me?". Then when the server eventually gave up trying to resolve the caller's name, it gave the normal password prompt as though nothing odd was going on. But the delay between the incoming call and the computer issuing the password prompt was about a minute. Configuring the server with a workling DNS server made the respomse instantaneous, even though the DSN server was just replying "I don't know".

---

### Post by moofdaddy on 2006-09-10
> **ProjectGod said:**
> Steve,

if its a dns problem wouldn't it reply with an "unknown host" message? and refuse connection? 

Moofdaddy, 

could you be more specific as to the type of network setup? is it intranet? or over the internet? dialup or broadband? behind what router? firewall? this too... however firewalls and blocked ports too will only either refuse or accept connection. 

slow connection establishment. hmmm. try and connect to another ssh server. that way you can find out whether it's your client or server that's slowing things down. although it seems its the server.

cheers.


It's an intranet.  It's definetly a server issue, not client because when I connect to remote servers I get the password prompt almost immediatly.  

There shouldn't be a firewall unless linux is running a firewall that I didn't configure.

---

### Post by ProjectGod on 2006-09-11
cool! do what Steve said... it just might work! 

would be a whole lot easier if the ssh client machine has static IP... on the ssh server edit the **/etc/hosts** file. insert a new line.

**<DNS name of client> <ip address of client>**

hope that helps!

:biggrin:

---

### Post by steve.horsley on 2006-09-11
It's the other way round actually (so you can have aliases easily):

IP_adress hostname other_hostname

e.g.

1.2.3.4    thatboxthere   thatboxoverthere   yesthatone

---

