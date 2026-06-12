---
title: "new life for old box"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by fldav76 on 2008-04-03
Hi, 

I have an old IBM Thinkcentre A50p 8432 97U with about 500Mb ram sitting around doing nothing and I’d like to make use of it. Currently there are three active computers in my house, 2 laptops running windows xp and one desktop running windows me. We only have one DSL line coming into the house so every time someone wants to use the internet they have to manually plug their Ethernet cable into the (badly located) DSL modem.

I would like to have the DSL line be connected to the thinkcentre and have the thinkcentre share the Internet connection wirelessly with the other computers. I would also like to use the thinkcentre as a print server so that all the computers can send documents to one printer. I would also like to use the thinkcentre as a file server so any computer can upload a file and then a different computer could download the file. This would eliminate the “sneakernet”. It would be nice if uploaded files could be organized into hierarchies and permissions used to specify who can download what. If each computer could send files to any other computer that was connected to the wireless network that would be great too.

I would like to be able to run the thinkcentre “headless” (without a monitor or keyboard or mouse). I would like to power up the thinkcentre in the morning and have it set itself up without my input, but if I connected the monitor etc.  I would like to be able to browse the Internet and access the usual GUI (gnome, kde) programs. 

After I have this all set up I’d like to find some application that will work with linux the way Norton ghost 2005 works with windows. That is, boot from floppy to take an image and boot from floppy to restore an image. Norton ghost also has a useful feature called autoback, each time the computer starts up it reverts back the stored image. That way no matter what crud you pick up online it gets wiped every day.

So to summarize, I want the old thinkcentre to be:

A file server
A print server
A wireless Internet server (I might also add another network card, if so I’d like to use it as a traditional Ethernet internet server as well as wireless)

I want it to be able to boot up and run without my input
I want to be able to use firefox to browse the Internet and use a graphical interface to run the usual programs.

I want a bootable “whole drive/partition image” recovery tool that works with linux.

I have absolutely no clue how I can make this happen. I don’t really have a preference for any particular linux distro. I have investigated this to some length, I’ve looked at ebox, weadmin, puppylinux…and I haven’t found a homerun yet.


Any help is appreciated.
If this post should be elsewhere I’ll happily repost.
Thanks in advance.

---

### Post by pseudo-random on 2008-04-03
That norton software works independent of the OS. So it will work with anything.
Install Ubunt. Just backup your data first.

---

### Post by privaterolf on 2008-04-03
You're better off getting a wireless router, then trying to set up a laptop as one.

You should be able to set it up as a print server and a file server, I've done it with Gutsy.

---

### Post by sowelie on 2008-04-03
You need a router.  You can pick up a decent router for like $60 or so.  Make sure it's a 5 port switch also so you can easily plug in up to 5 computers.  It's really easy to configure, you can put your dsl username  / password right into the router.  I would recommend a linksys or a belkin.  I have had good luck with both.

As far as the server setup goes, that's all pretty easy.  All you have to do is set up a folder as a shared folder (system -> administration -> shared folders).  It will ask you to install nfs / samba.  Then you just browse to the server by going into nautilus and putting in smb://computernamehere/sharenamehere.  Printing is also easy to setup, just plug the printer in and set it up through the printing settings (system -> administration -> printing).  If you google ubuntu shared printers, you'll find some good articles on sharing the printer with other computers.

The server will be fine running without a monitor, just turn it on and it will sit at the login screen.

---

### Post by aquinashub on 2008-04-03
I think you may be looking for this how-to (needs a little work, but all the references are at the bottom of the post):

[http://ubuntuforums.org/showthread.php?t=376283]("http://ubuntuforums.org/showthread.php?t=376283")

Keep in mind though, the person who set up their computer already assumes you have Ubuntu Server installed without DNS or LAMP. So you may have to do a little research as to how you want to go about that.

As for a print server and extra options, well, I'd set all that up after you've established a basic wireless network using your PC. I hope this helps you get things started!

I think it's a cool idea - Good Luck!

---

### Post by fldav76 on 2008-04-11
Thanks for the replies. I've been super bust this week but I'll try out some of suggestions soon.
Good to hear that ghost can still be used with Linux (i really should have known that) I was surprised that it operates independent of DOS.

I'd love a router, but I aint got the dough.

I'm trying to install the usb wireless card i have, but I'm not having much luck.
I went to the linksys website
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859929435&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2943528445B03&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859929435&packedargs=sku%3D1115416828445&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2943528445B03&displaypage=download#versiondetail)
and found a linux driver, but I can't figure out how to use it. I'm used to windows "exe" files. the filename is:
           linux_wlan_ng_0114_pre1_dr.tar%2CO.gz
it looks like this is a gzip file...but also a tar? and I have no clue what the "%2CO%" is.

And i can't deal with file and print sharing until i get the network set up. grr.

thanks again

---

