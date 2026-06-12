---
title: "Can't SMB into Ubuntu machine, Please help"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by kazamx on 2007-12-20
Hi, 

I am trying to share files from my Ubuntu computer with my Mac.

I followed this guide [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

I downloaded and installed samba without trouble, I modified the samba file like it told me to, from this 

    ####### Authentication #######

    # "security = user" is always a good idea. This will require a Unix account
    # in this server for every user accessing the server. See
    # /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
    # in the samba-doc package for details.
    ;  security = user

to this,

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
security = user
username map = /etc/samba/smbusers

the problems seem to start when I need to create a samba user. I paste the following into a terminal window sudo smbpasswd -a <username>

but nothing happens, if I click return then I get the following error

bash: syntax error near unexpected token `newline'

I am leaving the username as username etc. should I be changing that?

I know its going to be something really simple. But for the life of me I can't make this work

Any help would be fantastic

---

### Post by foolsh on 2007-12-20
yes
You should fill in the username with the username of your choice 
I don't think you need the <> around the username
But if your not worried about security you can change
security = user
to 
security = share
and anyone can connect without a username and password

---

### Post by lintoon on 2007-12-20
On your Mac go to System Preferences - Sharing, and enable windows file sharing.  If your firewall is turned on make sure it allows windows file sharing.

On your Mac.  Go to "Connect to server" and type in:

smb://Username:Password@Servername/Sharedfolder

eg:

User - Bob
Password - mypass123
Servername - UbuntuServer
Sharedfolder - Sharedfiles

smb://Bob:mypass123@UbuntuServer/SharedFiles

You can substitute the servername for it's IP address.

Hopefully that's it.

---

### Post by kazamx on 2007-12-20
thank you soooo much

---

### Post by lintoon on 2007-12-20
Did it work?

---

