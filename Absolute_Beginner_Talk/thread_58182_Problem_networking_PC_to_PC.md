---
title: "Problem networking PC to PC"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by stig on 2005-08-19
As a newbie to Ubuntu/Linux (and not knowing much about software and computers in general) I am having problems getting my PCs networked together, and I would be grateful for help.[http://www.ubuntuforums.org/editpost.php?do=editpost&p=308902#](http://www.ubuntuforums.org/editpost.php?do=editpost&p=308902#)

I have two PCs using Windows 98SE and networked with cable, router and DHCP. This network has worked for a long time with no problems. I have now added a third PC which uses Ubuntu hoary and is linked to the other two by cable. Also, one of the Windows PCs now has a 2nd hard disk with Ubuntu hoary.

I can still pass files between the two Win PCs but have had no success linking Win to Ubuntu or Ubuntu to Ubuntu (regardless of searching Google, Ubuntu Forums etc). On the Ubuntu systems the eth01 is active when I do System > Admin > Networking.

I followed the Unofficial Ubuntu guide &#8220;How to install Samba Server for files/folders sharing service?&#8221; and did:

sudo apt-get install samba
sudo apt-get install smbfs

The next step, &#8220; How to add/edit/delete network users?&#8221; says to do:

sudo smbpasswd -a system_username
sudo gedit /etc/samba/smbusers

When I did the first line of this with my username (and enter my requested user password) then press return it asked me for &#8220;New Samba password&#8221;. Whatever I entered it returned a &#8220;Failed&#8221; - I tried my username, my password, the username of the other Ubuntu disk, new passwords etc, but all failed. I tried the second line from the Guide but got the same results.

After more searching on the Forum I found the following instructions:
*********
sudo apt-get install samba
sudo gedit /etc/samba/smb.conf

look for this (line 76): 
Code:

; security = user

change it for 
Code:

security = share
(notice that the ; is gone)

sudo /etc/init.d/samba restart
**********

I tried this but the sudo /etc/init.d/samba restart gave me:
* Stopping Samba Daemons....ok
* Starting Samba Daemons.....fail

I again tried sudo smbpasswd -a system_username but now get:
Can&#8217;t load /etc/samba/smb.conf - run testparm to debug it

I put testparm into a terminal and got:
Processing section &#8220;[homes&#8221;]
Processing section &#8220;[printers&#8221;]
Processing section &#8220;[prints$]
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse()
Error loading services.
[N.B. I didn't ask for the smilies!]

I went back to the file and changed it back to the original setting, i.e.
security = share
changed back to 
; security = user
but sudo smbpasswd -a system_username still gives me Can&#8217;t load /etc/samba/smb.conf - run testparm to debug it.

Unfortunately the testparm output means nothing to me.

I seem to be digging myself into an ever-deeper hole! Can anyone please help?
Thanks

---

### Post by glug101 on 2005-08-19
Well, I hate doing things this way, but since I do not have my Linux box handy (a sad time indeed!) I cannot give you very good advice.  The best I have is this link to the official Samba howto documentation.  I have found this information highly useful in the past.  If this looks like not the answer, respond and I'll answer later when I'm at home and have my Ubuntu box available. :)

Cheers!

[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2532665](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2532665)

---

### Post by stig on 2005-08-20
Thanks for the reply and the Samba link. Unfortunately, as a Linux newbie, I find the information on the Samba pages too complicated. Also, does Samba only deal with links between Ubuntu and Windows? Should I be able to link Ubuntu to Ubuntu without Samba? (that is my first objective - Ubuntu to Windows comes second.) 

I'm still not sure about all the usernames, passwords, domain names, workgroups etc and whether they have to be the same in Ubuntu and Windows. Also, when I see something refer to a Samba password, is that the same as my Ubuntu password? And do all these names have to be the same on a Windows PC if I want to be able to link Ubuntu to Windows?

If Samba is needed for all networking, not just Ubuntu to Windows, then I guess I urgently need to get the smb.conf file working again. I don't understand why I got the failed messages, even when I changed the file back to the original setting. I even reinstalled Samba in the hope it would create a new file, but no luck.

---

### Post by glug101 on 2005-08-21
Samba is not necessary for sharing volumes between linux boxes.  I think that the actual official linux/unix file sharing protocal is nfs.  However, nfs has it's difficulties and while the one time that I setup nfs shares the result was pretty sweet, if you have anything other than a linux/unix box on your network, I would use samba. (and I would use a reliable grammer checker if your sentences are as long as mine :) )  Both OSX and Windoze can connect pretty easily to a samba share on a Linux box.  In fact, my experience has been that such a connection works better than a windows to windows connection. 

    As far as the passwd's go, the samba passwd can be setup to be separate from your Ubuntu passwd, or it can be setup to synchronize.  I prefer to have them sync because otherwise there are two passwds to keep track of.  (I'll look up the details on setting those up for my next post ;) )

    As for the testparm data... i'm not really experienced at using testparm, but it sounds like it's finding a command 'params.c' that doesn't make any sense.  First thing I would do is search through your smb.conf file for any lines that contain 'params.c' in it and comment them out by putting a '#' in front of them.  Then do the 'sudo /etc/init.d/samba restart' again and see if it at least loads correctly.  Pop up here and let me know the results,. :)

Good luck, and may the force be with you...

---

### Post by glug101 on 2005-08-22
Ok, I thought of one more thing while I was falling asleep last night....

You mentioned that you did a reinstall of the program but you are still getting the error while trying to start samba.  I am very much convinced that this is a result of your setup files being pooched. (yep, technical term :) )  I do not believe that a simple reinstall removes the configuration files.  Do a *complete* uninstall in synaptic (right click on samba and choose the complete uninstal) and then install it again.  This should at least get you to square one with a smb.conf that doesn't error out.

Hope this helps :)

---

### Post by stig on 2005-08-25
Thanks glug for your two further helpful replies and I apologize for not responding to them until now - due partly to absence from the computer, then not being able to access the Ubuntu forums for some time (perhaps the site was down?).

Your first reply triggered an idea and now I have got the smb.conf file working again (thanks!). I looked for &#8220;params.c&#8221; in the file but could not find it. But two lines in the testparm result had &#8220;()&#8221; and I noticed empty brackets near the end of my smb.conf file. I had earlier made a folder called Shared in my user directory and within that a folder called Documents. Through the GUI, I set both of them to be shared with my other computer.

But next time I looked, only the Documents folder was set to share - the folder named &#8220;Shared&#8221; had reverted to being not shared (and did so again when I set it back to shared). This seemed to be reflected by the two final entries in smb.conf - one started with [ ] followed by something like user1/Shared and the second was [user2] followed by user1/Shared/Documents.

Reasoning that I only really needed the &#8220;Shared&#8221; folder to be shared (the Documents folder within it should presumably then be shared too), I deleted the second entry and placed &#8220;user2" between the brackets of the first entry. When I did testparm on this edited file, it was OK (this time I remembered to make a backup too!).

However, I still could not access the network so since then I have been trying to set up NFS, following the LinuxHOWTO. This has meant that in Admin > Shared Folders > Properties > Share Folder I have since changed /home/user/Shared to NFS instead of Samba. I note that in the smb.conf file the entry described above has now disappeared - is it not possible to have a computer set up for both NFS and Samba at the same time?

On balance, I would prefer to use Samba because I also have a Windows 98 PC linked to the network. So I would be happy to drop the NFS settings and go for Samba again - with a little help from my (Ubuntu) friends!

Your last comment suggests a complete uninstall of Samba in Synaptic. I did consider this when I was still having the smb.conf problem. But when I went to Synaptic and marked Samba for complete uninstall it brought up a box saying what other things would have to be uninstalled - and it included &#8220;ubuntu-desktop&#8221;. This frightened me off!

Because I still could not sort out Samba and I had not (at the time) seen your replies, I posted several questions in one message on the Ubuntu 5.04 Desktop forum:
[http://ubuntuforums.org/showthread.php?t=59557](http://ubuntuforums.org/showthread.php?t=59557)
and have had two replies. It was to get some explanations of the meaning of various terms. I think a lack of understanding these terms has been holding me back with Samba.

Thanks for you help - now I will have a go at Samba again.

---

### Post by glug101 on 2005-08-25
Wow, that's a lot of typing!  Glad to here that you are making (some) headway.  Properly configured samba on a linux box is a beautiful thing when you have multiple boxes.  Sorry I don't have a lot more substance, but I did want to tell you that I do believe that you can share something via samba and nfs at the same time.  The computer shouldn't care.  I would wager that if your samba was disabled when you turned on nfs then this is a quirk of the Ubuntu setup programs. (you might have seen a few of those already;) )  Hang in there, keep your head up and I'll give you some better advise when I can.  Right now I'm a little busy making sure that I have a place to live next month (my lease runs out at the end of September)

Cheers!

---

### Post by stig on 2005-08-25
Thanks for all your help - I will make an attempt at Samba and you might see me again in the Forum. Hope you get somewhere good to live! :smile:

---

### Post by davmac on 2005-08-25
I don't know if it'll be of any use to you, but in getting samba set up myself, the real breakthrough came when I googled for "sample smb.conf" ([http://www.google.co.uk/search?hl=en&q=sample+smb.conf&meta=)](http://www.google.co.uk/search?hl=en&q=sample+smb.conf&meta=)). It throws up loads of different examples of working samba configurations. Working through each of these gave me a better insight into what I was doing wrong, as well as giving me a decent working starting point.

HTH,

Dave Mac

---

### Post by stig on 2005-08-26
Dave, thanks, it's all useful and I will have a good look at these. I find some of the most basic things on Linux/Ubuntu are the most difficult to get answers to. :-| 

For instance, to network two PCs on Linux/Samba each with its own user, do both users have to be named as users on both PCs? i.e. if user laurel has PC L and user hardy has PC H, does L have to have two users (listed through Admin > Users) and H have the same two? Does there have to be two Home directories on each PC, one for each user?

---

