---
title: "Login Problems $HOME/.dmrc"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-04-29
When loging in I receive an error:

Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permisions.

I verified that the file is owned by the user, and permissions are set to 644. I log out then back in, and get the same error. ](*,) 

Any assistance is greatly appreciated.

---

### Post by cwaldbieser on 2006-04-29
[QUOTE=DSn0wMan]When loging in I receive an error:

Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permisions.

I verified that the file is owned by the user, and permissions are set to 644. I log out then back in, and get the same error. ](*,) 

Any assistance is greatly appreciated.[/QUOTE]
Can you try renaming the file?  Sometimes if a config file isn't there, an app will create a new one for you.  e.g.
```

$ mv .dmrc .dmrc.bak

```

---

### Post by mostwanted on 2006-04-29
Usually that's a sign that something went wrong in the install and your hosts file is wrong:

[http://www.ubuntuforums.org/showpost.php?p=748387&postcount=13](http://www.ubuntuforums.org/showpost.php?p=748387&postcount=13)

Or you might try reinstalling. That usually fixes this issue (I've tried it myself once installing Ubuntu Breezy).

---

### Post by DSn0wMan on 2006-04-29
[QUOTE=cwaldbieser]Can you try renaming the file?  Sometimes if a config file isn't there, an app will create a new one for you.  e.g.
```

$ mv .dmrc .dmrc.bak

```[/QUOTE]

no dice, same error.

---

### Post by raovq on 2006-04-30
this is the same reply i made in the thread in bug reports. this is how i fixed it with information in that thread.


i had this problem for ages. i usually just ignore it, then out of frustration i just deleted the file and ignored it.

so, to fix it, i recreated the file;

gedit .dmrc
then i closed and saved the file


then i changed the permissions for my entire home directory (not sure why, it was suggested)

> 
sudo chmod 755 /home/{your username}


then i changed the permissions for .dmrc

> 
sudo chmod 644 .dmrc

sudo chown username .dmrc



im not sure what combination fixed the problem, but it worked for me perfectly.

---

### Post by DSn0wMan on 2006-04-30
/etc/hosts file looks fine

I tried chmod 755 $HOME/<user> 

and, recreated the file .dmrc, then chmod 644 and chown <user>

Still no dice.

The one thing I thought was strange is that the user that doesn't get this error has his .dmrc with 600 permissions. This is the way it installed.

I also reinstalled, and recreated the user. No luck! ](*,) 

I am only using this user to install oracle. Once the install is done, I really don't need to log in to any X applications with this user.

I guess my question now is-- Is there any compelling reason why I care if it dosn't save session information?

If it doesn't affect the install then I guess it's fine the way it is.:-|

---

### Post by patrick295767 on 2006-04-30
[QUOTE=mostwanted]Usually that's a sign that something went wrong in the install and your hosts file is wrong:

[http://www.ubuntuforums.org/showpost.php?p=748387&postcount=13](http://www.ubuntuforums.org/showpost.php?p=748387&postcount=13)

Or you might try reinstalling. That usually fixes this issue (I've tried it myself once installing Ubuntu Breezy).[/QUOTE]

 Meee Mee too, & 4 days ago  !! 
Just recently !
I installed e17, then after few days all went wrong
 
I am sure I didnt touch the hosts files ... & exports files and so on ...
 
No body was using the linux box during few hours, then pc was frozen,
then  I wanted to use it : nothg moved with mouse
folder sharing exports still working, but no mouse reaction
I reboot the guy (linux box) (cold reset)
then 
this error msg appeared chronocaly and constantly :-(
Reading files into subfolders is not possible anymore also
    
I hope we can find out what happened or were is the prob ... ! 
  
That's very strange, is nt it ??
( """"virus"""" :-) ??)

---

### Post by nalmeth on 2006-04-30
maybe

sudo chown username /home/username

??

---

### Post by patrick295767 on 2006-04-30
[QUOTE=raovq]this is the same reply i made in the thread in bug reports. this is how i fixed it with information in that thread.


i had this problem for ages. i usually just ignore it, then out of frustration i just deleted the file and ignored it.

so, to fix it, i recreated the file;

gedit .dmrc
then i closed and saved the file


then i changed the permissions for my entire home directory (not sure why, it was suggested)



then i changed the permissions for .dmrc




im not sure what combination fixed the problem, but it worked for me perfectly.[/QUOTE]
  
In my case, it's all the user folder that is giving some troubles ... 
 
That's strange error mistake ...

---

### Post by patrick295767 on 2006-04-30
[QUOTE=nalmeth]maybe

sudo chown username /home/username

??[/QUOTE]
  
The thing is that I didnt touch to the server, soo what could have happen to this machine by itself ... even all users of the linux server (that havent been used ) have same dmrc error msg ... 
  
I cant understand ... :-k

---

### Post by DSn0wMan on 2006-04-30
[QUOTE=patrick295767]The thing is that I didnt touch to the server, soo what could have happen to this machine by itself ... even all users of the linux server (that havent been used ) have same dmrc error msg ... 
  
I cant understand ... :-k[/QUOTE]

weird...  I only get this with my oracle user. My user created at install seems to be fine.

btw - I created this user from the command line after my reinstall, and it didn't even make a .dmrc file.

---

### Post by DSn0wMan on 2006-04-30
[QUOTE=raovq]this is the same reply i made in the thread in bug reports. this is how i fixed it with information in that thread.


i had this problem for ages. i usually just ignore it, then out of frustration i just deleted the file and ignored it.

so, to fix it, i recreated the file;

gedit .dmrc
then i closed and saved the file


then i changed the permissions for my entire home directory (not sure why, it was suggested)



then i changed the permissions for .dmrc




im not sure what combination fixed the problem, but it worked for me perfectly.[/QUOTE]


Its working now.

I guess I just needed to log in a second time after making the changes you suggested.

Thanks for all the help. :D

---

### Post by patrick295767 on 2006-05-02
I did : 

```
echo "  " >> /home/username/.dmrc
chmod u+rw -R /home/username
chown username /home/username
chgrp username /home/username
```
  is not working to login ... 
  
I'll try the chmod 755 /home/username with gedit 
this evenign ... I hope it'll work ;) 
  
Greetings!
-- 
other forum nfo ab. it ... :
[http://www.suseforums.net/lofiversion/index.php/t17510.html](http://www.suseforums.net/lofiversion/index.php/t17510.html)
the TODO cmd line:
> (chown crispy:users /home/crispy  )
   
---
also : 
[http://www.ubuntuforums.org/showthread.php?t=91455](http://www.ubuntuforums.org/showthread.php?t=91455)
  
[http://www.exgobz.com/article-30](http://www.exgobz.com/article-30)
  
[http://forum.ubuntu-fr.org/viewtopic.php?pid=270009](http://forum.ubuntu-fr.org/viewtopic.php?pid=270009)
 
>     your $home/.dmrc has incorrect permissions and is being ignored. This prevents the default session and language from beeing saved. File should be owned by user and have 644 permission

On obtient ce message d&#8217;erreur après avoir modifié les permissions de son répertoire utilisateur ( /home/votre_login ). Il s&#8217;agit semble t&#8217;il d&#8217;un problème de droits sur le fichier de configuration de lancement de session graphique. Le problème étant qu&#8217;effectuer les actions recommandées par le message d&#8217;erreur ne suffit pas à le faire disparaitre. Il faut donc modifier les droits du fichier (lecture/ecriture pour le proprietaire, lecture pour le groupe et le reste du monde) :

chmod 644 ~/.dmrc

Et eventuellement se remettre en tant que proprietaire

sudo chown votre_login /home/votre_login/.dmrc

Mais aussi modifier les droits du répertoire personnel (non récursivement) :

chmod 700 /home/votre_login

Ce qui n&#8217;est pas indiqué dans le message d&#8217;erreur.
  
> cd ~
sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username
  
> 
2. in /etc/gdm/gdm.conf in section security insert:
"RelaxPermissions=1"
  
And this problem happened indeed when the pc was rebooted :
> omment:
further the user who wrote that this problem occured only after a reeboot, WAS right
  
From Kai:
> Hi,
i think i found at least one problem.
this is in /etc/gdm/gdm.conf
solution:
1. leave your permission as they are(see below).

2. in /etc/gdm/gdm.conf in section security insert:
"RelaxPermissions=1"

3. restart gdm by killing and starting it again from a real console(ALT F1->login->#killall gdm->#gdm).

that should fix it if you havn't screwed up your permissions with your tryes to get them right. and never touch the graphical configuration tool or remember these steps.

bug(szenario):
this is a bug in the configuration tool, as it changes a setting, which it shouldn't(you didn't ask for it to do so!).
if you do a configuration via the graphical configuration tool(e.g. from the greeter) it deletes this key. that means default which falls to 0. so after configuration this key is no longer in the file and when gdm is restarted(and this IS usualy only after a reboot) permissions are checked "paranoid". this means at least no group writable home.

group writable homes are no security hole when intended - as well as umask 002. "user private groups" are common in debian(ubuntu as well). in this case each user has its own group and no one but the user can access a group writable home.


comment:
further the user who wrote that this problem occured only after a reeboot, WAS right. the configuration is reread only after a start of gdm - no logout and no zapping(ctrl-alt-backspace) causes a reread. after install he had a correct configuration from the maintainer, he changed the settings(e.g. language or the session, somthing like that) which where not read as long as gdm kept running and only after the reboot they where read in with the missing key. and the message popped up.

this is at least one bug causing this problem.
regards,
kai
  
And right again from kai : 
> Sorry raovq, but your solution does NOT help in many cases. In cases it helps you only need to follow the messagebox advice
  
The solution if users have their own group: 
> 
Code:

RelaxPermissions=1

means group writeble is ok. this is what you might want with debian(ubuntu) if your users have their own groups.
   
--- the user solution : 
> he way to go with traditional unix - "users" is the primary group
in /etc/gdm/gdm.conf as root set in section security
Code:

RelaxPermissions=0


Code:

chmod o-w,g-w,a-x .dmrc chmod o-w,g-w $HOME

additional steps if neccessary(give root password when asked):
Code:

su -c "chown $USER $HOME" 
su -c "chown $USER $HOME/.dmrc"

(if you delete .dmrc, it should be created automaticly correctly with the next start of gdm otherwise "touch .dmrc"). this was also suggested before.
  
Can someone report this to bugzilla ??
( as for debian, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=339965](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=339965))
 Is this bug corrected with Dapper ??

---

### Post by patrick295767 on 2006-05-02
Only this worked for me :
(no changes to the gdm)
```
sudo chown  username userfolder 
sudo chmod 755 /home/userfolder
sudo rm -rf /home/userfolder/.dmrc
```

---

