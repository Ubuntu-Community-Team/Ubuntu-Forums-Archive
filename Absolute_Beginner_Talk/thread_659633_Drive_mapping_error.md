---
title: "Drive mapping error"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by nu2ooboontoo on 2008-01-05
:confused:I hav 7.10 server and i followed the instructions to setup "samba" and all went well until I tried to map the drive on my windows xp system. I can brouse to the server and the drive but when I click ok I get the following error.

The mapped network drive could not be mapped because the following error occurred: an extended error occurred

---

### Post by Dr. C on 2008-01-06
Can you access, open and download files from Windows XP before mapping the drive or just browse?

---

### Post by rkd on 2008-01-06
Try looking in /usr/local/samba/var/smbd.log and /usr/local/samba/var/nmbd.log to see whether samba reported any problems obviously connected with the attempt. 

One way is to open a terminal and use the command:
```
tail /usr/local/samba/var/smbd.log
```
That will show you the last 10 lines. If you'd like to see more than 10 lines, make the command be:
```
tail -n 20 /usr/local/samba/var/smbd.log
```
Change the 20 to whatever number you like.

You can also use an editor to look at the log files. If you get a permission error when trying to open with the editor, but sudo in front of the command.

Also look in the Windows event log for error messages. One way to see the Windows event log is to right click on My Computer, choose Manage from the pop-up menu, then click on Event Viewer.  

There will be three or four entries under Event Viewer. I think the messages of interest will be under System or Security, but check the others, too. The full details of a particular message can be viewed by double-clicking on the message in the right pane of the event viewer.

If you find anything obvious, post what you learn here. If you don't find an immediate explanation of the problem, post to tell us that and we will help you track down the cause and fix it.

---

### Post by nu2ooboontoo on 2008-01-06
no such file as smbd.log or nmbd.log

---

### Post by nu2ooboontoo on 2008-01-06
Windows error log say's "The server did not register with DCOM within the requested timeout.

---

### Post by rkd on 2008-01-06
Do you have a software firewall on the Windows computer that might be blocking communication from the Samba computer to the Windows computer? Just a guess. That might not be the problem at all. If you do have a software firewall, try turning it completely off temporarily -- just long enough to try to map the share to see whether it works without the firewall.  If it does, then we know we have to alter the firewall configuration to allow the Samba activity to pass. If the map still fails, we know it isn't the firewall causing the problem.

Does the /usr/local/samba/var/ directory exist, but just doesn't have any log files in it, or does the directory not exist, either. If you installed samba in some place other than /usr/local/samba, that is the place to look for the log files.

---

### Post by nu2ooboontoo on 2008-01-06
I have turned off all firewall protection an I get the same error

---

### Post by nu2ooboontoo on 2008-01-06
I seem to have /usr/local/samba/ but no var/smbd.log

---

### Post by rkd on 2008-01-06
Which set of instructions did you use to set up Samba? There seem to be many to choose from. If you combined the steps from several different instructions, tell me all of them and which parts you used. I'll look over the instructions you followed, then I'll probably have some more things for you to check or to try.

---

### Post by nu2ooboontoo on 2008-01-06
A second guide on how to setup samba as Primary Domain Controller along with several other services such as DHCP, DNS and NTP will follow later on as this topic will be a little more thourough.


1. Prerequisites

- Your Linux box should have an static ip-address.
In case you're getting your ip from a router/server via DHCP make sure it's configured to provide a fixed dhcp-lease. If that's no valid option you cannot use WINS ... more on this way down.

- You need to have samba installed.
If you haven't done so already open a terminal and type:


Code:
sudo apt-get install sambaDon't close the terminal upon installation - we still need the commandline to get several tasks done!


2. Getting samba configured

First, let us make sure samba isn't running:


Code:
sudo /etc/init.d/samba stopAs a starting point I included an smb.conf below, and there are only a few simple things you may need to tweak.

Since the installation of samba just installed a rather useless template file we're going to rename it - we keep the file just in case.


Code:
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.templateNext we create a new empty file


Code:
sudo touch /etc/samba/smb.confAnd finally we need to open the file inside an editor


Code:
sudo gedit /etc/samba/smb.confNOTE: If you're on KDE replace "gedit" with "kate"

Copy / Paste the contents of the code-section below into your editor and read on ...


Code:
[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
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

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUPOk, I already mentioned that there are a few simple things you may need to tweak; so here they are:

-> netbios name = YOUR_HOSTNAME

Replace "YOUR_HOSTNAME" with your desired hostname (don't use spaces!). Best pratice would be to use the same name you configured upon installation.

Example:

netbios name = DAPPER

-> workgroup = YOUR_WORKGROUP

Replace "YOUR_WORKGROUP" with the name of your workgroup, but make sure you're using the same as configured in Windows.

To find out the Workgroup name in Windows follow these steps:

- Click "START"
- Click "Control Panel"
- Click "System"
- Click the 2nd Tab entitled "Computername" and find the name of the Workgroup there.

Example:

workgroup = MSHOME

-> wins support = yes

If your box doesn't have a static ip-address, or you cannot configure your router/server to provide you with a fixed dhcp-lease, change this configuration parameter to "no".

In this case you cannot use the benefits of WINS.

-> [MyFiles]

This is the name of the share. Leave it as it is or adjust it to whatever you prefer. Don't use more than 31 characters and try to avoid spaces!

-> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.

In case you don't have an extra hard drive/partition you may also create folder.

I assume you've been wise enough to put /home onto a separate partition having an reasonable amount of storage space.

To create the folder type (inside a new terminal) ...


Code:
sudo mkdir /home/samba... and adjust "path =" to read ...

path = /home/samba/

Remember that this is just an example - you are free to put things wherever you like.

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

Well, this should say it all. Replace "YOUR_USERNAME" with the name you use for login (no spaces!).

Example:

force user = stormbringer
force group = stormbringer

Now we completed the part of editing smb.conf

Save the file and close gedit.

Since we are going to share the folder with other users we should now make sure that the permissions are set. Type:


Code:
sudo chmod 0777 /media/sambaNOTE: Don't forget to correct the path to the location you chose above!

That's it - now we need to start samba ...


1.1 Starting samba and setting up user accounts

Let us fire up samba for the first time. Type:


Code:
sudo /etc/init.d/samba startThere shouldn't be any errors - if you are presented with an error message make sure everything is correct (search for typos and/or invalid paths).

Time to add yourself as an samba user.

NOTE: You will be asked for a password - make sure you use the same as you use for login!


Code:
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_usernameIn case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

In the following example we will add an user called "mark" ...

Example:


Code:
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e markThe "-s /bin/true" in the first line prevents the users from being able to access the commandline of your linux box ("-s" stands for "shell"). I strongly advise you to follow this recommendation! Don't change that setting to a valid login-shell unless you really know what you are doing!

Repeat this step until you configured all user accounts!

Now that we configured samba and created the user accounts we are done with the Linux-part - there's one more thing to do in Windows.


2. Changing network settings in Windows

Now we should let Windows know that there's a WINS server active in the network. 

If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows

Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
NOTE: Adjust this to the hostname and sharename you chose above!
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

That's it - samba is up and running now.

---

### Post by rkd on 2008-01-06
Could you post your smb.conf file here?

Did the error message you found in the Windows log that said the server did not register with DCOM in the required time include a long string of numbers, letters and dashes after the word "server"? If it did, could you post that string here? I think that if you double click on the message in event view, you will be able to copy the text and paste it into the post, so you don't have to try to copy that long string by hand.

Use the following command to try to find the Samba log files:

sudo find /var -name log.smbd

If you do find it, look at it and log.nmbd to see whether there are any useful clues about the problem there, but I think there won't be.

Is there a second Windows computer on your network? If so, can they share directories from one to the other?

I think you can see that I don't know what is wrong; I'm just casting about for some clues that might lead us in the right direction.

---

### Post by nu2ooboontoo on 2008-01-07
I think the issue is with my user accounts on the server because if I use my administrator account to map the drive I can connect fine.

---

### Post by nu2ooboontoo on 2008-01-07
Ok, if I browse to "my network places' I can see 
my server
DVD-ROM
MYFILES
NETLOGON
"user directory" 
Print

I can click on the dvd without errors but I can not see any files. The print shows "add a printer" but when I try to is says I don't have permission.The other 3 give me an error that says I don't have permission, this leads me to believe that the issue is with my user accounts on the server.

I have a 6gb drive that ubuntu is on and I setup a 15gb drive for my user files. How can I tell where the user files are going on the server or where they should be going for that matter.

---

### Post by rkd on 2008-01-07
That's an interesting discovery.

I wonder whether the problem is not on your server, but maybe mapping a network share from a limited account doesn't work.

Could you temporarily change one of the accounts that couldn't do the mapping to be an administrator, and see whether it then can do the mapping? Be sure to disconnect the drive that you mapped as administrator before trying this test.

(I imagine you know how to make that change, but in case not, one way is to open the Control Panel and select User Accounts. It should be obvious from there, but ask if you need more help.)

---

### Post by rkd on 2008-01-07
Looks like we posted at the same time.

The location of the user files is one of the (many) things specified in smb.conf -- could you post the current copy of that here so I can look at it?

---

### Post by nu2ooboontoo on 2008-01-08
I have no limited accounts in XP.

I will post my smb.conf later today.

---

### Post by nu2ooboontoo on 2008-01-08
How do I find my smb.conf?


I can login to XP with an administrator account with the same name as a user account on the Ubuntu server. When I map a drive to the server using the user credentials I get an error. If I click "log on using" and use my Ubuntu server administrator credentials I can connect and copy files to the server.

---

### Post by nu2ooboontoo on 2008-01-08
; General server settings
netbios name = MY_HOSTNAME
server string =
workgroup = MY_WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

[homes]
valid users = %S
create mode = 0600
directory mode = 0755
browseable = no
read only = no
veto files = /*.{*}/.*/mail/bin/

[netlogon]
path = /var/lib/samba/netlogon
admin users = Administrator
valid users = %U
read only = no

[Profiles]
path = /var/lib/samba/profiles
valid users = %U
create mode = 0600
directory mode = 0700
writeable = yes
browseable = no

[DVD-ROM Drive]
path = /media/cdrom
browseable = yes
read only = yes
guest ok = yes

[MyFiles]
path = /media/samba/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = MY_USERNAME
force group = MY_USERGROUP

---

### Post by nu2ooboontoo on 2008-01-14
I posted my smb.conf 5 days ago, did you forget about me?

---

### Post by rkd on 2008-01-15
Sorry for being slow. I didn't forget about you, but I haven't been able to spend much time trying to figure out your problems. We're just volunteers here, and real life gets in the way a lot ...

I'll try to look at your problem again in the next day or two.

Have you made any progress on your own? Have you tried things that did not work (that could save me some time).

---

### Post by nu2ooboontoo on 2008-01-15
as long as I know you're still here take your time... I do not know where to go from here so I have not tried anything else.

---

### Post by rkd on 2008-01-19
I can't figure out why you are having the problems you are getting. I am able to get file sharing to work, as I'll describe here for one case. If you want to make the file sharing do other things, explain what you want to do, and I'll see whether I can tell you how to make Samba do that.

I was unsure what sort of sharing you were trying to do. I made the guess that you'd like to have a number of users each have a private area on the file server in which they can put files that they can read and write, and others can read, but cannot write. (You could also make it impossible for others to read a given user's files, but that isn't the default.)

Briefly, you will set up Ubuntu users and Samba users that match the Windows users you want to be able to access Samba. A share name will be defined for each user, pointing to his Ubuntu home directory. The home directory is where the files for that user will be stored on the Ubuntu/Samba system. I suggest that the share name be given the same name as the userid, though they may be different.

The smb.conf file needed for that is pretty short:

```
[global]
        netbios name = ATHLON
        workgroup = SAMBAWORK
        server string = 
        obey pam restrictions = Yes
        security = user
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog = 1
        syslog only = yes

[test1]
        path = /home/test1
        read only = No

[test2]
        path = /home/test2
        read only = No
```
The indentation is not important -- I just did it for ease of seeing the sections.

In the smb.conf, you should change ATHLON to what you want to show up in the computer browser for the server. You can delete that line entirely and it will default to the Ubuntu system's name. You also should change SAMBAWORK to whatever the workgroup name is that your Windows PCs have specified. And everywhere test1 appears, change it to the name of one of your Windows users; everywhere test2 appears, change it to the name of another of your Windows users; if you have more Windows users, add sections like the [test1] or [test2] section using the names of those additional users. 

Restart Samba to make it read the new smb.conf file. It would be a good idea to check the system log (System -> Administration -> System Log and click on syslog) to be sure there are no error messages about the smb.conf file. Be sure to scroll down to the end of the log file (check the time in the messages to be sure you are looking at the current point).

In addition to the above smb.conf file, you must enter corresponding users and passwords in Ubuntu and Windows. In Windows, you use the User Accounts control panel to set up users. In Ubuntu, you use useradd and smbpasswd commands:

```
sudo adduser test1
sudo smbpasswd -a test1
sudo adduser test2
sudo smbpasswd -a test2
```
When you enter these commands using sudo, the first one might prompt you for your own password to authorize the sudo if you haven't used sudo in the past 15 minutes. Don't get that confused with the prompt for the password to place on the new account you are setting up.

The adduser commands create a Linux user named test1 (and test2), with home directory /home/test1 (and /home/test2). It will prompt you for the password to set up. Be sure to enter the same password as is on the Windows system for that user. Be sure to substitute the actual Windows user names for test1 and test2, and repeat the pair of commands for any additional Windows users you want to give access to storage on the Samba server. (Although the directions say the adduser password must match the Windows user password, by experiment, that is not actually true. However, it seems to me like a good practice so you have fewer passwords to remember.)

Note that the example you were following said to use the -s option on the adduser command. Ubuntu's adduser seems not to have that option. There is an equivalent, but I doubt the extra security of not allowing those users to logon to the Ubuntu system directly is necessary in many environments. If you need that extra protection, ask and I'll tell you how to do it.

The smbpasswd command enters the user and password into another file that Samba uses for user validation. When it prompts for the password, be sure to enter the same password as is on the Windows system for that user. (Matching the Windows user's password is not optional here -- it must match.)

The instructions you were following told you to make Samba be a WINS server and told you to set the Windows machines to consult that WINS server. That works, but isn't really necessary. The only advantage I understand that WINS has is in large networks. It reduces network traffic by eliminating some broadcasts and it allows PCs on different network segments to see each other in the Windows computer browser. Neither of those factors are an issue in a small home LAN. And if you don't set up Samba as a WINS server, you don't have to give it a fixed IP address, which can make your network management life slightly easier.

The minimal smb.conf file I show above does not enable WINS support in Samba. So I suggest you set your Windows machines back to the default WINS setup. Basically follow the directions about getting to the TCP/IP Properties Advanced, go to the WINS tab. Delete the WINS IP address in the top of the dialog box, and reset the NetBIOS setting to Default in the bottom of the dialog box. Click OK repeatedly to get out of all the dialogs, then reboot the PC to make the change take effect. 

If decide you really do want to have the Samba system be a WINS server, then the original directions seem correct for that.  If you do change smb.conf to add WINS support, be sure to restart Samba to make it read the new smb.conf.

If you are using Windows XP Pro, you probably should check to be sure that the Windows machines are set up for simple file sharing. That's the default when in a workgroup (not in a domain), but it might have gotten changed somehow. To do that, make sure you are logged on as an administrator, open My Computer, from the Tools menu, select Folder Options, then the View tab, then scroll to the end of the list and make sure "Use simple file sharing" is ticked.

If you are using Windows XP Home, you don't have a choice -- it is always simple file sharing.

I've seen conflicting advice about "Simple file sharing". I suggest making sure it is turned on because that is supposed to be the default when in a workgroup. Since what we are setting up with Samba is a workgroup environment, turning on "simple file sharing" seems to me to be a better bet for avoiding problems. 

Now log on to a PC with the one of the users you set up for access to Samba, open My Computer, from the Tools menu, select Map Network Drive. You should be able to browse to the Samba computer and see the share names you have set up. (A user who has not been set up on the Samba system will see the Samba system name in the computer browser, but won't see any share names under it.) If you select the share corresponding the the Windows user you are logged on as, you will have full read and write access to the files in that share. If you select one of the other shares, you will have read only access to the files in that share.

If you login on the PC as a user who has not been set up in Ubuntu and Samba, you can see the Samba computer when browsing the computer network, but you see none of the shares that were defined. However, you are not completely blocked. If you enter the direct name of the share, for example \\athlon\test1, you will be prompted for a userid and password. If you enter any of the userid/passwords that has been set up in Samba, you will be given access to the share you named with the access rights as if you had been logged in on the PC with the userid you gave in the Samba login prompt

I verified that this works with Ubuntu 7.10 and Windows XP Pro SP2. I imagine it would work for Windows XP Home, but have not tested that.

I imagine you noticed that Samba has a very large number of options, allowing a lot more control over access to the files on the server. If you want some other arrangement that what I've set up above, it probably can be done. It is pretty easy to make the files completely private to each user. Or to make all the files read/write for all users. Or to make a single share that all the users can connect to. And lots of other possibilties.

I haven't tried setting up printers. Samba does support printing, but you seemed not to be trying that, so I didn't check it out. If you do need to do that, I can check it out.

The example you were following seems to have set up a share for the CD drive. I suppose that works, but I didn't test it to work out the details.

So the arrangement I lay out in detail above may not meet all your needs, but I think it would be good to set up your computers according to those directions and see whether they work for you. If so, then we have a good starting point and can adjust it to make it do exactly what you need it to do, once you explain your needs and I can work out how to adjust the configuration to meet them.

---

