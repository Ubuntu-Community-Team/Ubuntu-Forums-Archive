---
title: "[SOLVED] sudo unable to resolve host"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Darkade on 2008-03-13
Every time I use sudo the terminal says

sudo: unable to resolve host icarus-laptop

It works but that didn't happened before, ideas? Thanks:lolflag:

---

### Post by PmDematagoda on 2008-03-13
Post the output of:-
```
cat /etc/hosts
```

---

### Post by Darkade on 2008-03-13
ivan@icarus-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 icarus-laptop.actuaria_rulz

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by PmDematagoda on 2008-03-13
Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 icarus-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.

That should fix the problem.

---

### Post by Darkade on 2008-03-13
Thanks :D:D it worked:guitar:

---

### Post by rhodry on 2008-03-13
This happened to me after upgrade to Hardy Heron. (which may or may not be relevant)

Check your /etc/hosts file.

My machine in question is "greywolf" and my domain is "home.net". I use DHCP but I have an IP address fixed by my router as 192.168.1.xx. The entry I have in the /etc/hosts file for that IP address is normally:

192.168.1.xx      greywolf.home.net    greywolf

The system (I assume network manager) had added the domain name to the end of the line again - ie

192.168.1.xx      greywolf.home.net    greywolf.home.net

I just removed the 2nd ".home.net" off the end and name resolution worked again.

This is not the 1st time this has happened to my /etc/hosts, but it was the 1st time it had caused name resolution errors in the terminal.

I just wish they would use a decent network manager like 'wicd' as the default instead of the crap they use now. Anyway, hope this helps?

rhodry.

---

### Post by selda on 2008-03-23
> **rhodry said:**
> This happened to me after upgrade to Hardy Heron. (which may or may not be relevant)

Check your /etc/hosts file.

My machine in question is "greywolf" and my domain is "home.net". I use DHCP but I have an IP address fixed by my router as 192.168.1.xx. The entry I have in the /etc/hosts file for that IP address is normally:

192.168.1.xx      greywolf.home.net    greywolf

The system (I assume network manager) had added the domain name to the end of the line again - ie

192.168.1.xx      greywolf.home.net    greywolf.home.net

I just removed the 2nd ".home.net" off the end and name resolution worked again.

This is not the 1st time this has happened to my /etc/hosts, but it was the 1st time it had caused name resolution errors in the terminal.

I just wish they would use a decent network manager like 'wicd' as the default instead of the crap they use now. Anyway, hope this helps?

rhodry.

I had similar problems. I use wicd and during upgrade it was unistalled, and replaced by network manager, which was not working. :confused::mad:

---

### Post by leohart on 2008-04-13
I had this problem as well after I upgraded to Hardy Heron. ^_^ Add/Remove... stopped working correctly as well and I didn't know what is going on. After this fix, things seem to get back to normal.

---

### Post by falkTX on 2008-04-15
I had that problem when installing FireStarter and trying to share a connection,
but now it's ok!! fixed!!

Thank you guys!

---

### Post by linuksamiko on 2008-04-18
I have the same problem, after updating to hardy (RC1). This problem should be fixed before the final releas!

---

### Post by tuskenraider on 2008-04-24
> **PmDematagoda said:**
> Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 icarus-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.

That should fix the problem.

That totally fixed my problem!!! i appreciate it!!!!!!!!!!!!!!!! thank you very much!!!!    :guitar: :)

---

### Post by wyild1 on 2008-04-24
> **PmDematagoda said:**
> Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 icarus-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.

That should fix the problem.

I was pretty sure that was the problem!  I just upgraded to Hardy and well, the problem is there too.  The other issue i have is i have no GUI, and the file i need to edit to fix that well is xorg.conf.  I cant gksudo or any gui based fix.  So that being said, would the only way to fix this problem is bust out the live cd and fix it that way?  

Cheers!

---

### Post by wyild1 on 2008-04-24
> **wyild1 said:**
> I was pretty sure that was the problem!  I just upgraded to Hardy and well, the problem is there too.  The other issue i have is i have no GUI, and the file i need to edit to fix that well is xorg.conf.  I cant gksudo or any gui based fix.  So that being said, would the only way to fix this problem is bust out the live cd and fix it that way?  

Cheers!


Accually i found my answer!

[http://www.kubuntuforums.net/forums/index.php?topic=3092772](http://www.kubuntuforums.net/forums/index.php?topic=3092772)


<snip>
tom@fawn:~$ sudo apt-get update
sudo: unable to resolve host fawn

FOUND THAT /ETC/HOSTS HAD BEEN MODIFIED, 'FAWN' REMOVED FROM LOCALHOST
REBOOTED IN RECOVERY MODE TO GET ROOT ACCESS, DID THE EDIT, NOW IT WORKS.

</snip>

Cheers!

---

### Post by agent8131 on 2008-04-24
See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

### Post by edwardecl on 2008-04-25
Yeah real nice, did the same to me removed a line out of my hosts file and broke sudo. Can't edit the hosts file as I need to be root but I can't be root because I can't sudo typical.

Plus as I have the computer plugged into a HDTV using a VGA lead I can't see the recovery console :D. Time to bring my real monitor back out the cupboard... Although I did notice in this release I can see my console on the HDTV that's one problem solved and another created for me :D.

Last week it was ubuntu failing fsck on startup but only displaying a flashing cursor on the screen... I had to get my real monitor out to fix that grrr always happens to me ^^.:lolflag:

---

### Post by Ederico on 2008-04-25
I'm getting the same problem, after I updated to Hardy Heron. Plus, the /etc/hosts/ isn't there!

Can anyone help?

---

### Post by alexidoia on 2008-04-25
hi there, I had similar problems when upgrading, the problem is that I am not in the xserver, just terminal mode and sudo being broken gksudo gedit /etc/hosts brings me:

(gksudo6294)/Gtk-WARNING **: cannot open display:

any idea ?
Alex

---

### Post by Searay on 2008-04-25
The fix didn work for me. My hostname in etc/hosts matches the name in network settings. But I still get unable to resolve host Old Dell. I have just upgraded to 8.04 from Gutsy. 

cat /etc/hosts   shows
127.0.0.1 localhost
127.0.1.1 Old Dell

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Fell upon this error while installing/configuring first network printer, which I get in CUPS "Can't load /etc/samba/smb.conf - run testparm to debug it.

and runing testparm gives this error
 
´can´t load /etc/samba/smb.conf permission denied


Any ideas will be greatly appreciated!

---

### Post by Mr Rough on 2008-04-26
I can confirm that upgrading from 7.10 to 8.04 this morning caused this bug. However gksu worked so I was able to edit the file. So for those that can't edit /etc/hosts, use this on GNOME.

```

gksu gedit /etc/hosts

```

For me it changed it from computername to computername.workgroup

Simple enough of a fix though, just an annoyance.

---

### Post by buntunub on 2008-04-26
> **Mr Rough said:**
> I can confirm that upgrading from 7.10 to 8.04 this morning caused this bug. However gksu worked so I was able to edit the file. So for those that can't edit /etc/hosts, use this on GNOME.

```

gksu gedit /etc/hosts

```

For me it changed it from computername to computername.workgroup

Simple enough of a fix though, just an annoyance.

Thats what fixed things for me.

---

### Post by Everywhere_at_Once on 2008-04-26
I have this identical problem, and i figured out on my own that i had to edit the hosts file, but i have no form of internet on my computer, there is no ethernet driver, nor a wireless driver. Is network required to use sudo? I don't think loopback even works because of the lack of driver...

my hosts entry is 
127.0.1.1 sean-laptop
i removed the domain using gksudo already, successfully, but it still isn't able to resolve the host.

If it is unable to access a network, sudo just craps out? I'm really frustrated by this, and i've already spent about 10 hours trying to get things back to the way i had them set up under gutsy, and i've got hours ahead of me, and maybe even a clean install.

I'd just really appreciate somebody's help, however small. I don't know all that much about linux, just the command-line basics, and this is something i've not encountered before.


***EDIT:  I fixed it, no need to all rush in to save the day. I had to change my hostname, and make sure that name was consistent in all the hosts files. That did the trick.
They should really consider changing it so that it doesn't automatically append your workgroup and domain to your hostname, because there are a great many people who aren't members of either of them.

---

### Post by ByteJuggler on 2008-04-27
> **Searay said:**
> The fix didn work for me. My hostname in etc/hosts matches the name in network settings. But I still get unable to resolve host Old Dell. I have just upgraded to 8.04 from Gutsy. 

cat /etc/hosts   shows
127.0.0.1 localhost
127.0.1.1 Old Dell

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Fell upon this error while installing/configuring first network printer, which I get in CUPS "Can't load /etc/samba/smb.conf - run testparm to debug it.

and runing testparm gives this error
 
´can´t load /etc/samba/smb.conf permission denied


Any ideas will be greatly appreciated!

That space will make the "old" and "dell" look like 2 hostnames.  You should quote the name (if that's possible...)

---

### Post by akbob on 2008-04-27
I wasn't able to edit the hosts file directly with sudo gedit however using the GUI I was able to.

System > Administration > Network
Click on "unlock"
Enter password and click on "authenticate"
Click on Hosts Tab
Select your host user alias and click properties
Edit alias by removing the addition of the domain
click ok and close

Hope this helps.

---

### Post by amitst on 2008-04-28
> **akbob said:**
> I wasn't able to edit the hosts file directly with sudo gedit however using the GUI I was able to.

System > Administration > Network
Click on "unlock"
Enter password and click on "authenticate"
Click on Hosts Tab
Select your host user alias and click properties
Edit alias by removing the addition of the domain
click ok and close

Hope this helps.

The above method didn't work for me. If I remove the domain through System > Admin > Network and save it then the domain comes back in the /etc/hosts. Editing /etc/hosts solved the issue temporarily, however, after taking my laptop home and after changing the settings through System > Admin > Network again brought back the same issue (domain name appended)

---

### Post by amitst on 2008-04-28
I have added a bug [https://bugs.launchpad.net/ubuntu/+bug/223448](https://bugs.launchpad.net/ubuntu/+bug/223448) for this.

---

### Post by dom on 2008-04-28
Good job.

I changed the hostname after an install of Hardy Today and this completly scuppered the machine. I couldn't launch anything !
From console logins or GUI/Gnome login.

For some reason, there appeared to be a time window, just after you log into gnome, where you could edit the network settings and fix it.
I set it back to my original hostname, which was in /etc/hosts.
Then edited /etc/hosts to add the new hostname.
Then change the hostname to the new one.

X would soon stop allowing new windows to open. Sudo access was blocked. Etc. It was crazy. 

Not sure if the block was after a time delay, or after opening the first app, or what, but I was very close to going back to 7.10, or another linux distro !

---

### Post by dom on 2008-04-28
Good job.

I changed the hostname after an install of Hardy Today and this completly scuppered the machine. I couldn't launch anything !
From console logins or GUI/Gnome login.

For some reason, there appeared to be a time window, just after you log into gnome, where you could edit the network settings and fix it.
I set it back to my original hostname, which was in /etc/hosts.
Then edited /etc/hosts to add the new hostname.
Then change the hostname to the new one.
Then things worked fine.

X would soon stop allowing new windows to open. Sudo access was blocked. Etc. It was crazy. 

Not sure if the block was after a time delay, or after opening the first app, or what, but I was very close to going back to 7.10, or another linux distro !

---

### Post by novus721 on 2008-04-28
> **akbob said:**
> I wasn't able to edit the hosts file directly with sudo gedit however using the GUI I was able to.

System > Administration > Network
Click on "unlock"
Enter password and click on "authenticate"
Click on Hosts Tab
Select your host user alias and click properties
Edit alias by removing the addition of the domain
click ok and close

Hope this helps.

This also worked for me, as I was not able to use either gksudo nor gksu to access my /etc/hosts file - terminal would state it was running, but nothing ever came up. Hopefully it sticks

---

### Post by Searay on 2008-04-29
Changed to Old_Dell did the trick. Thanks!

---

### Post by nuke_fluke on 2008-04-29
tried the methods given but was unsuccessful...
What I did was...

went to Network-> Hosts -> Alias and changed the name there from  x.laptop.192 to x.laptop and it worked...

---

### Post by evanct on 2008-04-30
i have this problem too, except when i run gksu gedit /etc/hosts i get an alert box with this:

"Failed to run gedit /etc/hosts as user root.

The underlying authorization mechanism(sudo) does not allow you to run this program. Contact the system administrator."

gksudo doesn't do anything.

This is so frustrating, its only one of the problems i've had with 8.04. this is supposed to be a final release?

---

### Post by agent8131 on 2008-04-30
> **evanct said:**
> i have this problem too, except when i run gksu gedit /etc/hosts i get an alert box with this:

"Failed to run gedit /etc/hosts as user root.

The underlying authorization mechanism(sudo) does not allow you to run this program. Contact the system administrator."

gksudo doesn't do anything.

This is so frustrating, its only one of the problems i've had with 8.04. this is supposed to be a final release?

You can reboot and select recovery mode - drop to root shell - and then edit the hosts file with "nano /etc/hosts" to make the changes.  Yes this is a frustrating bug, especially for those of us who tried, in vain, to point out how serious this bug was (you can read the conversations here if you're interested: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)).  On the upside it should be possible to recover relatively quickly.  I had to use the recovery mode process myself so I'd give that a try.

---

### Post by hartdg on 2008-05-01
Using the network manager I tried changing the original entry from the form:
127.0.1.1 hostname.networkname
to:
127.0.1.1 hostname.networkname hostname
only to find after closing and reopening network manager that the entry had been **changed** to:
127.0.1.1 hostname.networkname hostname**.networkname**

I then added a new entry:
127.0.1.1 hostname.networkname hostname
and deleted the original entry.

That seems to have fixed the problem and SUDO no longer results in the "unable to resolve host xxx" error.

Synaptic also opens properly now and Update Manager appears to be working (previously Synaptic would not open and Update Manager would freeze).

thanks to all for sharing.
let's hope that the configuration bug in network manager (or where ever the root cause of the problem is) is fixed soon. It's a silly error that will do nothing to advance the cause of fixing "bug 1".

Dave

---

### Post by aheckler on 2008-05-01
A user over in ABT appears to be having this problem, but I can't seem to fix it for him. Would someone who has experience with this bug and the fix/workaround please help him out? Thanks!

His thread: [http://ubuntuforums.org/showthread.php?t=777447](http://ubuntuforums.org/showthread.php?t=777447)

---

### Post by evanct on 2008-05-02
> **agent8131 said:**
> You can reboot and select recovery mode - drop to root shell - and then edit the hosts file with "nano /etc/hosts" to make the changes.  Yes this is a frustrating bug, especially for those of us who tried, in vain, to point out how serious this bug was (you can read the conversations here if you're interested: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)).  On the upside it should be possible to recover relatively quickly.  I had to use the recovery mode process myself so I'd give that a try.

i did that, changed the first two lines of /etc/hosts file to read:
127.0.0.1 localhost
127.0.1.1 evans-computer

i reboot, use sudo, and nothing happens. i'll type sudo gedit somefile.txt or something, and i get no error messages or anything, it just goes back to the prompt. gksu and gksudo results in the same error message i specified earlier.

---

### Post by buntunub on 2008-05-02
Although doing the gksu gedit /etc/hosts thing did fix my ability to do things like Add/Remove Software, there seems to still be some pretty major authentication/ownership issues that continue to rage on that has to be associated. Everyone please post or continue to post/follow up on this bug with the bugzilla system. This is indeed a game breaking bug for Hardy.

---

### Post by evanct on 2008-05-02
yeah, it's kind of ridiculous.

---

### Post by neilg4rqn on 2008-05-04
> **Darkade said:**
> Every time I use sudo the terminal says

sudo: unable to resolve host icarus-laptop

It works but that didn't happened before, ideas? Thanks:lolflag:

I have the same problem and found that I could get round it by typing "su root", entering my password and then dropping the use of sudo or gksudo for that session. 
So
su do-something-useful<enter> 
becomes
sudo root<enter>
password<enter>
do-something-useful<enter>

neil

---

### Post by adk1us on 2008-05-04
Neil:

I believe the word "root" in your command "su root" is redundant.  the command "su" will log you in as the superuser (root).  The command takes no argument.

Since I encountered this problem I would just "su",  then run the command(s) I needed, then "exit" from the root shell.  It's great if you have to enter a number of commands, but a pain if you are only entering one.

--Kris

> **neilg4rqn said:**
> I have the same problem and found that I could get round it by typing "su root", entering my password and then dropping the use of sudo or gksudo for that session. 
So
su do-something-useful<enter> 
becomes
sudo root<enter>
password<enter>
do-something-useful<enter>

neil

---

### Post by neilg4rqn on 2008-05-05
> **adk1us said:**
> Neil:

I believe the word "root" in your command "su root" is redundant.  the command "su" will log you in as the superuser (root).  The command takes no argument.

Since I encountered this problem I would just "su",  then run the command(s) I needed, then "exit" from the root shell.  It's great if you have to enter a number of commands, but a pain if you are only entering one.

--Kris

Yes you're right "su" on its own does indeed work, thanks for that. However I was also looking into a problem where any menu entry that would require a password (eg synaptic) would not run, the timer would come up for about 20 seconds and then the normal pointer would return, all appeared then normal apart from that synaptic or whatever would not be running.
Researching the above I came across a thread on this forum (lost the path sorry) which suggested I edit "gksu gedit /etc/hosts" - my initial result was
127.0.0.1 localhost
127.0.1.1 neil-ubuntu.workgroup

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I edited the second line to read 
127.0.1.1 neil-ubuntu.workgroup neil-ubuntu

Now synaptic etc. run fine and "su root" also works.
hope that explains ok
Neil

---

### Post by stokerw on 2008-05-05
Many Thanks for your helpful thread.
I too had the same problem after trying to set up a network connection.
changing hosts solved the problem.
Stoker Wilson.:)

---

### Post by neilg4rqn on 2008-05-05
Hi, is that stoker as in tandem?

---

### Post by stokerw on 2008-05-06
Nope! Just an unusual Christian name.

---

### Post by stinger30au on 2008-05-06
thanks for the info at the start of this thread. fixxed my pc with the same error this afternoon.

---

### Post by VCF on 2008-05-06
Yup, taking the workgroup off the end of pc name worked perfectly for me on my Asus Eee PC, as well, I'm getting snappy response on things that required admin passwords as well, the dialog comes back immediately.

---

### Post by dgruetter on 2008-05-06
I was no longer able to get sksudo password prompts due to this. Looks like this solution fixed my problem. Thanks :guitar:!

---

### Post by stankopp on 2008-05-08
This fix also solved my inability to open synaptic package manager!
Thanks for the help!

---

### Post by diegomedaglia on 2008-05-08
Hi, in case you have this problem but do not have a root password set (that's the default in new installations) checking [this post out]("http://ubuntuforums.org/showpost.php?p=4915657&postcount=13") might help.

---

### Post by EmilyRose on 2008-05-12
Oh thank goodness! This fixed it and now I can load administrative stuff again!! Thank you so much!!

---

### Post by Claus_T on 2008-05-15
I had upgraded my 7.10 to 8.04 and it went without a problem.  I had installed one of the follow-on updates and had installed the HPLIB package so I could use my HP printer.  After this I had installed another update.

When the latest update showed up 2 days ago, the update manager just hung up, and I had to use the "Forced Quit" function to stop it.  I'm an ex-Windows guy and prefer to use the GUI operations whenever I can.  The update manager started, but it hung up, apparently waiting for the administrative password window to appear (which it never did - and no error message showed up either).

When I found this post, I tried the trick posted in the the first couple of posts.  I found that /etc/hosts had appended my network name to the computer name (apparently that was done by the previous "update").  I made the correction and now the current update installed correctly.

Thank you.

---

### Post by steve_waters on 2008-05-16
Thank you worked like a treat......

---

### Post by Malac on 2008-05-16
Exact same here editing /etc/hosts worked for me, cheers.

---

### Post by kiwi-pete on 2008-05-19
Does anyone know how to prevent tNM from adding the "Network Name" to the end of the "Host Name"

Mine does this in Hardy on a regular basis as I try to enable wireless support/connection.
There are a host of applications that will not run when this happens too.

---

### Post by jolyan on 2008-05-20
The fix for me was to enable the root password, su into root, then edit the hosts file using:
127.0.1.1 host.domain.com host (swap host and domain.com for yours).

Just using the sudo'd network gui without the second host would replace my changes after close.

When presented with many solutions, there's a good chance one will work.

Cheers.

---

### Post by kiwi-pete on 2008-05-20
> **jolyan said:**
> The fix for me was to enable the root password, su into root, then edit the hosts file using:
127.0.1.1 host.domain.com host (swap host and domain.com for yours).

Just using the sudo'd network gui without the second host would replace my changes after close.

When presented with many solutions, there's a good chance one will work.

Cheers.

Sorry, I am a little confused about your instructions, could you simplify them a little for me? I am still getting my head around this new OS.
Cheers.

---

### Post by thotmos on 2008-05-22
Wonderful post, now sudo, apache, dansguardian and others work fine
PmDematagoda, you're a life saver!

---

### Post by longpete on 2008-05-27
When I updated my system sudo still complained about not being able to resolve my hostname, but it worked! So something's been done right somewhere.

However, there are two questions:
[LIST]
[*]Why does the network manager add the domain name to the end of the host (and only this host under all its guises - 192.168.1.1, 127.0.0.1 etc. - whereas all the other hosts on the same lan - 192.168.1.0/24 are left alone)
[*]Why doesn't a qualified hostname get resolved anyway?!
[/LIST]

---

### Post by Naughty_Girl on 2008-05-27
Good morning everyone

---

### Post by hagnat on 2008-05-29
ran with the problem here, tried the solution given in the first page (change my desktop name from desktop.network to simply desktop), but ran with some issues with the gksudo... after a simple reboot in the recovery mode and some vim, i managed to correct this.

---

### Post by giancast on 2008-05-31
> **PmDematagoda said:**
> Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 icarus-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.

That should fix the problem.
Thanks for the information. It worked for me. I removed everything after the first period.
from 127.0.0.1 giancarlo.desktop giancarlo.desktop.home.com
to   127.0.0.1 giancarlo

Now apt-get update and apt-get upgrade is working.
Next time I will try and see if Update Manager works. This is why I tried apt-get, I received the message that there were 117 updates available (I do not use my computer much, I have been playing with an old Sony Vaio PCGn505, I installed XUBUNTU and is working great, I wanted Skype for travel. Skype just kills Win98, but Skype runs fine with Xubuntu in this machine, voice a little choppy but what do you expect of a 333 Celeron and 128Mb of memory ). When I opened Update Manager and told it to install the updates, it just hung there doing nothing. So I tried apt-get and got the Unable to Resolve message.

Thanks again.

---

### Post by ByteJuggler on 2008-06-01
> **jolyan said:**
> The fix for me was to enable the root password, su into root, then edit the hosts file using:

Please do not suggest people enable the root account, it's not neccesary 99.99999999% of the time and eliminates one possible attack vector on user's computers completely.  Instead, use "sudo", that's what it's for.  

To edit the hosts file with root privileges, press alt-f2 and enter "gksudo gedit /etc/hosts".  Or you can open a terminal prompt and use "sudo gedit /etc/hosts" instead, if you want.  In neither case should you mess directly with the root account itself or unlock/enable it.

---

### Post by mainak_sen on 2008-06-03
> **PmDematagoda said:**
> Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 icarus-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.

That should fix the problem.
Thanks!!

---

### Post by Mander on 2008-06-03
> **PmDematagoda said:**
> Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 icarus-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.

That should fix the problem.

This worked for me; however, it seems that I have to keep doing it over and over.  Sometimes after a reboot, when I go to open synaptic or anything else that require the admin password, I get the same symptom ("starting administrative task" window appears in the taskbar, then disappears with no warning) and I have to go edit the hosts file again.

How do I go about troubleshooting this?  I'm running Hardy, via a Wubi install, with all the usual updates and so on.

---

### Post by Darkade on 2008-06-04
Hey everyone! you know I've been wanting to post this a while now so I'm just gonna do it
In case you didn't noticed I am the one that first opened this thread and definitly I didn't spected it to be this big? i guess?

As you may see from the first I got really quick help and worked for me in just a couple of minutes. So the main point in this is to tell you all that I hope this works as fine for you as it did for me.
have a great day:lolflag:

---

### Post by blutowski on 2008-06-05
My host file looks normal and yet I still cannot get any admin functions. I think I my problem may be that I changed my system name from michael to Home PC awhile back. This problem just started after a recent update. 
127.0.0.1 localhost
127.0.1.1 michael

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by grumpy_geologist on 2008-06-08
Hi.  Not sure this is related but - I can't update - just starts up and sits there.  Also if I do anything that requires admin, it starts up, shows the action on the bar at the bottom of the screen, and then stops - does nothing

my /etc/hosts file id

gc@lostworld:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Aluminus-ubu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


localhost is my network name and I do not have a domain.  :confused:

Any suggestions please????????

Thanks

---

### Post by PmDematagoda on 2008-06-08
Post the output of:-
```
hostname
```

---

### Post by DavidOC on 2008-06-08
I have the same problem as grumpy, here is the contents of my hosts file:

127.0.0.1	localhost
127.0.1.1	danieloc-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

The output from hostname is:
dococ-desktop

Please note there are two accounts on my machine. Any suggestions for this? Thanks.

---

### Post by PmDematagoda on 2008-06-08
Well, your post shows the mistake:-
```
127.0.0.1 localhost
**127.0.1.1 danieloc-desktop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
``` is supposed to be:-
```
127.0.1.1 dococ-desktop
```

---

### Post by heyubob on 2008-06-08
:guitar:Yeah, first shot, worked great.  thx

---

### Post by DavidOC on 2008-06-08
That got them working, thanks for that!

---

### Post by grumpy_geologist on 2008-06-08
Thanks guys - made 2 mistakes - first, my network name was lostworld, not localhost and second changing 127.0.1.1 to 127.0.1.1 lostworld worked

Thanks again - solved the problem  :)

> **grumpy_geologist said:**
> Hi.  Not sure this is related but - I can't update - just starts up and sits there.  Also if I do anything that requires admin, it starts up, shows the action on the bar at the bottom of the screen, and then stops - does nothing

my /etc/hosts file id

gc@lostworld:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Aluminus-ubu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


localhost is my network name and I do not have a domain.  :confused:

Any suggestions please????????

Thanks

---

### Post by evertmantel on 2008-06-17
Same here.. gksudo gedit /etc/hosts did the trick.. my line was ***-laptop.MsHome
After removing the .MsHome it worked again. 
I did make a change to the domain name recently, using the network settings menu (System>Administration>Network).
Thanks! that save me a reinstall.

---

### Post by strife4201 on 2008-06-25
Im having the same problum 
i get this user home drmc file is being ignored 
and then i do the sudo comand thing and i cant do anything cuz it says 
sudo: unable to resolve host HOME
i have tried alot fo the things on this post and im at a loss i think i might have to just reinstall i dont want to do this though but oh well

---

### Post by tuxofunic on 2008-07-04
> **tuskenraider said:**
> That totally fixed my problem!!! i appreciate it!!!!!!!!!!!!!!!! thank you very much!!!!    :guitar: :)

Hi ! Verrrry useful tip ! I have had same problem. Now it works fine, thanks !:)

---

### Post by bsabbato on 2008-07-07
My user admin and network is also greyed out since I added KDE to my desktop and post the latest linux release upgrade...   My hosts file looks like the below.  I don't think I have the same issue... I have no domain..  I'm befuddled.

127.0.0.1 localhost
127.0.1.1 ronbuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Malac on 2008-07-08
> **bsabbato said:**
>  I have no domain..  I'm befuddled.
You do, the default domain is WORKGROUP assigned in /etc/samba/smb.conf and/or in/etc/hostname

This is worth changing anyway as that's the default, even if you don't have a domain as such.

Change yours to:
```
127.0.0.1 localhost
127.0.1.1 ronbuntu [COLOR=Green]*ronbuntu.**rondomain***[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Replacing [COLOR=Green]***rondomain***[/COLOR] with whatever you like.
Do the same in /etc/samba/smb.conf and /etc/hostname.

Hope this helps.

---

### Post by Mr.Useless on 2008-07-15
The reason why it does this is because you domain is set.

gksudo gedit /etc/hosts is the easy bash way you can also do it through 

System/Admin/Network and uncheck your Domain...

worked for me anyway, that was the cause of the problem, because it was once i checked my domain that i got the "error"

---

