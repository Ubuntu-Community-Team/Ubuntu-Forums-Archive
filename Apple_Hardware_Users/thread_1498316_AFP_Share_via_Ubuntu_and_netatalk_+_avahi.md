---
title: "AFP Share via Ubuntu and netatalk + avahi"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by jarrod.payne5 on 2010-05-31
First, I would like to say that I am completely new to Linux and fairly new to Mac OS X as I have been a Microsoft 'fanboy' in the past (not anymore).

I have setup an Ubuntu Server with the netatalk package installed. Using avahi package, I have successfully connected to the server on my Mac OS X machine. Now, that the server station has been rebooted and I am trying to reconnect to the Ubuntu machine via the Mac OS X machine in the Finder the system is notifying me that the password has expired. What is going on here? I have used the chage command in linux to ensure that my passwords are to never reset, but this is not fixing the problem. Could I get some help on this.

---

### Post by sha.goyjo on 2010-06-01
Could you give us some more information, such as:

Make of both systems,
OS in use on the server.

Any other pertinent information.

---

### Post by jarrod.payne5 on 2010-06-01
OS on the server computer is Ubuntu 8.0.4.4 desktop version. 
OS on the workstation computer is Mac OS X Snow Leopard. 

I used a combination of these tutorials when creating the AFP and SMB shares. 

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

[http://www.lowtek.ca/roo/2009/ubuntu-with-apples-time-machine/](http://www.lowtek.ca/roo/2009/ubuntu-with-apples-time-machine/)

[http://blog.delacelle.com/post/2009/01/19/tuto-comment-creer-votre-serveur-timecapsule-sous-debian-ou-ubuntu/](http://blog.delacelle.com/post/2009/01/19/tuto-comment-creer-votre-serveur-timecapsule-sous-debian-ou-ubuntu/)

[http://www.cognitivecombine.com/2009/12/diy-ubuntu-nas-with-afp-smb-dlna-and-itunes/](http://www.cognitivecombine.com/2009/12/diy-ubuntu-nas-with-afp-smb-dlna-and-itunes/)


When the AFP share worked I was using the same login credentials as my ubuntu username and password. Now, using those credentials, I am notified that my password has expired. I am not sure if this is a problem with the Ubuntu system or the Mac system though. Let me know if you need to know anything else.

---

### Post by jarrod.payne5 on 2010-06-01
More specifically (if this helps), I did use this section from [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")

Now we have to tell the afpd daemon what Volumes to share. This is defined in the AppleVolumes.default file inside /etc/netatalk/. The following line will open this file in the gedit editor with superuser privileges (required for saving) where we can define our shared volumes:

    sudo gedit /etc/netatalk/AppleVolumes.default

Scroll to the bottom of the document and define your Volume shares. By adding the following line you will share each users home directory with the user name as the Volume name. To make things more secure you can define all users who are allowed to connect to your Ubuntu box via AFP:

      ~/ "$u" allow:username1,username2 cnidscheme:cdb

I erased username2 and replace username1 with my ubuntu username.

---

### Post by jarrod.payne5 on 2010-06-01
More info...

After uninstalling avahi-daemon and netatalk and reinstalling using this link [http://www.lowtek.ca/roo/2009/ubuntu-with-apples-time-machine/](http://www.lowtek.ca/roo/2009/ubuntu-with-apples-time-machine/)
My AFP share now works correctly again (for the time being).
Could anyone shed some light on why this would happen?

---

### Post by sha.goyjo on 2010-06-02
> **jarrod.payne5 said:**
> More info...
Could anyone shed some light on why this would happen?

Do not question the magical Apple smoke, unless it fails to work!:P

---

### Post by jarrod.payne5 on 2010-06-02
Well it's now a new day, and it is failing to work again...My mt-daapd (Firefly) server is working properly with Itunes, but my AFP share accessed via the Mac OS X finder is now saying "You have entered an invalid username or password" even though I am surely using the same credentials as when it was working after a reinstall of netatalk and avahi-daemon. What gives here? Anyone have any suggestions?

---

### Post by jarrod.payne5 on 2010-06-04
Now, even on my Ubuntu machine, I cannot login to the system at all using my username and password that have been set up! I never set up a root password, what is the default?

Solved this issue. It seems that when I was executing chage, I was entering the the wrong information when I was asked about the account expiration.

Although all is well for now, I am sure I will be back to the thread later to discuss further what will go wrong in the future. Hopefully I wake up tomorrow with access to my AFP share still!

---

### Post by sha.goyjo on 2010-06-04
Could you please put in an example of what you did to fix the problem so that future searchers will find it? If you've solved the problem it is usually a good idea to note how.

---

### Post by jarrod.payne5 on 2010-06-07
I do plan to place the solution here once I find out how to make the solution work for good.

---

### Post by jarrod.payne5 on 2010-06-07
For now though, it seems as if it may be fixed, but all I did was uninstall avahi-daemon and netatalk, then reinstall using [http://www.lowtek.ca/roo/2009/ubuntu-with-apples-time-machine/](http://www.lowtek.ca/roo/2009/ubuntu-with-apples-time-machine/) 
If I run into anymore problems I will be sure to come back here with a better solution, but, for now, reinstalling seems to have done the trick! 

The actual solution I mentioned a couple of posts ago involved actually logging into my Ubuntu system via the Ubuntu login screen, not what the original post involved which was an issue logging into the Ubuntu system via the Mac OS X finder window.

---

### Post by atca on 2011-08-02
This is my updated guide based on the Kremakicious link which deals with issues I faced following that guide:

[http://confoundedtech.blogspot.com/2011/07/draft-draft-ubuntu-as-apple-time.html](http://confoundedtech.blogspot.com/2011/07/draft-draft-ubuntu-as-apple-time.html)

---

