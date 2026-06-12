---
title: "ubuntu to xp and vice versa file sharing"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by 95aspire on 2007-02-09
ok im still working out the kwirks (only had it running for a few days) and so far running smooth with no problems at all cept being confused as heck., i have a ftp server and my webserver sorta setup but thats another topic here lol

anyway im tryin to make it to where i can browse ubuntu shares via windows network and i get a password box. i enter my linux username and pass and it just keeps popping up, cant get past that.

also when i try to view shares in windows via ubuntu, i can see my xp pro machine but i get an error saying 
"folder contents could not be displayed" 

ive tried to search the fourms but didnt find nething helpful lol. 

ive installed this 

sudo apt-get install samba smbfs

and didnt help, do i have to do somthing to get it running?? any help is appriciated, btw im MAINLY worried about files from xp maching to ubuntu as ill be modifying web pages on my xp machine and moving to ubuntu. thanks in advance all

---

### Post by dannyboy79 on 2007-02-09
did you add a samba user??? so basically if your username on ubuntu is rick, you need to do this. sudo smbpasswd -L -a rick and then sudo smbpasswd -L -e rick. then it's going to want you to enter a password twice. this is the password and username you'll need to use on windows. this is because samba doesn't use pam to authenticate (which is what ubuntu uses) samba uses Default: passdb backend = smbpasswd as it's default. hence why you need to add your user to the smbpasswd database. that should get you going. let me know if not. oh, you'll need to restart samba also. that would be accompished by typing, sudo /etc/init.d/samba restart

---

### Post by dannyboy79 on 2007-02-09
well, here is a great link for ya. [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by 95aspire on 2007-02-09
> **dannyboy79 said:**
> did you add a samba user??? so basically if your username on ubuntu is rick, you need to do this. sudo smbpasswd -L -a rick and then sudo smbpasswd -L -e rick. then it's going to want you to enter a password twice. this is the password and username you'll need to use on windows. this is because samba doesn't use pam to authenticate (which is what ubuntu uses) samba uses Default: passdb backend = smbpasswd as it's default. hence why you need to add your user to the smbpasswd database. that should get you going. let me know if not. oh, you'll need to restart samba also. that would be accompished by typing, sudo /etc/init.d/samba restart

ok didnt find that one lol got it to work with xp-ubuntu now. 


and going to that link now

---

### Post by dokumentamarble on 2007-02-09
I feel like i have tried everything, but more than likely did it all wrong.. Ive been trying a while now to setup GUI ubuntu 5.10 (breezy) as my network FileServer, I finally got windows to find the computer, and yes i have done everything shown on that link, but it can not connect to it. And the ubuntu machine cannot connect to the windows machine. 

i have tried it with and without the WINs server. ive also tried to install ftp but that didnt work. 

any suggestions on 1 easy way to do this (use ubuntu (gui) as a fileserver on a windows network)?

Thanks

.dok

---

### Post by dannyboy79 on 2007-02-09
dok,
do you use a domain or a workgroup? did you do anything to the default smb.conf? have you installed samba, smbfs, Have you tried this guide?

---

### Post by dokumentamarble on 2007-02-09
i use a workgroup MSHOME. yes i just re-installed ubuntu 5.10 again and followed the guide exactly. (except i did not use WINS) . still i get an error on windown when i try to connect, it shows up but when i try to connect it says that it is not accessibble and that i might not have permission to connect to it. i did setup the useraccount on my ubuntu machine that has 1 account for the ubuntu user, and another for my windows machine, the ubuntu account for it has the same un and password.

---

### Post by dannyboy79 on 2007-02-09
dok, did you read my suggestion about not using the connect to server thing. there is something wrong with nautilus and the url. you need to type in the url manually. what happens when you type in the terminal smbclient -L computername. example: smbclient -L WINXP. it should ask you for a password, then it should show you the shares available. or try smbtree, then enter your password. what about findsmb, does it show your ubuntu server?

---

### Post by dokumentamarble on 2007-02-09
this is what i get with smbclient -L compname

Domain=[FILESERVER] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        Files           Disk
        IPC$            IPC       IPC Service ()
        ADMIN$          IPC       IPC Service ()
Domain=[FILESERVER] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        MSHOME               DOKTOP


yesi did read that, but i figured id try anyway. I also manually entered it with no luck

with smbtree i got nothing but timeouts

Doktop is my windows laptop

---

### Post by dannyboy79 on 2007-02-09
ok well you were suppose to use the computer name of your windows computer with smbclient NOT your linux server. can you ping it first? you need to be able communicate over tcp before any samba is gonna work. here is my smb.conf if you;d like to try it. don't forget to restart samba.

[global]
    netbios name = UBUNTU
    server string = Dans Linux Desktop
    workgroup = LINUX
    encrypt passwords = yes
#    guest ok = yes
    smb passwd file = /etc/samba/smbpasswd
    domain master = yes
    local master = yes
    preferred master = yes
    os level = 99
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
#   passdb backend = tdbsam
    null passwords = true
    username map = /etc/samba/username.map
#   name resolve order = wins lmhosts host bcast
    hosts allow = 127.0.0.1 127.0.1.1 192.168. EXCEPT 192.168.0.20
    hosts deny = 0.0.0.0/0
#   hostname lookups = yes
#   hosts equiv = /etc/samba/lmhosts 
#   map to guest = Bad User   
#   guest account = nobody
#   wins support = yes
#   smb ports = 139
    browse list = yes
    mangled names = yes
    default case = lower
    case sensitive = no
    preserve case = yes
    short preserve case = yes

#global logging
    syslog = 1
    syslog only = yes

#global printing settings
    printing = CUPS
    printcap name = CUPS

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
wins support = no
[homes]
    valid users = daniel root
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    ;veto files = /*.{*}/.*/mail/bin/

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
    browseable = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive                                                              [ ok ]
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

the only thing that's kind of custom is this line
username map = /etc/samba/username.map
this is to make my windows username equate to the ubuntu username. so, the file will have this in it IF you have a different user name on your windows machine than on your ubuntu machine.

greg = "Greg Sanders"
root = administrator Administrator
nobody = guest pcguest smbguest Guest

also, there are a lot of things commented out, this is because I spent many days trying to get this to work and I fianlly got it. My samba pc is the local master browser for he network,. I have a win xp pro machine and a xubuntu laptop which i can share files between them all. also I have an xbox which has xbmc on it that can stream movies, music, and pics from any one of my computers. good luck

---

### Post by dokumentamarble on 2007-02-09
i tried smbtree again and got an actual reply with some timeouts. that was after i restarted samba. when i tried smbclient to my windows machine i got timeouts. i can ping the ubuntu machine sucessfully. but i can not ping my windows machine from ubuntu.


Thank You for the help, i really appreciate it

.dok

---

### Post by dannyboy79 on 2007-02-09
if you can't ping windows than start there.

---

### Post by dokumentamarble on 2007-02-09
any suggestions? i just restarted the ubuntu machine and remembered to restart samba. (is there anyway to get it to run on startup?) but now i cant connect to MSHOME from my windows machine?

edit: i have a wireless router and was using my wifi with my windows machine, now its hardlined to the router (so is the ubuntu machine)

---

### Post by dokumentamarble on 2007-02-09
i just restarted samba again and now i cant even access it or my windows computer from ubuntu. the windows network shows up, but neither computer is inside. from xp i cant see anything inside mshome either. oh yeah and im back on wifi now

thanks for the help

---

### Post by dokumentamarble on 2007-02-09
just tried restarting ubuntu, then had to startup samba, nothing, rebooted windows, nothing, rebooted samba, ubuntu and windows. nothing. im still not getting anything under MSHOME. nothings showing up.

still can ping ubuntu from windows

still cant ping windows from ubuntu

---

### Post by dannyboy79 on 2007-02-09
ok, i'll say this again, you need to make sure that you can ping all machines. if you;re using a router than you need to be able to ping that as well. so after you're able to ping all computers by ip address as well the router, than we'll look at samba.  do you have winxp home or pro? and you need to decide do you want windows to be the local master browser or do you want your ubuntu machine to be the local master browser? you can't have both obviously. did you check out my smb.conf? i am running out of ideas as this took me a long time to get it work as well.

---

### Post by dokumentamarble on 2007-02-09
dannyboy, thank you alot for your help.

yes i can ping the rounter, but i still cant ping windows. i'm using winxp home. probably ubuntu's gonna be the local master browser. 

i am reinstalling ubuntu again, ill try your smb.conf instead of the other(making changes of course) again thanks for the help

---

### Post by dokumentamarble on 2007-02-09
i just finished reinstalling and setting up samba with your smb file. i can ping to and from windows and ubuntu now. after setting up samba i attempted to access the ubuntu file from ubuntu. i was given a login screen everywhere i went, untill i got to the folder with my login name on it ( the only folder i am supposed to be sharing. supposed to be named Files) but i cannot log into it. my ubuntu password and login do not work, and i setup samba with the sam e password and usernames,  i remember reading now that i am supposed to get a login screen in windows, i have never had it pop up, ever... after restarting samba, i cant find my fileserver inside the windows network anymore(from ubuntu)

windows still doesnt see anything (including itself) inside the mshome folder

thanks

---

### Post by dokumentamarble on 2007-02-09
after typing that i tried again, and it shows up but "the folder contents could not be displayed" talking abotu the main shared folder, not the one with my login name on it

---

### Post by dokumentamarble on 2007-02-09
after closing and going to places> network servers again i can now see my windows laptop, i try pinging it again, and now i cannot, but i can ping the ubuntu machine from windows

---

