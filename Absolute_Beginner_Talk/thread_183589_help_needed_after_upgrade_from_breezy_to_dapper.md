---
title: "help needed after upgrade from breezy to dapper"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by tipi on 2006-05-28
Hi there,
recently i upgraded from breezy to dapper by doing "sudo apt-get dist upgrade",
everything went smooth, accept now  the loginscreen has changed 
to a xubuntu screen and I use kde (the others are installed do)
Before upgrade i enabled root login trough loginscreen (to make it easy on myself, and no things of great importance on this pc)
this is not possible anymore,
also when I try to do things as su, for example "update-manager" (see screenshot)
it promps for password , and says I got the wrong one????

can anyone assist?
greetz

---

### Post by Eversmann on 2006-05-28
Maybe a broken upgrade? upgrading to dapper should be done using kdesu "update-manager -d" on kde. 

try to login as root (or boot as single user) and make an apt-get update and run then what i said, maybe something is broken, running xfce is really weird, looks like there were some problems with the kubuntu system.

I don't have any other ideas, maybe the guys from here would help more than I ;-)

---

### Post by gypsy_roadhog on 2006-05-28
If you really want to be able to login or su to root you need to set a password for the root user. 

You can do this through your normal power user and use the system>>administration>> users and groups menu or I guess  from the commandline  via sudo passwd

Neil

---

### Post by tipi on 2006-05-28
so I try to log in as su
and than theres this,
Il try to translate it to English

thijs@ubuntu:~$ su
Password:
configurationfault - unknown item 'QUOTAS_ENAB' (warn a systemadmin)
configurationfault - onbekend item 'NOLOGIN_STR' (warn a systemadmin)
configurationfault - onbekend item 'ENV_HZ' (warn a systemadmin)
configurationfault - onbekend item 'CHFN_AUTH' (warn a systemadmin)
configurationfault - onbekend item 'CLOSE_SESSIONS' (warn a systemadmin)
root@ubuntu:/home/thijs# sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: wachtwoord is mes succes aangepast
root@ubuntu:/home/thijs#

it says password has been succesfully changed , but after that when I try to run
something like synaptics, again it says that I have the wrong password

---

### Post by tipi on 2006-05-28
by the way, this dapper thing and kde, its alot faster and resposive than 
breezy with gnome, like it

---

### Post by F Cocquyt on 2006-05-28
[QUOTE=tipi]
configurationfault - unknown item 'QUOTAS_ENAB' (warn a systemadmin)
configurationfault - onbekend item 'NOLOGIN_STR' (warn a systemadmin)
configurationfault - onbekend item 'ENV_HZ' (warn a systemadmin)
configurationfault - onbekend item 'CHFN_AUTH' (warn a systemadmin)
configurationfault - onbekend item 'CLOSE_SESSIONS' (warn a systemadmin)
[/QUOTE]

It seems I'am having a similar problem and haven't found the solution yet.
anybody got an idea?

see:
[http://www.ubuntuforums.org/showpost.php?p=1061647&postcount=14]("http://www.ubuntuforums.org/showpost.php?p=1061647&postcount=14")

---

### Post by tipi on 2006-05-28
maybe its something belgian :cool:

---

### Post by tipi on 2006-05-28
found this googeling  but not sure what to do with it

Chris Lale wrote:
 
 
Since upgrading unstable a week or two ago, running su from a terminal reports these errors:
 
 configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
 configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
 configuration error - unknown item 'ENV_HZ' (notify administrator)
 configuration error - unknown item 'PASS_MAX_LEN' (notify administrator)
 configuration error - unknown item 'CHFN_AUTH' (notify administrator)
 configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)
 
 The root prompt appears and is useable. However, gksu fails to run applications such as synaptic:
 
 
Failed to run synaptic as user root:
Failed to communicate with gksu-run-helper.
Received:
configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)

 Some cron scripts also mail errors to root. Further upgrades have failed to fix the problem. I currently have login 1:4.0.12-6 (the package which provides su). I would be grateful for any suggestions.
 
 Chris.
 
 

The problem disappeared after I upgraded again today (2005/10/14). The following two files were replaced:
 /etc/pam.d/su
 /etc/login.defs
 
 Looks like the suggestions about pam and login were close to the mark!
 
 
Thanks to all,
Chris.

---

### Post by richbarna on 2006-05-28
[QUOTE=tipi]so I try to log in as su
and than theres this,
Il try to translate it to English

thijs@ubuntu:~$ su
Password:
configurationfault - unknown item 'QUOTAS_ENAB' (warn a systemadmin)
configurationfault - onbekend item 'NOLOGIN_STR' (warn a systemadmin)
configurationfault - onbekend item 'ENV_HZ' (warn a systemadmin)
configurationfault - onbekend item 'CHFN_AUTH' (warn a systemadmin)
configurationfault - onbekend item 'CLOSE_SESSIONS' (warn a systemadmin)
[/QUOTE]
I think this may relate to your /etc/login.defs file.
I just found this for another Belgian user with the same sort of problem.
Have a look at this :-
[UbuntuLoginDefs]("https://wiki.ubuntu.com/LoginDefs")
All of your errors from above relate to settings in the "login.defs" file.
Maybe you can compare them and edit them manually?

---

### Post by tipi on 2006-05-28
i found out that 
i just have to rename the file "/etc/login.defs.dpkg-dist" to "/etc/login.defs.dpkg-dist login.defs"[COLOR="black"][/COLOR]
and this file "/etc/login.defs" to "/etc/login.defs_old"

I renamed these files trough terminal (sweat), put them in the same folder /etc and now I just need to delete the old ones,
how do I do that from terminal?

---

### Post by richbarna on 2006-05-28
I think it's :-
> cd /etc/
sudo rm login.defs_old

Also, you might like this :- 
[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

---

### Post by tipi on 2006-05-28
okay found it, 

sudo rm /etc/....

---

### Post by tipi on 2006-05-28
please don't do any of the above things , it will totaly screw up your system
for me it  will be a reinstall :D

---

### Post by richbarna on 2006-05-28
What happened ?

---

### Post by gypsy_roadhog on 2006-05-29
I think you are using sudo (which effectively gives your own user root privileges) rather that su which actually switches you to the root user.

So when prompted for a password you should enter your own password and not the root password. Have you tried this?

Neil

---

### Post by tipi on 2006-05-29
before I was able to perform actions as root by using su, 
but now after changing these two files theres no more acces possible,
it's like a circle, 
you need to be root to fix the whole thing but thats just the problem I can not become root,

here's what I get in teminal
see screenshot

you can see that after saying su it asks for password, 
and than after saying the pass.(the right one) i'm still the same user while it shouls be root@ubuntu blabla
can I reset this whole damn thing?

---

### Post by gypsy_roadhog on 2006-05-29
I think that the problem is that root does not currently have a password assigned to it.   try this....:-
[I]
jake@sam:~$ sudo passwd root
Password:         ***************** enter the password of your normal user
Enter new UNIX password:    ***************** enter a new password for root
Retype new UNIX password:  ******************  repeat the new root password
passwd: password updated successfully
jake@sam:~$ su
Password:    ******************** enter the new root password
root@sam:/home/jake#
[/I]


You should be able to dowhatever you need from your normal  login using sudo but  as you can see the above dialogue should either create or reset the root password as needed.

Neil

---

### Post by tipi on 2006-05-29
thijs@ubuntu:~$ sudo passwd root
Password:
thijs@ubuntu:~$

allready tried this, as you can see it won't let me do anything
and yes its the right password

---

### Post by tipi on 2006-05-31
downloaded the dapper cd, and reinstalled the whole thing,
so the problem is solved now, ofcourse now there are other problems :)

---

