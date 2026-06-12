---
title: "Changed Hosts file... lost sudo.... HELP!"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Vinic0com on 2006-03-28
I've been trying all day to have my internet settings stick after the box has been turned off.  Came across a note in this forum about editing the /etc/hosts file, which I played around with a bit.

In the first line, I changed the second localhost to my actual hostname (routers given name: misn ).  Now sudo commands don't recognize me.

Here's what's in my hosts file now:

change127.0.0.1 localhost.localdomain misn cc

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Previously, the first line was:

change127.0.0.1 localhost.localdomain localhost cc

Here's what happens in the terminal:


cc@cc:~$ sudo gedit /etc/hosts
sudo: unable to lookup cc via gethostbyname()


Is a total reinstall the only way around?

TIA

clyde

---

### Post by sn123 on 2006-03-28
[QUOTE=Vinic0com]I've been trying all day to have my internet settings stick after the box has been turned off.  Came across a note in this forum about editing the /etc/hosts file, which I played around with a bit.

In the first line, I changed the second localhost to my actual hostname (routers given name: misn ).  Now sudo commands don't recognize me.

Here's what's in my hosts file now:

change127.0.0.1 localhost.localdomain misn cc

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Previously, the first line was:

change127.0.0.1 localhost.localdomain localhost cc

Here's what happens in the terminal:


cc@cc:~$ sudo gedit /etc/hosts
sudo: unable to lookup cc via gethostbyname()


Is a total reinstall the only way around?

TIA

clyde[/QUOTE]
Boot into linux using recovery mode & fix up the messed up hosts file, restart and boot into the normal linux kernel, sudo should work then.

S

---

### Post by Vinic0com on 2006-03-28
[QUOTE=sn123]Boot into linux using recovery mode & fix up the messed up hosts file, restart and boot into the normal linux kernel, sudo should work then.

S[/QUOTE]

I did tried that.  But don't really know enough about how to do that.  Could you step me throug the process.... I can get to the prompt, and tried the sudo command from there (only thing I know to do to access that file), and it gave me the same response as it did from the teminal in gnome.

clyde

---

### Post by sn123 on 2006-03-28
[QUOTE=Vinic0com]I did tried that.  But don't really know enough about how to do that.  Could you step me throug the process.... I can get to the prompt, and tried the sudo command from there (only thing I know to do to access that file), and it gave me the same response as it did from the teminal in gnome.

clyde[/QUOTE]
When you login in recovery mode, you don't have to use sudo (you're logged in as root), so if you made a backup of your hosts file then all you have to do is to rename the backup file to hosts file or else use the gedit (without sudo) and revert back any changes that you've made.
```

$ gedit /etc/hosts

```
(note no sudo with gedit when in recovery mode).

HTH,
S

---

### Post by IDipSkoalMint on 2006-03-28
This won't really help now, but in the future, *always* make a back-up of any config file you're going to edit so you don't have this problem ;)

---

### Post by Vinic0com on 2006-03-28
getting 

"(gedit:6125): Gtk-WARNING **: cannot open display :"

when using

gedit /etc/hosts

in the recovery mode.

also tried adding the $ first, and it kicks back

"bash: $: command not found"

How can I rename a backup version?

clyde

---

### Post by Mustard on 2006-03-28
You don't need to totally reinstall.  You just need to edit it back to a working hosts file.  That first line looks all over the place.  What is this 'change' part?

Also gedit is not going to work in recovery mode, as it's a graphical editor and recovery mode is a command line environment.  You are going to need a command line editor like nano.

Here are some instructions for editing your /etc/hosts file anyway..

HowToEditEtcHostsCreated Friday 20/01/2006 10:34

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the **recovery mode** option from the **grub menu** at bootup.

When you get to a root prompt,
**1. Making a backup of misconfigured file**
If you really have no idea what you are doing then first make a backup of the file just in case you really muck things up.  A misconfigured file is at least a reference you can work from.
```
#make a backup
cp /etc/hosts /etc/hosts_backup
```
**2. Editing the misconfigured file**
Open up the /etc/hosts file with this command.
```

#this will open the hosts file in a command line text editor
nano /etc/hosts 
```

(To save files in in nano use ctrl + o and to exit from nano use ctrl + x)

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

An additional command you can look at with regards to hostnames is this command below.

```
hostname
#returns the current hostname
hostname <hostname>
#sets the hostname according to the value entered for <hostname>

```

---

### Post by Mustard on 2006-03-28
[QUOTE=Vinic0com]getting 

"(gedit:6125): Gtk-WARNING **: cannot open display :"
when using
gedit /etc/hosts
in the recovery mode.
also tried adding the $ first, and it kicks back
"bash: $: command not found"
How can I rename a backup version?
clyde[/QUOTE]

Use nano in command line.  Gedit is a graphical text editor and won't work in a command line environment.

To backup a file use the copy command, cp

```
#example of making a backup of the hosts file
#when logged in as root
cp /etc/hosts /etc/hosts_backup

#if your sudo was functioning then you would do this

sudo cp /etc/hosts /etc/hosts_backup
```

---

### Post by sn123 on 2006-03-28
[QUOTE=Mustard]Use nano in command line.  Gedit is a graphical text editor and won't work in a command line environment.

To backup a file use the copy command, cp

```
#example of making a backup of the hosts file
#when logged in as root
cp /etc/hosts /etc/hosts_backup

#if your sudo was functioning then you would do this

sudo cp /etc/hosts /etc/hosts_backup
```[/QUOTE]
EDIT: sorry didn't read the previous post by mustard carefully enough, follow the instructions and you should be fine -S.
you **don't** need sudo in recovery mode cause you're always logged in as root in recovery.
so you can do:
[code]
cp /etc/hosts_back /etc/hosts
[/code
(Assuming that you had named your backup file as hosts_back and you want to overwrite the messed up hosts file with that).
Otherwise you can use nano to fix the messed up lines in your hosts file.

HTH,
S
ps: $ was used to depict a prompt in my previous post.

---

### Post by Mustard on 2006-03-28
[QUOTE=sn123]EDIT: sorry didn't read the previous post by mustard carefully enough, follow the instructions and you should be fine -S.
you **don't** need sudo in recovery mode cause you're always logged in as root in recovery.
so you can do:
```

cp /etc/hosts_back /etc/hosts

```
(Assuming that you had named your backup file as hosts_back and you want to overwrite the messed up hosts file with that).
Otherwise you can use nano to fix the messed up lines in your hosts file.

HTH,
S
ps: $ was used to depict a prompt in my previous post.[/QUOTE]

Yep, I was just giving an example.  I also just realised that I never explained how to cp the backup back to the original. :)  From what I can see though the backup is messed up to, I've never seen the word 'change' tacked on to '127.0.0.1' like it is in the above examples.  It exists in both the old copy and the new copy, so thats why I suspect the old copy is stuffed too.

---

### Post by sn123 on 2006-03-28
[QUOTE=Mustard]I've never seen the word 'change' tacked on to '127.0.0.1' like it is in the above examples.  It exists in both the old copy and the new copy, so thats why I suspect the old copy is stuffed too.[/QUOTE]
great observation! I never even noticed "change" stuffed in both files! I assumed change was the word which poster used to denote that this was the line he changed/modified :D

S

---

### Post by Vinic0com on 2006-03-29
Ok, got the hosts file back to it's original state (including that "change" text that I'm not sure how got there. I had manually copied it in the post.... it was not in the original file).  Got command of the sudo back in the terminal.  Internet settings seem to be stable (main problem I started with.... would have to reset dhclient and router if box was turned off).

But what's really cool is the network is working perfectly!  I have full access to and from all pc's ( other 4 are all xp at this point).

I'm pretty sure my whole problem was in the ROM.  These pc's I'm working with came from surplus of a local university and had been wiped clean.  There was setting in ROM for "Plugins"..... set thta on and everything seems to have fallen in place.

Every once and awhile a blind squirrel will find a nut.  'Course it helps to have others pointing the way.  Thanx a million for your help!

On to the next PC!!!:mrgreen: :mrgreen: :mrgreen: :mrgreen: :mrgreen: 

Kind Regards,

Clyde Gill
[http://www.PeacefulBend.com](http://www.PeacefulBend.com)

---

### Post by Mustard on 2006-03-29
Well done, and good luck with the next PC. :)

---

### Post by piccolo solo on 2006-04-07
Thank you thank you Mustard & company.
Newbie install yesterday with a number of problems - but now I can actually access utilities & enter commands to find out whats going on

yours gratefully

---

### Post by Mustard on 2006-04-07
[QUOTE=piccolo solo]Thank you thank you Mustard & company.
Newbie install yesterday with a number of problems - but now I can actually access utilities & enter commands to find out whats going on

yours gratefully[/QUOTE]

I'm glad you could benefit from an old thread.   Welcome to the world of Ubuntu. :)

---

### Post by Terecia on 2006-04-16
Hi,
I've followed the thread, since I've managed to erase the contents of the etc/hosts file, have now rebooted into recovery mode, changed the etc/hosts file with nano - but don't now howto get out of the file - and get the changes saved?
I have made several searches in the forums, to find the answer to my question - but without result.
Would be very greatful for some help.
Suppose don't need to mention that I'm tooootal newbie? :rolleyes: 
Thanks in advance!
/Terecia

---

### Post by htinn on 2006-04-16
Ctrl+o = save
Ctrl+x = exit

---

### Post by Terecia on 2006-04-16
Thank you very much! :-D
/Terecia

---

### Post by Mustard on 2006-04-16
I'll edit the guide I use to point this out explicitly.  Thanks for the input.

---

### Post by findik1 on 2006-04-19
Hey man, thanks, it also worked for me now when I did step by step what yu wrote :D . I remember you wrote previously to my question too. The answers are straighforward for the starters to Ubuntu. You are mentioning you prepared documents for these issues. Do you have a web page for that or they are in the threads?

Thanks again =D> 
findik

[QUOTE=Mustard]You don't need to totally reinstall.  You just need to edit it back to a working hosts file.  That first line looks all over the place.  What is this 'change' part?

Also gedit is not going to work in recovery mode, as it's a graphical editor and recovery mode is a command line environment.  You are going to need a command line editor like nano.

Here are some instructions for editing your /etc/hosts file anyway..

HowToEditEtcHostsCreated Friday 20/01/2006 10:34

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the **recovery mode** option from the **grub menu** at bootup.

When you get to a root prompt,
**1. Making a backup of misconfigured file**
If you really have no idea what you are doing then first make a backup of the file just in case you really muck things up.  A misconfigured file is at least a reference you can work from.
```
#make a backup
cp /etc/hosts /etc/hosts_backup
```
**2. Editing the misconfigured file**
Open up the /etc/hosts file with this command.
```

#this will open the hosts file in a command line text editor
nano /etc/hosts 
```

(To save files in in nano use ctrl + o and to exit from nano use ctrl + x)

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

An additional command you can look at with regards to hostnames is this command below.

```
hostname
#returns the current hostname
hostname <hostname>
#sets the hostname according to the value entered for <hostname>

```[/QUOTE]

---

### Post by Mustard on 2006-04-19
Yeah, I updated the post in this thread to reflect the changes, so this should be the most up to date guide that I have. :)

I have discovered another issue that people sometimes have in which the 'hostname' file in the /etc/ doesn't exist. It returns a completely different error code though.  Usually at the gdm login prompt it give a message saying that it can't find something, usually an empty string, or I have seen a '.' character, and warns that the installation might not work well without it.   I'm still trying to work out how this occurs (it happened to me the other day while playing around with a Debian from Scratch installation).  This particular issue is easy to fix though, as you just create a file called hostname in your /etc/ folder and put the hostname inside this file.

This new issue that I'm trying to work out is separate from the problems people have had in this thread, although still related to host problems, but can occur at the same time.

---

