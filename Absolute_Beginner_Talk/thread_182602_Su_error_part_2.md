---
title: "Su error part 2"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by essendon on 2006-05-26
when i type sudo in a terminal I get this:

sudo: unable to lookup via  gethostbyname()

](*,)

---

### Post by bruce89 on 2006-05-26
Are you in the /etc/sudoers file?
Are you running as root?

---

### Post by essendon on 2006-05-26
I am a normal user.

i opened the termial program from the system menu

---

### Post by essendon on 2006-05-26
also the host name after the @ symbol is missing.

---

### Post by steve.horsley on 2006-05-26
You need recovery mode to fix this. Boot recovery mode (this should give you a root prompt - with a # instead of a $). 

Choose a hostname for the PC, e.g. MyPC
Edit the file /etc/hostname so that this hostname is the only thing in the file. Launch the editor with the command:
> nano /etc/hostname

Now you need to make sure that hostname is mentioned in the file /etc/hosts as a name against the IP address 127.0.0.1. Make sure you use exactly the name name as you put in /etc/hostname. Here is a copy of the appropriate line from my PC: > 127.0.0.1       localhost StevesPC Launch the editor with the command > nano /etc/hosts

Having saved, reboot and see if it's any better.

---

### Post by Mustard on 2006-05-26
Steve.horsley's instructions are correct, but I can't resist the temptation to throw in my 'premade' guide for this error. :)

**How to edit the /etc/hosts file (troubleshooting guide)**

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

**Additional problems that may be present**
An additional issue you might need to look into in some cases, is whether a file exists in the /etc/ folder called 'hostname'.  For various reasons, usually related to user intervention, it will sometimes not exist at all, or exists but is a blank file.  Normally the /etc/hostname will look like this (using my own host file as an example)..

```
slave
```

If it is absent then you should create a file in /etc/ folder called *hostname* and edit it to include your chosen hostname.  You can create a new file by opening the nano text editor using the path and name of the file you wish to create.
```
nano /etc/hostname
```

**Command relating to the hostname (I've included this for informational purposes)**
An additional command you can look at with regards to hostnames is this command below.
```
hostname
#returns the current hostname
hostname <hostname>
#sets the hostname according to the value entered for <hostname>

```

---

