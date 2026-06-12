---
title: "using partimage (/etc/aptsources.lst is empty???)"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by molly_001 on 2006-07-15
Hi, all.  I was all fired up and ready to go through a partimage routine, to make a backup image of my linux installation before starting/attempting to install XGL/Compiz.

I am following the directions [here]("http://www.psychocats.net/ubuntu/partimage.html"), and something weird came up right away in the first line of instructions.

I booted from the Ubuntu LiveCD.  I typed in the first command, which is:
sudo nano /etc/apt/sources.lst

...and while this nano editor loaded up --  the area where a return of sources.lst is supposed to appear was completely empty.  There was no display of several lines of text, as appear in the instructions [here]("http://www.psychocats.net/ubuntu/partimage.html").

I was looking for several 'deb' lines to (I guess) access the restricted/security repositories.  Where do I go from here if sources.lst is empty like this?

Thanks!

---

### Post by catlett on 2006-07-15
Are you sure you typed in the correct command? If you missed typed a letter anbd that document doesn't exist, the app thinks you are creating a document called that and will load an empty document.
Try it again and cut/paste the command from Aysiu's guide. Or go to Places<Computer when the window opens go to the etc folder. Find the apt folder and open it. Then navigate to the sources.list and launch it by double clicking. Then edit it from there.

---

### Post by molly_001 on 2006-07-15
I double- and triple-checked.  Even when copy and pasting from his web page, it doesn't work.

So I navigated to the directory as you suggested, and I had to open it with gedit because nano does not appear as an 'Open With..." option.

In gedit, it looks like I cannot save after making alterations to that file (sources.lst).

Therefore this problem I am having (with nano) might be related to permissions on that file.  How do I change the properties/permissions so that I can write changes to it?

Thanks in advance.

---

### Post by [S|G] on 2006-07-15
You can try this: ```
sudo gedit /etc/apt/sources.lst
```
However it is very strange that it would show on gedit and not on nano.

---

### Post by molly_001 on 2006-07-15
Ok, a new mystery ...

To recap, I am trying to use nano or gedit to edit changes to the file
/etc/apt/sources.lst

1) When I use
   sudo nano /etc/apt/sources.lst
nano starts up and the edit screen is blank -- not any text in the file as expected

2) When I navigate to the directory /etc/apt
and I see the file sources.lst there ...
I can double-click to open it (gedit default loads it up) but the option/permission for me to Save is not there, I can't save changes.

and finally ...

3) When I use the command
    sudo gedit /etc/apt/sources.lst
gedit loads up but the text area is empty.

This has to be something with permissions.  How can I change the permissions for this text file.  I do have a root password set.  Please help.
Thanks!

Edit: I also tried the command using su + root login, and still no joy.

---

### Post by molly_001 on 2006-07-15
I finally got it.  On my machine, sources.lst has a different file extension.  It is sources.list ...

Now to see if it will allow me to make changes to it.

---

### Post by molly_001 on 2006-07-16
Thanks, aysiu, for the excellent partimage page.  I feel better moving on to try XGL/Compiz.  Also, I apparently need new glasses.
Molly


------------------------------------


> **molly_001 said:**
> I finally got it.  On my machine, sources.lst has a different file extension.  It is sources.list ...

Now to see if it will allow me to make changes to it.

I've now installed partimage and I can invoke it using sudo partimage command.

But ... it's running EXTREMELY slowly ... several minutes between pages when I move onto the next page.  Very very odd.  There is nothing slow about my hardware.

Sorry for my .list versus .lst error above.

---

### Post by catlett on 2006-07-16
> **molly_001 said:**
> Thanks, aysiu, for the excellent partimage page.  I feel better moving on to try XGL/Compiz.  Also, I apparently need new glasses.
Molly


------------------------------------




I've now installed partimage and I can invoke it using sudo partimage command.

But ... it's running EXTREMELY slowly ... several minutes between pages when I move onto the next page.  Very very odd.  There is nothing slow about my hardware.

Sorry for my .list versus .lst error above.
No need to be sorry about anything, at least the issue is resolved. Part image may be running slow because you are running off the live cd. The live sessions are slower because (as you know) they are running off the cd drive instead of the hard drive.
It was definately I good idea to backup. I didn't and ran into an isue with xgl/compiz and had to re-install. FYI... the window controllers disappeared, even when I logged into a regulae gnome session. I couldn't close a window id it didn't have a "File" option to "quit" and I couln't move a window because there wasn't a border to grab onto and drag.
Hopefully, you will have better luck.

---

