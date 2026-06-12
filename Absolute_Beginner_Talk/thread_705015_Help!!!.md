---
title: "Help!!!"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by internetishere on 2008-02-22
ok now that your reading this i need some help
look at this for a minute

killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
sudo chown -R teko:teko ~/.etwolf/
et

i need to make that into a script (.sh) ive tried making it like that but it stops after sudo -i heres what it says

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@teko-desktop:~#

i would apreciate any help on makeing this into a running script
p.s. i have fakeroot

---

### Post by kool_kat_os on 2008-02-22
i think it tells you what to do? Or maybe i just suck at reading...

---

### Post by internetishere on 2008-02-22
> **kool_kat_os said:**
> i think it tells you what to do? Or maybe i just suck at reading...

i could run all that copy and pasteing it in terminal but thats a hasel takes to long and i have to do it at every reboot so i want to make a script that basically when i click on it and click run in terminal
it will do all those commands for me maybe i have to rearrange them or something??? or change parts of the commands or add to it???
p.s. its a script to make sound work and allow to download maps in enemy territory.

---

### Post by steveneddy on 2008-02-22
> **kool_kat_os said:**
> i think it tells you what to do? Or maybe i just suck at reading...

Edit

Not sure, but I think it start with:

#!/bin/sh

or 

#!/bash/sh

but I'm no programmer.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-22
> **internetishere said:**
> ok now that your reading this i need some help
look at this for a minute

killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
sudo chown -R teko:teko ~/.etwolf/
et

i need to make that into a script (.sh) ive tried making it like that but it stops after sudo -i heres what it says

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@teko-desktop:~#

i would apreciate any help on makeing this into a running script
p.s. i have fakeroot

Try this:
```

#!/bin/bash

sudo su
killall esd
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
chown -R teko:teko /home/teko/.etwolf/
exit
et

```

Save the script to /home/teko/bin/run_et.sh
and type this in terminal:
```

chmod +x /home/teko/bin/run_et.sh

```

PS: You'll prompted for "sudo" password the each time your run "run_et.sh".
PS2: You must run the "run_et.sh" script in the terminal.
PS3: Just a suggestion, but next time you post a thread, please use a more descriptive title :)

---

### Post by internetishere on 2008-02-22
> **Milk & Toast & Honey said:**
> Try this:
```

#!/bin/bash

sudo su
killall esd
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
chown -R teko:teko /home/teko/.etwolf/
exit
et

```

Save the script to /home/teko/bin/run_et.sh
and type this in terminal:
```

chmod +x /home/teko/bin/run_et.sh

```

PS: You'll prompted for "sudo" password the each time your run "run_et.sh".
PS2: You must run the "run_et.sh" script in the terminal.
PS3: Just a suggestion, but next time you post a thread, please use a more descriptive title :)

sounds like it will work one prob though i dont have a bin directory
i have a filesytem/bin and a home/teko but no home/teko/bin
should i make that directory?

---

### Post by mgranet on 2008-02-22
How would one make the shell script autoload at boot? Cronjob?

---

### Post by internetishere on 2008-02-22
> **mgranet said:**
> How would one make the shell script autoload at boot? Cronjob?

huh???

---

### Post by mgranet on 2008-02-22
Yeah, sorry. I kind of threadjacked there. I saw shell scripting and wandered...

---

### Post by mbsullivan on 2008-02-22
Hi All,

I have a few things to add to this discussion:

First off, it should be noted that extreme care should always be taken when making  a script that executes commands with root access. As a general rule, you never want to execute any commands that require root permissions in a script, because if somebody modifies your script (i.e. adds some nastiness that reformats your computer, etc), you will most likely blindly execute the script anyway.

That being said, if we are very careful, it should be possible to create a script that can't be modified without root access and will be fine to execute. The easiest way to do this would be to:

(1) Make the script, as has been recommended.

(3) Change the permissions of the file to allow it to be executed by the root user, but NOT read and written to:

```
chmod 100 [filename]
```

(4) Change the owner/group of the file to root, so that you need root access to modify permissions/ownership of the file:

```
sudo chown root [filename]; sudo chgrp root [filename]
```

Afterwards, the script should function normally, and you can call it by saying:

```
sudo ./[filename]
```

> sounds like it will work one prob though i dont have a bin directory
i have a filesytem/bin and a home/teko but no home/teko/bin
should i make that directory?

It doesn't matter where it is, so long as you can remember its location. You don't need to make a ~/bin/ directory. In fact, since you've made it owned by root, you could even place it in your "proper" bin directory: 

```
sudo mv [filename] /usr/bin/
```

Then you can always execute your command without providing a leading path (just like a "regular" program). Or, alternatively, you could make it be executed at startup, like somebody else asked about. Or you could do both.

> How would one make the shell script autoload at boot? Cronjob?

Nope... cron jobs are used for periodically scheduled execution of programs. To execute a script @ boot, you can add the path to the script to /etc/rc.local (which is a script itself), or you could do it the proper way:

(1) place the script in /etc/init.d

(2) add it to the proper start levels:

```
sudo update-rc.d [filename] defaults
```

Hope this helps!
Mike

---

### Post by Milk &amp; Toast &amp; Honey on 2008-02-22
> **internetishere said:**
> sounds like it will work one prob though i dont have a bin directory
i have a filesytem/bin and a home/teko but no home/teko/bin
should i make that directory?

Sorry, is your username "teko"? If not, change "'/home/teko/bin" to "/home/yourname/bin".
And yes, you should create the "bin" directory in your "home" folder.

---

### Post by bodhi.zazen on 2008-02-23
Well, if you just want to run a few command at boot add them to 

/etc/rc.local

Be sure to add a & to anything that needs to run in the backgound.

/etc/rc.lcoal is run as root after all other boot scripts.

Add this to /etc/rc.local :

> killall esd
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
sudo chown -R teko:teko /home/teko/.etwolf/

===============

Rambelings of a mad man :

Also sudo works just fine in scripts and is not a security risk.

Example:

here is a script called "sudo_script"

> /bin/bash
echo "who am i"
echo `whoami`
echo
echo "fdisk -l"
fdisk -l
echo
echo "sudo fdisk -l"
sudo fdisk -l

OK, lets run the script as a user outside of the admin group :

Here is what I get when "test" runs that script :

> test@VirtualUbuntu:~$ ~/bin/sudo_script 
who am i
test

fdisk -l

sudo fdisk -l
test is not in the sudoers file.  This incident will be reported.

OK, now when I run the script as a user with admin

> bodhi@VirtualUbuntu:~$ ~/bin/sudo_script
who am i
bodhi

fdisk -l
/home/bodhi/bin/sudo_script: 6: fdisk: not found

sudo fdisk -l
[sudo] password for bodhi:  <-- Entered wrong PW, nothing happened

Now with entering the password:

> bodhi@VirtualUbuntu:~$ ~/bin/sudo_script
who am i
bodhi

fdisk -l
/home/bodhi/bin/sudo_script: 6: fdisk: not found

sudo fdisk -l
[sudo] password for bodhi:  <-- Enter correct password

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000842a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1180     9478318+  83  Linux
/dev/sda2            1181        1305     1004062+  82  Linux swap / Solaris
bodhi@VirtualUbuntu:~$  

The problem with sudo in scripting is that usually people do not want to enter a password. There are several solutions to this as well, but that is another discussion.

---

### Post by internetishere on 2008-02-23
> **bodhi.zazen said:**
> Well, if you just want to run a few command at boot add them to 

/etc/rc.local

Be sure to add a & to anything that needs to run in the backgound.

/etc/rc.lcoal is run as root after all other boot scripts.

Add this to /etc/rc.local :



===============

Rambelings of a mad man :

Also sudo works just fine in scripts and is not a security risk.

Example:

here is a script called "sudo_script"



OK, lets run the script as a user outside of the admin group :

Here is what I get when "test" runs that script :



OK, now when I run the script as a user with admin



Now with entering the password:



The problem with sudo in scripting is that usually people do not want to enter a password. There are several solutions to this as well, but that is another discussion.

i like your idea but my rc.local says this
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
should i just replace that with what you said???

---

### Post by internetishere on 2008-02-23
srry double post but also i cant save the rc.local with the modifications you said
it says the owner is root and i dont know how to change that

---

### Post by Mustard on 2008-02-23
> **internetishere said:**
> srry double post but also i cant save the rc.local with the modifications you said
it says the owner is root and i dont know how to change that

You dont  want to change it to anything.  You want it to remain owned by root.  The purpose of it being owned by root, is that only root should have control over that file for security reasons.

Approach the problem from the opposite direction.  Ask instead '**How can I be root** so that I can change the files contents?'  It would seem that you need to do some research on permissions and ownership before you start getting too involved in this task.

---

### Post by Mustard on 2008-02-23
Try reading through this link to understand why Ubuntu uses the **sudo** command and its relationship to executing commands as **root**.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by JoshuaRL on 2008-02-23
Okay, I'm not very familiar with scripting but couldn't he use "gksu" instead of all the chmod so that whenever the script was run it graphically asked for the root password?

Or would there be issues with running like that?

---

### Post by mbsullivan on 2008-02-23
> Also sudo works just fine in scripts and is not a security risk.

Sorry, but that's just not true. The problem arises because sudo'ed commands in close proximity all operate off of a single provided password, and with sudo'ed commands, one EXPECTS to put in a root password, 

For example, let's pretend somebody has a very important file on the root of their machine called /IMANIMPORTANTFILE (I'm not using a real example in case somebody actually runs this script). If you want, create it with:

```
sudo touch /IMANIMPORTANTFILE
```

Now, you have your script, with a sudo'ed command that you provide a password for:

```
#!/bin/sh

sudo echo "I AM ROOT"
```

As you've shown, this script operates as one might expect (you have to provide a password). Now say the file permissions are set incorrectly (i.e. can be edited without root permissions) and me, an evil person out to no good, MODIFIES the script to read:


```
#!/bin/sh

sudo echo "I AM ROOT"
sudo rm /IMANIMPORTANTFILE
```

... Next time you run your script, you provide the password, like you always do. It only asks once. Both commands will be executed. Your important file is lost. In actuality, the executed action could be arbitrarily wicked. That's why you always need to make absolutely sure that scripts that require root access belong to root, and can't be globally modified.

Mike

---

### Post by mbsullivan on 2008-02-23
> i like your idea but my rc.local says this
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
should i just replace that with what you said???

Put it before the "exit 0" statement.

> Okay, I'm not very familiar with scripting but couldn't he use "gksu" instead of all the chmod so that whenever the script was run it graphically asked for the root password?

Or would there be issues with running like that?

The "chmoding" doesn't make it execute as root... it just makes sure that anybody who isn't root can't modify the file. Either way you'll have to do some command (gksu or sudo) to make it execute with permission.

See the above post I made... despite what some people on these forums may say, correctly setting the permissions (and, most importantly, the ownership) of any script containing privileged instructions is critical!

Mike

---

### Post by internetishere on 2008-02-23
ok so i think were all wanderin a bit to far here. the rc.local thing i wanna go with that idea but it belongs to root. so how do i edit the rc.local thing to add what you guys said to add?

---

### Post by JoshuaRL on 2008-02-23
> **Mustard said:**
> You dont  want to change it to anything.  You want it to remain owned by root.  The purpose of it being owned by root, is that only root should have control over that file for security reasons.

Approach the problem from the opposite direction.  Ask instead '**How can I be root** so that I can change the files contents?'  It would seem that you need to do some research on permissions and ownership before you start getting too involved in this task.

> **Mustard said:**
> Try reading through this link to understand why Ubuntu uses the **sudo** command and its relationship to executing commands as **root**.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Your answer would lie here Internetshere.

---

### Post by internetishere on 2008-02-23
can someone just please give me the specific command to type in terminal to edit rc.local

---

### Post by JoshuaRL on 2008-02-23
Dude, you'll need to log in as root to mess with it.

That's what Mustard was trying to point you to.

Just be really careful you don't do anything else.  You can really mess up some stuff logged in as root.

---

### Post by seventhc on 2008-02-23
```

gksu gedit /etc/rc.local

```

---

### Post by internetishere on 2008-02-23
ok i was able to add that to rc.local but it didnt work in fact none of this has worked is there any other ideas or ways to do it?

---

### Post by internetishere on 2008-02-23
anyone?

---

### Post by bodhi.zazen on 2008-02-23
> **mbsullivan said:**
> Sorry, but that's just not true.

<clip>

As you've shown, this script operates as one might expect (you have to provide a password). Now say the file permissions are set incorrectly ...

<clip>

Mike

I disagree, that is poor permissions. If you are sloppy with permissions many (bad) things are possible.

> **internetishere said:**
> anyone?

1. Exactly what are you trying to do, what commands are you running ?

2. Edit /etc/rc.local with [gksu gedit /etc/rc.local[/code]

When you boot, rc.local is run as root, so there is no need for sudo or su or any of that, just the commands.

Add those ABOVE "exit 0"

TIP: Always use the full path to commands and files in rc.local (rather then ./file user /home/user_name/file)

3. If you need help, please re-post the commands you need to run and the current contents of rc.local ;)

---

### Post by mbsullivan on 2008-02-24
> I disagree, that is poor permissions. If you are sloppy with permissions many (bad) things are possible.

The permissions part isn't really a necessary factor in the equation -- it just simplifies it. The fact remains that if you (the user) own a file, then any program you execute can set the permissions of it to be writable, inject a malicious command, and could even reset the permissions afterwards. We're talking about programs YOU run changing the script. Think about it... it's really not a permissions failure, but an ownership oversight which deserves more attention on these forums, I feel. This sort of attack is the most transparent when you have sudo'ed commands in a file, so it is smart to have any file requiring root access to be owned by root.

True, an attack of this sort probably won't affect a desktop user any more than the 1,000,000 other ways to hose your machine (accidental or otherwise). However, lots of people read these forums, and it is a security problem. If a sysadmin who's managing machines with 15,000 users makes a script that requires root access that's owned by a normal user, that's a big problem. That means that any program he/she executes has the potential to change that script, and put the data of all users in jeopardy.

> ok i was able to add that to rc.local but it didnt work in fact none of this has worked is there any other ideas or ways to do it?

internetisphere, what didn't work? 

Putting the commands in rc.local will make them execute at startup... nothing less, nothing more. If you want this to happen (which isn't clear, reading over the previous posts), the contents of your rc.local file should look like the following (you can check and make sure that they're correct):

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


killall esd
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
chown -R teko:teko ~/.etwolf/
et

exit 0
```

Originally, the premise of this thread was to come up with a script containing these commands. If you don't need them executed at startup, and just need a script, just create a file named [filename].sh, that contains the following:

```
#!/bin/sh

killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
sudo chown -R teko:teko ~/.etwolf/
et
```

If you want to protect yourself from some malicious behavior, you can change the ownership of the file. Either way, you need to set it to be executable:

```
chmod +x [filename].sh
sudo chown root [filename].sh
```

Then just execute the file, using ./[filename].sh. 

Mike

---

### Post by bodhi.zazen on 2008-02-24
The line :

> chown -R teko:teko ~/.etwolf/  is too vague.

As rc.local is running as root, ~ = /root

I think we want /home/teko/.etwolf

Again I advise you use the full path rather then ~ or ./ , they are too vague (and this kind of vagueness is also a potential security hole.)

Also my guess it > et is a typo

---

### Post by mbsullivan on 2008-02-24
> 
Again I advise you use the full path rather then ~ or ./ , they are too vague (and this kind of vagueness is also a potential security hole.)

Haha actually this is true... although normally only from an internal perspective (a verified user in your network can sometimes gain root access through these means).

> Also my guess it
Quote:
et
is a typo

Yeah... I wondered about that myself, but to each his own... internetishere, I think we need a bit more clarification about what you're having problems with before we can be of much more help.

Mike

---

