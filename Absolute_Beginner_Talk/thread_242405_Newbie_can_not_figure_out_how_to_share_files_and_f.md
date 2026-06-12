---
title: "Newbie can not figure out how to share files and folders."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by tmtjjhnsn on 2006-08-23
I have been searching for over a day for a guide to networking between two Dapper machines and a Windows XP machine.  The two Dapper machines are wired to a Netgear router, while the XP machine is connected wirelessly to that same router/WAP.   The three machines share the same broadband internet connection. I can not figure out how to share files between the two Dapper machines, much less the XP machine.  I would be so grateful for any help.  I am relatively new to Linux, as you can tell.

---

### Post by BatteryCell on 2006-08-23
One way to do this is to set up a samba server (so that you can share between the Dappers and the XP)
Theres a good guide to this here:
[http://www.ubuntuforums.org/showthread.php?t=202605&page=14&highlight=howto+samba](http://www.ubuntuforums.org/showthread.php?t=202605&page=14&highlight=howto+samba)
Just make one of the Dapper machines the server.

---

### Post by ciscosurfer on 2006-08-23
While Samba is great if you've got the time to configure it, another option that doesn't require any configuration (at least, it didn't for me), is to see if Ubuntu automatically recognizes the other machines on your network.  I have one Ubuntu machine and one XP machine both connected to my router.  When I go to Places > Network Servers and then click on Windows Network, I am presented with the name of my XP machine as an icon.  I can then click on this icon and can see all the files on my XP machine (if you're machine is connected wirelessly, you need to make sure that all of your setting allow connections from other machines on your network.  I would then advise you to check out the wireless networking posts on UbuntuForums for additional assistance).  I can then read these files and/or copy them over to my Ubuntu machine quite easily if I want to edit/work on them.  This may not work for you, but then again, it just might! :D

---

### Post by benfindlay on 2006-08-23
I'd say its definitely worth installing the samba server. Its a bit of a pig to get going at first but once its up and running you won't have to tweak it again.

First of all I just used synaptic to install samba

Then I typed:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

Itll ask you for a password to use with your username. Once these 2 lines have been typed, your specific user account will be enabled with the samba server. You can use this account to log into ur linux shares from windows (once you've set some up!).


Once it's on, you then need to choose which folders you want to share on your linux computer (I have a folder called shared on my desktop

Go to System > Admin > Shared folders and add whatever folder you have chosen.
Share the file with "SMB" i named it the same as the folder name and gave it an identical comment (don't think those 2 matter much). I also ticked the box to "Allow browsing folder"

Then in General Windows sharing settings i just called the computer the name i gave it in boot up and chose to share it on my "HOME" workgroup. As for WINS I set it not to use WINS.

Then just click ok and it should be good to go!

---

### Post by Aggienator on 2006-08-23
A Couple of links I found useful:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.ubuntuforums.org/showthread.php?t=211628](http://www.ubuntuforums.org/showthread.php?t=211628)

---

### Post by tmtjjhnsn on 2006-08-23
> **benfindlay said:**
> I'd say its definitely worth installing the samba server. Its a bit of a pig to get going at first but once its up and running you won't have to tweak it again.

First of all I just used synaptic to install samba

Then I typed:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

Itll ask you for a password to use with your username. Once these 2 lines have been typed, your specific user account will be enabled with the samba server. You can use this account to log into ur linux shares from windows (once you've set some up!).


Once it's on, you then need to choose which folders you want to share on your linux computer (I have a folder called shared on my desktop

Go to System > Admin > Shared folders and add whatever folder you have chosen.
Share the file with "SMB" i named it the same as the folder name and gave it an identical comment (don't think those 2 matter much). I also ticked the box to "Allow browsing folder"

Then in General Windows sharing settings i just called the computer the name i gave it in boot up and chose to share it on my "HOME" workgroup. As for WINS I set it not to use WINS.

Then just click ok and it should be good to go!


Thank you, very much.  I did just what you said, but when I click on Network Servers, the box where my other machines should be listed is empty.  In the pane to the left of the empty box, is listed mshome.  When I click on mshome, I receive a message that the contents of mshome can not be displayed.  I can not even see my other Dapper machine.  The very same thing occurs when I click on Network Servers on either Dapper machine.  I have an entire day invested in this, with no success.  Thanks to those who have tried to help.

---

