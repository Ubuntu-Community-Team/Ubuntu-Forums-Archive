---
title: "Newbie Home Network Advice Needed"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Tracker|1 on 2008-03-04
Here is my set-up:  I have three XP-Pro, one Win98, one Vista Home Premium and I've also just set up a machine with Ubuntu 7.10 Desktop.   They all access the Internet through a  residential DSL gateway.     None are set up through anytype of home networking other than being connected to the common gateway. 

All I would like to do is make the Ubuntu machine esentially a network file sharing archive.  In other words I would like all the computers in the network to be able to see and access the Ubuntu machine shared folders, but not necessarily each other.

Please keep in mind while I have some knowledge from the hardware side I am a complete and absolute Newbie to networking and Ubuntu.

Any advice and or direction to knowledge sources would be greatly appreciated.

Thanks Much!!  :)

---

### Post by {BzF}~JOKesTER on 2008-03-04
In The Tray Goto: System>>Preferences>>Control Center>>Shared Folders. 
When It Asks To -Install The Needed Packages-Let It Download File Sharing For Windows.
Click Plus To Add Shared Folders. And Thats It!

Note {In The Second Tab Called "General Properties" You Must Assign The Proper Workgroup Name}

Hope This Helps

---

### Post by Tracker|1 on 2008-03-04
That was the easy part.  :biggrin:  So, at least I know I did something right.  I've also added a few shared folders and set up the appropriate workgroup through one of the XP-Pro machines as an experiment.

Unfortunately when I try to locate the Ubuntu computer in the workgroup on the XP-Pro machine I get an error telling me that I do not have access to that server and I need to contact the adminisrator (that's me :lol: ) 

If I try to access the shared folders through the DSL gateway's interface I'm asked for a username and password.  Entering the username and password I use for the Ubuntu PC does not give me access.  (it's not the admin password for the gateway either.)


Any ideas?

---

### Post by dstew on 2008-03-04
You may need to set up user accounts on your Ubuntu server. That is one thing the graphical user interface does not do your you.

Set up an account for each user on your Ubuntu machine first. Use the Users and Groups tool in System --> Administration. They can just be ordinary Desktop users.

Then, open the terminal and from the command line do:```
sudo smbpasswd <user name>
```. Just use the same password that the users have in their regular Ubuntu account. That should take care of it. Oh, restart samba before you try to log in to the server:```
sudo /etc/init.d samba restart
```

---

### Post by Tracker|1 on 2008-03-04
OK, I'm *not *following you. 

If I already have a user account running and I just want to see the shared folders in the Ubuntu PC on that account, how will setting up other user accounts grant me access to seeing the shared folders on the account I can't access now?   (Man, I hope that made sense :) )

---

### Post by la3875 on 2008-03-04
I have been successful doing exactly what you are asking. what you have to make sure of is that samba is installed then search the forums or the samba site ([www.samba.org](www.samba.org)) for how to edit your samba.conf file so that everyone can see and access the the shares you create. I dont have the details at hand. will check in again later.

good luck!

---

### Post by dstew on 2008-03-04
You do not need to set up a new Ubuntu account for yourself, only create a user in Samba with smbpasswd. I mentioned setting up Ubuntu accounts in case you want to give others access to the shared drive.

---

### Post by Tracker|1 on 2008-03-04
Investigating further I found **System/Administration/Users and Groups**, which allows the addition of users and apparently the managing of groups.  I'll be investigating this more, but thought I'd mention that there does appear to be a way to add users through the GUI at least in 7.10.


In case anyone else has more suggestions below is my original question:

[INDENT]"Here is my set-up: I have three XP-Pro, one Win98, one Vista Home Premium and I've also just set up a machine with Ubuntu 7.10 Desktop. They all access the Internet through a residential DSL gateway. None are set up through anytype of home networking other than being connected to the common gateway. 

All I would like to do is make the Ubuntu machine esentially a network file sharing archive. In other words I would like all the computers in the network to be able to see and access the Ubuntu machine shared folders, but not necessarily each other.

Please keep in mind while I have some knowledge from the hardware side I am a complete and absolute Newbie to networking and Ubuntu.

Any advice and or direction to knowledge sources would be greatly appreciated.

Thanks Much!! "[/INDENT]

---

### Post by dstew on 2008-03-04
> there does appear to be a way to add users through the GUIYes, but they are not Samba users until you do smbpasswd

---

### Post by Tracker|1 on 2008-03-04
> **dstew said:**
> Yes, but they are not Samba users until you do smbpasswd

OK, see now the lights are starting to come on slowly....Llike I said in my original post I am an absolute newbie to Umbutu, I guess I should have also added and everything related to it :lol:.  

So, I'm guessing that "Samba" is what handles network sharing?  In other words what would be usually handled as a service in Windows and manipulated through the interface has to edited through what you are calling a "Terminal"?

---

### Post by knitmom on 2008-03-04
wow, I'm dealing with the same stuff!  I'm hoping to get the network printer to work once I get this setup.  Since adding the server smbpasswd, I can see my files from the windows computer that are on my ubuntu machines.  

Now, how can I get my ubuntu machines to print to the network printer located thru mshome?  This worked with no problem when I had 7.04, but since upgrading to 7.10 I haven't been able to print.  I've given my ubuntu machines static IP addresses, but I can't get in to mshome.  It says I don't have authorization or whatever.

Thanks!
Knitmom

---

### Post by dstew on 2008-03-04
> So, I'm guessing that "Samba" is what handles network sharing? In other words what would be usually handled as a service in Windows and manipulated through the interface has to edited through what you are calling a "Terminal"?Yes, that is correct. The Graphical User Interface (GUI) for Ubuntu is incomplete in this area, at least throught 7.04 Feisty. I don't have Gutsy, so I can't say for sure. Maybe in Hardy Heron file sharing with users will have complete GUI support.

Samba is the program suite that Ubuntu uses to share and connect with Windows networks. When you create shares using the Share Folders GUI, new entries are added to the smb.conf file that Samba uses. So the GUI and Samba talk to each other, but not completely.

To enter commands, open the Terminal application. Lots of Ubuntu configuration is done with the command line.

---

### Post by knitmom on 2008-03-04
Question, can you have two samba servers w/ different names listed in the mshome (or whatever workgroup)?  I'm on the windows machine and can only see one at a time.  Earlier I could see both, but I can't remember if I've done something different to one of the machines or not.  Been working on two different issues with different OS today on different computers!

Thanks

PS:  You mentioned samba and networking.  When I used 7.04 I needed samba to get cups to print.  I'm still working on that!  I'm now up to 7.10

---

### Post by la3875 on 2008-03-04
Knitmom, are you trying to use one or both of your Ubuntu machines as a print server or just trying to get them to print over your network?

---

### Post by Tracker|1 on 2008-03-04
> **dstew said:**
> Yes, that is correct. The Graphical User Interface (GUI) for Ubuntu is incomplete in this area, at least throught 7.04 Feisty. I don't have Gutsy, so I can't say for sure. Maybe in Hardy Heron file sharing with users will have complete GUI support.

Samba is the program suite that Ubuntu uses to share and connect with Windows networks. When you create shares using the Share Folders GUI, new entries are added to the smb.conf file that Samba uses. So the GUI and Samba talk to each other, but not completely.

To enter commands, open the Terminal application. Lots of Ubuntu configuration is done with the command line.


OK, thanks.  I'll jump into it and give it a try.   I'm sure I'll have more questions.  Thanks for your patience!


**Edit:  Worked like a charm!    Thanks again!!!!**

---

### Post by knitmom on 2008-03-04
> **la3875 said:**
> Knitmom, are you trying to use one or both of your Ubuntu machines as a print server or just trying to get them to print over your network?

I'm using windows as the print server.  I used to be able to print through that when I had 7.04.  I now can't print since upgrading to 7.10.  Today is the first day I've been able to access the ubuntu computers through windows and get some of my files.  (I set up the samba passwords)  It doesn't work the other direction  ubuntu to windows computers.

I just originally thought it was  networking problem.  Now that I can access it one way, I'm hoping to fix it the other direction and get the printer to work.  I guess I need to do something on the windows end, and then maybe the cups printer to my windows printer will work.

Thanks,
Knitmom

---

### Post by knitmom on 2008-03-04
Hey,
I had a chance to do some searches and I think this might help, check it out:  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)  I haven't tried it all the way thru, but will give it a go tomorrow.
knitmom

---

### Post by paydaydaddy on 2008-03-05
The best how-to on setting up samba that I have seen.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)

---

