---
title: "Delete a shared folder"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by npaisnel on 2007-05-07
Hi all,

I have had this problem for a while, and even after a couple of weeks posted on the Kubuntu forum, still no answers, evven after 'bumping ' up a couple of times.  Since no answer there I wondered if anyone here with Ubuntu might know

Using Kubuntu Feisty.

I had created a couple of shares in the Remote places using 'Add network folder'
They are samba shares, such as :
smb://su/My Documents/My Pictures/Street art.

I just cant delete them. There is no right click /delete option, and dragging to the Trash, gives an Access denied error.

I have tried various searches, using google as well as forum searches, but cant find anything.  Is this a know problem? a bug? or what


Thanks

Neil

---

### Post by jaclynL on 2007-05-07
Is there an "unmount volume" option?  That sounds like it should do it.

---

### Post by MikeEvans on 2007-05-07
I'm more familiar with Gnome than KDE but here it goes.

First make sure there are no running programs accessing the shared folders like picasa.   If not then it sounds like a permission issue.  Give yourself full access to the files with chmod.

```
sudo chmod -R 777 /target/folder
```

Now you should be able to delete it.  If you can't do it from KDE try it from the command line with sudo

```
sudo rm -r /target/folder
```

Just noticed your using smb://.   For the above directions you need to access the folder directly like /home/user/share.  If you're trying to do this over your network read over this post:

[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by npaisnel on 2007-05-07
Hi, thanks

Firstly, no, there is no un mount option, and a right click and properties  only shows one tab called General, no permissions tab.

Thanks for the link, that was the one I used originally when I set up the network, but cant see anythin grelevant to deleting the share.  

Two reasons for that:
1) I just plain missed it,
2) I am too much of a newbie to recognise the reference for what it is.


There were other files/folders that I could not remove until I changed the permissions  to 777, but how would I use that to change perms for a samba share?  I just cant see it

Will have another read through and see if another reading brings up anything new


thanks

Nei

Edit:
BTW the shares were on a networked Windows XP machine.  Thoses folders are no longer on the XP machine.

---

### Post by MikeEvans on 2007-05-07
Ah,  I misunderstood your question.  I don't think i can be more help since this is a KDE issue.  In Gnome I open up my network places folder, right click on the network place, and there there is an unmount option.  I can also click on the bookmarks tab at the top of the dialog and choose 'edit bookmarks', there is then an option to remove a bookmark/network share.

I noticed that items mounted to the network places folder don't show up when you check system mounts with the 'mount' command.  It think they should.. hmpf.

---

### Post by npaisnel on 2007-05-07
Hey, well thanks for trying

No one on the kubuntu forum seemed to be able to help, maybe will try a couple of postings on other forums

Thanks

Neil

---

