---
title: "Gutsy CIFS share network manager shutdown"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by max69 on 2007-12-05
Hello,
I have Gutsy installed but I have a problem. I have a Freenas file server connected to my network but when I shut the computer down in Gutsy the Network Manager shuts down first before the shares in fstab so it takes ages for my computer to shut dow down because the CIFS server is not responding (of course because it cant access it). How could I change the shutdown sequence so that it unmounts stuff in fstab before the Network Manager. I looked everywhere on the net but could not not find a solution. Thanks in advance for your help. Max

---

### Post by vikram on 2007-12-05
does the CIFS server have a script in /etc/init.d ?

---

### Post by max69 on 2007-12-05
I have no idea. It used to work fine in previous ubuntu versions. The only problem is that the Network Manager (that was not there in previous versions) shuts down before the system unmounts stuff in fstab so when it tries to unmount the network share there is no more network connection so it says the server is not responding so it takes 30 more seconds to shut down.

---

### Post by max69 on 2007-12-05
Oh and my server is on freenas based on freebsd moonwall I think. I could check if you need me too.

---

### Post by vikram on 2007-12-05
not sure if I understand 100% do you want to disable samba client before the network while shutting down ? 

sequence of shutdown scripts are in 
/etc/rc.*

not sure of the dir since i am not on my linux box right now. each has a link like S20service  to start service AFTER services 1-19 and before services > 21. similarly there will be other links like
K20service to stop the service.

these are symlinks the actual scripts are in /etc/init.d. 

be careful when you change the order of these scripts as you can potentially make your system unstable and/or behave wierdly

hope this was helpful

---

### Post by max69 on 2007-12-05
Thanks for your help.
So do you think I could change the shutdown sequence in /etc/rc.* so that the Network Manager shuts down after it unmounts the stuff in fstab? If you need more details just ask and I will give them to you. It is just a shame because it is the only reason why my client cannot switch completely to ubuntu from Windows XP.

---

### Post by vikram on 2007-12-05
sorry i cant be more specific since I dont know how you ahve mounted the shares. if you have the command to unmount the shares (or specifics like are you using smbclient) you could write a script to unmount the shares, put it in /etc/init.d and create a symlink to the file. the name of the symllink K10 as opposed to K99 will change the order of it being run.

I have used this as a template to create my own init script in the past but not for shares.

[http://users.piuha.net/martti/comp/ubuntu/en/firewall](http://users.piuha.net/martti/comp/ubuntu/en/firewall)

---

### Post by vikram on 2007-12-05
when i googled i found this ...

[http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

based on this it looks like allyou need is the umount (not unmount) command.

---

### Post by max69 on 2007-12-05
Thanks it looks like what I need. Thanks so much for your help. I am going to try it and post my feedback here.

---

### Post by max69 on 2007-12-05
I did not emphasise it enough. [COLOR="Magenta"]THANKYOU[/COLOR]. Will post my feedback tomorrow when I can test it. THANKS. Max

---

### Post by dgermann on 2007-12-17
Hi--

Will [this]("http://ubuntuforums.org/showthread.php?t=293513&highlight=cifs+shut+down&page=2") perhaps help?

---

