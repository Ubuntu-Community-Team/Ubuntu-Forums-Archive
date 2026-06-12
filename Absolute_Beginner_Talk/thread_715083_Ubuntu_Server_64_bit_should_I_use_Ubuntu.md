---
title: "Ubuntu Server 64 bit: should I use Ubuntu?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Temagami on 2008-03-04
Hi all,

I'm a computer science teacher at a smaller high school in Ontario and my grade 12's wish to make a server.  So we pooled all our spare parts and made a duo core machine with 2 gigs of ram, DVD burner and an 80 gig HD (I may go buy a sata for them this weekend - damn I'm a nice guy ;-)  

Anyhow, all it would be used for is a file server, a terminal server, and maybe an internal game host for their gaming club.  We would LOVE to use LAMP and to test php and mysql websites but we can't get outside of the school network because of the firewall and the board won't open a port for us.   I also want them to see that there are other O/S's out there besides microslop.

Questions:

When I installed Ubuntu server it appeared to be a command line?  Do I need to install the client first and then the server?  Can someone direct me to a step-by-step tutorial?

I need the kids to be able to run software from the box and NOT have it installed on their machines (ie. microsoft office).  Can Ubuntu do this terminal service type thing with that "wine" program installed - or is it too much of a mess?

I don't know anything about linux and trying to teach my kids this is going to be really hard so if anyonw could help it would be greatly appreciated.

:)

---

### Post by ptn107 on 2008-03-04
There is a special derivative of Ubuntu called Edubuntu.  It's specifically designed for classroom use.

[http://www.edubuntu.org/](http://www.edubuntu.org/)

With this version of Ubuntu it also allows you to set up a single machine as a LTSP server and run multiple Edubuntu thin client machines from that server machine.  So you only have to install software to the server machine and you can run it from any of the thin client machines (keeps overall cost down and makes administration easier too).

[https://wiki.edubuntu.org/](https://wiki.edubuntu.org/)

---

### Post by lswest on 2008-03-04
Well, to answer your original question (and being from Ontario myself, i feel obliged to help out^^) Ubuntu Server edition is just a CLI by default, but if you need a GUI you can easily install Gnome, KDE, XFCE (ubuntu-desktop, kubuntu-desktop, xubuntu-desktop packages) or install GDM and some light-weight GUI such as openbox or fluxbox or so (not really necessary on that machine, i'd go with Gnome if that's what you're used to).  However, an alternative is to install a Desktop edition and then installing the LAMP packages.  Seeing as how you've already installed the server, might as well just go with ```
sudo aptitude install ubuntu-desktop
``` to get everything you need GUI-wise ;)

Also, about it functioning as a software server, seeing as i've got little experience with that kind of a server, i'd assume would be better off if you ran linux programs from it (e.g. OpenOffice, instead of Microsoft Office), but the older versions (2003 and below) should run fine in Wine, so it really is up to you

---

### Post by tarpon_bill on 2008-03-04
I would install just the base Ubuntu gnome desktop and add from there. The server edition is a minimalist command line driven version strictly for servers. Using the desktop edition, you will find installing the server software additions instructive and you can use that aspect as class projects. There are plenty of HowTo recipes to show you how to setup the server software you want ...

By far a GUI would be better to learn from. I might also suggest tweak-ubuntu for settings that you might want to change for server use.

Many ways to accomplish the same thing with Ubuntu.

---

### Post by Temagami on 2008-03-06
Wow - Thanks for the advice.  I took a look at that EdBuntu.  It looks great but I couldn't really find much about using it as an actual server rather than a client.  So much to read!! I'm probably missing something.

Ok... so let me get this straight.  What I should do is install the 64 bit Ubuntu client software.  THEN download the server software and that will install overtop of the client (right?)  Lwest: you were saying that is the way to go right?  I think the gnome version would be my best bet.  (You're in Germany now from Ontario?  - well, you're in a country which still has the proper respect for a pint) :)

Now, with Windows Server 2003, I set in a group and then I add a bunch of users to that group, then I can set permissions - all done through 'wizards'.  Now, with Ubuntu server (overtop of the client) will I have to figure this all out with a command line?  Or is it also run in a simple type of GUI?

Thanks again!

---

### Post by guilly on 2008-03-06
> **Temagami said:**
> Wow - Thanks for the advice.  I took a look at that EdBuntu.  It looks great but I couldn't really find much about using it as an actual server rather than a client.  So much to read!! I'm probably missing something.

Ok... so let me get this straight.  What I should do is install the 64 bit Ubuntu client software.  THEN download the server software and that will install overtop of the client (right?)  Lwest: you were saying that is the way to go right?  I think the gnome version would be my best bet.  (You're in Germany now from Ontario?  - well, you're in a country which still has the proper respect for a pint) :)

Now, with Windows Server 2003, I set in a group and then I add a bunch of users to that group, then I can set permissions - all done through 'wizards'.  Now, with Ubuntu server (overtop of the client) will I have to figure this all out with a command line?  Or is it also run in a simple type of GUI?

Thanks again!

Alright i'll pitch in to help out a fellow Ontarion, not to mention Temagami!!! great place...(originally from North Bay over here!!) 

anyways i can answer the group question, the groups can be configured thru GUI or CLI your choice really.... I just thought I would bring up the 64 bit issue as well. There has been known to be some issues regarding 64 bit, nothing that can't be worked around but I don't know what kind of timeline your under so you may want to consider 32 bit to save you some headaches, However with that said many people have had great success with 64 bit (myself as well) so really it is all up to you, You may want to do some research on your hardware first just to make sure.

---

### Post by Temagami on 2008-03-07
Ahhh your from the Bay - cool.  I used to have a few pop and then get on the "chief commanda' and head down to the reservation.  Get some pickeral.  Then I moved ton Ottawa - I lived there for 5 years from Vanier, to Blackburn Hamlet to Laurier Ave West - nice town!  Then I went to Korea, the U.S., Georgetown and now I live outside of Guelph - so I'm staying put!!  Ha!

The ironic thing is that Ubuntu sent me a bunch of disk to give out to other educators.  They went like hot cakes and now I don't even have one for myself.  Ugh!  So I should go with the 32 bit version client and then drop the server on top of that.  It's all run on menu's.... ok, I think I can start with that. 

There really is no timeline involved, in fact, I 'm on March break right now so I'll just be researching from now on.  

I haver a version of Red Hat Enterprise Edition but I can't make heads or tails of it.  As far as clients go I have an old copy of linspire 5.0 and Mepis.  However, Ubuntu is totally new to me.  So, I assume Ubuntu server can host websites too?  Is there a cpanel with it?

---

### Post by guilly on 2008-03-08
I would personally go with 32 bit, you'll prevent some hardware issues you may run into. Especially since your only using this server for education purposes, I'm sure it won't be getting tons of hits... Anyways yes you can install the desktop version then just install the server services on top of it. So for example you want to create a web server, install the desktop version with gnome then just install apache as an additional "service".

---

### Post by Temagami on 2008-03-14
Ok... it sounds too simple to me :)  I'll give it a shot when I get back to school.  I still need to buy my kids a sata drive.  I stuck an older IDE drive in it I had  laying around.... but I think a second drive for a second O/S would be good.  The only problem is setting it up as a dual boot.... hmmm.

---

