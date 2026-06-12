---
title: "sharing files between mac (os x) and pc (ubuntu) wirelessly"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by johnbrouillette on 2007-02-19
can someone to help me out????

when i had windows i used to be able to create a home network and share files between my macbook and my pc running windows wirelessly. 

i have no idea of how to do this now. can someone help me out please!? i have the latest Ubuntu.

the file i need to share is 4.2 gb. and i have no dvd burner.

---

### Post by n8bounds on 2007-02-19
open a terminal and say (just copy/paste from here):
```
 sudo apt-get update && sudo apt-get install samba -y && sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.ORIGINAL && sudo gedit /etc/samba/smb.conf 
```

when it stops, it should have offered you a text editor with the default samba config file open.

remove all the contents and put this in it:
```


[global]
   ; General server settings
   netbios name = YOURLINUXHOSTNAME
   server string = Linux Rox
   workgroup = MSHOME
   announce version = 5.0
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

   passdb backend = tdbsam
   security = share
   null passwords = true
   name resolve order = hosts wins bcast

   wins support = yes

   printing = CUPS
   printcap name = CUPS

   syslog = 1
   syslog only = yes

[print$]
   path = /var/lib/samba/printers
   browseable = yes
   guest ok = yes
   read only = yes
   write list = root
   create mask = 0664
   directory mask = 0775

[printers]
   path = /tmp
   printable = yes
   guest ok = yes
   browseable = no


[sharefolder]
   path = /home/YOURLINUXUSERNAME/sharefolder
   browseable = yes
   read only = no
   guest ok = yes
   create mask = 0644
   directory mask = 0755
   force user = YOURLINUXUSERNAME
   force group = YOURLINUXUSERNAME

```

please change your netbios name, workgroup and YOURLINUXUSERNAME as appropriate (netbios name can be whatever you want, but to keep it simple just make it whatever your hostname is)

save and close

be sure to make a folder as described near the bottom

"/home/YOURLINUXUSERNAME/sharefolder" 

it has to match the config file or it won't work

doing this should work:
```

mkdir ~/sharefolder && chmod 0777 ~/sharefolder

```

you may also want to say:
```

sudo apt-get install winbind && sudo gedit /etc/nsswitch.conf

```

this time the text editor will show you a different file that you will need to change..

  make the line that says:
```

 hosts:          files dns mdns

```
  read like:
```

 hosts:          files dns mdns wins

```

to apply your changes to the samba server (windows file sharing protocol) say this in a terminal:
```

sudo /etc/init.d/samba restart

```

now you can move whatever you want into your /home/WHATEVERYOURLINUXUSERNAMEIS/sharefolder folder and other machines on your network should be able to see it as if it were shared from windows...it may help to know your ipaddress..in a terminal say:
```

ifconfig

```
and in the results will be your ipv4 addr or something like that...otherwise known as your ipaddress

good luck

---

### Post by zorkerz on 2007-04-10
Nice how to i must say.  But is all of that necessary? In feisty gnome i go system -> administration -> shared folders
than just add the folders i want shared

in places -> network  i can see everyone on the network including windows and mac comps

whats your status johnbrouillette any luck?
Its handy to hear back so others visiting this post know how helpful it is.

---

### Post by devnulljp on 2007-04-11
You can ssh into/out of macOSX and Linux and share files using rsync or scp.
If you want to mount shares though, use either samba or nfs.

---

### Post by sastian on 2008-02-07
I tried this and it did not work :(

---

