---
title: "Need help with some Linux basics"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by WeeGraeme on 2006-08-14
Hi.

I installed Ubuntu 6.0.6 yesterday, using a magazine DVD.  For years I've wanted to try Linux and I finally took the plunge.  I copied off files I'll want to use again and then installed Ubuntu letting it completely replace Windows.  I guess that means there are less potential conflicts or contaminants, but it also means that the disk structure I had and with which I was familiar is no longer there as a reference to learn where things are located now.

There are a number of things I have yet to get working.

I can't connect wirelessly to my router yet.  Well actually, that's not quite true.  I can, but I'm still working on getting WPA working.  Luckily for me, I've been able to get wired networking enabled.

I haven't worked out what I need to do to get my printers working.  They're all attached to Windows XP Pro machines on my home network.

I'm sure I'll get there.  I just have one or two questions though, to help me understand what I'm doing.

With regard to my WPA issue, I tried to copy a file into a directory (Sorry if that's not the name used in Linux.  I still think in dos and OS/2 terms when it comes to navigating my PC).  I was told I didn't have permission.  I was using Nautilus as I still have no idea of the layout of the harddrive now.  So after all that long-windedness, here comes my question.

I'm aware of the sudo command to be used from the terminal.  Is there an equivalent you can use from Nautilus?

The file I was trying to copy was for wpk_supplicant.  I'm making slow progress on how to install it, but one thing I'm not sure on is how to install it so that it applies for all users.

My last question is regarding my printers.  From reading this and other forums, I've accepted that one of them just won't work (Lexmark X6170), one might work (Lexmark E230) and one should work (Canon Pixma ip4200)

The two printers that may work are both attached to the same computer which is running Windows XP pro.  I've found the section in Ubuntu where printers are added, and I've seen where you need to select whether it's a local or network printer.  I've had a passing look at CUPS (meaning I started it, looked at a few menus and then realised I didn't know enough about it to use it.)  It has several different methods of connecting to network printers.  That's made me realise that I really need to know a bit more about that too.  In particular, when trying to setup a network printer, it asks for the name for the name of a host.  For want of a better term, what syntax should that take?

Well I hope that's not too long winded.  I'm not asking to be spoonfed.  I'm just realising that I don't know more than I knew I didn't know.  :-)

---

### Post by Paul41 on 2006-08-14
> I'm aware of the sudo command to be used from the terminal. Is there an equivalent you can use from Nautilus?
Type the following in the terminal and it will open Nautilus with root premissions.
```
sudo nautilus
```
Sorry but I don't have any experience with the rest of your questions.

---

### Post by xpod on 2006-08-14
To one Weegraeme from another Wee Graham...."welcome to THE machine"

I liked the "letting it completely replace windows" bit.

I take it you have an xp cd in case you decide you`d rather go back??(unlikely)

Somebody here will get you "rocking & rolling"....Good Stuff

---

### Post by bruce89 on 2006-08-14
> **Paul41 said:**
> Type the following in the terminal and it will open Nautilus with root premissions.
```
sudo nautilus
```


That could break something, use ```
gksudo nautilus
```
gksudo needs to be used for graphical apps, otherwise it could break the .ICEauthority file.

---

### Post by WeeGraeme on 2006-08-14
> **Paul41 said:**
> Type the following in the terminal and it will open Nautilus with root premissions.
```
sudo nautilus
```
Sorry but I don't have any experience with the rest of your questions.

Thanks.  I never thought to type just that.  I didn't (and still don't for that matter) know where the programme was stored, or what it was called.

---

### Post by davebgimp on 2006-08-14
Check here for a howto on WPA:
[http://ubuntuforums.org/showthread.php?t=125150](http://ubuntuforums.org/showthread.php?t=125150)

---

### Post by WeeGraeme on 2006-08-14
> **xpod said:**
> To one Weegraeme from another Wee Graham...."welcome to THE machine"

I liked the "letting it completely replace windows" bit.

I take it you have an xp cd in case you decide you`d rather go back??(unlikely)

Somebody here will get you "rocking & rolling"....Good Stuff

Yes, the laptop came with Windows XP Home installed.  I think it comes with a recovery disk.  Hopefully I'll only need it again if and when I eventually dispose of the laptop.

I thought it was just gimmicky when I first saw it, but I'm already sold on the multiple workspaces.

Graeme

---

### Post by mscman on 2006-08-14
First, welcome to Linux! Hope you have fun!
Now to business...

Regarding your WPA/wireless router situation, you should try using NetworkManager, as it provides a nice graphical way of dealing with WPA. Install it using the command:
```
sudo apt-get install network-manager-gnome
```

For root access in nautilus, definitely use the gksudo version of the command given above.

Finally, I really am not sure about how to set up your printers. My advice is to try searching the forums for your printer model and see if you can find anything that way.

Good luck, and happy computing!

---

### Post by WeeGraeme on 2006-08-14
> **bruce89 said:**
> That could break something, use ```
gksudo nautilus
```
gksudo needs to be used for graphical apps, otherwise it could break the .ICEauthority file.

Thanks.  I appreciate that.

---

### Post by WeeGraeme on 2006-08-14
> **mscman said:**
> First, welcome to Linux! Hope you have fun!
Now to business...

Regarding your WPA/wireless router situation, you should try using NetworkManager, as it provides a nice graphical way of dealing with WPA. Install it using the command:
```
sudo apt-get install network-manager-gnome
```

For root access in nautilus, definitely use the gksudo version of the command given above.

Finally, I really am not sure about how to set up your printers. My advice is to try searching the forums for your printer model and see if you can find anything that way.

Good luck, and happy computing!

Thanks.  I tried installing Network Manager but I didn't get the results I was expecting.  I can still only use WEP, not WPA.  When I installed Network Manager, which I did, following directions on a sticky post somewhere (I've read so much today that I can't remember exactly where it was) it gave a command to add Network Manager to the menu, but for some reason it doesn't appear anywhere.

Thanks for your suggestions though.

---

### Post by Paul41 on 2006-08-14
> **bruce89 said:**
> That could break something, use ```
gksudo nautilus
```
gksudo needs to be used for graphical apps, otherwise it could break the .ICEauthority file.
Thanks for the info on gksudo.  I didn't know about gksudo and have always used sudo without any problems (maybe I'm lucky?).  I will start using gksudo also.

---

### Post by steve.horsley on 2006-08-14
> I thought it was just gimmicky when I first saw it, but I'm already sold on the multiple workspaces.
I think you will find lots of things you like as you get more familiar with it.
> it gave a command to add Network Manager to the menu, but for some reason it doesn't appear anywhere.
Sometimes you need to use the command **killall gnome-panel** to restart the gnome panel application before the new menu items appear. 

Wish I could help you wiht the printer, but I've never printed to an MS shared printer.

---

### Post by Iowan on 2006-08-14
> **WeeGraeme said:**
> Hi.
In particular, when trying to setup a network printer, it asks for the name for the name of a host.  For want of a better term, what syntax should that take? Forgive me if I'm stating the obvious, but the host is the name of the computer to which the printer is attached.  I'm nowhere near my home network, or I'd see how I set up one of my shared printers (attached to an XP box).  If a "good" answer doesn't appear first, I'll check when I get home (in another 4 hours) and post the results.

Well, it looks like the windows box that had the printer attached got disconnected from my network - thus, the printer is no longer available.  Perhaps I'll try connecting the printer to another machine (or running a cable down the hall to the machine that had it).

---

### Post by WeeGraeme on 2006-08-14
> **bruce89 said:**
> That could break something, use ```
gksudo nautilus
```
gksudo needs to be used for graphical apps, otherwise it could break the .ICEauthority file.

This is probably dumb question of the week.

I can run gksudo nautilus.  I got an error message saying that Authentication was Rejected, but it appears to run anyway.  On the top, it says "root - File Browser".

When I browse through the directories, it's obvious that filesystem for root isn't the same space as filesystem for my normal login.  How do I access the same physical space when logged in as root, as I do when logged in as me?

---

### Post by Paul41 on 2006-08-15
> I can run gksudo nautilus. I got an error message saying that Authentication was Rejected, but it appears to run anyway. On the top, it says "root - File Browser".
It looks like this error is normal and everything should be working fine. [http://www.psychocats.net/ubuntu/graphicalsudo.php](http://www.psychocats.net/ubuntu/graphicalsudo.php)

> When I browse through the directories, it's obvious that filesystem for root isn't the same space as filesystem for my normal login. How do I access the same physical space when logged in as root, as I do when logged in as me?
I think there is a directory with your user name that would be your home folder.  I am at my work comupter now (which unfortunately is Windows) so I can't check to see if that is right.  If you can't find it or no one corrects me before I get home I will check then to be sure.

---

### Post by Gustav on 2006-08-15
The directory you normally enter when you run nautilus is /home/<yourusername>

In this directory you can edit stuff without having to use sudo, everywhere else (except /tmp) sudo is needed.

---

### Post by WeeGraeme on 2006-08-15
Well I managed to get my wireless networking going.  I don't know what was wrong.  My laptop has a Broadcom wireless card in it.  I followed the directions provided by nickm elsewhere in these forums, again and again, but it wouldn't work.  I ended up reinstalling Ubuntu from scratch.  I didn't think I'd changed much, but I must've.  It works now.  That's the main thing.

All I need to do now is work on the printers.

Thanks to everyone who has offered suggestions so far.  Even if they didn't directly solve the problem, I've learnt more about Ubuntu than I would have without your suggestions.

---

