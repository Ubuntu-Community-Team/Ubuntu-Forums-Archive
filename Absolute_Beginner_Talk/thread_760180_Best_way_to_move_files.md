---
title: "Best way to move files"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-19
I have a desktop pc which i use for editing all my web pages (with gedit) i have another computer with just a CLI(command-line install) what is the best way to either edit the files on the CLI computer with gedit from my desktop, or transfer the files from my desktop to the CLI computer. Bear in mind i have to use terminal to set up any programs needed on the CLI computer.


Thanks
Saj

---

### Post by HermanAB on 2008-04-19
Ssh

---

### Post by freebeer on 2008-04-19
"Best way"?  I suppose that's dependent upon your preferences.  ;) I would imagine the easiest way it to set up a share on the CLI machine, then just open up the files from within gedit.

---

### Post by thewump on 2008-04-19
I'm a big fan of SSHFS.  That mounts a a folder on the remote machine just like it's local. I use it all the time on remote machines where I don't have NFS setup.

google "sshfs on ubuntu"

All you need is ssh installed on the receiver and sshfs on the machine you want to connect from.. then you just do:

sshfs remote_ip:/folder_you_want_to_link_to /path_to_local_folder 

If the user is different between the machines then its..


sshfs username@remote_ip:/folder_you_want_to_link_to /path_to_local_folder 

Keith

---

### Post by saj0577 on 2008-04-20
> **HermanAB said:**
> Ssh

Could you please be more descriptive.

Saj

---

### Post by bodhi.zazen on 2008-04-20
For ssh you will need to set up a ssh server on the CLI server.

[uwiki]SSHHowto[/uwiki]

If you do that you might want also look at securing it 

[uwiki]AdvancedOpenSSH[/uwiki]

You can then move the files with scp

[http://www.arvindatwork.com/index.php/2007/04/02/how-to-scp-on-linux/](http://www.arvindatwork.com/index.php/2007/04/02/how-to-scp-on-linux/)

scp is a command line tool

sshfs will allow you to mount a remote directory

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

Alternates would be samba or NFS

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

