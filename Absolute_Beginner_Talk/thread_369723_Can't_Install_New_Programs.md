---
title: "Can't Install New Programs"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by kurtstricker on 2007-02-24
Total Newby here...

I can no longer install or remove programs.  When running add/remove programs, I can select a program to install  for example, Kopete, after clicking OK, I receive the confirmation dialog asking to Apply the changes.  I click Apply and the Add/Remove dialog disappears completely.  I also cannot remove programs, for example, GAIM.  This notifies me to run the Synaptic package installer to uninstall.  When I run the Synaptic Program Manager nothing comes up at all.  Help!  Thanks, I'm working on converting before I'm forced to VISTA...anything but that...

---

### Post by taurus on 2007-02-24
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install kopete
sudo aptitude remove gaim
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by kurtstricker on 2007-02-26
Thanks for the reply.

I receive the following:

kim@kim-desktop:~$ sudo aptitude update
sudo: unable to lookup kim-desktop via gethostbyname()
kim@kim-desktop:~$ cd..
bash: cd..: command not found

---

### Post by kurtstricker on 2007-02-27
I found some threads that point to the hosts file as the problem for what I was experiencing.  I edited the host file and now I receive the following:

kim@kim-desktop:~$ sudo aptitude update
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0


How could I have broken this operating system so easily and quickly?  Do I need to reinstall it?  Seriously, I'm new to Ubuntu but have 25 years of computer  experience...

---

### Post by Bachstelze on 2007-02-27
How exactly did you edit your hosts file ? Please paste it here.

---

### Post by taurus on 2007-02-27
You need to use the same name in /etc/hostname as well as /etc/hosts or sudo will break.  So, post both of them here and besides, did you modify /etc/sudoers at all?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by Tulx on 2007-02-27
Another newbie here, I have no idea what these errors mean. But have you installed updates. It solved some some serious problems. After installed from cd ubuntu was quite broke. I messed up my first installion too:)  I hope that helps.

---

### Post by kurtstricker on 2007-02-27
Hosts.

127.0.1.1 kim-desktop




# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.1 stricker

Hostname.
kim-desktop

I edited the hosts file using vi in recovery mode.

---

### Post by taurus on 2007-02-27
Shouldn't the first line in /etc/hosts read like this?

```
127.0.0.1     localhost
```

---

### Post by rjfioravanti on 2007-02-27
Thats what mine looks like too

leave the 127.0.1.1   computer name 

but before that add the line

127.0.0.1      localhost

---

### Post by kurtstricker on 2007-02-27
OK.  

Hosts now looks like this:
127.0.0.1 localhost
127.0.1.1 kim-desktop




# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.1 stricker


and Hostname:
kim-desktop


Still having the same problems:

kim@kim-desktop:/$ sudo aptitude update
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
kim@kim-desktop:/$ 

This looks like a permissions problem.  I cannot run Root Terminal either.  I'm no longer prompted for the root password.

---

### Post by taurus on 2007-02-27
Did you edit or play around with /etc/sudoers at all?  After making changes to /etc/hosts, did you reboot?  What are the output of these two commands?

```
ls -la /etc/sudoers
sudo cat /etc/sudoers
```

---

### Post by kurtstricker on 2007-02-27
kim@kim-desktop:/$ ls -la /etc/sudoers
-r--r----- 1 root root 1031 2007-02-12 12:38 /etc/sudoers
kim@kim-desktop:/$ sudo cat /etc/sudoers
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
kim@kim-desktop:/$

---

### Post by kurtstricker on 2007-02-27
I did  not play in the sudoers at all...

---

### Post by taurus on 2007-02-27
Boot into recovery mode from GRUB menu and post your /etc/sudoers again.

```
cat /etc/sudoers
```

---

### Post by kurtstricker on 2007-02-27
Is there a way to pipe the output of the cat  to a file or the printer?  The output is a little much to copy and post without erroring...

---

### Post by taurus on 2007-02-27
Do you have a USB thumbdrive or floppy drive?  Or better yet, boot your machine with the LiveCD (so you would have a GUI), mount the partition where / is, and paste the content of /etc/sudoers from the harddrive here.

If you want to use the LiveCD, post this command here so I would know which partition is your /.

```
sudo fdisk -l
```

---

### Post by kurtstricker on 2007-02-27
I have a thumb drive in the machine right now, but don't have the LiveCD handy.  How would I copy to it?  The thumb is at /media/LEXAR MEDIA.  Pardon my ignorance, but what is /?  Is that the root?

---

### Post by taurus on 2007-02-27
Yes, / is the root.

Okay, you can copy /etc/sudoers to your thumbdrive in recovery mode with

```
cp /etc/sudoers "/media/LEXAR MEDIA"
umount "/media/LEXAR MEDIA"
shutdown -r now
```

---

### Post by kurtstricker on 2007-02-27
That didn't work too well.  does not  look like the LEXAR device is mounted.  All this did was create a file (?) called LEXAR MEDIA in the media directory.

---

### Post by kurtstricker on 2007-02-27
Here's the contents of sudoers.  I created a password for root so I now have root that is how I was able to access the file.  There looks like some junk at the top should I use visudo and edit this.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Entries for Smb4K users.
# Generated by Smb4K. Please do not modify!
User_Alias      SMB4KUSERS = kim
Defaults:SMB4KUSERS     env_keep="PASSWD USER"
SMB4KUSERS      kim-desktop = NOPASSWD: /usr/bin/smb4k_kill
SMB4KUSERS      kim-desktop = NOPASSWD: /usr/bin/smb4k_umount
SMB4KUSERS      kim-desktop = NOPASSWD: /usr/bin/smb4k_mount
# End of Smb4K user entries.

---

### Post by kurtstricker on 2007-02-27
Problem solved!

Taurus thanks a ton for your help!

Here's what I did:

1.  Created a password for root by rebooting in recovery mode using passwd command.  Restarted.
2.  Used su- to login as root with the new password.  As root, used visudo to edit the sudoers file.  Restarted.

---

### Post by taurus on 2007-02-27
Glad to hear you finally got your system working again.  Just be real careful with the /etc/sudoers and both /etc/hostname & /etc/hosts.  ;)

---

