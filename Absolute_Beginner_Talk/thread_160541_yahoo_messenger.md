---
title: "yahoo messenger"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by alastair mccracken on 2006-04-15
I've just loaded Ubuntu 5.10 onto an old Sony Vaio PCG-Z600TEK laptop that was running Windows 2000, which I've wiped so that Ubuntu is the sole operating system.
This is my first time with Linux and I've been following the "start here" advice and installed java, real player etc etc
I've come up against a problem whilst trying to install Yahoo Messenger for Unix which can be found on [http://uk.messenger.yahoo.com/](http://uk.messenger.yahoo.com/)
I chose the instructions for Debian, as I believe Ubuntu is based on it. I can download the .deb file and run the dpkg instruction but the install advice on the yahoo web page then tells me "3. Run /usr/bin/ymessenger from X Window to launch the application." and I haven't got a clue what an X Window is or how to carry out this instruction.
I've been running round in circles for hours trying to figure out X Window in the Wiki and help pages but I'm lost.
Can anyone point me in the right direction?

Thanks in advance.

---

### Post by OffHand on 2006-04-15
Why don't you use Gaim? It is already part of Ubuntu and lets you connect to basicly all IM networks.

---

### Post by andlinux21 on 2006-04-15
Yes I think you would be better off using GAIM for your yahoo messenger needs. It looks a little different but it should get the job done for you without the fancy bells and whistles

---

### Post by alastair mccracken on 2006-04-15
Yeah, i thought gaim would do the trick but apparently it doesn't. I better explain - I don't use Yahoo IM but my wife does and she tells me that Gaim doesn't let her use all the features she's used to on our XP desktop systems - we have two on a home network. Basically I've put Linux on this old laptop because I've been intrigued by Linux for some time and I thought I would give it a go. Chose Ubuntu because of good press. So far I'm impressed with it but I can see why people complain about ease of use versus Windows or Mac. (Don't get me started on Apple - whole bad experience with them - they are worse than Microsoft)

Anyway, my question about what is X Window, where do I find it and how do I use it - any ideas?

Bye the way, thanks for taking the trouble to reply.

---

### Post by derjames on 2006-04-15
Hi there!

The Yahoo executable file is in /usr/bin/ymessenger

now
-point to applications (in gnome) but don't open the menu
-right click
-click on edit menus
-A new window appear
-Select Internet (left pane)
-on the right pane on the bottom click new entry
In the new window type the following

Name: Yahoo Messenger
Comment: (any comment, or leave in blank)
Command: /usr/bin/ymessenger

Now if you check the menu 
applications>internet

you will see the new entry: Yahoo messenger
just click on it and ready.
Later you can change the icon if you wish, in my case in borrowed one from GAIM

Hope this helps
Cheers

---

### Post by alastair mccracken on 2006-04-16
Thanks very much Derjames. You're instructions were clear, easy to follow and they worked. Thanks a lot:D

---

### Post by Kimm on 2006-04-16
X Window is the graphical parts of Linux and UNIX.
so, by "Running in X Window" it means that X11 should be up and running (graphics should be working, and be on) so that the application can connect to the graphical server.

But I strongly suggest you use Gaim, Yahoo Messenger for Linux is extremely outdated and you'd be better of with Gaim.
If you want you can try the latest beta of Kopete (the KDE IM program). That requires you to build it from source however, and that might be somewhat hard for a new user. Kopete has more features then Gaim, though I have never used it with Yahoo

---

### Post by kwyjibo on 2006-04-16
not sure but does gaim allow you to browse the yahoo chat rooms, or does it just have the IM side of it... as maybe that is what she wants, yahoo messenger has a lot more to it than just the IM part as far i know

---

### Post by Kimm on 2006-04-16
I dont know about browsing the chatrooms, but I can join chatrooms thats for sure.
You might want to look into the latest build of gaim too (gaim 2.0 beta3, I think theres an autopackage at their website gaim.sf.net)

---

