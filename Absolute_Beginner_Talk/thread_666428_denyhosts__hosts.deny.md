---
title: "denyhosts / hosts.deny"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by lupgop on 2008-01-13
I recently (after help here) installed denyhosts. Once installed i noticed  that under /ECT/  i had no file called hosts.deny as mentioned in the setup procedure. There was however a hosts.allow file which had text similar to the example for Hosts.deny. Hmm - i created a file called hosts.deny and it does get entries of IP address that try to many times to log on. I just wonder if any program is picking up on this and blocking those IP from future attempts or if im just creating a nice log with no action ???  if my system looks at Hosts.allow ??? what should i do ??
Im guessing denyhosts generates it's entries in Hosts.deny from the auth.log file via the denyhosts file - however it is the hosts.deny list that actually get blocked ??? is this right ??? I use Ubuntu 7.1

also however much i delete an IP address from the hosts.deny file it re-appears !??

---

### Post by The Cog on 2008-01-13
I believe that many programs look at hosts.allow and hosts.deny, although the only one I know for certain (I have tested it) is the SSH server.

---

### Post by lupgop on 2008-01-13
if SSH looks at both would that not be a conflict ??

ie allow x,y,z
deny a,b,c

where does  r,s,t fit ?? not denied but not allowed.

ie if you have allowed IP surely all else are denied
and if you have denied IP all else are allowed ??


and if the allowed list has an IP address that logs in enough times to get on the deny list does dny supercede allow ??

---

### Post by The Cog on 2008-01-13
I seem to remember that allow overrides deny. In fact when I tested SSH, one thing I did was to deny ALL, and then add selected addresses to hosts.allow.

The command 
**man hosts.allow**
gets you a manual page for the files.

---

### Post by fudoki on 2008-01-14
> **The Cog said:**
> I seem to remember that allow overrides deny. In fact when I tested SSH, one thing I did was to deny ALL, and then add selected addresses to hosts.allow.

The command 
**man hosts.allow**
gets you a manual page for the files.

You are correct, ALLOW does [by default] override DENY; but this behavior can be modified also.

The setup you mention, where hosts.deny has DENY ALL as the parameter, then implicitly ALLOWing the desired IPs is the preferred setup, regardless whether SSH is used or not.  The .allow and .deny files control RPC PORTMAPped (NFS) connectivity.

CUPS shares are usually set up this way as well.

---

### Post by fudoki on 2008-01-14
It appears your problem is that you are making your changes as "yourself", not as "ROOT".  This is why your hosts.deny file did not save and why your changes don't "stick".

To become "ROOT" in [xxx]buntu, you usually invoke the required application (Text Editor, Konqueror, etc.) with the SUDO or KDESU preface command.  This can be done from the "RUN" command in the menu (KDE) or the "Application Launcher" applet (Gnome); or from a Terminal (xTerm, Konsole, aTerm, etc.).  The advantage with using a terminal is you can see what the error is if the program does not run - just ignore, and don't "X" the terminal window until you close the "child" application you launched!

Anyhow, if you edit using the command "sudo gedit", "kdesu kate", etc. your files will save in /etc and your changes will save because you will have the "Superuser" permissions you need to edit and create System files.

Hope this helps!

---

### Post by sewmyheadon on 2008-01-29
I just had a similar issue and, after doing some research and testing, here's what I found:

denyhosts 'reads' your auth.log file in order to figure out which IPs should be added to the hosts.deny file.

You're right, according to the man pages, if you've entered your approved IPs in the hosts.allow file, you should be fine as it's given preferential treatment, but if your auth.log shows any recent failed login attempts within the parameters of your settings in denyhosts.conf file, the IPs listed in auth.log will be added again to the hosts.deny file.

I think this would only be a problem if you're synchronizing your deny file with the denyhosts server, then your IP could be banned from connecting to other servers that also rely on denyhosts for their list of bad IPs.

So, although I'm not sure if this is the best solution, I think you've a couple options to remedy this problem:

1. backup your auth.log file and erase all the entries, or

2. scrub your failed login attempts from the auth.log file so denyhosts won't parse your IP address and add it to hosts.deny

Either way, until I get more comfortable with the operation and settings of denyhosts, I'm not going to setup the upload sync.

Hope that helps.

---

