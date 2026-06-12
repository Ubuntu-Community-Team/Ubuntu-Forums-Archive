---
title: "Can anyone recommend some apps?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by AndrewEsther on 2008-04-06
So, I finally got apache installed and working. Now I need to decide on what I'm going to use for an ftp program, and a good server admin program. I had webmin suggested to me, as well as a few ftp clients. As n00bly as this may sound, I would kind of enjoy something with a gui slapped on it. I could do without, but as I am new to ubuntu and linux systems in general, I would like that warm fuzzy feeling of colors and buttons attached to my programs.

---

### Post by softtower on 2008-04-06
I find that under Gnome Nautilus works pretty well as an FTP client. Just type [ftp://username@yoursrever](ftp://username@yoursrever) in the address field and it works pretty well: you can have shortcuts to your FTP shares on your desktop, and it will remember the passwords if you want to.

---

### Post by wolfen69 on 2008-04-06
i heard gftp is a decent client.

---

### Post by AndrewEsther on 2008-04-06
I have also heard that gftp is a good client, but alas, it appears to be gui-less :(

and as for Nautilus, I need a program that will allow me to create an ftp server on my machine, as that is what I'm trying to accomplish here. I just use the standard firefox interface for ftp-ing out to things...

---

### Post by Rocket2DMn on 2008-04-06
+1 for gftp, and yes, it has a GUI.  What are you doing to not have it show in a GUI?
To create an ftp server, you need a program like proftpd or vsftpd.

---

### Post by AndrewEsther on 2008-04-06
Well, I did a quick google for it and looked at the gftp website... looked at the features and it didn't appear like it had a gui..

I found literature that pointed me toward proftp, as well. do either proftp or vsftp have a gui? it's not like I NEED a gui, I just don't think that I will be able to stumble my way around editing config files very easily, and my goal was to have this server up by monday...

---

### Post by Drakkor on 2008-04-06
Here's my gftp gui, I installed it with Add/Remove programs,and it's in Application>Internet

---

### Post by supertux on 2008-04-06
i should go for filezilla

---

### Post by Drakkor on 2008-04-06
Can anyone see my attached thumbnail ?  I can't for some reason, it worked in Gutsy :confused:

---

### Post by Oldsoldier2003 on 2008-04-06
> **Rocket2DMn said:**
> +1 for gftp, and yes, it has a GUI.  What are you doing to not have it show in a GUI?
To create an ftp server, you need a program like proftpd or vsftpd.

+1 For GFtp, if you have to support a mixed environment I always recommend Filezilla as a client.
As of 3.0.8.1 Filezilla handles Public Key authentication on SFTP out of the Box

---

### Post by Rocket2DMn on 2008-04-06
> **Drakkor said:**
> Can anyone see my attached thumbnail ?  I can't for some reason, it worked in Gutsy :confused:

I can see it fine ( though I'm actually in windows :( )

I'm not sure if proftp or vsftp have GUI, but to be honest, I wouldn't be surprised if they don't.  Try not to be scared away by configuration files though, they usually aren't terribly complicated, and there should be plenty of guides online to help you out.

---

### Post by softtower on 2008-04-06
I see now. AndrewEsther is asking for an FTP server, not the client. You need
sudo apt-get install ftp-server 

and then read some documentation

---

### Post by AndrewEsther on 2008-04-06
yes :-) I am trying to set up an ftp server.. I found pureadmin, though, based off of pureftpd and I like it's simplicity.

not sure what anyone else thinks of it.... and on those lines, would anyone happen to know how to define which ports it uses??

---

### Post by Rocket2DMn on 2008-04-06
There should be a file somewhere, like pureadmin.conf
Standard port for FTP is 21, and for SFTP it's 22 (same as SSH).

---

### Post by apostate on 2008-04-07
> **Rocket2DMn said:**
> There should be a file somewhere, like pureadmin.conf
Standard port for FTP is 21, and for SFTP it's 22 (same as SSH).

pure-ftp does indeed have a GUI admin app, and is a very serviceable ftp server. Give it a shot. It is easy and straightforward to set up, even if you do have to hack the config file, which you should not, given pureadmin...

---

### Post by nonewmsgs on 2008-04-08
wrong ubuntuforum tab.  sorry.

---

