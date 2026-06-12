---
title: "Xbox Media Center - SMB Share how?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by monomaniacpat on 2007-02-08
Alright - I confess: I don't get it!

I've used samba before to share printers with a windows computer and I remember it took me days to finally get it working. Even this work was lost, however, as I have had to reformat since then.

So how do I go about getting XBMC to find my SMB shares/video files? I have followed [these]("http://ubuntuguide.org/wiki/Dapper#Samba_Server") instructions with no luck. I found a couple of other threads on the issue, but I couldn't make any progress. FYI: I changed "network username" to my actual username, if that makes any difference.) 

If you could not only tell me how to set up ubuntu, but also what options I need to check in XBMC that would be great.

Thanks in advance,

mono.

P.S. I've never managed to get SWAT to work.

---

### Post by monomaniacpat on 2007-02-08
I finally set up samba (allegedly) using [this]("http://ubuntuforums.org/showthread.php?t=202605") guide but it's made no difference to the Xbox. I click on SBM files under videos and it says 'nope' (or words to that effect). I've entered the user details there, of course (though I'm not entirely sure they're correct).

I loaded up a windows computer to see if the share was visible and although I can't connect to it, it did come up as Samba Server (hostname). I fiddled for a couple of hours, but no progress.

Please help :'(

---

### Post by barney_1 on 2007-02-13
Hi there, sorry to hear you're having issues with your samba shares to XBMC.  You are indeed using the guide that i would use, so let's go over everything one by one and see if it will work for you.

1. Make sure you have an xbox smbuser.
```
sudo smbpasswd -a xbox    #my username and password will both be "xbox"
```
2. Now edit your /etc/samba/smb.conf file:
```
sudo nano /etc/samba/smb.conf
```
Under "Authentication" make sure this line doesn't have a semicolon ( ; ) in it:
```
security = user
```
At the bottom of the file add this:
```
[DvdImage]
    comment = DvdImage
    path = /Lenny/DvdImage
    public = no
    writable = no
    create mask = 0777
    directory mask = 0777
    force user = nobody
    force group = nogroup

available = yes
browsable = yes

```

Let me explain:  DVDImages will be will be the name of the samba share.  The local path that will be available in the samba share will be /Lenny/DvdImage so change this as necessary.  You want to make sure that you have "available = yes" or you will not be able to access this share.

CTRL-X and choose to save the file.  Restart samba using this command:
```
sudo /etc/init.d/samba restart
```

3. Now test out what you just set up.  Press alt-F2 and type:
```
smb://localhost/
```
A window should come up and you should see your samba share folders in it.  When you double click on DvdImage it should ask for your password.  Enter Xbox (or whatever you setup the username and password to be) and it should show your files.  If not, you don't have you samba set up correctly.

4. On to the Xbox end of things. (I'm using Version 2.0.1 stable of XBMC)

***You need to know either the static IP or hostname of the computer you just setup samba on***

-Start up XBMC, go to Settings-->Network-->SMB Client
-Enter the username and password you setup on your linux box as the Default Username and Default Password (I used 'xbox' for both)
-Press the back button until you are again at the main menu screen-- choose "My Videos"
-On the remote control press "title" (white on a controller) and choose "add source" from the menu that pops up.
-You will be prompted to "Enter paths", click on <none> and fill in your path.  Here is my example, you need to change the ip address to fit yours.
```
smb://192.168.1.100/
```
-Choose "done" go to the next field and enter a name for this source (this will be the displayed name in My Videos)
-Select OK
-You should now see a selection in the My Videos screen with the name you just chose, click on it, if all went well you should see the files in your samba share.

---

### Post by Chemist on 2007-02-13
i've been trying to work this out for ages mate, I'll give this a try in teh next few days

---

### Post by thomas_nyquil on 2007-02-21
Hey barney_1 I registered to thank you for this post. I've had my fair share of headaches lately trying to switch from xp to ubuntu. This is the first time I've found all the info for a particular task in one place. Thanks!


Now I just have to figure out how to organize my mp3s so that xbmc doesn't take 5 minutes indexing them every time.

---

