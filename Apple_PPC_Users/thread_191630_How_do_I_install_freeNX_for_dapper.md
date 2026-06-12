---
title: "How do I install freeNX for dapper?"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by n00bWillingToLearn on 2006-06-07
Digg users may hate me for this, but title says it all:)

---

### Post by LBailey on 2006-08-03
Hi,
I'm a noobie too, but I managed, after reading a lot, and a little help in the final stretch from my bf:)
[I]NOTE: This assumes you want to generate your own keys. If you want to use the nomachine-keys option, there are quite a few other posts.
[/I]
Anyway, here goes:
1) download server
[INDENT]In the Terminal as root, type:
*> nano /etc/apt/sources.list*
add to bottom:[/INDENT]
```
deb http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx
deb-src http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx
```
[INDENT]Then, type:
*> wget [http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg](http://free.linux.hp.com/~brett/seveas/freenx/1135D466.gpg) -O- | sudo apt-key add -*
[/INDENT]
2) install server
[INDENT]*> apt-get install freenx*
(choose Custom Keys)[/INDENT]

3) test the server
[INDENT]*> /usr/bin/nxserver --status*[/INDENT]

4) set up users
[INDENT][I]> /home/<username># nxserver --adduser <username>
> /home/<username># nxserver --passwd <username>[/I][/INDENT]

Then, the final stretch. To connect from WinXP:
5) Install client on XP:
[INDENT]Install NoMachine client v1.5 **(NOT 2.0)** build 114 from [http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768](http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768)[/INDENT]

[INDENT]**[EDIT] **Or, you can install v2.0, but do the fix described here:
[http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0](http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0)
Thanks Predseda3D!
[/INDENT]

6) copy key from server (Ubuntu) to client (XP)
[INDENT]The key is in: /var/lib/nxserver/home/.ssh/client.id_dsa.key

Copy the contents to windows (you can't copy the file cause of permissions)
You can either chmod the file, or I just copied the text and messaged it to myself using GAIM...not secure but.. as I said I'm a noobie myself:)

Then, on the client (XP) side you can create the file where ever, and paste the contents.

Finally, run the NX Client, hit "configure", and in the General tab hit "Key.." then "Import.." and select the key file you created (or copied).[/INDENT]

---

### Post by LBailey on 2006-08-03
Hrm.
It seems that everything is not quite right after all. 

Logging in and then suspending works fine. Resuming works... sortof. The window holder (blue outline thing in std XP) does something crazy and isn't attached to the server's display. It's a little box that can be moved around. When I click on it's "X" to close, which normally allows me to suspend or terminate the session, nothing happens! I can only log out (from the freenx window), or halt the process from winblows. Anyone have a clue??

And yes... before anyone asks, I really do need to resume multiple times, as I'm running freenx on my processing server (week-long jobs that I need to check up on).

Also, I tried the fix in this post (even though my symptoms are slightly different), but no luck:
[http://www.ubuntuforums.org/showthread.php?t=48473](http://www.ubuntuforums.org/showthread.php?t=48473)

---

