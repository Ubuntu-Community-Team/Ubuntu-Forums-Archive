---
title: "Still need help getting online."
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Chappy on 2006-02-13
I tried everything you guys suggested and came up empty. I cannot find anywhere on Ubuntu that even remotely seems like a place where I can let it find my modem, and the type in my ISP's name and phone number, along w/my own userID and password. It shouldn't be this hard to get attached to the net. Afterall, one reason for using Linux is the relative safety one has while surfing. Anymore ideas? Really, I tried everything you guys came up with and I found nothing. Orlox, I made a stab at what you suggested. Ferebee, I went thru System/Admin/Networking, and all I got was a thing on the taskbar saying "Starting Network", and that disappeared after 30 secs or so. GnomePPP sounds exactly like what I need, but if I have to download it, I need to get online. Catch 22. Argghhh. ferebee, I agree and I would guess that there are still more folks using regular dialup than anything else. Due either to the cost or no choice. Regardless. it will be a long time before dialup is no longer needed. So... why is it so hard to get attached to the net w/Ubuntu? I really like it, and would prefer to use it rather than Xandros. But at least w/Xandros it is as ez as w/Windoze to get online. Is there so other way of getting GnomePPP? Is it on the Ubuntu install somewhere? I know that I have maybe, maybe, seen 1% of Ubuntu. 

Anyhow, please don't force me to use Windoze, or kill Ubuntu and try another distro. I want to use Ubuntu. Baaaawhaaa. LOL.

And, again, thnx for all the help you guys have been so far. ferebee, I was sure that what you suggested would work. It sounds so logical. Oh well.

---

### Post by Zerocool10482 on 2006-02-13
Good luck. I tried having ubuntu on a dial up and it's really sucks.

---

### Post by OtrMan on 2006-02-13
Hi;  Some of your post sure sounds familiar!  I am online now with dial-up and the firewall started to work.
I've had some applications do the long blink routine and dissappear.  I'm not sure what causes that but if you try to launch them from the console it will give a reason (I just don't know how to figure it out)

Now for GNOME ppp.  After I had it all set up it would dial and as soon as it connected the connection would be dropped.  That was caused by the ppp program wanting authentication.  You can go into /etc/ppp/options file and about 35 lines down there is a line "auth" .  if you comment that line out it should work (it did for me)
hope that helps a little.  I agree it is to hard to make things work in linux.  But it has a great look and feel to it.

---

### Post by Bartender on 2006-02-13
[QUOTE=OtrMan]You can go into /etc/ppp/options file...[/QUOTE]

otrman, could you please spell that command out for me?  Hopefully I just typed it in wrong.

---

### Post by OtrMan on 2006-02-13
here is what the section looks like after I commented it:
---------------------------------
# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
# auth
-----------------------------------------
The last line was the only one I changed.  Did you get GNOMEppp installed?  From your original message I wasn't sure if you have it.  At first I used the System/Networking tools to get online.

---

### Post by Chappy on 2006-02-13
thnx otrman, no i did not get GNOMEppp installed. I don't know what or where it is. Right now I am back on Xandros, and while it looks kinda ugly, at least it is pretty straightforward. Doh, it must be because I managed to get online w/it. Actually it works  pretty darn well. Anyhow, thnx guys, and keep the ideas coming. I need to figure out why it is not allowing me to use system/admin/networking.

---

### Post by Zyphrexi on 2006-02-13
I'll try to help you if I can. Do you know what kind of modem you have?

type lspci in console to list devices, including your modem

try lspci -vv for more info

Additionally, you can check out
System>Administration>Device Manager

to see the names and types of hardware on your computer.

If your modem is supported, you should have no problems getting online.

And you tried 
System>Administration>Networking ?

A box should have popped up asking for your root password.
Did it pop up?

---

### Post by Chappy on 2006-02-14
Zyphrexi, please read my post at the top of this thread for the answers to most of your questions. I don't see Device Manager as option under System >Administration? Is the more than one way to get to it? I will try the other tips in the am, thnx alot. Oh, it's a USR Sportster 56K X2 Internal Modem. Goes into an ISA slot, and is a hardware modem.

---

### Post by ferebee on 2006-02-15
[QUOTE=Chappy]I tried everything you guys suggested and came up empty. I cannot find anywhere on Ubuntu that even remotely seems like a place where I can let it find my modem, and the type in my ISP's name and phone number, along w/my own userID and password. It shouldn't be this hard to get attached to the net. Afterall, one reason for using Linux is the relative safety one has while surfing. Anymore ideas? Really, I tried everything you guys came up with and I found nothing. Orlox, I made a stab at what you suggested. Ferebee, I went thru System/Admin/Networking, and all I got was a thing on the taskbar saying "Starting Network", and that disappeared after 30 secs or so. GnomePPP sounds exactly like what I need, but if I have to download it, I need to get online. Catch 22. Argghhh. ferebee, I agree and I would guess that there are still more folks using regular dialup than anything else. Due either to the cost or no choice. Regardless. it will be a long time before dialup is no longer needed. So... why is it so hard to get attached to the net w/Ubuntu? I really like it, and would prefer to use it rather than Xandros. But at least w/Xandros it is as ez as w/Windoze to get online. Is there so other way of getting GnomePPP? Is it on the Ubuntu install somewhere? I know that I have maybe, maybe, seen 1% of Ubuntu. 

Anyhow, please don't force me to use Windoze, or kill Ubuntu and try another distro. I want to use Ubuntu. Baaaawhaaa. LOL.

And, again, thnx for all the help you guys have been so far. ferebee, I was sure that what you suggested would work. It sounds so logical. Oh well.[/QUOTE]

Hi Chappy,

I'm sorry it didn't work for you. I made up some screenshots of what I did to 
get connected and download Gnome ppp and if you would
like me to post them I will. It's possible that even though your modem is a 
hardware modem it might not be supported. I did a little searching on this forum and found that a few other 
users has trouble with their sportsters too. 

I couldn't be sure that you can get GnomePPP working without getting your Networking set up first, though maybe another more 
experienced user could tell us?

You could certainly download the file  (gnome-ppp_0.3.21-1_i386.deb)
from here:
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/)

while you are on Xandros and burn the file to a cdrw. (Make sure you download the .deb file.)
If you try installing Ubuntu again, you could copy it to your 
desktop and install it from there, though you would have to use the terminal to do so. In terminal you would type:
```
cd Desktop
```
Make sure you capitalise the D in Desktop.This is case-sensitive.
Then you would type:
```
sudo dpkg -i  gnome-ppp_0.3.21-1_i386.deb
```
It will ask for your password , and then install it. After it goes back to the command prompt, you should be able to find the program under
 Applications>Internet.

If that doesn't work, I'm not sure what else to suggest. If you have a few extra bucks, and a free serial port you
might try getting an external serial modem. They can be had reasonably cheaply
off Ebay, and work with most Distros. Thats where I got mine, and It's never met a distro it didn't like!

I wouldn't get too discouraged if you can't get Ubuntu to work for you. Finding
the Distro that is right for you can take a while, but is very rewarding in the end,
when you do find the one that 'just works'.

I'd recommend trying out a few LiveCd's before installing. If you can get your hardware working from the LiveCd then it should work once it's on your
hard drive. If not, then that distro is probably not for you. A couple of 
distros I've seen recommended for Linux newcomers (other than Ubuntu and Xandros)
are PclinuxOS and  Mepis. I've tried both and they are quite nice. 
[http://distrowatch.com/](http://distrowatch.com/) has loads of info on different distros
and lots of links to reviews and forums, which can be very helpful in choosing
a distro.

I certainly don't mean to push you away from Ubuntu, though. Maybe you might try dual booting Xandros and Ubuntu, so you can keep on trying to get 
Ubuntu working, while also having your working Xandros install to do your
regular computing. There are guides to dual booting with Ubuntu 
here:
 [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 
[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)
[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html)

Thay are for dual booting with windows, but the basic principles are the same.

Good luck, and I really hope you can get this working!

---

