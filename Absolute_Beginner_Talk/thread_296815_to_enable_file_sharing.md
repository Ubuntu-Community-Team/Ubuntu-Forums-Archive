---
title: "to enable file sharing"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by benner on 2006-11-10
I have been trying to enable file sharing on my newly upgraded edgy kubuntu system.  kmenu>system settings>sharing and to make changes requires root access.  i click on 'administrator mode' and it asks for my password.  no problems.  but then nothing happens.  the box now has a red outline and the 'administrator mode' button is no longer active and that's it.  is this a bug?  when i was runnng dapper i had the same problem and i was hoping it would work here.  i am running a dual boot notebook going through a router to a desktop that runs edubuntu.  i can use konquerer to access the other machine through remote places>samba shares but the other machine can't access this one until i enable the files to be shared.
also, another question...  can i attach a printer to one of the machines and print from both?  where should i look to learn how to do that?

thanks in advance,
-benner

---

### Post by biffta on 2006-11-10
I am have seen similar things to this before. What I used to try would be to open the application as root via kdesu and Alt+F2. 
What I mean by this is say the application you want to run is called kate (in your case it must be kdeshare or something similar), I would press ALT+F2 then type "kdesu kate". This will mean all the admin functions are already enabled.
You can do similar stuff to this in Ubuntu just swap kdesu for gksudo!

---

### Post by benner on 2006-11-10
thanks.  that is a good tip for the future.  but in this case, i have no idea what the program would be called.  i imagine that the file sharing settings are a part of the base system.  when i go into admin mode, it lets me put in the password but then the settings remain greyed out.  i can read them but can't change them.

---

### Post by id12586 on 2006-11-13
I have the same problem also :rolleyes: ](*,) 

Kubuntu 6.10

---

### Post by RudolfMDLT on 2006-11-13
To find the command to something in the "start bar"-menu rightclick the thing and say "put in run dialog" or "Edit item" and copy the command from there. Are you trying to network Linux to Linux or Linu to windows. If the latter then just edit the config file and configure Samba by hand - If you need help I'll be happy to.

---

### Post by mep on 2006-11-13
> **RudolfMDLT said:**
>  If the latter then just edit the config file and configure Samba by hand - If you need help I'll be happy to.

I was wondering if you could tell me how to config samba by hand.  I install gsambad but it's default conf is rather confusing to e.  I am running Ubuntu 6.10 new install and I am trying to get my printer and file sharing going.  My printer is fine locally but not being seen by my windows 2000 headless machine.  Win2000 sees the Ubuntu box but will not connect to printer or to file sharing.

I have at least ubuntu box in Workgroup... :)

Hope you can help..

-mep

---

### Post by RudolfMDLT on 2006-11-14
Hi there,

Okay, let start from scratch, enter the following in the terminal:

> sudo apt-get install samba smbfs

Now we are going to edit and add users to samba:

Copy and paste the following lines into the terminal with the appropriate changes.

> sudo smbpasswd -e yourname 
Where yourname = you're user name - This will be the Admin user for Samba. Type and retype new Samba password

> sudo smbpasswd -a XP windowsusername
(kitchenpc)
Where windowsusername = the usernames of your network users
Type and retype their passwords. Do this for every machine on the network.


next you have to add these users to your computers user list.

System => Administration=> Users and groups. Here you add all the users exactly as you added them to samba.

Now,
> 
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf

To backup your current samba config file and edit the original.

Find this line

...
;  security = user
...

and replace it with this line:

  security = share

To enable printer sharing, find the following lines


 # printing = cups
 # printcap name = cups

and uncomment them. (remove the #'s)

save the file and restart the your machine.

This should work now. Sharing folders should now be possible via the preferences menu or the administration menu and any printers installed should be shared.

Post back if you have any problems! 

Goodluck,

Rudolf

---

### Post by mep on 2006-11-14
Thanks...  That got me going in the right direction... :) I setup the folder sharing.  All is working...  Thanks!

-mep

---

### Post by RudolfMDLT on 2006-11-14
My pleasure!:)

---

### Post by Zeroangel on 2006-11-27
Helped me too. 

Thanks! :KS

---

