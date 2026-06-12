---
title: "a simple how to for home network"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by randlieb on 2006-09-16
i have been searching google and this forum for a simple, non technical, step by step how to for setting up a home network using 2 ubuntu machines. i just want to share files and learn a bit about networking in the process. 

anybody can point me to another thread or web address? even a book if i have to?

i have been using and learning on ubuntu since hoary. however i am not a savvy technophile at all, though i can learn if things are explained to me clearly enough. ASSUME I AM AN IMBECILE!!!!!

---

### Post by Garyu on 2006-09-16
You can always use samba, then you will be able to connect to windows machines as well:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

Otherwise, the best way is to use ssh. 
```
sudo apt-get install ssh ssh-client ssh-server
```

I'm not sure you need all of those or maybe something else, like sshfs might be useful if you want to mount your harddrive over the network.

Anyways, what you do once it is installed is:
```
ssh username@hostname
```
or possibly (if you haven't got wins and winbind installed)
```
ssh username@IP
```

You may also connect through nautilus. Press Ctrl-L and type
```
ssh://username@hostname
```

Aside from those two alternatives there is something called VNC that you can setup to use your computer over a network with X and everything just as if you were there. But I don't know how to configure that.

---

### Post by tagra123 on 2006-09-16
A good file sharing how to:

[http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)

Troubleshooting:

[http://www.ubuntuforums.org/showthread.php?t=258322](http://www.ubuntuforums.org/showthread.php?t=258322)

---

### Post by Garyu on 2006-09-16
personally, I would not recommend NFS as tagra123 is linking to... but if you like smashing your head to the wall and use old obfuscated technologies, go right ahead. :cool:

heh, no, I am exaggerating of course. but seriously, ssh is the best choice by far, and samba for talking to windows-machines. that is all you will ever need.

---

### Post by randlieb on 2006-09-16
i have some questions but have to get to work now. i'll be back this afternoon. thanks for the quick response.

---

### Post by tagra123 on 2006-09-30
> **Garyu said:**
> personally, I would not recommend NFS as tagra123 is linking to... but if you like smashing your head to the wall and use old obfuscated technologies, go right ahead. :cool:

heh, no, I am exaggerating of course. but seriously, ssh is the best choice by far, and samba for talking to windows-machines. that is all you will ever need.

Hey 

NFS is easy to set up for ubuntu to ubuntu. Less than 5 minutes per machine. Do that with Samba!!!

Samba is the best for windows to windows but if you've already shared with the windows machines you might as well sharer with the ubuntu machines too.

I also have ssh set up too I found the sshfs file sharing ot be a little on the slow side -- especially over wireless networks but it does work.

---

### Post by David Corrales on 2006-09-30
I'd go with Samba since it's easy to get going and it's from GUI. Also, you can share printers that way.

---

### Post by Garyu on 2006-10-01
> **David Corrales said:**
> I'd go with Samba since it's easy to get going and it's from GUI. Also, you can share printers that way.

How to use SSH - the GUI way:

1) Search in Synaptic for ssh. Install ssh-client and ssh-server.
2) Open Nautilus. Press Ctrl-L for Go to location. Enter "ssh://IP-number/sharename". Voila, drag and drop files or folders, etc.

How to use SSH - the terminal commands way:

1) sudo apt-get install ssh-client ssh-server
2) ssh username@IP-number
3) you're up. use scp to copy files. run any terminal commands you like on your remote machine. etc.

Are you saying samba is easier? For linux to windows, sure. NFS in five minutes? Setting up SSH will take a lot less time than five minutes. No messing about with settings or sharing folders is needed. By far the best solution for an absolute beginner. :cool:

---

### Post by Garyu on 2006-10-01
> **Garyu said:**
> How to use SSH - the GUI way:

1) Search in Synaptic for ssh. Install ssh-client and ssh-server.
2) Open Nautilus. Press Ctrl-L for Go to location. Enter "ssh://IP-number/sharename". Voila, drag and drop files or folders, etc.

How to use SSH - the terminal commands way:

1) sudo apt-get install ssh-client ssh-server
2) ssh username@IP-number
3) you're up. use scp to copy files. run any terminal commands you like on your remote machine. etc.

Are you saying samba is easier? For linux to windows, sure. NFS in five minutes? Setting up SSH will take a lot less time than five minutes. No messing about with settings or sharing folders is needed. By far the best solution for an absolute beginner. :cool:

EDIT:
If you set up WINS and winbind you don't even need to know IP-numbers, just use the hostname.

---

### Post by David Corrales on 2006-10-01
I found out that samba was actually quite easy to activate. Just go to System->Administration->Shared Folders and choose the option to install samba. Afterwards you can share/browse normally.
SSH is great for controlling remote machines and setting up some static shares, but for regular network browsing, samba is the easiest way I think.

---

### Post by neilyweily on 2006-10-02
thanks, but i can't get it to work

when i type in terminal ssh user@192.168.0.2

i get port 22 connection refused

don't know why though :confused:

---

### Post by jd65pl on 2006-10-02
You will probably need to turn on the ssh server on the server machine use

```
sudo sshd
```

To start it

---

### Post by neilyweily on 2006-10-03
all fixed now

finally got the laptop connected to the internet through the desktop, so then could do a dist-upgrade

then reinstalled ssh and it all works now perfectly

thanks for the howto, and for the help :D

---

### Post by sunspots on 2006-11-15
This topic helped another ... me. Thanks everyone.

---

