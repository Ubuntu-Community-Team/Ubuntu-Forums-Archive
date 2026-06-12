---
title: "Serious samba help"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Znort_Ubern00b on 2007-11-21
Hi All,

am having serious trouble getting samba to work with my xp machine.have followed link below ( i think to the T)and no luck...so tried link below that still no luck...

I have file and print sharing enabled on xp machine and it sees itself in the work group but not my ubuntu machine. ubuntu is in same workgroup as xp machine have shared folder i want to share...do i need to share home folder for the link user?

have enabled samba in and out in firestarter, what else should i do???

regards in advance of any help.

[http://ubuntuforums.org/showthread.php?t=26438&page=5]("http://ubuntuforums.org/showthread.php?t=26438&page=5")

[http://ubuntuforums.org/showthread.php?t=184234]("http://ubuntuforums.org/showthread.php?t=184234")

---

### Post by jonandrews on 2007-11-21
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

### Post by Znort_Ubern00b on 2007-11-21
I'm on wireless..does that make a difference...?sorry should have mentioned earlier...

---

### Post by Znort_Ubern00b on 2007-11-21
bump...

---

### Post by HermanAB on 2007-11-21
Debug it with smbclient as explained here: [http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by earthtux on 2007-11-26
> **HermanAB said:**
> Debug it with smbclient as explained here: [http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

I have a similar situation

I have a windows XP Pro box(192.168.4.101) and a Ubuntu box(192.168.4.100)
I followed the instructions and set up the samba
However I can't see the ubuntu shared folder in Windows xp's my network space
I can ping each other so physical connection is working

i can manually use tool-->connect network disk to manually add the ubuntu shared folder
Q1 Why cant I see ubuntu shared folder in my workspace?

if i use the same username login on both boxes
At the ubuntu box side,
when I go to places-->network-->double click on the windows network icon
it shows nothing
i also have problem using places-->connect to the xp box
it works if i use the same username on Both boxes for the first time to mount the xp shared folder

when i tried the smbclient to debug
I typed
smbclient //192.168.4.100/username
i got this error
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
#start of my smd.conf
[global]

## Browsing/Identification ###

#add by min-chieh
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = XPTEST
   netbios name = min-chieh-desktop

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
   hosts allow = 127.0.0.1, 192.168.4.101, 192.168.4.100
   hosts deny = all
   security = share

[matthew]
        comment = tempShare
        path = /tmp
        read only = yes
        guest only = yes

#end of my smd.conf

both boxes using same workgroup name:XPTEST
I already added username to smbpasswd and enabled it too
Q2 why cant i see the xp shared folder in windows network?
thanks

---

### Post by earthtux on 2007-11-27
I uninstalled samba and re-installed it again
now i can see the ubuntu box in my xp's "my network space"

However i found i have 2 smbd threads running
after i type "ps -e | grep smbd"
Is this normal?

still I got error message that i cant access the ubuntu box if i double click on the ubuntu box icon in my network space....

here is my new smb.conf file
#start of smb.conf

[global]

## Browsing/Identification ###

#add by min-chieh
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = XPTEST
   netbios name = testub

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
   hosts allow = 127.0.0.1, 192.168.4.101, 192.168.4.100
   hosts deny = all
   security = share

#wins support = no

[tmp]
path = /tmp
available = yes
browsable = yes
read only = no
guest only = yes



#end of smb.conf

---

### Post by earthtux on 2007-11-28
bump pls someone help me T_T

---

