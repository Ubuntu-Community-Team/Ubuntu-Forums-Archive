---
title: "Samba: Mixing user-level security with share-level behavior"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by WebHorn on 2007-07-02
This special Samba problem took me a couple of days to figure out and I wanted to document the fix so the next person doesn't spend as much time on it as I did.

THE PROBLEM: You want to have user-level security on your Samba server, but you want Windows clients to be able to see a list of shares on the Samba server without authenticating, like a share level server.  My reason for this is...

I have a set of private share folders for myself (WinXP client) and my wife (OS X client).  I am using user level security to enforce that we can each read the others share and can write only to our own.  However sometimes friends come over and we want them to be able to read our shares, and have a separate Public share that anyone can read and write to.  I also want to have a Private share that does not show up in the list of shares that only my wife and I can read or write to, for files that we would not want guest users to read.

The popular answer seems to be use share-level security.  With share-level security, Samba does not even care about user names, it matches passwords to shares and expects a certain password for a certain share.  You can list the shares without authenticating, and don't have to present a password until you attempt to connect to a protected share.

This is not ideal for security for reasons that are explained fully in other tutorials (see samba.org for a complete discussion).  User-level is much better; you have to authenticate to Samba with a user name/password BEFORE you are even presented with a list of shares to connect to (at which point your credentials are checked against the folders permissions in Samba).  In both share and user level security, shares are only presented in the list if ```
browseable = yes
``` is set in your smb.conf file on a per share basis.

The problem with this is that if you are using user-level auth, and have to authenticate before you get a list of shares, then your public users are in trouble.  Regular users are fine, create accounts in Linux and Samba for them, map them with your smbusers file, and you are good to go.  Public users don't have an account.  So you say, "OK, I'll treat them like guests" and add 

```
guest ok = yes
public = yes
writable = yes
``` 

...to your shares that you want public users to access.  But it still doesn't work.  Check your /etc/shadow file with ```
sudo cat /etc/shadow
``` to see if you have a nobody account.  You should.

Next make sure that nobody is enabled in Samba's backend:```

sudo smbpasswd -n nobody
sudo smbpasswd -e nobody
```

The first command creates the nobody account with a null password.  The second enables this account.  See this [bug report](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/39717) for more information.  It took me awhile to track that down, but if I knew what I was doing it might have been faster. ;)

Finallly, add these two lines to your smb.conf:```
[global]
null passwords = yes
map to guest = Bad User
```

The first tells Samba that null passwords are OK.  The second that non-recognized users (which is what any user who doesn't have an account on your Ubuntu box will be) should be silently mapped to Guest (nobody).

This allows a non-authenticated Windows box to list the shares advertised as browseable by Samba.  When the user attempts to connect to a share, Samba evaluates their credentials (in this case, Guest), and either allows them access, or prompts for a new user name/password.  You can also always prevent shares from being listed by marking them as browseable = no.

You do sacrifice a little security for this convienince: anyone with access to your Samba server can now list your browesable shares and connect to any share that allows guest access.  Samba isn't designed to face the Internet so all the normal rules for not doing that still apply.  See the much more extensive [Samba HOWTO](http://ubuntuforums.org/showthread.php?t=202605) for Ubuntu for general setup.

Here is a dump of my smb.conf so you can see the options I've set:

```


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = YOURWORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h Server

show add printer wizard = no
null passwords = yes
map to guest = Bad User

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes

   guest account = nobody
   invalid users = root

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\successfully* .

############ Misc ############

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

#======================= Share Definitions =======================

[Public]
comment = Public Share Directory
path = /mnt/raid/share
read only = no
browseable = yes
public = yes
writable = yes
guest ok = yes

[Paul]
comment = Paul's Public Directory
path = /mnt/raid/paul
read only = no
browseable = yes
write list = user1 user2
create mask = 0777
directory mask = 0775

[Mandy]
comment = Mandy's Public Directory
path = /mnt/raid/mandy
read only = no
browseable = yes
write list = user1 user2
create mask = 0777
directory mask = 0775

[Private]
comment = Private Directory
path = /mnt/raid/private
valid users = user1 user2
browseable = no
public = no
writable = yes
printable = no
create mask = 0777
directory mask = 0775

```

Good luck! :popcorn:

---

### Post by WebHorn on 2007-07-02
BTW I am a newb so I reserve the right for all the above to be completely wrong. :)

---

### Post by c0rrupt on 2008-01-16
Thank you **so much** for writing this!  I searched all over the internet on how to setup a Public share with user level security before I found your guide.

---

