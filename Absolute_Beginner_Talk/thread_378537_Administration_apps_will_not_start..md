---
title: "Administration apps will not start."
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by geoff628 on 2007-03-07
Administration apps appear in the GUI menu but will not start. I'm logged in as the person who installed the OS. When I try to start any application from the administration menu, the GUI says "starting administration app", then nothing happens. It does not ask for my password. 

I am an absolute beginner with Linux. I've sifted through various posts and tried the following things, but the problem persists. 

$sudo ls
sudo: unable to lookup 008 via gethostbyname()

$gksudo users-admin
sudo: unable to lookup 008 via gethostbyname()

$cat /etc/hostname
008

$cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 008

A post indicated that
127.0.0.1 localhost 
should read 
127.0.0.1 localhost 008

$sudo gedit /etc/hosts
sudo: unable to lookup 008 via gethostbyname()

$gedit /etc/hosts
I edited the file to read
127.0.0.1 localhost 008
but could not save it. I got the error: "you do not have permission..."


Next, I reboot in recovery mode. I have read that it is a bad idea to do this, but I don't see any other way of giving myself permission to perform admin tasks. 
After the reboot I see:

root@008:~# nano /etc/hosts
I edited the file to read

127.0.0.1 localhost 008

ctrl + o to save
ctrl + x to exit

Then I check that things are as I think they are in this House of Mirrors:

root@008:~# cat /etc/hosts
127.0.0.1 localhost 008
127.0.1.1 008

Great.

~# exit 
to reboot.

Reboot into Ubuntu normally. 

As before, the admin apps are displayed in the menu, but still won't start.

$sudo ls
sudo: unable to lookup 008 via gethostbyname()

Back to square one. Help! 

(I need get the administration > networking app working before I can connect to the internet.)

---

### Post by geoff628 on 2007-03-07
My administration apps are still not working.

This web page 

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

made me think the problem might be in the files 

/etc/sudoers 
or
/etc/group

So I rebooted in safe mode (which logged me in as root user) and started typing away...

root@008# cat /etc/sudoers
#/etc/sudoers
#
#This file MUST be edited with the 'visudo' command as root.
#etc etc

Defaults !lecture, tty_tickets, !fydn
#User privilege specification
root ALL=(ALL) ALL
#Members of the admin group gain root privileges
%admin ALL=(ALL) ALL

Evidently this is correct. So I check the /etc/groups file.

root@008# more /etc/group

the file contains the following lines:
adm:x:4:geoff
lpadmin:x:106:geoff
admin:x:112:geoff

Evidently this is also correct; I am already in the admin group. 
This proves it:

root@008# addgroup geoff admin
The user 'geoff' is already a member of 'admin'


If I'm in the admin group, why do the admin apps crash when I try to run them? Help!

---

### Post by wpshooter on 2007-03-07
Has this just started happening or have these programs worked previously and NOW will not work ?

---

### Post by geoff628 on 2007-03-08
The admin apps refused to start right from the beginning.

I don't know if this is relevant, but right after installing Ubuntu, I changed my password using the GUI:

system---preferences---about me---change password

The new password works (I can log in). But the admin apps don't work.

Is sudo broken?

Is there some other item that gethostbyname depends on?

Is there a known bug in gethostbyname?

Is this a known bug in Dapper? Should I upgrade to Edgy?

---

### Post by steve101101 on 2007-03-08
When i was working in edgy one day i lost the ability to run administrative programs. The only thing that resolved this problem was to reinstall Ubuntu completely

---

### Post by geoff628 on 2007-03-08
OK. Thanks for the advice!

So I reinstalled Ubuntu Dapper. Some but not all of the admin apps are working. 
Bear in mind this is a clean install *straight from the cd*... I have not modified *anything* from the defaults. The first thing I did was check the admin apps.

The admin apps that are working are marked with y; n means not working:

device manager y
disks n
language support n
login window n
networking n --------------------this one really hurts---still can't connect to internet
network tools y------------------I'll learn this next I guess
printing y
services n
shared folders n
software properties n
synaptic n---------------------------ouch. no new software for me evidently.
system log y
system monitor y
time and date n
update manager n
users and groups n

I'm perplexed. Surely others have had the same experience?

---

### Post by glotz on 2007-03-08
I had this problem and I conquered it by googling for the solution but I cannot quite remember what I did. It had something to do with changing the name of the box. Try this, reboot again into recovery mode and edit **/etc/hosts** to **127.0.0.1 localhost.localdomain localhost 008**

EDIT: Wow, so you get that straight after a new install too?? Did you check the download and the cd for defects?

---

### Post by geoff628 on 2007-03-08
Thanks for the suggestion.

I rebooted in recovery mode, got my root prompt, and typed

cp /etc/hosts /etc/hosts.old

nano /etc/hosts

then changed the line
127.0.0.1 localhost
to
127.0.0.1 localhost.localdomain localhost 008

then saved the file, exited nano, typed exit at the prompt to reboot.

Started Ubuntu normally. Unfortunately the administrative applications that were not working are still not working.

---

### Post by geoff628 on 2007-03-08
Yes! 
The problem is solved! 

I reformatted the Ubuntu Dapper partition and installed Ubuntu Edgy. Now *ALL* the administration apps (including networking) work immediately! Hurrah!

Thank you for your tips regarding /etc/hosts, hostname, sudoers, root, nano, etc. Quite educational.

---

### Post by glotz on 2007-03-08
Attention! Ubuntu Administrator on the deck! :)

---

