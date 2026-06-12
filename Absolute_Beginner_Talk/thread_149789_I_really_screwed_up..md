---
title: "I really screwed up."
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by gpeck157 on 2006-03-24
Hi All,

I really screwed up. Normally I'm more careful. I wanted to change the file permissions in my wife's "teresa" directory. I used the command sudo chmod  -R 777 *. To my horror, I realized afterward that I was in the "home" directory.

The sudoers file permissions were changed as well as the .dmrc file permissions. I was able to fix those two after reading a number of posts, but now I'm finding that the internet is not working, nor is the ability to view the other network computers in Samba. I need help.

I'm starting to think my only option is to reinstall everything but I really don't want to do that if I don't have to. If I do have to reinstall everything, is there a way to do it without losing all her user files (documents, pictures etc.)?

I guess this is a testament to being careful with sudo.

Thanks,
G

---

### Post by dcstar on 2006-03-24
[QUOTE=gpeck157]Hi All,

I really screwed up. Normally I'm more careful. I wanted to change the file permissions in my wife's "teresa" directory. I used the command sudo chmod  -R 777 *. To my horror, I realized afterward that I was in the "home" directory.
.......[/QUOTE]
If you were just in the HOME directory, probably the easiest thing to do would be is to create a new user, and then look at the files/directories created to learn what the actual various permissions should be, and then manually fix those you have borked.

---

### Post by gpeck157 on 2006-03-24
[QUOTE=dcstar]If you were just in the HOME directory, probably the easiest thing to do would be is to create a new user, and then look at the files/directories created to learn what the actual various permissions should be, and then manually fix those you have borked.[/QUOTE]

David, thanks. I'll give that a try. On the same note, is it possible to transfer user files such as pictures etc. to the new user account? I'm thinking I could create a new user, move all the user files over then delete the old account.

Thanks,

Glen

---

### Post by rcmiv on 2006-03-24
First of all, I am not able to help you with your problem.  All I can do is commiserate.

I recently did the exact same thing to my system, by chmod'ing an entire / directory of a mounted network drive, simply because I wanted to edit a file, and was pissed. I couldn't figure it how to (quickly, or easily) fix it.  

I am sure someone here can help you though. I hope so, cuz the info would be useful for me as well.

It reminds me of the Hole Hawg metaphor from Neal Stephenson's "In the Beginning was the Command Line."  The whole essay is great reading for (l)unix beginners, but you should at least grab the text, search for "drill," and read what follows...it's available free here:

[http://www.cryptonomicon.com/beginning.html](http://www.cryptonomicon.com/beginning.html)

A quote therefrom:
[SIZE="1"]"After a few such run-ins, when I got ready to use the Hole Hawg my heart actually began to pound with atavistic terror.

But I never blamed the Hole Hawg; I blamed myself. The Hole Hawg is dangerous because it does exactly what you tell it to. It is not bound by the physical limitations that are inherent in a cheap drill, and neither is it limited by safety interlocks that might be built into a homeowner's product by a liability-conscious manufacturer. The danger lies not in the machine itself but in the user's failure to envision the full consequences of the instructions he gives to it.

A smaller tool is dangerous too, but for a completely different reason: it tries to do what you tell it to, and fails in some way that is unpredictable and almost always undesirable. But the Hole Hawg is like the genie of the ancient fairy tales, who carries out his master's instructions literally and precisely and with unlimited power, often with disastrous, unforeseen consequences."[/SIZE]
-Stephenson, ITBWTCL

Sound familiar?

-rcmiv

---

### Post by aysiu on 2006-03-24
[QUOTE=gpeck157]David, thanks. I'll give that a try.On the same note, is it possible to transfer user files shuch as pictures etc to the new user account? I'm thinking I could create a new user, move all the user files over then delete the old account.

Thanks,

Glen[/QUOTE] Yes, you can do that. Make sure you *chown* (change ownership) of those files after you move them.

So if you create a new user called teresa2 and move everything from teresa there, you'd want to ```
sudo chown -R teresa2:teresa2 /home/teresa2
```

---

### Post by gpeck157 on 2006-03-24
[QUOTE=aysiu]Yes, you can do that. Make sure you *chown* (change ownership) of those files after you move them.

So if you create a new user called teresa2 and move everything from teresa there, you'd want to ```
sudo chown -R teresa2:teresa2 /home/teresa2
```[/QUOTE]

Wonderful! Thanks Aysiu. I'll do that. I knew I could count on this terrific Ubuntu community.

Glen

---

### Post by gpeck157 on 2006-03-24
[QUOTE=rcmiv]First of all, I am not able to help you with your problem.  All I can do is commiserate.

I recently did the exact same thing to my system, by chmod'ing an entire / directory of a mounted network drive, simply because I wanted to edit a file, and was pissed. I couldn't figure it how to (quickly, or easily) fix it.  

I am sure someone here can help you though. I hope so, cuz the info would be useful for me as well.

It reminds me of the Hole Hawg metaphor from Neal Stephenson's "In the Beginning was the Command Line."  The whole essay is great reading for (l)unix beginners, but you should at least grab the text, search for "drill," and read what follows...it's available free here:

[http://www.cryptonomicon.com/beginning.html](http://www.cryptonomicon.com/beginning.html)

A quote therefrom:
[SIZE="1"]"After a few such run-ins, when I got ready to use the Hole Hawg my heart actually began to pound with atavistic terror.

But I never blamed the Hole Hawg; I blamed myself. The Hole Hawg is dangerous because it does exactly what you tell it to. It is not bound by the physical limitations that are inherent in a cheap drill, and neither is it limited by safety interlocks that might be built into a homeowner's product by a liability-conscious manufacturer. The danger lies not in the machine itself but in the user's failure to envision the full consequences of the instructions he gives to it.

A smaller tool is dangerous too, but for a completely different reason: it tries to do what you tell it to, and fails in some way that is unpredictable and almost always undesirable. But the Hole Hawg is like the genie of the ancient fairy tales, who carries out his master's instructions literally and precisely and with unlimited power, often with disastrous, unforeseen consequences."[/SIZE]
-Stephenson, ITBWTCL

Sound familiar?

-rcmiv[/QUOTE

Well said, and I appreciate the moral support. The thing is, I should know better. I'm a former network admin under the Gates system. I hadn't had my coffee, and I was in a BAH (big a??ed hurry) . I know too that most people using Linux are pioneers at least in spirit if not in fact. They are not satisfied with the status quo and with paying undue tribute to Redmond or anywhere else. Community is an appropriate name for this forum for it truly is that, a community of like minded, adventurous souls who don't mind helping each other. I'm proud to be a part of it, even if at times it is a painful learning curve.

Thanks,
Glen

---

### Post by gpeck157 on 2006-03-24
[QUOTE=dcstar]If you were just in the HOME directory, probably the easiest thing to do would be is to create a new user, and then look at the files/directories created to learn what the actual various permissions should be, and then manually fix those you have borked.[/QUOTE]

Hi David,
I was only able to create a new user from the terminal but not from the graphical interface (Users and Groups won't even open). After creating the new user "teresa2" I still cannot access the internet, nor do a number of other things work. I'm afraid I've screwed this up more than I originally thought. Any other suggestions?

Thanks,

Glen

---

### Post by dcstar on 2006-03-24
[QUOTE=gpeck157]Hi David,
I was only able to create a new user from the terminal but not from the graphical interface (Users and Groups won't even open). After creating the new user "teresa2" I still cannot access the internet, nor do a number of other things work. I'm afraid I've screwed this up more than I originally thought. Any other suggestions?

Thanks,

Glen[/QUOTE]
Can you log in on that account after booting up?

If you cannot then it is possible that you have also changed the HOME directory permissions, so open a terminal and try:
```
sudo chown root /home
sudo chgrp root /home
sudo chmod 755 /home
```

---

### Post by trent dillman on 2006-03-24
Make sure you're in the admin group, first off....


boot with a live cd, remount your / drive read/write, and add yourself to /etc/sudoers 

```
username     ALL=(ALL) ALL
```

save that, reboot, log in then open a root shell 

```
sudo -s
```

add your username to the admin group

```
usermod -G admin username
```

finally, edit /etc/sudoers and remove what you changed

then you can get back on your feet....

---

### Post by gpeck157 on 2006-03-25
[QUOTE=dcstar]Can you log in on that account after booting up?

If you cannot then it is possible that you have also changed the HOME directory permissions, so open a terminal and try:
```
sudo chown root /home
sudo chgrp root /home
sudo chmod 755 /home
```[/QUOTE]
 
Hi David,

I am not able to login. I ran the code you suggest but I'm getting the following message:
"GDM could not write to your authorization file..."
Any suggestions?
I have now deleted the "teresa2" account.

Thanks,

Glen

---

### Post by gpeck157 on 2006-03-25
[QUOTE=trent dillman]Make sure you're in the admin group, first off....


boot with a live cd, remount your / drive read/write, and add yourself to /etc/sudoers 

```
username     ALL=(ALL) ALL
```

save that, reboot, log in then open a root shell 

```
sudo -s
```

add your username to the admin group

```
usermod -G admin username
```

finally, edit /etc/sudoers and remove what you changed

then you can get back on your feet....[/QUOTE]

Hi Trent,

Thanks for the suggestion. I added "teresa" to the admin group from the recovery command prompt, but I cannot login at all except in recovery mode.

Thanks,
Glen

---

### Post by gpeck157 on 2006-03-25
[QUOTE=dcstar]Can you log in on that account after booting up?

If you cannot then it is possible that you have also changed the HOME directory permissions, so open a terminal and try:
```
sudo chown root /home
sudo chgrp root /home
sudo chmod 755 /home
```[/QUOTE]

Hi David,

At this point, all I want to do is get my wife's personal files off of her computer, things like her documents, and pictures, and transfer them to my computer via my local area network. Then I'll just reinstall Breezy. I had Samba working perfectly before all of this occurred. Is it possible to transfer her personal files from her computer to mine (mine is running either Breezy or WinXP) from the recovery mode? If so what are the commands I need? I can't see my wife's computer through Samba on my computer.

Thanks,
Glen

P.S. Is there a way to reinstall Breezy without destroying her personal files? During installation Breezy always wants to repartition the drive.

---

### Post by trent dillman on 2006-03-25
Is your home drive on a separate partition? If so, you should be able to reinstall and just not format that partition. Also, try pinging your other box from recovery and send your files that way.

---

### Post by gpeck157 on 2006-03-25
[QUOTE=trent dillman]Is your home drive on a separate partition? If so, you should be able to reinstall and just not format that partition. Also, try pinging your other box from recovery and send your files that way.[/QUOTE]
 
Hey Trent, thanks for responding. Yes the partitions are separate. I just used the installation CDs defaults when I set up my wife's computer to use Breezy.

I hadn't thought of trying to ping the other box since I couldn't see her computer from mine, but I'll give it a try.

I just boot to a live CD on her computer. Is it possible to transfer the files from her hard drive while using the live CD? If so, how?

Thanks,

Glen

---

### Post by gpeck157 on 2006-03-25
[QUOTE=trent dillman]Is your home drive on a separate partition? If so, you should be able to reinstall and just not format that partition. Also, try pinging your other box from recovery and send your files that way.[/QUOTE]

Hey Trent,

Ok, here's what I did. I boot to a live CD. Then I mounted the hard drive to be useable under the live CD. Then I set up Samba to share files. I was able to mount my wife's hard drive and retrieve her files. I then transferred all her personal files, pictures, documents etc. over to my computer via my LAN here at home. Now, I'll simply reinstall Ubuntu Breezy on my wife's computer and transfer all her personal files back to her computer.

Thanks for your input and to David for his input. You both were very helpfull.

Glen

---

### Post by trent dillman on 2006-03-25
No problem. Glad I could help!

---

### Post by Mustard on 2006-03-25
I'm just curious about the use of the usermod command, as when I read the manual on usermod it says that any groups that are not listed in the command that the user is a member of will be removed.  From this I assume it means that you have to explicitly state every group that the user needs to be part of.  So what groups are going to be dropped if you only choose 'admin'?

For instance, my user is part of all these groups..
```
mustard adm dialout cdrom floppy audio dip video plugdev lpadmin scanner

```

---

### Post by gpeck157 on 2006-03-27
[QUOTE=Mustard]I'm just curious about the use of the usermod command, as when I read the manual on usermod it says that any groups that are not listed in the command that the user is a member of will be removed.  From this I assume it means that you have to explicitly state every group that the user needs to be part of.  So what groups are going to be dropped if you only choose 'admin'?

For instance, my user is part of all these groups..
```
mustard adm dialout cdrom floppy audio dip video plugdev lpadmin scanner

```[/QUOTE]

Mustard, 

Great question. I hadn't used the "usermod" command before, and now that everything is reinstalled and working fine, it might be interesting to do an experiment to find out. Do you already know the answer? What would be the syntax for the command in defining multiple groups. (I'm not in Ubuntu at the moment or I'd try it now.)

Thanks,

Glen

---

### Post by Mustard on 2006-03-27
[QUOTE=gpeck157]Mustard, 

Great question. I hadn't used the "usermod" command before, and now that everything is reinstalled and working fine, it might be interesting to do an experiment to find out. Do you already know the answer? What would be the syntax for the command in defining multiple groups. (I'm not in Ubuntu at the moment or I'd try it now.)

Thanks,

Glen[/QUOTE]

I'm away from my computer too atm. :)  I'm not sure of what the syntax was, but seeing as I had never seen it before, I just went off and had a read and was hopeful someone would clarify it for me too. :D

---

### Post by gpeck157 on 2006-03-29
[QUOTE=Mustard]I'm away from my computer too atm. :)  I'm not sure of what the syntax was, but seeing as I had never seen it before, I just went off and had a read and was hopeful someone would clarify it for me too. :D[/QUOTE]

Hey Mustard,

I used the command the other day when I was working with cups. When I "added" myself to a printadmin group, I hosed myself. I was no longer able to use sudo or use a whole host of other programs. I wound up reinstalling Breezy. I'm sure there was another solution to straighten this out, but I just didn't want to fool with it. Thanks for pointing this out! 

Glen

---

### Post by Mustard on 2006-03-30
[QUOTE=gpeck157]Hey Mustard,

I used the command the other day when I was working with cups. When I "added" myself to a printadmin group, I hosed myself. I was no longer able to use sudo or use a whole host of other programs. I wound up reinstalling Breezy. I'm sure there was another solution to straighten this out, but I just didn't want to fool with it. Thanks for pointing this out! 

Glen[/QUOTE]


I think the correct command to use is 'adduser', but it needs to be called with just two options, user and group.  For example

```
sudo adduser user group

#this should add an existing user to an existing group
```

I'm still a little fuzzy on this myself. :)

---

### Post by gpeck157 on 2006-03-30
[QUOTE=Mustard]I think the correct command to use is 'adduser', but it needs to be called with just two options, user and group.  For example

```
sudo adduser user group

#this should add an existing user to an existing group
```

I'm still a little fuzzy on this myself. :)[/QUOTE]

Me too. If I'm going to add myself to a new group, I'm going to use the graphical interface, at least until I know for sure. I think it's safer. I've wound up hosing myself more than once just using a simple command or two. 

Thanks again for the input.

Glen

---

