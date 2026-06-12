---
title: "Network Configuration Icon"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by dmiller40 on 2008-01-24
So im using xubuntu and some how i ended up getting 2 network configuration icons in my panel. 

Also when i log in i get 
"could not look up internet address for ubuntu. this will prevent xfce from operating correctly. it may be possible to correct the problem by adding ubuntu to the file /etc/hosts on your system."

I have been trying to get my windows xp shared files on the computer and im sure i messed up somewhere. I've search around and found the same error but no fix. Can someone help me fix this?
thanks
dm

---

### Post by Michl on 2008-01-24
Guessing here on the basis of my experience in ubuntu.
One is the network manager applet and the other
is the network monitor.  Backup and then edit
/etc/network/interfaces
so that you have only the command for the internal loop:
```
auto lo
iface lo inet loopback
```
Erase everything else.

Then network manager can take over.   You might have to
reboot for network manager to manage your network
connections.  The network manager is very efficient.

If this messes-up your network connections, then go
back to your original interface file.

Michl

---

### Post by dmiller40 on 2008-01-24
Ok soo, i've spent the past couple of hours trying to grant myself permission to edit the file. 

I followed a tutorial on how to login as root and the last thing i have to do, is in the login manager check allow. Well i have 800x600 resolution and the window extends past my monitor so i can click close to save the changes.

I tried looking behind the monitor but that doesn't work, its just all black back there & i cant see anything. :-D 

dm

---

### Post by dmiller40 on 2008-01-24
I edited the copy i made, then used terminal to copy it to my file system, made sure it took, rebooted and I'm still getting the same error and still have 2 network connection icons in my panel.

:-(
dm

---

### Post by Michl on 2008-01-24
Hmm  the resolution is a separate issue.  Have you fixed matters in
Screen Resolution?  Did your screen resolution change?  It
shoudn't change just because you use root commands.

The easiest way to edit files is to open the terminal window and
enter
```
sudo gedit /etc/network/interfaces
```

you will be asked for your password and then edit and save.

---

### Post by dmiller40 on 2008-01-24
no i have an old laptop, and im sure 800x600 is its max. no big deal except that some windows extend past the screen.

dm

---

### Post by Michl on 2008-01-24
If gedit extends your monitor, use
sudo nano /etc/network/interfaces

that'll be small enough for sure.

---

### Post by dmiller40 on 2008-01-24
I got the file edited, but it did not fix. I had to edit it locally then copy it over in the terminal.
dm

---

### Post by dmiller40 on 2008-01-25
I was running some commands in terminal for samba when this started.

thanks
dm

---

### Post by Michl on 2008-01-25
Check your interfaces file to make sure you
just have those two lines, reboot, and then
click on the network manager icon.

About shared folders.  The easiest way
to do it is to go to Administration->Shared
FOlders.   You will then be asked to install
the appropriate files.  Before you do that,
though, you need to mount windows.  Here is
a link for that:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

The psychocats ubuntu page is an excellent
resource.

Sorry I couldn't help you better.
Michael

---

