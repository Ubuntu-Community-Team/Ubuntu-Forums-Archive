---
title: "[SOLVED] Help - Can no longer log in"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Ylona on 2007-11-13
Ok. I have some really basic experience with Linux and someone just installed Ubuntu for me.

But now I changed my name as user and also the name of the homedirectory in the top right botton menu. At restarting however I can use my new user name, but than it states it can not find my home directory and stuff. What it exactly stated I can not read because the letters are too large and outside my screen (and trying to come there does notwork). I however tried all options and none allows me to get in. I just go back to the login window again.

When I go in in recovery mode as root I can see that the old homedirectory name still exists.

As a XXX option I tried to make a new user account in this recovery mode using  useradd testtest with different options ( -p -d -r ) on, but I can see no change and can not log in with this new username.

Does anybody have some tips or information for me? Becuase I do noy know what to do anymore, except for re'install.

thank you very much for your help!!!!

Ylona

---

### Post by ruibernardo on 2007-11-13
> **Ylona said:**
> But now I changed my name as user and also the name of the homedirectory in the top right botton menu.
Can you explain exactly how did you change your username?

---

### Post by Znort_Ubern00b on 2007-11-13
I had a similar problem, it was due to the permissions on the folder being incorrect. think you need to change ownership in terminal. Am only new to this myself so cant remember what you need to write. think its something like

sudo chown *new username* /home/*username(old)*

hope thats right, anyone else know?

---

### Post by ruibernardo on 2007-11-13
If that is the problem, it should be:
```
sudo chown -R new_username /home/renamed_home
```That will change the owner of files and directories inside the renamed home directory.

That would resolve the login problem, but you might find yourself out of sudoers (can't do "sudo commands"). If that happen, reboot in rescue mode and add the new user to the "adm" group.

---

### Post by Ylona on 2007-11-13
Thanks for you help!!! The problem was that at first I could not log in, but now I made a new user in the reboot mode that can log in. 

Now I however about 10 user that I all tried. How can I delete these? Therefore I first have to put my working account in the admin group. How do I to this?? 

And is there a way than to reset my old account to the old name and home directory, so that maybe it will start working again? Maybe using that chown command (I could however not read the code above...).

---

### Post by Ylona on 2007-11-13
Ok. I am a bit further now.

I have added my new testuser account to the primairy group admin and secondary group adm as I can see in the file /etc/group.

I also see in this file something more about what the problem was. In several groups, e.g. adm and admin. the user ylona now stands, while the original account is still called vandinther I think. This I interpreted from the text below again in the file /etc/group .

..
adm:x:4:ylona,testuser
..
admin:x:110:ylona,testuser
..
vandinther:x:1000:
ylonatests:x:100X:  (all the attempted to make user account) 
testuser:x:1007:

So there is never a ylona as first entry in this file.

Now how do I reset the names ylona above again in vandinther (as it was originally)??

As in the last post: the name of my homedirectory remained /home/vandinther, while the username is ylona.

I hope somebpdy still understands this and can help me..

---

### Post by Ylona on 2007-11-13
Woops. All my : x changed into angry smiles.

---

### Post by Znort_Ubern00b on 2007-11-13
So you wish to change the name ylona to vandinther? and then reconnect the \home\vandinther directory...is that correct?

---

### Post by Ylona on 2007-11-13
I hope this will undo all my changes and will allow me to get into my original account vandinther again yes. But I do not know if I manage to do that by only changing this name. But I can try that.

---

### Post by SpiritIsReality on 2007-11-13
howdy
on startup if you hit excape key to get grub menu and choose the recovery mode, your the administrator. every command you type will ! be done. The head honcho, king whatever his
name was. type start x and hit the enter key.. let me know if it starts.
those smiles and faces are part of, when you are going to post, on the faces listed on the sidebar, click more , and it shows you how to type keys to make faces.
If, when on the post reply page, you scroll down th3e page you'll see a check box saying disable faces. that's your box you want.
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)
trails

---

### Post by Znort_Ubern00b on 2007-11-13
I take it the ylona account is an admin account.
If so log in and the go to
System - admin - users and groups
reset the password for vandinther and add the account to the admin group

then open a terminal and type

sudo chown -R vandinther /home/vandinther

you should then be able to log in as vandinther with admin rights.

---

### Post by Ylona on 2007-11-13
I do not understand. Where do I need to type start x?????

---

### Post by ruibernardo on 2007-11-13
Do it as Znort_Ubern00b is saying. Forget about "startx", it doesn't work in Ubuntu.

---

### Post by Ylona on 2007-11-13
Well I managed to get into my old account vandinther again thanks t you guys!!! Thank you very much.

Than I have one last question. The top bar (even the one of the menu options) and the inlog tab at the inlgowindow and all text displaying if you are not yet logged in and somehting goes wrong have a really large sizes are are sometimes also located wrong. This means I can not read crucial information if somethings goes wrong within the inlogwindow and it is irritating to see 1-5 of your screen filled in with a useless bar for each window if you are logged in.

Do you know where I can change this??

Thank you very much in advance!!

Ylona

---

### Post by Znort_Ubern00b on 2007-11-13
Go to:

System - preferences - screen resolution

what is that set at? may need to change resolution

---

### Post by Ylona on 2007-11-13
Resolution: 1280*800
Refresh rate: 60 Hz
Rotation: Normal

---

### Post by Ylona on 2007-11-13
The resolution for the rest of the screen is absolutely fine. Only for the situations mentioned above it is abnormally large. So that is probably not it. Right??

---

### Post by Znort_Ubern00b on 2007-11-13
Unfortunately on that one i am lost. Check the link below for solution.

[Large Login window problem]("http://ubuntuforums.org/showthread.php?t=583915&highlight=login+window+huge")
Regards

---

### Post by Ylona on 2007-11-13
Thanks again!!!

---

### Post by Znort_Ubern00b on 2007-11-13
No problem, glad i could help...don't forget to mark this thread solved.

---

