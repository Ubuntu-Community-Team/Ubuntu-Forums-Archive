---
title: "[help] The Beginner's Panic Attack"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by pcsrao on 2008-03-20
New To Ubuntu. New To This Forum.

But loved both... the interface, the usability, the configurability... my!! Am surprised Windows exists still!!

Well, I searched some parts of this forum, but I still haven't got a definitive answer to my queries:
So here I shoot:

1. **No Internet Connection In Ubuntu**
I've got Windows XP where the connection works extremely fine(and that's where I am posting from, btw)

2. **Security Issue**
And because I couldn't connect to the internet during the installation of Ubuntu, I was unable to do security checks and updates.

Also,

3. **Where Is My Ubuntu?**
I used the "Guided installation - use the maximum continuous free space" type of installation to install ubuntu. My E: and G: drives were completely vacant. After installation, I thought Ubuntu would get there. (I had problems with installing the whole thing manually.. some error came up, screaming "No root file specified"). E: and G: and still empty, my 40GB hard-disk with FOUR drives is still just like that... absolutely no sign of Ubuntu anywhere, BUT still I am able to get to ubuntu during start up!! Get this clear, please... I am able to use Ubuntu (Oh, and it's such a lovely thing), but where's Ubuntu actually in my HD ???

I will surely do a coup dè grace (or whatever) if you solve my problem..

Thanks a million, guys!

---

### Post by Emerzen on 2008-03-20
Hi - forum members will need some more info before being able to help you:
  Please your computer specs?  (Desktop/laptop, what's inside, etc?)
  When you ran Ubuntu from the LiveCD, did you have an internet connection?  Wired vs. wireless?

Regarding the security, w/o internet connection there's not much to worry about except local security.

Regarding where is Ubuntu.  If Windows had drive partitions E: G: NTFS formatted, when you installed Ubuntu this was not considered "free space."  So, Ubuntu won't touch those unless you delete those partitions 1st.  Probably, it installed on some minor fraction of your drive.  Windows will not list Ubuntu drives by default.  Right click your "My Computer" icon and select "manage."  Then click on the drives menu.  A layout of your entire drive should show up.  The one that windows doesn't recognize is probably Ubuntu.

---

### Post by ohzopants on 2008-03-20
1) I don't think anyone will be able to troubleshoot your internet problem without more details: wired vs wireless, router vs direct connection, cable vs dsl vs dialup?

2) Fixing 1 should fix 2

3) Your ubuntu is installed onto it's own partition, just like your e: and g: drives are partitions of the same physical drive.  Ubuntu uses a different file system than windows, so windows doesn't know what it is.  Did drives e: or g: shrink?

A good way to find it would be to do Start -> Run -> compmgmt.msc

Then go to disk management, if there any parts of a disk that windows doesn't seem to recognize, that's probably your ubuntu partition.

---

### Post by pcsrao on 2008-03-22
Thanks a lot guys.
Now, these are the things:

1. I've got a WIRED ADSL connection.
2. No Network.. Individual PC with XP running... 
3. I'm fine with the partition stuff after I had a look at the Disk Management! Thanks to you.

---

### Post by Mustard on 2008-03-22
Are you using a router?  I assume you are using a pppoe connection.  If you have a router you could set up the router to do the connecting for you usually.  Here is a link that goes over the basics and has links to your specific connection method.

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by oedha on 2008-03-22
1. system - administration - network ( fill it base on your ISP ) and also DNS tab.......after that open terminal and type :==> sudo /etc/init.d/networking restart

2. Go to system - administration - software sources ( activate your repositories ).....
then open terminal :==> sudo apt-get update
then : sudo apt-get upgrade

3. You can see from terminal by typing :==> sudo fdisk -l
the one with 83 - linux is your ubuntu

:)

---

