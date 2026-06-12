---
title: "Problem with directory link on desktop"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by jsiii on 2006-02-12
Hello, I don't understand how links in Ubuntu work, but I have this problem here:

I have directory /data which is mounted NTFS readonly drive. I can read it but when I place the link on desktop, it is locked and root owns it, so that I cannot delete it. I know I can delete it as super user but that is not what I want to do.

The best solution would be (I doubt it is possible): I created this link as 'js' user, why is 'root' owning it? Is this bug? Or security policy flaw? I surely would like to own it when I created it. I think that people who are not superusers (and thus don't know the su password) should be available to delete files that they created.

Maybe this will be possible: I want to change ownership of this so that 'js' owns it.

I tried this, but it didn't work:
```
js@home:~$ cd Desktop
js@home:~/Desktop$ dir
data
js@home:~/Desktop$ sudo chown -v js data
ownership of `data' retained as js
js@home:~/Desktop$
```

---

### Post by bscbrit on 2006-02-12
How are you creating this 'link' to your /data directory?

---

### Post by jsiii on 2006-02-12
[QUOTE=bscbrit]How are you creating this 'link' to your /data directory?[/QUOTE]

I drag the icon with mouse and ALT pressed, then I choose 'link here'.

---

### Post by bscbrit on 2006-02-12
Well on my system (Ubuntu / Gnome) when I do that I create a link for which I am the owner and which I can delete without problem.  So it seems that there is something unusual with the way that the link is being set up on your system.

Please open a command line / terminal and move to your Desktop directory.  What is the output from the following command?

ls -l *

---

### Post by jsiii on 2006-02-13
[QUOTE=bscbrit]Please open a command line / terminal and move to your Desktop directory.  What is the output from the following command?

ls -l *[/QUOTE]

This and only line
```
lrwxrwxrwx  1 js js 5 2006-02-12 10:14 Data -> /data
```

Strange, itsn't it... I would think that the link would have all the access rights, but in properties window it tells that the owner is 'root' and permissions are 555. 

Additionally when I press 'delete' over it, nothing happens (It is same when I select 'Move to Wastebasket' from context menu.)

---

### Post by bscbrit on 2006-02-13
No, what it is telling you is that the drive that the link is pointing to is owned by root.  The display you have just shown me indicates that the _link_ is owned by you and that you can do everything you want to it.  What it will not let you do is delete the data that the link is pointing to.  

Imagine you have a folder on your desktop (Home). If you click on that folder do you want it to open the link itself, of the data that the icon is linked to?  The latter of course.  That is what I suspect is happening with your link to your /data drive.

As I haven't got an ntfs drive on this computer I cannot test this immediately, but I will do so over the next few days (or even possibly this evening!)

---

### Post by jsiii on 2006-02-13
Yes, I know that it looks like that. It even sounds logical. But it is not like that.

1. The icon on desktop has lock aside it.
2. When I press delete over it, nothing happens.
3. When I write
```
rm /Desktop/Data
```
The link is NOT deleted
4. When I write
```
sudo bash
rm /Desktop/Data
```
The link IS deleted (not the /Data itself. I cannot delete it even as SU as it is readonly)

I am pretty puzzled about it. Do you think it may a bug (it would be pretty strange:))

And hey, thank you very much for your effort ;-)

---

### Post by bscbrit on 2006-02-13
Well, I cannot reproduce it and it shouldn't happen!  I'm afraid that I have run out of ideas - not that there were many ideas to start with.

Sorry :(

---

### Post by bscbrit on 2006-02-13
What happens if you create the link manually from the command line?

ln -s /data /home/<username>/Desktop/testlink

Do you get the same problem.  If not, then it is something to do with the way the link is being created using Gnome.  Not sure if that helps?

---

### Post by jsiii on 2006-02-13
It is just same like dragging... Cannot be removed until changed to superuser :-(

---

### Post by jsiii on 2006-02-13
[QUOTE=bscbrit]Well, I cannot reproduce it and it shouldn't happen!  I'm afraid that I have run out of ideas - not that there were many ideas to start with.

Sorry :([/QUOTE]

There surely is not need to apologize :-) Not a bad problem since I still can remove it as superuser. It is cosmetical problem and something that developer guys should be interested in. Thanks for helping anyway;-)

---

