---
title: "kubuntu ppc iMac G3"
date: 2006-11-16
forum: Apple PPC Users
---

### Post by n_hendrick on 2006-11-16
I have a couple of questions. First off I´m not getting any sound from xmms. Its setup to use the alsa driver but its not producing any sound. Secondly I have a network problem. I can see the other computers on my home network but   
I can´t see  this iMac from the other computer. When I click on the Sharing tab on the dialog box for the folder I get ¨configure sharing¨, but when I click configure sharing I get a dialog box thats de-highlighted and I can´t  set anything up. And Thirdly I was wondering if its possible to convert a i386 deb to powerpc format for installation purposes. Thanks in advance to a response.

---

### Post by n_hendrick on 2006-11-16
hey...just got xmms to work. I had to copy the file to this machine to get it to run...is there a way to setup the host machine so all I have to do is double click it on the network share. Still can see the imac and still don know about i386 to ppc conversion....

---

### Post by n_hendrick on 2006-11-16
okay I got xmms to work for local files only and still can´t run from samba share. I read an article on i386 to ppc conversion and found out it was impossible. And I got the sharing dialog to work, but the other ubuntu machine still can´t see it on the network. Any help would be appreciated.

---

### Post by stmiller on 2006-11-17
Have you edited your smb.conf? Can you post it?

You have to be a registered samba user on the other machines to browse them. Or have guest access enabled on those machines. Are they win or Linux boxes?

FWIW Samba is fully supported in Linux. x86 or PPC makes no difference.

---

### Post by n_hendrick on 2006-11-17
I have guest logon turned on....I just install smbclient and smbfs and the workgroup appeared finally, but when I go to click on the pc it fails. This is a Ubuntu machine connecting to a Kubuntu Machine.

the only thing active (without the #) in my smb.conf file is as follows:

path = /home/nathan/downloads
comment = /home/nathan/downloads
public = yes
guest ok = yes
writable = no
wide links = no 

The file is virtually the same on both machines.
As I said I can view the ubuntu directories but I can´t see the Kubuntu directories from the ubuntu machine and I can see and view the ubuntu directories but I can't load any mp3 or video file. I was setting up the share so I only had to have my mp3s and music videos on one computer so as to save disk space. Now why with the install of the packages I listed above does the workgroup appear clickable now? I´m wondering if I just have to install something for samba...don´t know just an idea and theres gotta be a way to run the files from the host system.

---

