---
title: "Log in denied"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by xyz on 2005-12-06
Hi everyone
Several small windows appear booting into Breezy:
> your home dir is listed as /home/th but it doesn't appear to exist.Do you wnat to log in with / dir as your home dir?It's unlikely anything will work unless you use a failsafe session
I've got Recovery Mode.Is it equivalent to Failsafe??
Anyway,I cklick on Yes and then:
> your $HOME/.dmrc file has incorrect permissions and is being ignored.This prevents the default session and language from being saved.File should be owned by user and have 644 permissions
Next...
> your session only lasted 10 seconds...this could mean there's some installation problems or out of disk space.Try logging in with one of the failsafe sessions to see if you can fix this problem
I don't lack disk space.I want to see "View details (~/.Xsession-errors file)"
> /etc/gdm/Presession/Default: Registering your session with wtmp and utmp
/etc/gdm/Presession/Default: Running /usr/bin/X11/session -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0 .Xservers" -h " " -l "0" "th"
/etc/gdm/Xsession: Beginning session setup...
(gnome-session: 6217): libgnomevfs-Warning **: Unable to create ~/.gnome2 dir: No such file or dir
Could not create per-user conf dir '/home/th/.gnome2/': No such file or dir

Please note that I can't log in ubuntuforums,gmail either running Breezy.
I've tried to be as explicit as I am capable of being and if anyone can help,I'd be most grateful

---

### Post by fourchannel on 2005-12-06
ok from your description it sounds like your home directory has been wiped out.

can you log into one of the virtual consoles? when your back at the login screen hit:
```
ctrl-alt-F1
``` 


if so.. login and then run this command:

```
cd ~ ; pwd
``` 
if the command *doesn't* output```
/home/<your user name>
``` 
then the system has got the wrong directory associated with your username.

in that case paste the output of this command:
```
cat /etc/passwd
``` 
and we will see what is wrong with your login.

edit!!!

forgot you cant cut and paste in VC mode.

run this command instead and, somehow, paste it in here.

```
cat /etc/passwd | grep $USER
```

---

### Post by xyz on 2005-12-06
[QUOTE=fourchannel]ok from your description it sounds like your home directory has been wiped out.

can you log into one of the virtual consoles? when your back at the login screen hit:
```
ctrl-alt-F1
``` 


if so.. login and then run this command:

```
cd ~ ; pwd
``` 
if the command *doesn't* output```
/home/<your user name>
``` 
then the system has got the wrong directory associated with your username.

in that case paste the output of this command:
```
cat /etc/passwd
``` 
and we will see what is wrong with your login.

edit!!!

forgot you cant cut and paste in VC mode.

run this command instead and, somehow, paste it in here.

```
cat /etc/passwd | grep $USER
```[/QUOTE]


Thanks!I'm jotting down your instructions and will go and ckeck it all out.Will get back to you as soon as possible.

---

### Post by xyz on 2005-12-06
Just trying to post my output and I get this:

 "  1. You have included 31 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator."

I must say I don't get it.I've got no smilies,img or anything else except [CODE] and [QUOTE]???

---

### Post by fourchannel on 2005-12-07
hmm...weird.

ok, email me the output and then i'll post it here for you.

[http://ubuntuforums.org/sendmessage.php?do=mailmember&u=43771](http://ubuntuforums.org/sendmessage.php?do=mailmember&u=43771)

---

### Post by fourchannel on 2005-12-07
```
cat /etc/passwd

 I've got what follows on my screen:

sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man/var/cache/man:/bin/sh
lp:x:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/ww:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:irc:/var/run/irc:/bin/sh
gnats:x:41:41:Gnats Bug Reporting System(admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
postfix:x:100:103::/var/spool/postfix:/bin/false
syslog:x:105:105::/home/syslog:/bin/false
klog:x:106:106::/home/klog:/bin/false
th:x:1000:1000:terry,,,:/home/th:/bin/false
messagebugs:x:101:110::/Var/run/dbus:/bin/false
cupsys:x:102:107::/:/bin/false
fetchmail:x:103:65534::/var/run/fetchmail:/bin/sh
hal:x:111:111:Hardware abstraction layer,,,:/var/run/hal:/bin/false
saned:x:113:113:/home/saned:/bin/false
gdm:x:104:114:Gnome Dysplay Manager:/var/lib/gdm:/bin/false
dhcp:x:115:115::/nonexistent:/bin/false
hplip:x:107:7:HPLIP system user,,,:/var/run/hplip:/bin/false
privoxy:x:108:65534::/etc/privoxy:/bin/false
debian-tor:x:116:116::/var/lib/tor:/bin/bash
entrance:x:109:117:Enlightened Display Manager:/var/lib/entrance:/bin/false


and running

cat /etc/passwd | grep $USER

th:x:1000:1000:terry,,,:/home/th:/bin/bash
``` 

ok, first off i know why it won't let you post.

```
th:x:1000

the :x is treated as a smilely and there are 30 of them in that output
so wrap them in just 1 set of {code} tags and it lets you post
``` 

```
 th:x:1000:1000:terry,,,:/home/th:/bin/bash
``` is what i was looking for.

th = your login name
x = means that your password is located in another file (/etc/shadow)
1000:1000 = means that your user id is 1000, and your group id is 1000

terry,,, = is just some personal info that the system doesn't actually need.

/home/th = this tells your system that your home directory is /home/th , which is correct. so now we have to see what the status /home/th really is.

/bin/bash = is the shell you use when you login.

__________________________

ok so your /etc/passwd file is in good order so the problem must lie with the directory /home/th

to see a detailed view of just the folder /home/th we need to execute:
```
ls -Flahd /home/th
``` 
for example:
```
limewire@limewire:~$ ls -Flahd /home/limewire/
drwxr-xr-x  35 limewire limewire 4.0K 2005-12-07 02:25 /home/limewire/
``` 
drwxr-xr-x are the permissions on my home folder(d means directory). meaning
user limewire can read/write/execute
those in group limewire can read/execute
and everyone else can read/execute

a couple things come to mind as to what's wrong.

1.) your permissions are set so that no one can read or write to your home directory
2.) your home directory doesn't exist.

if no one can read or write to your directory, then you can change back with this:
```
chmod -R 755 /home/th
``` and what -R does is set everything inside the folder with the same permisions.

and if for some strange reason you no longer own your home directory then
```
sudo chown -R th:th /home/th
``` 
that's about all I can think of right now, hope this helps.

post what you find out.

---

### Post by xyz on 2005-12-07
I executed
```
ls -Flahd /home/th
chmod -R 755 /home/th
sudo chown -R th:th /home/th
```
and I get one single answer each time
> no access or no such file or dir:confused: 
thanks a lot for taking the time to explain step by step!

---

### Post by fourchannel on 2005-12-07
your welcome.

k, from what I can tell, the reason you get those errors is that you no longer have a home directory. which is not good.

you *can* fix this by running
```
sudo mkdir /home/th
sudo cp /etc/skel/* /home/th
sudo chown th:th /home/th
chmod -R 755 /home/th
``` 
and what that does is:

1.) use root privileges to make a new user directory
2.) copy a default set of files into your home directory, from a skeleton folder, or a basic setup.
3.) change ownership from root, to you
4.) make sure that only YOU have the ability to make changes to what is inside your home folder.

but the bad news is that any files you had saved in your home folder, appear to be gone. and i really don't know how to go about getting them back. :(

but see if that at least lets you login now.

---

### Post by xyz on 2005-12-07
Well,I'm back where I want to be (Ubuntu)! thanks to you.
The good news is that important stuff in /home/th was saved on CD;the bad news is I lost lots of goodies bookmarks...but i'ts a small price to pay!
There was one problem running
```
sudo cp /etc/skel/* /home/th
```
> cp cannot stat '/etc/skel/* :No such file or dir
I don't know whether it's important!
Again thank you for having taken the time to explain...I was thus able to solve the problem and learn something.;-)

---

### Post by fourchannel on 2005-12-07
the ```
/etc/skel
``` directory just holds a blank set of files that bash uses to store your profile. Nowadays it's more of a formality, since bash will create those files if they are not there. (i think...)

and glad i could help.

---

### Post by jdong on 2005-12-07
[QUOTE=xyz]Well,I'm back where I want to be (Ubuntu)! thanks to you.
The good news is that important stuff in /home/th was saved on CD;the bad news is I lost lots of goodies bookmarks...but i'ts a small price to pay!
There was one problem running
```
sudo cp /etc/skel/* /home/th
```

I don't know whether it's important!
Again thank you for having taken the time to explain...I was thus able to solve the problem and learn something.;-)[/QUOTE]

Actually, the command
```
sudo cp /etc/skel/. /home/th/. -R; sudo chown th /home/th -R
```

is more appropriate. "*" doesn't catch hidden files that start with "."

---

