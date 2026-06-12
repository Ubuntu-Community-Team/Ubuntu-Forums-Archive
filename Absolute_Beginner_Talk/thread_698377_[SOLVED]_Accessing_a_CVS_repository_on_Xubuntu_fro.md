---
title: "[SOLVED] Accessing a CVS repository on Xubuntu from WinXP"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by PapaGuru on 2008-02-16
L.S.,

I've created a CVS repository on my Xubuntu machine (loosely basing my steps on [_[COLOR="DarkOrange"]this guide for Red Hat 6.1[/COLOR]_]("http://www.taursys.com/howto/cvs/")), which I'd like to access from NetBeans 6.0.1, which I'm running on WinXP. Unfortunately, NetBeans reports "Cannot connect to: 192.168.1.106". I can't figure out where things have gone wrong, and I appreciate any help.

My exact steps were:
I installed CVS:
```
sudo apt-get install cvs
```
Then, via applications>system>users and groups, I created a user "cvsuser" and a group "cvsusers". I added cvsuser, root and my personal account to the group cvsusers.
I created a directory that is to serve as repository, and gave the ownership to user cvsuser and group cvsusers:
```
sudo mkdir /rep
sudo chown –R cvsuser:cvsusers /rep
```
So far, so good (I guess).
Now, I made sure that a cvspserver was defined in /etc/services:
```
sudo mousepad /etc/services
```
It should contain a line like this:
```
cvspserver 2401/tcp #CVS Pserver
```
This exact line was already present, so I didn't change the file. As far as I understand it, this means that there is a service called cvspserver, using the TCP protocol, running on port 2401.
Having a service is one thing, having it running another. So edited /etc/inted.conf:
```
sudo mousepad /etc/inetd.conf
```
and added the following lines:
```
#
# CVS PServer
#
cvspserver stream tcp nowait cvs /usr/bin/cvs cvs --allow-root=/usr/local/cvsroot pserver
```
I made sure the above line "cvspserver stream ..." appeared on a single line, and restarted inetd, to start the service:
```
sudo /etc/init.d/inetd restart 
```
As far as I understand it, I should now have a cvspserver service running. Still, I needed to transform /rep into an actual CVS repository. Being a n00b, I chose to avoid the commandline and use Cervisia as a GUI for CVS.
```
sudo apt-get install cervisia
```
And this is what I love about Xubuntu, when the command is done, the applications menu has a Development section, containing a shortcut to Cervisia. So easy.
Using Cervisia, I turned /rep into a repository. This resulted in a directory /rep/CVSROOT. As I couldn't figure out how to administer the repository from Cervisia (any tips are welcome), I reverted to the guide for directions on how to give access to the repository. As it required encrypted passwords for the CVS users, I first created a perl script crypt.pl in my directory:
```
#!/usr/bin/perl

my $salt = arandomstring;
my $plaintext = thepasswordtobeencrypted;
my $crypttext = crypt ($plaintext, $salt);

print "${crypttext}\n";
```
I executed the script:
```
perl /home/papaguru/crypt.pl
```
Which neatly gave me an unrepeatable/unpronounceable string.
Using Thunar's Create Document option (right click in the folder, don't know the commandline equivalent), I created a file passwd in /rep/CVSROOT.
I then edited this file:
```
sudo mousepad /rep/CVSROOT/passwd
```
In the file, I created an entry like this:
```
papaguru:3NcRyPt3dPwD:cvsuser
```
To make sure everything was properly initialized, I rebooted the Xubuntu machine.
As far as I know, I should now be able to connect to the repository from any machine in my local network using this connect string:
```
:pserver:papaguru@192.168.1.106:/rep
```
Alas, no such luck. Variations on this string (including the port, using the machines hostname instead of IP) made no difference. I'm the most puzzled by the message NetBeans gives: Cannot connect. While I have both VNC and Samba running on the same machine and I can connect without problems to either.

I'd really appreciate any help.

---

### Post by PapaGuru on 2008-02-16
1st mistake found, I think. 

I deviated from the original guide when I chose to name my Linux CVS user "cvsuser" instead of "cvs" (I did that to avoid confusion over when I was addressing the user, and when I was addressing the app). I also chose a different location for my repository. 
Of course, that also means I have to change the configuration in inetd aswell (See? never just follow HOW-TO's, always keep thinking of what you're doing):
```
sudo mousepad /etc/inetd.conf
```
I changed the line for cvspserver into:
```
cvspserver stream tcp nowait **cvsuser** /usr/bin/cvs cvs --allow-root=**/rep** pserver

```
I restarted inetd, to restart the service:
```
sudo /etc/init.d/inetd restart
```
and held my breath. Would this be it?

Ehm... No. NetBeans still can't connect. So any help is still greatly appreciated.

---

### Post by PapaGuru on 2008-02-16
Hmmm. Odd things have happened. On the Xubuntu machine, I opened a terminal and tried the following:
```
papaguru@xubu01:~$ cvs -d :pserver:papaguru@xubu01:/rep login
Logging in to :pserver:papaguru@xubu01:2401/rep
CVS password:
cvs [login aborted]: connect to xubu01(127.0.1.1):2401 failed: Connection refused
```
I'm confused. :confused:
What happened there? Is it the client CVS I invoked on the commandline that asks for a password before it attempts to connect to the repository, and then fails to connect as the service isn't running properly?
Or is there a connection made that later gets refused because my password is not recognized?

---

### Post by PapaGuru on 2008-02-16
There's more info [_[COLOR="DarkOrange"]here[/COLOR]_]("http://ximbiot.com/cvs/manual/cvs-1.11.22/cvs_21.html#SEC189") on trouble connexting to CVS. I don't see an immediate solution yet, but any progress will get reported.
In the mean time, is there anyone who can tell me the difference between xinetd and inetd, and which gets used by Xubuntu?

---

### Post by PapaGuru on 2008-02-16
Right. It seems Xubuntu makes use of xinetd instead of inetd. I don't know the difference or why (I would like to, though. Anyone?), but the solution seems to be to create a file /etc/xinetd.d/cvspserver.
```
sudo mousepad /etc/xinetd.d/cvspserver
```
Include the following:
```
service cvspserver
{
   port              = 2401
   socket_type       = stream
   protocol          = tcp
   wait              = no
   user              = cvsuser
   passenv           = PATH
   server            = /usr/bin/cvs
   server_args       = -f --allow-root=/rep pserver
}

```
Then restart xinetd:
```
sudo /etc/init.d/xinetd  restart
```
That does the trick!

---

