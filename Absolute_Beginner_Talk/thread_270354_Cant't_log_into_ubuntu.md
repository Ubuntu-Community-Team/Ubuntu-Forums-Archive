---
title: "Cant't log into ubuntu"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by boogyman on 2006-10-03
Hi When I try to login after I enter the correct username and password it goes to a black screen and then to a maroon screen then back to the login screen. I'm the only user and have tried entering an incorrect password to check if the same thing happens but it just says incorrect user or password so I know that I have my user and pass are right. 
Any ideas what I'm doing wrong. I have only been using it like two days and the only thing I've tried to do in it is change resolution so don't think I could have done anything wrong with the command line.

---

### Post by boogyman on 2006-10-03
Does no one know how to fix this? Please I would really like to be able to get into ubuntu

---

### Post by risbac on 2006-10-03
Mmmmm. Not so easy. Here is what I would maybe try: there is apparently something wrong in your account. You can probably still boot in recovery mode. 

I would then first create a new account to see if all the accounts have the same problem. Then it means it's probably a problem with Gnome. But let's say the other account is working fine. 

Two solutions from there, first you can also try to create another account, and give him the sudo rights. 

Otherwise second solution, go into your account home (/home/yourlogin), and remove all the files except the needed ones. I think it's only the .bashxxx files, all the rest can be deleted. But I'm not sure, maybe someone will correct me or propose a much better solution? 

Of course, if you want to try this, backup your documents or any other useful files to another directory.

---

### Post by boogyman on 2006-10-03
Well seeing I have just started using it I have no files on there. It is as stock as you can get. Also I've discovered in the few seconds that the screen goes black if I press enter the same screen as the recovery screen (resembles DOS) comes up and I can enter in recovery mode but as I am a newbie I don't know what to do there.
Thanks for the response.
Bartman

---

### Post by xyz on 2006-10-03
Perhaps getting some infos here would help:
[http://ubuntuforums.org/showthread.php?t=90361](http://ubuntuforums.org/showthread.php?t=90361)

---

### Post by boogyman on 2006-10-03
Sorry but in that thread weren't they talking about not having permission but seeing I have the only account on this computer and that was the account that I installed ubuntu with that I should have all the permissions. Sorry I'm getting confused.

---

### Post by LookTJ on 2006-10-03
Do you have an ATI Driver? if yes you will need to edit /etc/gdm/gdm.conf then find AlwaysRestartServer and set it to true.

---

### Post by risbac on 2006-10-03
Could be a problem with your video drivers maybe? But you would probably not see the login screen then. 

I would still try to go into your /home/login directory, delete everything except the .bashxxx three files, and reboot.

---

### Post by boogyman on 2006-10-03
I personally haven't installed one but do have an ATi GPU so would it have been installed automatically?

---

### Post by LookTJ on 2006-10-03
> **boogyman said:**
> I personally haven't installed one but do have an ATi GPU so would it have been installed automatically?

do what i said in my above post

to edit that file

open terminal

type

gksudo gedit /etc/gdm/gdm.conf

---

### Post by Ben Sprinkle on 2006-10-03
> **Taylor said:**
> do what i said in my above post

to edit that file

open terminal

type

gksudo gedit /etc/gdm/gdm.conf

Hello taylor. :)
As for you, try to remote login with the ubuntu live cd, or do a terminal login and see what works.

---

### Post by boogyman on 2006-10-03
Well I went into recovery mode and entered in 'gksudo gedit /etc/gdm/gdm.conf' and got the response '(gksudo:4065): Gtk-WARNING **: cannot open display:' so I'm not sure if that's good or bad but I don't think it did anything. Also should I try using the live cd to start up and see if that makes a difference. I'll try that now.

---

### Post by LookTJ on 2006-10-03
I don't think recovery mode has xserver started?

---

### Post by boogyman on 2006-10-03
well with the live disc I got into ubuntu, but not as my user and I couldnt log in as my user either so there goes that idea.
Any more suggestions?

---

### Post by risbac on 2006-10-03
It doesn't look so much like a video driver problem... 
Did you try to delete everything in your home except the .bash* files? There are plenty of hidden files and folders, you won't see them with a regular "ls", you must use "ls -a" instead.

And if you can to check your gdm conf, you must enter a "nano /etc/gdm/gdm.conf".

---

### Post by risbac on 2006-10-03
Did you check your logs? We don't even know for sure where is the problem.

Check for the gdm and Xorg logs in /var/logs/, there must be something there.

---

### Post by HareBall on 2006-10-03
> **boogyman said:**
> Well seeing I have just started using it I have no files on there. It is as stock as you can get. Also I've discovered in the few seconds that the screen goes black if I press enter the same screen as the recovery screen (resembles DOS) comes up and I can enter in recovery mode but as I am a newbie I don't know what to do there.
Thanks for the response.
Bartman

If you don't have any files, why not try reloading the OS. I have had a few problems and the only way around it was to reload Ubuntu. The last time I made my /home on a different partition so I could reload the os without having to lose anything.
Maybe someone else has a better idea, but I would try this and see if maybe something just got corrupted in the loading.
Larry

---

