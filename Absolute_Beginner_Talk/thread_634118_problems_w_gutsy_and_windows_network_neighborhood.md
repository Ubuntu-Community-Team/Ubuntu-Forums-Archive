---
title: "problems w/ gutsy and windows network neighborhood"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-12-07
i know theres other posts on this.  However, I don't see any that address the problem when DHCP is used.  Also,  I can't access the windows network.  I go to: network then click the "windows network" icon then click the "mshome" icon.  then i either don't see the computer that i am trying to access or i get an error message saying that it can't be displayed.  I checked the windows computer and the file sharing IS enabled.  There is not a firewall issue with the windows machine either.  I did not have this problem with feisty fawn.  Now with gutsy i've had numerous problems besides this one. but i want to focus on this one for now.

---

### Post by pclark36 on 2007-12-07
I was reading about this, but haven't got to try it yet,  You might try:

sudo apt-get install smbfs

Apparently that installs samba files needed to see the files on the windows box.  You might need to enter some login information for your windows box also when trying to access it.

---

### Post by bradmayne on 2007-12-07
no good.  I already have it but tried what you said anyways to be sure. any other ideas that you have are totally welcome!

---

### Post by Rick Z on 2007-12-07
are you able to ping to windows or vise versa?

---

### Post by bradmayne on 2007-12-07
yes i am able to ping my vista box as shown:

brad@brad-laptop:~$ ping 10.0.0.3
PING 10.0.0.3 (10.0.0.3) 56(84) bytes of data.
64 bytes from 10.0.0.3: icmp_seq=1 ttl=128 time=9.61 ms
64 bytes from 10.0.0.3: icmp_seq=2 ttl=128 time=4.02 ms
64 bytes from 10.0.0.3: icmp_seq=3 ttl=128 time=1.69 ms
64 bytes from 10.0.0.3: icmp_seq=4 ttl=128 time=1.66 ms

---

### Post by maybeway36 on 2007-12-07
Post the output of:
```
smbclient -L //your-computer-name
```
Don't use the IP address, use the computer's name.
You might want to try changing your smb.conf resolve order to put bcast first.

---

### Post by bradmayne on 2007-12-07
brad@brad-laptop:~$ smbclient -L //brad-laptop
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE
brad@brad-laptop:~$ 

just a note:  i've never tried to access my lappy this way so I'm not sure what password is needed.  I'm also assuming that you meant the computer where you wrote "your-computer-name" is the computer i am on now, not the "target computer" that i am trying to access.

---

### Post by markyb86 on 2007-12-08
I have this same problem!
bethyb@ubuntu-dell:~$ smbclient -L //ubuntu-dell
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE
bethyb@ubuntu-dell:~$

---

### Post by bradmayne on 2007-12-08
so thats two of us! if you figure it out please let me know!  If ubu doesn't get it's act together I'm moving on to another distro.  openSuse is looking better all the time...

---

### Post by bradmayne on 2007-12-10
i went back to feisty!  I'm still having problems with connecting to the windows machine from my lappy running feisty.  I had trouble connecting to the windows computer from the vista partition also.  What I did was to turn off the "intermediate network filter"  from symantic.  (i can't stand them but the owner of that computer swears by that and vista ugh!) After that filter was turned off i could then access their computer from my vista partition.  Are there any dependencies that I need to satisfy?  I forget what i may have had in the past as i had to do a fresh install of feisty.  I have installed samba again so far but i'm at a loss as to what i should do next... Any ideas anyone?? I'm open.  I'm not working anymore at this time as my cancer has progressed to far so i'll be around most of the time now.

---

### Post by Rick Z on 2007-12-10
Are you able to access the target PC from another window workstation?  In windows workstation, you may have to enable the window share modules.  (my configuration is Windows 2000)

Control panel> Network and Dial-up Connections > right click the NIC that is connect to your network (usually says LAN) > click properties > make sure that 'Client for Microsoft Networks' is checked.
Also make sure that under TCP/IP doesn't have any filter enable.
Now you should be able to access from Windows to Windows or Ubuntu to Windows.  Notes* you HAVE TO make a share folder in the target PC.

if you wish windows to access your ubuntu samba server, do the following.
On the Ubuntu side... check the following...(I am at work and just going by photo memory of where the location is...)

System > Administration > Network (login your root password)>General.  The host will be the name that you will see on the windows when access ubuntu server.
System>Administration>Share Folder (at this point you may need to install some of the package, please allow it to finish install)>select a directory to share (ex. /home/yourname) make sure that we are using smb/samba protocol.  

Enable the share directory browseable by the editing the following configuration.  Open up the terminal 
Login as root
#sudo –i

After you login as root, let’s backup your current smb.conf first.
#cp /etc/samba/smb.conf /etc/samba/smb.conf.bkup

Now let’s edit the smb.conf so windows/ubuntu can access the share directory (you can use nano /etc/samba/smb.conf or gedit /etc/samba/smb.conf)
#nano /etc/samba/smb.conf

Look for a word called ‘browseable’
Change the following as show below.

[homes]
   comment = Home Directories
   browseable = yes
   writable = yes

*** If you are using nano to edit the smb.conf, you can exit and save the edit file by clicking “Ctrl X or Ctrl  o” and hit Y for yes.

Now, we need to add account/user that is able to access your samba share folder.  You can sync or have server automatic setup account, but I haven’t figured it out yet.
#smbpasswd -a username

After all the above is done, run the following command and close your terminal windows.
#/etc/init.d/samba reload

Finally, you will be able to see ubuntu server from windows.  Your ubuntu pc will be able to see windows share folder.

---

### Post by Rick Z on 2007-12-10
One last things...  I got most of this tips from [https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

---

### Post by bradmayne on 2007-12-16
i solved part of the problem.  the firewall on the windows machine that i want to connect to that has the printer had symantec norton.  there was an intermediate network filter or some crap.  once disabled i could then "see" the windows computer from the GUI in "network" under places.  i just could not access it.  what used to happen was i would then see a password request for the windows machine.  after typing in my password and username i would then be able to go to the computer.  So i guess this is a step in the right direction. i dunno this is kinda annoying but whatever.

---

