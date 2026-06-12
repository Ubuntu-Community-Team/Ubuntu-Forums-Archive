---
title: "switching to ubuntu"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by eddieg0304 on 2007-07-31
well i i have been wanting to start switching to a form of Linux and so i decided to use Ubuntu. i downloaded the disk and burned it that all went smoothly. to try it out and make sure i like it i used the LiveCD so i can try it out. well so i got it up and working but i couldn't get my internet to "work". i quote work because it wasn't that the access point wasn't working( yes i am using wireless internet) and i know that because it was able to see my home network. when i tried to connect to it, it wouldn't connect and i wasn't able to log onto the internet, my question is why? and how can i fix this because using a wired connection is out of the question because my computer is up stairs and over two rooms.


a little bit of more info i have WEP security enabled and i input the pass code but nothing happened


oo and thanks for any help

---

### Post by yabbadabbadont on 2007-07-31
You need to list your wireless hardware make/model/chipset, or at least as much information as you know about it.  Otherwise it will be difficult for anyone to help you.  :D

---

### Post by Spr0k3t on 2007-07-31
To get the chipset, you can open up a terminal and type "lspci".  Post the whole output if you would like.  Using the wireless are you able to see any access points at least?  From a terminal try "iwscan list" and you should see something if wireless is working correctly.

---

### Post by eddieg0304 on 2007-07-31
router= netgear WGR614v6

access point= linksys WUSB54G

thats the equipment i am using to connect, it works with my xp computer


i am able to see my wireless network its just that it doesn't connect

and is there a  way to get the chipset through XP because like i said i was only using the liveCD and well  i need the internet working so i haven't yet installed Ubuntu

---

### Post by Spr0k3t on 2007-07-31
Oh boy... that's the Linksys USB 54G wireless adapter... USB is not fun with wireless.  You may need to use the ndiswrapper with the Windows drivers.  If you could, see which chipset you have on the adaptor by performing a lspci and lsusb.

You may need this link, so keep it handy
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It does look like someone has been able to get it working though, perhaps a revision of the chipset? [http://ubuntuforums.org/showthread.php?t=296959](http://ubuntuforums.org/showthread.php?t=296959)

-- Edit --
Oops, I missed some information in your post.  You should be able to check the chipset through XP by going to the System Information found in start/programs/accessories/system tools/system information .

---

### Post by eddieg0304 on 2007-07-31
ok thanks for the help so far


in system information it only says LINKSYS WIRELESS-G USB Network Adapter

for the first link [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) i found my access point and it has my chipset info there so i am not sure if i should post it but just to make it easier i will..  it says Chipset: RT2500USB (RT2571F)

and well since i am new to linux i am not sure that since he had version 6.06 if that will change what i should do or not

umm... i believe thats all i needed to put and again thanks

---

