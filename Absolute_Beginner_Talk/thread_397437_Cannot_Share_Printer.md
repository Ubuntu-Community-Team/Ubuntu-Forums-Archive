---
title: "Cannot Share Printer"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by shaft350x on 2007-03-30
My wife just got a new Darter from system76 and I need to setup printer sharing so she can use the printer that is connected to my computer.  I had gotten her old laptop (WinXP sp2) to work and print to the printer attached to the desktop.  It has been a while since I have set this up and I don't really remember how I got it to work.

I want to share the printer from the desktop running Ubuntu 6.10 (for now) and not mess it up for the old laptop (which will probably be getting Ubuntu in the near future).  However, I did the logical and had the Darter look for the shared printer, and didn't find it.  I tried to point it to the desktop similar to the way I did in WinXP on the old laptop, but it didn't work.  I don't want to mess too much with the settings on the Desktop because it works at least between it and the old laptop.

So I would like to make the printer work for her new Darter, but I don't know where to start (and yes I've looked at some of the howto threads and search the forums, but wouldn't mind if someone could point me to one that would work).  Any help on sharing between two Ubuntu computers would be helpful.  Thanks!

---

### Post by wpshooter on 2007-03-30
Shaft:

I hate to tell you this, but this last time I tried what you are wanting to do, I could NOT get it to work.  Unless they have made some improvements to CUPS lately, I am not sure that this is doneable by a person that is not a linux programmer.  I have given up for the time being.  Maybe I will try again when Feisty is finalized.  

But good luck if you decide to try.

---

### Post by PurplePenguin on 2007-03-30
I might be missing something here... seems you want to have a printer connected to one computer running Ubuntu, and have other computers see it and print to the printer, right?  It's pretty easy to do.  I've got that kind of thing set up right now and it works great.

Let me know... maybe I didn't quite understand your question or particular problem.

This part of [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Print_Server_.28cupsd.29") walks you through it step by step.  I had mine up and running in about 10 minutes (with a Canon Pixma printer, too!).  And I'm the farthest thing from a linux programmer that you'll find...

---

### Post by shaft350x on 2007-03-30
Part of the problem is how the particular network is setup I think.  The cable internet comes in at my friends who shares it with us via a ethernet cable from his router to ours.  So I don't know that the IP configurations would be the same.  Our router is acting as a repeater.

Cable Internet > Neighbor's Router > Our Router > Desktop Ubuntu w/printer
                                                                                        > Laptop Windows XP
                                                                                        > Laptop Darter Ubuntu

My neighbor's router is the one that has the normal IP addrsess.

---

### Post by chaplanger on 2007-03-30
> **shaft350x said:**
> Part of the problem is how the particular network is setup I think.  The cable internet comes in at my friends who shares it with us via a ethernet cable from his router to ours.  So I don't know that the IP configurations would be the same.  Our router is acting as a repeater.

Cable Internet > Neighbor's Router > Our Router > Desktop Ubuntu w/printer
                                                                                        > Laptop Windows XP
                                                                                        > Laptop Darter Ubuntu

My neighbor's router is the one that has the normal IP addrsess.


See if this helps -- it got me up and going from a WIN 2k box to my printer server  running Ununtu 6.10.

---

### Post by shaft350x on 2007-03-30
Awesome!  Thank you chaplanger.  That did the trick.  I used the ifconfig in the terminal as the instructions said and then changed the settings in the Darter to reflect that IP address, and bingo!

9th time is the charm.

---

### Post by wpshooter on 2007-04-01
> **PurplePenguin said:**
> I might be missing something here... seems you want to have a printer connected to one computer running Ubuntu, and have other computers see it and print to the printer, right?  It's pretty easy to do.  I've got that kind of thing set up right now and it works great.

Let me know... maybe I didn't quite understand your question or particular problem.

This part of [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Print_Server_.28cupsd.29") walks you through it step by step.  I had mine up and running in about 10 minutes (with a Canon Pixma printer, too!).  And I'm the farthest thing from a linux programmer that you'll find...

Am I correct that the IP address as shown in this guide are examples only and not the actual IP address that would be used ?

Thanks.

---

### Post by shaft350x on 2007-04-01
correct.  You should run "ifconfig" in the terminal to get your own IP

---

### Post by wpshooter on 2007-04-02
> **shaft350x said:**
> correct.  You should run "ifconfig" in the terminal to get your own IP

Yes, that is what I tried but I still can not seem to get this to work !!!

How come when I go to the client machine and try to follow the instructions it tell me that the client file can not be found when I try to edit it ?  Perhaps I am typing it work ??  I am going to try again when I get a chance and I will paste the instructions.  

Can you give me a bit more detail about what section in the files to edit ?  It seems like on one of the files that there were several section similar to the ones in the instructions and I did not know which one to edit.  Also, when the IP addresses are inserted in the files, please give me the exact syntax that is to be used, i.e. are they to be place inside of the <   >s that are already in the file or are they just put on a separate line by them selves ?  The instructions leave a little to be desired, as far as I am concerned.

Thanks.

---

### Post by shaft350x on 2007-04-03
Sorry I've been tweaking around with Ubuntu since I first got it, so I will try to post here soon exactly what I did to get it to work.  Right now I'm still in a technically mixed environment because we still have one laptop with WinXP, so I'm using Samba.  (However, I'll probably have them all on Feisty soon, woot!).

---

### Post by shaft350x on 2007-04-06
Ok looking through the way that I have things setup, I don't think that I really modified samba or cupsd files.

I ran ifconfig, on my Ubuntu machine with printer attached.

Next on the laptop I went to System > Administration > Printing

I created a new printer, and checked that it was a network printer.

When it asked for the URL I entered:  ipp://myIPnumber/printers/PrinterName

the IP number you enter should be the one from the computer that has the printer connected.

Now since I am still on a mixed network (wanting an XP machine to have access) I am using Samba.  I don't know if this is at all necessary for a Linux only network.

So all of my computers are part of the same workgroup.

To check to make sure your computers are all part of the same workgroup check samba on all of them.

```

sudo gedit /etc/samba/smb/conf

```

There will be a section that says:
```

#=============== Global Settings =====================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT -domain name your Samba server will part of
     workgroup = **workgroup**

....

```

that won't actually be bold but you need to make sure it is the same on all of your computers.

You may need to setup logins and passwords for connecting via Samba.  There is a how-to here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Print_Server_.28cupsd.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Print_Server_.28cupsd.29)

I hope that this helps.

---

