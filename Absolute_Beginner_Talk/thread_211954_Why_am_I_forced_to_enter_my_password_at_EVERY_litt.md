---
title: "Why am I forced to enter my password at EVERY little change or upgrade or install...?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-07-09
Why am I forced to enter my password at EVERY little change or upgrade or install...??? ITs getting quite annoying and I can't seem to remove this function? Is there a way to not have to do this?

Thx for your help on this.

---

### Post by Kuraboy on 2006-07-09
Hi it is for your security I belive :)

there is a way to log in as root always... but you could very easly break the system or someone that takes controll of your system can do everything he wants... 

but if you are a normal users only your home directory is at risk.. and other  drives that you have mounted and have full acess.

---

### Post by codejunkie on 2006-07-09
> **BlackMambo said:**
> Why am I forced to enter my password at EVERY little change or upgrade or install...??? ITs getting quite annoying and I can't seem to remove this function? Is there a way to not have to do this?

Thx for your help on this.
It's for security reasons, so someone or something can't install software without your knowledge. but if you really want to disable the password prompts enter this in a terminal ```
sudo adduser [COLOR=Red]username[/COLOR] sudo
```replace [COLOR=Red]username[/COLOR] with your account name.
Just a warning though this can put your machine at risk for an attack from a virus rootkit etc, so do this at your own risk..

---

### Post by BlackMambo on 2006-07-09
Thx! But no one is going to be able to install stuff unless they're sitting at my machine, right..? I've disabled this now, I'm sure I can re-enable this somewhere later if need be.

---

### Post by _simon_ on 2006-07-09
lol this made me laugh in disbelief. It's like taking the locks off your car because you're fed up with having to lock / unlock it all the time.

---

### Post by johnsymons on 2006-07-09
> **BlackMambo said:**
> Thx! But no one is going to be able to install stuff unless they're sitting at my machine, right..? I've disabled this now, I'm sure I can re-enable this somewhere later if need be.

DUUUUUDE
you really think thats right, then go for it.......
oh and the last bit of your post about re-enabling it sometime....well i think now would be a great time to do it

---

### Post by johnsymons on 2006-07-09
> **_simon_ said:**
> lol this made me laugh in disbelief. It's like taking the locks off your car because you're fed up with having to lock / unlock it all the time.

like the man said, he will re-enable it later if necessary.
like locking your car after someone stole your cd player

---

### Post by Kuraboy on 2006-07-09
> **BlackMambo said:**
> Thx! But **[COLOR="Red"]no one is going to be able to install stuff unless they're sitting at my machine, right..?[/COLOR]** I've disabled this now, I'm sure I can re-enable this somewhere later if need be.

unless you dont have an internet connection, and dont borrow suspesious CD/floppy from friends... then YES.

---

### Post by phen on 2006-07-09
Hi!
It makes your pc more secure on the network, too. Without the password, software could be installed without your admission, like the dialers and adware on windows... It is not going to happen 100% sure, but it could happen, if there are some security holes in applications you use.

It also reminds you whenever you are about to touch any important files...

---

### Post by codejunkie on 2006-07-09
> **BlackMambo said:**
> Thx! But no one is going to be able to install stuff unless they're sitting at my machine, right..? I've disabled this now, I'm sure I can re-enable this somewhere later if need be.
if you run a malicous script or program, copy and paste code into a terminal without knowing what it is first, or you shared the account /password with someone you can still be at risk , so it's a good idea to take precautions before you run things now. it should be ok but by doing this you lowered the security almost to that of windows so you might want to install a virus scanner like clamscan and a rootkit scanner like chkrootkit or rkhunter and a firewall.

and yes BlackMambo you can reenable the password prompt at anytime by entering this into the terminal
```
sudo deluser [COLOR=Red]username[/COLOR] sudo
```replace [COLOR=Red]username[/COLOR] with your account name.

---

### Post by johnsymons on 2006-07-09
> **BlackMambo said:**
> Why am I forced to enter my password at EVERY little change or upgrade or install...??? ITs getting quite annoying and I can't seem to remove this function? Is there a way to not have to do this?

Thx for your help on this.
hey man, i really wouldn't do that, the whole point is that anyone else that you may or may not let use your computer cannot install OR uninstall anything without the password, whether they are in your house using you computer, or doing it remotely (as in from another computer), either with or without your consent and/or knowledge of it happening.
it is the most fundamental security feature, but one of the strongest measure to guard against your system being corrupted by another person.
anyway, all i can say is i wouldn't do it.

---

### Post by hyapadi on 2006-07-09
I agreed with the useful of password. However I think update manager shouldn't need password prompt everytime it executed as it is quite safe. Is there anyway to stop update manager asking for password? I mean, only update manager. The rest ( such as install/remove software ) should still request the password.

Thanks

---

### Post by MrHorus on 2006-07-09
Not really as it still defeats the point of nothing being installed in your system unless you, the person knowing the admin password explicitly authorises it.

---

### Post by Kimm on 2006-07-09
hyapadi, the password promt is not a limitation in the software itself, its the system that wount allow ANY software access to critical system files unless the correct password has been entered.

---

### Post by codejunkie on 2006-07-09
> **hyapadi said:**
> I agreed with the useful of password. However I think update manager shouldn't need password prompt everytime it executed as it is quite safe. Is there anyway to stop update manager asking for password? I mean, only update manager. The rest ( such as install/remove software ) should still request the password.

Thanks
yep you can add applications to the sudoers file and it will execute them with root privliges, i just can't rember how to do it right now but theres a howto floating around here somewhere that explains how to do it.

---

### Post by BlackMambo on 2006-07-09
alright alright.... I'm glad I brightened up everyone's morning.....

I decided to re-enable the password, but I went into Users/Groups and in Advanced, unticked the box that said something like 'allow system admin functions' (this was before I read the post above explaining how to re-enable it)

Now when I try to access Users/Groups it tells me [COLOR="Red"]'Failed to run users-admin. The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the damn system administrator'[/COLOR]

Have aliens already got hold of my system??

By the way, I have to congratulate you guys on how quickly people give help, its amazing.

---

### Post by infoseeker on 2006-07-09
If you REALLY want something more permanent then use> sudo -ibut i'm not sure just how secure that is.

---

### Post by Jucato on 2006-07-09
@hyapadi: I think the reason why the update manager still requires root privileges is not because it is installing something, but because modifies/updates some files that are owned by the administrator, hence, the need for a password.

-------
The ability to install/remove programs, whether locally or remotely, is just one side of the whole permissions issue. Another issue is that it prevents you, or at least reminds you, that the action you are about to take will inevitably have a system-wide effect, meaning it affects not just your user, but the whole system, including any present or future users. take for example the simple *sudo rm -f ** command. It doesn't install/remove any package, but will delete every file on your system. And the fact that the command line has no Trash feature, it's unrecoverable. Of course that's a very extreme example, but what if you "accidentally" delete the whole /usr/bin directory? Or accidentally modifying /boot/grub/menu.lst? Having the system prompt you for the admin password ensures that you are reminded of such risks.

@BlackMambo: AFAIK, you have effictively your user's ability to do any administrative tasks. Not even using sudo. Meaning that you can't add yourself to the group that can use sudo to do administrative work, because you need sudo to do that. I'm not sure if it's possible to still use your username/password in Recovery Mode (the one you can choose in GRUB) to correct this. Unless, of course, you have another user account that has admin privileges (can use sudo).

---

### Post by BlackMambo on 2006-07-09
arrggh. I can't seem to even load Synaptics now... how can I restore my permissions...?

---

### Post by simonn on 2006-07-09
Not 100% on this, but I suspect that you have removed your user from the admin group.

You will need to boot from a bootcd or disk and mount the root directory of your ubuntu installation.

Next, on the root file system mounted above edit /etc/group e.g.

```

% nano [mount]/etc/group

```

The % means you must do this as root (probably the default with a bootcd/disk).

Replace [mount] with the directory where you mounted your ubuntu installations root partition.

Find a line like:

```

admin:x:106:your_user

```

The important bit is the admin bit, this is the line which states the properties of the admin group.

Is your user name listed where your_user is? If not insert your user name there and save it.

Now reboot into ubuntu and you should have your admin rights back.

---

### Post by codejunkie on 2006-07-09
> **BlackMambo said:**
> arrggh. I can't seem to even load Synaptics now... how can I restore my permissions...?
reboot at the grub menu choose the recovery mode if you don't see recovery mode press the ESC key to show the grub menu.
when you get to teh root prompt enter 
```
adduser yourusername admin
```that should fix it.

---

### Post by BlackMambo on 2006-07-09
thx a million codejunkie, that did it!

---

### Post by codejunkie on 2006-07-09
> **BlackMambo said:**
> thx a million codejunkie, that did it!
happy to help

---

### Post by kinematic on 2006-07-09
> **BlackMambo said:**
> Why am I forced to enter my password at EVERY little change or upgrade or install...??? ITs getting quite annoying and I can't seem to remove this function? Is there a way to not have to do this?

Thx for your help on this.

yet another windows user who has never even heard of the windows administrator account ;) 
but if you don't wanna have any security on your ubuntu system whatsoever then go right ahead and disable it ;)

---

### Post by shoot2kill on 2006-07-09
> **kinematic said:**
> yet another windows user who has never even heard of the windows administrator account ;) 
but if you don't wanna have any security on your ubuntu system whatsoever then go right ahead and disable ;)

however, not advisable... (that will lower the stability of the OS dramatically)

---

### Post by kinematic on 2006-07-09
i was being sarcastic :rolleyes:

---

### Post by shoot2kill on 2006-07-09
> **kinematic said:**
> i was being sarcastic :rolleyes:

LOL... some people would post that and be serious.. LOL

---

### Post by BlackMambo on 2006-07-09
> **kinematic said:**
> yet another windows user who has never even heard of the windows administrator account ;)
yet another smug Linux user

---

### Post by rohan! on 2006-07-09
> **codejunkie said:**
> yep you can add applications to the sudoers file and it will execute them with root privliges, i just can't rember how to do it right now but theres a howto floating around here somewhere that explains how to do it.

```
sudo visudo
```
it'll ask you for a password, i'm sorry :P

Append to the bottom...

```
[COLOR="Red"]user  computername[/COLOR]  = NOPASSWD: [COLOR="Red"]command_you_want_to_run,another_command_you_want_to_run [/color]

```

[COLOR="Red"]user [/COLOR] is your username
[COLOR="Red"]computername[/COLOR] is your computername*
[COLOR="Red"]command_you_want_to_run[/COLOR]  is the command you want to run without the password. If you have multiple commands then you seperate them with a comma. Not too difficult.
I think you can put in *apt-get update, apt-get dist-upgrade* 

From then you don't have to run them in sudo -- i think that synaptic will still want root priv though -- it might be an incentive to use the terminal (terminal=much faster) :P

if you want anymore info on visudo and sudoers then you can always...
```
man sudoers
man visudo
```

Good Luck!

(* ref: if your command prompt is unchanged then you can see user and computername easily - [COLOR="Red"]user[/COLOR]@[COLOR="Red"]computername[/COLOR]:~$)

ps.> yet another smug Linux usermost of us were windows users once ;)

---

### Post by Drakkor on 2006-07-09
If it ain't broke.....fix it till it is !!  :idea:

---

### Post by kinematic on 2006-07-09
> **BlackMambo said:**
> yet another smug Linux user

that's not being smug....it's basic security and using some common sense.
i mean why do you think virusses and crapware designed for windows are so highly effective?......because 90% of the average home users always log in as administrator.
(and thnx for the compliment...you're the first person who has ever called me a smug linux user :D  )

---

### Post by aysiu on 2006-07-09
> **BlackMambo said:**
> yet another smug Linux user
I hate to say it, but when it comes to security, Linux users have a right to feel smug.

---

### Post by steve.horsley on 2006-07-09
There are a few heated comments here, but no clear explanation for the newcomer as to why it's regarded as a bad idea to disable the need for these passwords when you do admin stuff.

Of course the original reason, for multiuser systems was the the sysadmin didn't want normal users messing the system over. But even for single user systems, it gives added security from two different perspectives. Firstly mistakes. If you have to go out of your way to get the rights to mess with system config, you are less likely to make a mistake that leaves the system unuseable. 

But the real reason is as protection against malware - viruses, worms and trojans. Although a lot of MS fanboys think the reason that Linux is less bothered by malware is that windows is more popular and therfore the prime target, a second reason is that it is much more difficult for malware to get a good hold on the system. Even if a user is tricked into running bad code somehow, it can't take control of the system if the user doesn't have admin rights. Don't underestimate this line of defence. It's important enough that even MS will be adopting it in Vista, now that they are taking security more seriously. Yes, it's sometimes inconvenient, especially with a new system that you are still shaping to your liking, but I think it's the real reason Linux has fewer security problems.

---

### Post by Thiesen on 2006-07-09
> **BlackMambo said:**
> alright alright.... I'm glad I brightened up everyone's morning.....

I decided to re-enable the password, **but I went into Users/Groups and in Advanced, unticked the box that said something like 'allow system admin functions' (this was before I read the post above explaining how to re-enable it)**

Now when I try to access Users/Groups it tells me [COLOR=Red]'Failed to run users-admin. The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the damn system administrator'[/COLOR]

Have aliens already got hold of my system??

By the way, I have to congratulate you guys on how quickly people give help, its amazing.

You basically REMOVED your priviliges to use sudo (the first Ubuntu account get the sudo privilege by default) so you can't run sudo anymore (the same as would happen if you had added a second account).

However there is a solution to this I think; use the rescue option at the Grub loader when the system loads up (reboot the machine and wait till you see something like "Press ESC..."... do that and change to Rescue-something... after a while you will be logged in as *drumroll*... root... :-) This next step I am unsure if it'll work or not but try "startx" at the prompt and see what happens... if you're lucky you get into x... :-)

---

### Post by Jucato on 2006-07-09
> **steve.horsley said:**
> There are a few heated comments here, but no clear explanation for the newcomer as to why it's regarded as a bad idea to disable the need for these passwords when you do admin stuff.

Take a look a few posts back.  I did give an explanation. I don't know if that was "clear" enough, though.

> Of course the original reason, for multiuser systems was the the sysadmin didn't want normal users messing the system over. But even for single user systems, it gives added security from two different perspectives. Firstly mistakes. If you have to go out of your way to get the rights to mess with system config, you are less likely to make a mistake that leaves the system unuseable. 

But the real reason is as protection against malware - viruses, worms and trojans. Although a lot of MS fanboys think the reason that Linux is less bothered by malware is that windows is more popular and therfore the prime target, a second reason is that it is much more difficult for malware to get a good hold on the system. Even if a user is tricked into running bad code somehow, it can't take control of the system if the user doesn't have admin rights. Don't underestimate this line of defence. It's important enough that even MS will be adopting it in Vista, now that they are taking security more seriously. Yes, it's sometimes inconvenient, especially with a new system that you are still shaping to your liking, but I think it's the real reason Linux has fewer security problems. 
I guess you have it the other way around. The "real" and original reason for the use of sudo is really to limit regular users' ability to make system-wide changes, including the ability to hose down the system because of some error. The incapability of malware and viruses to be installed is just a logical byproduct of that reason. It's just an effect, not the cause nor the reason. It just so happens that it's been the one that's most publicized because of it's anit-Windows/Internet Explorer tones.

---

### Post by mech7 on 2006-07-09
i tried vista and it is the same.. also asking for password for every little thing :)

you cant even install downloaded exe files anymore as they can only unpack in one directory..

---

### Post by Max Luebbe on 2006-07-09
Mech7 beat me too it!

I'm in the Vista Developer Beta program, and there are infinitely more annoyances of this nature.

I love being asked if I want to give the system permission to move items to the trash, then asked if im sure i want to empty the trash, then asked to give the system permission to empty the trash.

In terms of security - the best way to describe Windows Vista is to compare it to trying to fix a sinking boat with a hull full of holes by giving it a new paint job.

Not looking forward to writing apps for it....
(This is not a Microsoft bash. Although I don't like their software, I've got lots of friends there - and lots of smartest people in our field work at redmond. It just seems that their management is hopeless, and they're never going to make a break from supporting all the legacy garbage from Win95 and earlier that would allow them a fresh slate to make a real os.)

Extra Sidenote: I am definately a Linux advocate, I just think that people are more often than not unfair towards whats really going on at Msft.

---

### Post by AirRaven on 2006-07-09
With all the points concerning malware and rootkits etc, do any rootkits or viruses actually *exist* for Linux today?

---

### Post by lapsey on 2006-07-09
> **Max Luebbe said:**
> I love being asked if I want to give the system permission to move items to the trash, then asked if im sure i want to empty the trash, then asked to give the system permission to empty the trash.

In terms of security - the best way to describe Windows Vista is to compare it to trying to fix a sinking boat with a hull full of holes by giving it a new paint job.

The crazy thing is that the 'give password to do serious stuff' thing is actually well applied in linux.

What's more annoying: having to be careful about what you do with your system; or having no control and an internet full of viruses bred on insecure operating systems?

damn it's hard not to sound terribly smug but thems the facts

---

### Post by steve.horsley on 2006-07-10
> **AirRaven said:**
> With all the points concerning malware and rootkits etc, do any rootkits or viruses actually *exist* for Linux today?

My understanding is that no Linux viruses have been found "in the wild" although a number of lab specemins have been created. 

Root kits do exist, and have existed for some years. The most common way to "get rooted" at the moment is (as I understand it) an SSH server with an insecure password. Any publicly visible SSH server will soon find robots connecting to it and brute-force guessing passwords 24x7. That's why it's best to use certificates for your SSH server.

---

### Post by Drakkor on 2006-07-10
Re:Rootkits.....found this in Scot's Newsletter:

Linux Explorer: Guarding Linux Against Rootkits
By Bruno of Amsterdam

Viruses, schmiruses. If you want something really scary to worry about on your Linux box, worry about rootkits. They are far more dangerous than a pesky virus. A rootkit is a toolkit typically installed by a cracker looking to gain access to information on your computer and any network it's attached to. Rootkits are self-hiding toolkits that are activated on system boot up. They typically go active before the operating system completes start up, so they can be difficult for the average antivirus scanner to detect.

A rootkit is completely customized to the hacker who installs it. It may include trojans, viruses and other malware. Rootkits are also able to intercept data from network connections and the keyboard, to steal passwords and attack other computers. They can also alter log files and processes to hide their presence on your computer. For more information on rootkits, see Wikipedia.

Many rootkits will be stopped by a decent firewall, but virus scanners are no protection against rootkits. Running a rootkit checker regularly is strongly recommended. It will scan for rootkits, backdoors, and local exploits.

There are two tools I recommend: chkrootkit and rkhunter.

-----------------------
IMPORTANT: The tips in this document require the use of command-line commands. For more information about how to read and execute Linux command-line prompts and commands, please check the Linux Clues Linux Cheat Sheet, especially Linux Prompt Basics and Linux Command-Line Nomenclature.
-----------------------

chkrootkit is an easy to use tool and included with many distros. Log in as root and run:

# chkrootkit

For a reminder on how to log in as root, check the Linux Cheat Sheet at LinuxClues.com (the navigable, searchable companion site to Linux Explorer): Logging in and out as Root.

If your distro hasn't installed it, download the latest chkrootkit.tar.gz.

Then unzip it with this command:

# tar -xvzf chkrootkit.tar.gz

That extracts files into a folder called chkrootkit-0.46a (for the version we tested). Then type:

# cd chkrootkit-0.46a

Compile the program:

# make sense

You'll see in the terminal something like:

gcc -DHAVE_LASTLOG_H -o chklastlog chklastlog.c
gcc -DHAVE_LASTLOG_H -o chkwtmp chkwtmp.c
gcc -DHAVE_LASTLOG_H -D_FILE_OFFSET_BITS=64 -o ifpromisc ifpromisc.c
gcc -o chkproc chkproc.c
gcc -o chkdirs chkdirs.c
gcc -o check_wtmpx check_wtmpx.c
gcc -static -o strings-static strings.c
gcc -o chkutmp chkutmp.c

>From there you can run the chkrootkit:

# ./chkrootkit

In terminal, you should see something like:

ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not infected
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not infected

The actual list will be considerably longer, of course, covering all the files. If chkrootkit finds something it writes "INFECTED" to the log file. You may be able to restore the process that has been compromised, but you'll probably need to re-install the operating system. In severe cases you may need to wipe the hard disk and re-install.

You could keep chkrootkit on your system and re-run it every week, but that's not good security. Chkrootkit doesn't prevent rootkits from being installed, it merely detects them after the fact. So a hacker could conceivably install a rootkit in between your scans. And any hacker worth his salt would be able to change the configuration to avoid chkrootkit's detection.

Better security is to burn chkrootkit to a CD and run it from there next time. And for the most up-to-date protection, delete the chkrootkit directory after each scan, then download and compile a fresh copy of chkrootkit. It doesn't take long and that way you will be confident of a reliable scan.

Big Game Hunting
Another option for protection against rootkits is rkhunter. It does a bit more than just looking for rootkits. It performs a system-wide check for vulnerable files and dependencies on your system, including:


MD5 hash compare
  * Look for default files used by rootkits
  * Wrong file permissions for binaries
  * Look for suspected strings in LKM and KLD modules
  * Look for hidden files
  * Optional scan within plaintext and binary files
  * 
The rkhunterinstall file is available as tarball. Complete download, decompress, and install instructions are available in the Rootkit Hunder FAQ.

An RPM version for Mandrake/Mandriva is also available, maintained by a third party. Some distros (Slackware for example) also require "Perl-Digest-SHA1" for a successful install.

You can find more installation tips from this thread on the Scot's Newsletter forums.

Once installed, run the program by typing:

# rkhunter -c --createlogfile

Rkhunter runs its scans and writes results and tips to the log file.

To ensure security of your system, don't rely on yourself to perform manual scans. Make rkhunter a daily cron job and have it mail you the scan results. To do that, type:

# rkhunter --cronjob

For more on cron jobs, see Taming the Cron Daemon on Linux Clues.

Have fun securing your system.

Sources
Most of the material found in Linux Explorer comes from Bruno of Amsterdam, lead moderator of the popular All Things Linux forum at Scot's Newsletter Forums. Bruno is helped by All Things Linux co-moderators Peachy, BarryB, and Teacher, as well as other forum members who have posted in the highly useful Tips for Linux Explorers thread (from which Linux Explorer and the LinuxClues.com site are adapted). All previous installments of this section of the newsletter can be found at LinuxClues.com, a service of Scot's Newsletter. For more from Bruno, please see his Tips for Linux Explorers website.

---

