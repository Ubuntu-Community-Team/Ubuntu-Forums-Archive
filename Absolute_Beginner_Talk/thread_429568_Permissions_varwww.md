---
title: "Permissions /var/www"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by aleska on 2007-05-01
not sure if this needs to be posted in a more specific forum or not.  
I just set up a LAMP server on an old pc, and have been able to both ssh into the server from command line, and also using fish:// in konquerer from my regular Kubuntu Feisty pc.  I thought the konquerer route using fish:// would be great for conveniently copying, moving, editing, etc. files.  Problem is that the files I would want to edit, those in /var/www (i.e. the webpages being served) aren't editable without sudo privileges.  

Should I simply change the privileges of /var/www to include my user?  Is that not considered safe or preferable for some reason?  If I was to change permission to allow the user to write to /var/www , how do I do that?  Is it a chown coommand?  

Thanks in advance.

---

### Post by Bachstelze on 2007-05-01
Changing ownership of /var/www is the easiest way to go, and is not very harmful security-wise. However, a more elegant solution would be to change the root of your webserver to somewhere in your home dir.

---

### Post by darkrose on 2007-05-01
is the server actually live on the net?
If not, and it's just for loacal use then changing permissions on the document root wont be a problem:
chmod o+rw -R /var/www

If it is on the net then changing the permissions like that wouldn't really be secure enough. The better options in this case would be to setup either an ftp server, giving you a pasword protected login, or an NFS server with only your desktop IP allowed to connect.

---

### Post by darkworld on 2007-05-01
> **HymnToLife said:**
> Changing ownership of /var/www is the easiest way to go, and is not very harmful security-wise. However, a more elegant solution would be to change the root of your webserver to somewhere in your home dir.

Newbie alert: Thats exactly what i would like to do! Please could you tell me how? Newbie alert:

---

### Post by viciouslime on 2007-05-01
> **darkworld said:**
> Newbie alert: Thats exactly what i would like to do! Please could you tell me how? Newbie alert:

You need to edit your apache config file: /etc/apache2/apache2.conf

I'm not exactly sure what needs chaning though, it is very different in apache2, a quick google should help, or wait until someone with more knowledge of apache sees this post. If you do find the solution via google, please post back here for everyone else :)

---

### Post by Bachstelze on 2007-05-01
(This is for Dapper, I don't think there's any difference for newer Ubuntu releases)

```
sudo nano -w /etc/apache2/sites-available/default
```

Edit the DocumentRoot directive to match the directory which you want to set as the root of your server. It is also a good idea to edit the <Directory /...> directive below. Then restart apache :

```
sudo /etc/init.d/apache2 restart
```

---

### Post by darkworld on 2007-05-01
Thanks all of the above.

viciouslime your not wrong! changed! I just updated to fiesty from dapper and reloaded apache2 and php mod.............then total horror! Went to httpd.conf to configure and the page was blank! :lolflag: 

Php wasnt working, but found module enabled folder, but couldnt find LoadModule bla bla in apache2.conf ....no loadmodule anywhere. restarted apache and refreshed browser and php was working.

This is really tough on newbies....my teach yourself apache book is out of date already and it cost me £25 :( 


Sorted now thanks. :KS

---

### Post by aleska on 2007-05-01
Many many thanks.  HymnToLife, that was perfect.  
While I'm not positive where, my grandfather was born in Breton.  His name was Pierre Castel.  Is Castel a common name in your part of the country?

---

