---
title: "tinyerp misery..."
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jamesbeat on 2008-01-14
I'm trying to get tinyerp running on my system (gutsy) but I have an odd problem that I can't find an answer to.
I installed the client, which worked fine ((but couldn't connect to the server as it wasn't installed) and I followed an online tutorial to get the server set up and create a database.
I installed the server via synaptic package manager after enabling the repository.
I also installed the dependencies, and set up a database called 'terp'

Now, when i try to start the client, nothing happens! 
I tried removing and reinstalling the client but the problem is still there.
Also, on the applications menu, where there used to be a graphic icon of a red letter 'T' for Tinyerp, now it's just showing a generic program icon.

It seems a lot of people have problems installing this application, and my problem is that I'm still very much a novice Linux user.
I need to install Tinyerp to have a mess around with it and find out if it will be suitable for my needs, but it's such a problematic thing to get running that I'm shooting in the dark.
There is an online demo, but it doesn't contain the modules that I would be using, so it's not much help.


I have a clothing store, and I am starting up an online store to compliment it. The idea is that I have a POS system in the physical store that also talks to the online store for stock control.

You would think that there must be thousands of people who want this same thing, but there are hardly any software packages that will do this seemingly simple and obvious task.
Either they're WAY out of my price range, or far too simplistic.

From what I can gather, a lot of people with both a physical and an online shop end up manually controlling their stock and hoping for the best, but in my business, that would be a disaster waiting to happen!

I tried using a POS system called 'PHP POS' which is web based and has a version that will talk to an oscommerce shop, but this version doesn't allow reorder levels to be set, so is pretty much unusable.

The only other option I seem to be able to find is tinyerp with the oscommerce compatibility module and the POS module, but it seems that I have to become a programmer just to get the thing to work!


Is anyone prepared to hold my hand through this installation procedure, or suggest another piece of software that would do what I require?

Thanks in advance for any help,
James

---

### Post by Directrix1 on 2008-02-01
I got TinyERP running by following the instructions on the site on how to set it up.  Granted I am not using it yet (just experimenting for now).  But it looks to be quite a program.  Although, it doesn't look POS oriented but there might be a module for that. *EDIT:* There is a module for that [http://tinyerp.com/component/option,com_mtree/Itemid,111/task,viewlink/link_id,305/](http://tinyerp.com/component/option,com_mtree/Itemid,111/task,viewlink/link_id,305/) .

---

### Post by wohenben on 2008-05-28
It may be the same problem I had.  The latest release is missing some icons.  See

[https://bugs.launchpad.net/ubuntu/+source/tinyerp-client/+bug/203906](https://bugs.launchpad.net/ubuntu/+source/tinyerp-client/+bug/203906)

You can download the tar file (link in the discussion) and install the icons where suggested.

---

### Post by kagy on 2008-06-26
as well as installing the icons, you should stick with using the username, database name *terp* as given in the install instructions, otherwise you have to go around changing conf files.

It also seems that the programmers have used *substring* for dates although it isn't valid. To finally get it working I had to follow the instructions in this post (openerp forum) (editing py files and recompiling)
 [http://www.openerp.com/forum/post17573.html](http://www.openerp.com/forum/post17573.html)

---

### Post by iulianpojar on 2008-07-04
A good guide (all your errors explained):

[http://openerp.com/wiki/index.php/InstallationManual/Installation_Linux/ServerInstallUbuntu](http://openerp.com/wiki/index.php/InstallationManual/Installation_Linux/ServerInstallUbuntu)

---

