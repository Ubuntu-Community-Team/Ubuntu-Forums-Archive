---
title: "[SOLVED] Help setting up a home network"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by bconverse on 2007-11-17
Ok, so I have my desktop and laptop both running Gutsy.  The laptop uses a wireless connection, the desktop is hardwired.  I have music, videos, ect. on the desktop, as well as a printer that I'd like to access from the laptop.  Can anyone point me to a good how-to for setting up a home network in ubuntu? Basically, I just want to be able to view whatever folders I choose to share from the desktop on my laptop, and I'd also like to share the printer.  I've tried setting up folders as shared on the desktop, but they still don't show up on the laptop, so I am guessing there is something more complex to it. Thanks for any advice.

---

### Post by overdrank on 2007-11-17
> **bconverse said:**
> Ok, so I have my desktop and laptop both running Gutsy.  The laptop uses a wireless connection, the desktop is hardwired.  I have music, videos, ect. on the desktop, as well as a printer that I'd like to access from the laptop.  Can anyone point me to a good how-to for setting up a home network in ubuntu? Basically, I just want to be able to view whatever folders I choose to share from the desktop on my laptop, and I'd also like to share the printer.  I've tried setting up folders as shared on the desktop, but they still don't show up on the laptop, so I am guessing there is something more complex to it. Thanks for any advice.

Hi and maybe this link will help
[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)
Good luck!

---

### Post by tyggna1 on 2007-11-17
[The community documentation rocks]("https://help.ubuntu.com/community/SettingUpNFSHowTo")  

After it's set up, you just need to mount your network shares the same way you would a hard drive.  Note:  This is documentation for a Linux home network.

---

### Post by bconverse on 2007-11-17
Thanks for the quick replies.  I am still a newbie, however, and those guides seem a little over my head.  I can't quite follow the NFS guide as I am not quite sure if I need to be working just from the desktop (as I basically want to make it a server) or from the laptop as well.  I may need some hand holding with this process.

---

### Post by ofb on 2007-11-18
Couple of questions. 

Are you using the same username on both machines by chance? If so, you can skip the information on Users, Groups, & NIS. Simplifies life marvelously.

Next, how are the computers communicating to each other? Sounds like they both have single network connections. Are they both connecting to the internet through a hub then? Reason I'm asking is if that's right, then this is identical to sharing between machines across the internet -- you'll have to follow the security precautions for NFS to the letter. Sharing on a protected LAN is simpler to set up.

So it'll help people help you if you describe your setup, and let us know how you're handling firewalls on the individual machines -- like are you using the Firestarter or Guarddog configuration tools?

Take your time with this and ask lots of questions. The community documentation is a little hard to swallow because of necessity it must cover everything for all setups. And as a bonus, it's a little out of date -- the Shared Folders GUI takes care of editing exports for you now. Also nfs and portmap are already installed by default I believe.

> I am not quite sure if I need to be working just from the desktop (as I basically want to make it a server) or from the laptop as well.

Think about the terms this way: The Server is the the machine serving a filesystem to be shared. Machines that access that share are Clients.

The Server is the machine you make the Shared Folder on. On the Client you make a mountpoint for that share, so the share becomes part of the Client's normal file system.

IE, let's say you share ~/files/music on the Server. On the client you can make a mountpoint also called ~/files/music, or whatever you like, and the shared files will show up in there, exactly as if they were on the physical machine.

That's NFS - it mounts a filesystem over a network seamlessly into the Client. If you'd prefer something similar to Windows Network Neighborhood, then you'd be looking at SMB aka Samba.

---

### Post by bconverse on 2007-11-18
> **ofb said:**
> Couple of questions. 

Are you using the same username on both machines by chance? If so, you can skip the information on Users, Groups, & NIS. Simplifies life marvelously.

Next, how are the computers communicating to each other? Sounds like they both have single network connections. Are they both connecting to the internet through a hub then? Reason I'm asking is if that's right, then this is identical to sharing between machines across the internet -- you'll have to follow the security precautions for NFS to the letter. Sharing on a protected LAN is simpler to set up.

So it'll help people help you if you describe your setup, and let us know how you're handling firewalls on the individual machines -- like are you using the Firestarter or Guarddog configuration tools?

Take your time with this and ask lots of questions. The community documentation is a little hard to swallow because of necessity it must cover everything for all setups. And as a bonus, it's a little out of date -- the Shared Folders GUI takes care of editing exports for you now. Also nfs and portmap are already installed by default I believe.



Think about the terms this way: The Server is the the machine serving a filesystem to be shared. Machines that access that share are Clients.

The Server is the machine you make the Shared Folder on. On the Client you make a mountpoint for that share, so the share becomes part of the Client's normal file system.

IE, let's say you share ~/files/music on the Server. On the client you can make a mountpoint also called ~/files/music, or whatever you like, and the shared files will show up in there, exactly as if they were on the physical machine.

That's NFS - it mounts a filesystem over a network seamlessly into the Client. If you'd prefer something similar to Windows Network Neighborhood, then you'd be looking at SMB aka Samba.


Yes, I am using the same username on both the laptop and desktop.  They are connected to a router.  The laptop uses a wireless connection, and the desktop uses an ethernet cable. So yes, I suppose it is considered a protected lan then.  I have firestarter running on both computers, though, I have never used it on the laptop, I've only needed to forward ports, ect. on my desktop.  
All I am really looking to do is to share a couple of folders from my desktop, so that I can access them from my laptop.  I also want to share the printer I have connected to my desktop with my laptop.  I am not sure if this is involved in the same type of steps, but that is a major part of why I wan to set this up.

Thanks again for the advice.  I guess I just need to know where to proceed from here?

---

### Post by ofb on 2007-11-18
Okay, your setup is not my setup so hopefully someone will jump in. Meanwhile, let's forge ahead with an outline.

You'll share the printer via SMB. This is hopefully straightforward using the GUI at System > Admin > Printing. On the serving machine with the printer, you'll want to tell it to share that printer - possibly only to the address of the other machine if that's an option, and you'll want to get the printer's newly assigned network address. Then on the client use the same GUI to set up a network printer, using that address. Then you'll probably have to allow this access through Firestarter on each, which is definitely out of my ken - I use Guarddog.

Back to file sharing in general, have a look at System > Admin > Network to find out the IP addresses that your router has assigned to your computers. On the client you'll have to make an entry in the fstab with the address and mountpoint that the NFS share it is going to use.

So the steps are roughly like this,

1] Use the Shared Folders GUI to make an NFS share on the serving machine.

2] On the client create an empty directory that will be the mountpoint. Edit the fstab to include the new NFS. Example from my machine's fstab,

192.168.0.2:/home/o/files/downloads /home/o/files/nfs nfs hard,intr

The syntax above is Address Of Share, Mountpoint, Declaration Of Type, Options.

3] Allow the sharing though Firestarter on each. Again, I use Guarddog. Firestarter might be quite simple, like telling it to trust the address of the other machine, or a little more complex. You'll have to look into it. Fortunately your setup is very common these days, so you can probably find what you want in Firestarter's own documentation.

Anyhow, that's the outline. I'm skipping wee details because I want to give you an idea of what you're doing first to help your reading make sense.

So, first question I guess is does the outline make sense? Got any question there?


Also I'd like someone to comment about the security of firewalls built into today's home routers. Can we set trust that and set up this NFS like a fully protected LAN, or should we be more cautious and protect against IP masquerading?

---

### Post by ofb on 2007-11-19
Oh, such nice timing. Keep an eye on this thread as it develops.
[http://ubuntuforums.org/showthread.php?t=617132](http://ubuntuforums.org/showthread.php?t=617132)

---

### Post by bconverse on 2007-11-19
> **ofb said:**
> Okay, your setup is not my setup so hopefully someone will jump in. Meanwhile, let's forge ahead with an outline.

You'll share the printer via SMB. This is hopefully straightforward using the GUI at System > Admin > Printing. On the serving machine with the printer, you'll want to tell it to share that printer - possibly only to the address of the other machine if that's an option, and you'll want to get the printer's newly assigned network address. Then on the client use the same GUI to set up a network printer, using that address. Then you'll probably have to allow this access through Firestarter on each, which is definitely out of my ken - I use Guarddog.

Back to file sharing in general, have a look at System > Admin > Network to find out the IP addresses that your router has assigned to your computers. On the client you'll have to make an entry in the fstab with the address and mountpoint that the NFS share it is going to use.

So the steps are roughly like this,

1] Use the Shared Folders GUI to make an NFS share on the serving machine.

2] On the client create an empty directory that will be the mountpoint. Edit the fstab to include the new NFS. Example from my machine's fstab,

192.168.0.2:/home/o/files/downloads /home/o/files/nfs nfs hard,intr

The syntax above is Address Of Share, Mountpoint, Declaration Of Type, Options.

3] Allow the sharing though Firestarter on each. Again, I use Guarddog. Firestarter might be quite simple, like telling it to trust the address of the other machine, or a little more complex. You'll have to look into it. Fortunately your setup is very common these days, so you can probably find what you want in Firestarter's own documentation.

Anyhow, that's the outline. I'm skipping wee details because I want to give you an idea of what you're doing first to help your reading make sense.

So, first question I guess is does the outline make sense? Got any question there?


Also I'd like someone to comment about the security of firewalls built into today's home routers. Can we set trust that and set up this NFS like a fully protected LAN, or should we be more cautious and protect against IP masquerading?


Ok, I am less confused now.  Most of this makes a good deal of sense, and I read the guide you posted in the reply below this one.  That made sense of the whole folders thing.  I have folders set up to be shared with the GUI on the server machine now, but, like the poster of that thread, there may be a problem with firestarter. But then again, I dont know.  I can't trace the path from the client to the server, but I can from the server to client.  So, something is wrong with the client I think. I also think I may have narrowed down the printer issue.  On the server, I have enabled sharing, in the printing GUI.  However, I am unable to locate the address assigned by the network.  
There is an option in there to connect to the server, which is localhost on the the server, which I think is correct?  But, when I open the printing gui on the latop (client) I see no shared printers, but, if I try to hit connect to server, It gives me a CUPs server (I have CUPS on the latop as well, I think I should probably remove it?) But I see no mention of the shared printer from my server.  Nor do I see the right connection that could be made.

Thanks again for all your help, I just wish this issue was resolving faster than it is.

---

### Post by ofb on 2007-11-19
> **bconverse said:**
>  I just wish this issue was resolving faster than it is.

I can sure understand that. Simple Sharing On Ubuntu just isn't quite there yet, alas. And setup is necessarily tricky because getting it wrong ruins security.

Okay, back to your problems.

Printing I won't try to help with further - I never print at home anymore so haven't wrestled with Ubuntu printing. Probably at this point there's one or two small configuration gotchas to be figured out. Now that you've got your general ideas straight, you can search for the relevant answers as easily as I can. (No offense - I've just got other things I need to do. My intent here is to switch you from drowning to swiming.)

Just a mild suggestion - unless you're finding people are making Firestarter work with your type of setup, you may need to use Guarddog instead.

Firestarter does a great job of quick configuration for a very few widely used setups. Outside of those, I've found I've needed Guarddog.

If you end up that way, here's some Guarddog pointers.

First and foremost - it has excellent online documentation that walks you through setup. Guarddog looks intimidating at first, but you spend an evening with the documentation and then afterwards wonder why you thought it'd be hard.

How Guarddog works is everything is shut off by default, and you have to enable the protocols you wish to use. That's not as hard as it sounds because said online documentation tells you what you need for the Web, Mail, etc.

There is /one/ gotcha that I'll cover now. You may need SMTPS to send mail. That's an option in the current Guarddog, but 7.10 is one version behind, so a user-created protocol must be made if you need it.

How to figure out if you need it... Okay, if you handle your own mail, like with say Evolution or Thunderbird or Claws, rather than an online service like Gmail, **and** your mailserver is not the people you buy your internet connection from (like in my case my mail is sent through my website server which is a hosted by a separate outfit in California) **then** probably you need SMTPS to send mail to your separate outfit because probably your internet-connection ISP is blocking mail *that does not go to its own mail servers* sent from port 25 .

(Wasn't that a mouthful.) A lot of ISPs have begun doing that in an effort to cut down on spam. The first thing a client like me notices is suddenly I can't send mail. I have to swtich ports, and use SMTPS. In my case port 465, and I have to make SMTPS work myself because our Guarddog doesn't have it yet.

In which case you do this,

> For future readers, the specific steps I used are:
1)in Guarddog, advanced tab,click 'New Protocol' then
create name SMTP, type TCP, port 465, click Apply.
2)next, pick 'protocol tab', 'internet zone',
expand the 'user defined' selections and check the
box for SMTP (which was created in step 1) above.
3) click 'Apply' and you should be done.

Which is simple, but I've just saved you a lot of searching to figure it out.

**Anyway**, that's only if you need it. Most people send mail via their internet-connection ISP servers these days. I just thought I'd mention it here in case you get Guarddog all set up and find you can't send mail.

---

### Post by gigaferz on 2007-11-21
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

I did it a while a go and it works!

 bout to do it again,

---

