---
title: "[SOLVED] Can't enable sharing! What to do?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-03-02
I go to admin and click on shared folders. Says sharing services are not installed.

I have verified that samba is installed. I also checked NFS and it seems to be installed.

When I click on the install services button it does nothing. Just pops the error message back up again.

Is this a bug with Gutsy? Or what am I doing wrong?

---

### Post by wesleybailey on 2008-03-02
What error message does it pop up?

---

### Post by linuxjerk on 2008-03-02
This is the error popup:

Sharing services are not installed
You need to install at least either Samba or NFS in order to share your folders.
Install Unix networks support (NFS)
Install Windows networks support (SMB)
Close      Install Services


When I click install services the popup goes away for a second and re apears.

I am on the internet when I click button. The same internet I'm using right now to
post this.

Like I said above I have verified in the synaptic package manager that both of these
services are installed. Now I don't know if they are installed correctly or are active.
I don't know enough about this to check that. What is installed was installed during
ubuntu setup. I didn't try to install them later or something.
I'm clueless here. I had folder sharing over lan working on edgy.

---

### Post by wesleybailey on 2008-03-02
Here is how I checked the services are installed 
```
/etc/init.d/samba start
 * Starting Samba daemons  [ OK ]

```
```
/etc/init.d/nfs-common start
 * Starting NFS common utilities                                 [ OK ] 

```

If you don't receive OK message when you try to start the services, post the error.

---

### Post by paydaydaddy on 2008-03-02
Samba as it arrives default from the repositories is pretty mush useless. The following link is a good guide to getting samba up and working.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)

This is useful if you are sharing with a windows machine. If you are sharing with another linux machine I can't help you with that except to say that I know there is lots of info in the forum.

---

### Post by linuxjerk on 2008-03-02
Hey wesleybailey
When I do what you said....   /etc/init.d/samba start   I get no such directory
When I do.....    sudo /etc/init.d/samba start     I get command not found.

paydaydaddy

When I do this......  sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate


When I do this.....        sudo apt-get install  smbclient samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


This is saying samba is already there.  WTF???

---

### Post by linuxjerk on 2008-03-02
I'm using Gutsy. Is samba different in gutsy? Is this a bug? Because if samba is installed why can't I enable sharing?

---

### Post by linuxjerk on 2008-03-02
How do I find out the network name of the linux machine

---

### Post by linuxjerk on 2008-03-02
help

---

### Post by linuxjerk on 2008-03-02
Is this a bug with gutsy. Has no one seen this error before?

---

### Post by wesleybailey on 2008-03-02
When you try to enable sharing do you have synaptic package manager open?

Make sure (synaptic manager)/(Add/Remove Programs) is closed, before trying to turn on sharing,

---

### Post by linuxjerk on 2008-03-03
Yes the synaptic package manager and add/remove are closed when I try to enable sharing.

The only thing happening is the error. I push the install button and nothing. Just pops the error up again.

This must be a bug with gutsy.

Man this forum moves fast. There must be a lot of people with ubuntu problems!!!

---

### Post by linuxjerk on 2008-03-03
Seems like such a simple problem. Why does no one know anything about this?

---

### Post by linuxjerk on 2008-03-03
Is this a bug with Gutsy? Why does no one know about this???

---

### Post by linuxjerk on 2008-03-03
why can't I get any help on this?

---

### Post by Brian4 on 2008-03-03
I truly know what you mean about this forum moving so fast.  You post a question and 1 hour later, it's on page 5-20! ;)
I'm new to linux myself, but I have sharing via samba working with an XP installation.  In my case it happened almost right out of the box, thankfully.

Assuming you're wanting to connect to a windows share, like me:
I actually never touched the 'shared folders' under the administration tab, but I was able to get it working by opening Nautilus..  ie. go to places/home folder.. Under the 'file' menu, select 'connect to server'.  Under 'service type' select windows share.  In the 'user name' box, type your user account on the xp-machine.  When you click 'connect', you should be asked for the password of that xp-username-account.  Type in that password and it should connect.

The way I have shared any windows folders was actually by creating a separate user account in computer management (within windows) for the specific purpose of sharing folders - giving it a more secure password.  YOU HAVE TO BE SURE that you set any folder's properties that you want to share, to be able to be shared under that specific user account!  I have found though, that it'll even work if you supply the main account's(the one that you log on with) username and password, which I find to be a security risk - I'll have to work on that.. ;)

If this is what your wanting (to share a window's folder), then I hope this helps you in some way.  Linux can certainly be daunting for us new users.  I even bought a book on it! =)

---

### Post by linuxjerk on 2008-03-03
Thanks Brian4 for your post. I was beginning to think I was only talking to myself.

Yes that's exactly what I want to do except I'm using windows 2000.

It seems that gutsy is different than edgy which I was previously using.

But I still don't understand why I get the error when I try to enable shared folders???

I'm going to try what you suggested and I'll post the results.

thanks again

---

### Post by linuxjerk on 2008-03-03
Wow I think I have it working. I guess there always more than one way to skin a penguin :lolflag:

I have it working one way at least for now. From the windows machine to the linux machine.

Do you know what is the equivalent server name on the linux side? Is it your login name?
Have't quite figured that one out.

Thanks again for your helpful suggestions.

---

### Post by linuxjerk on 2008-03-04
SOLVED      SOLVED         SOLVED

Let this be a lesson to me!!!


go to:   system, administration, sofware sources      (check all the boxes)

When that's done loading you can install all restricted software.

Linux never ceases to test my patience!!!!!

---

