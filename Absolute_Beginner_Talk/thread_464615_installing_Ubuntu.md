---
title: "installing Ubuntu"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by stanleyhugh on 2007-06-04
I have spent a couple of days trying to install Version 5.10 from the CD, which travels well until it reaches Grub, when it comes up with the message

Ubuntu kernel 2.6.12-9-306
/bin/sh: can't access tty; job control turned off.

Iis there a command  I can put after the # that follows that will fix the problem?

---

### Post by FleetAdmiral74 on 2007-06-04
I am no expert, but unless you have a reason for using your version, maybe try a newer one. Feisty is 7.something I think...

---

### Post by locke.dragon on 2007-06-04
yeah.  feisty is up to 7.4...  i think...  7.x i guess...  not sure how far it is now.  why such an old version?

---

### Post by Inxsible on 2007-06-04
5.10 is the Breezy Badger -- if I am not mistaken -- that was my first look at Linux. Really liked it. But now I use Feisty and let me tell you its so much better.

Try the Feisty Fawn(7.04), you will like it :)

---

### Post by NeoGreen on 2007-06-04
Yeah, 5.10 is the one I started with, as I type this message. I am installing 7.x on the laptop that had 5.10.  I really learned a lot from 5.10.  But to answer your question:  You probably have a bad CD, you may have to download again and burn another copy.  Try to burn it at a slower speed.

---

### Post by Marious on 2007-06-04
Is this from the LiveCD or from an installation of 5.10? If its from a LiveCD try the newest version or even another distro such as Knoppix which is normally great for troubleshooting, in this case just to see if in fact its your CD, it should not be your hardware since Ubuntu normally runs on a lot of older hardware and 5.10 specifically would have older drivers and all that. Is the CD old or new? Is there a specific reason for you to use 5.10 versus the Feisty Fawn release? I have not used 5.10 myself just 6.10 and 7.04 which are both great.

Marious

Edit. One other thing that comes to mind is that perhaps the structure is incorrect in your Grub file.

---

### Post by stanleyhugh on 2007-06-06
Thanks all.  Will downlaod an up-to-date version and see how it goes.

---

### Post by stanleyhugh on 2007-06-12
Everything worked fine.  I downloaded and installed 7.4 but now it will not start up because it rejects the user name and password, even though I wrote them both down at the time and believe them to be what I am putting in.

Is there a way around this, please.

---

### Post by 3rdalbum on 2007-06-12
When you get the Grub menu on startup, choose the Ubuntu with "Recovery Mode" alongside it. This will bring you to a root terminal. Type:

```
startx
```

And press Enter. You will be brought to the desktop where you can run the Users And Groups program to create a new user. Make sure you go into the "Permissions" tab and check all the permission options, especially "Run administration tasks".

---

### Post by stanleyhugh on 2007-06-12
"When you get the Grub menu on startup, choose the Ubuntu with "Recovery Mode" alongside it. This will bring you to a root terminal. Type:"

Thanks a lot.  Will give it a try.

---

### Post by stanleyhugh on 2007-06-12
"When you get the Grub menu on startup, choose the Ubuntu with "Recovery Mode" alongside it. This will bring you to a root terminal. Type:

Thanks a lot. Will give it a try."

Did that.  Got to Users and Groups 

Message there said

  "The configuration could not be loaded.

You are not allowed to access the system configuration

---

### Post by stanleyhugh on 2007-06-13
> **stanleyhugh said:**
> "When you get the Grub menu on startup, choose the Ubuntu with "Recovery Mode" alongside it. This will bring you to a root terminal. Type:"

Thanks a lot.  Will give it a try.

Got as far as Users and Groups and the message The configuration could not be loaded: You are not allowed to access the system configuation.

So gave up and downloaded and installed it again from scratch.

Thanks all.

Will now try and understand all the new symbols and systems.

Bye.

---

### Post by ncappel1 on 2007-06-13
I wanted to suggest that if numlock is not turned on by default at the installation, the keypad will not enter numbers, so if your password uses numbers, you have to use the ones over the alphabet. Also, passwords and user names are case sensitive, so try not to make the mistake of having caps lock on (which I've made so many times, it isn't funny...).

Just another idea to try out.

---

