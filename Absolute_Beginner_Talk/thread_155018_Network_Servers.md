---
title: "Network Servers"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by micrologix on 2006-04-04
Can anyone tell me how to find Network Servers in KDE, I am trying to view the shared folder on another Windows PC on my network. Do I need to set up the workgroup first and if so, how do I do that, thanks.

---

### Post by echo $USER on 2006-04-04
Usually you can go to: Places > Network Servers > Windows Share + plus the ip address of the machine you want to connect to.  But the best thing to do is install Samba.  Follow this guide:  [http://ubuntuguide.org/#sambaserver]("http://ubuntuguide.org/#sambaserver")

---

### Post by micrologix on 2006-04-04
Thanks for the info, I have installed Samba but haven't added users as yet. Do I need to do this to be able to view my Windows PC?? What I need to do is access this Windows computer so I can transfer files across to Linux, thanks in advince for your help.

---

### Post by echo $USER on 2006-04-04
Create a user and a home folder.  Then set up that user as the Samba user using the directions in the [link]("http://ubuntuguide.org/#sambaserver") I gave you.  Dont forget to change the workgroup in the smb.conf to the name of your windows workgroup.  Then you should be able to see your linux box in my network places on windows.  Double click the link then you will be prompted for your samba user/password.  That should do it.  If you can't write to it, check the permissions on your /home/samba_user folder.

---

