---
title: "How to install USB wireless adapterBelkin F5D7050"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by abouttogiveup on 2007-04-26
Ok..  so i am an absolute beginner here..

I have installed xubuntu-6.10-alternate-i386.iso ...  i have just found out how to get round my old Voodoo 3dfx card, and i am on to the next problem.  Wireless.

I'm guessing it needs the specific drivers for my usb adapter listed in the title.  Now i read somewhere that you install the windows driver and copy over a couple of files.  Problem is, being so new, i don't know how to do the install or where to copy the files to...

So..  i have the install CD and would like to get the wireless adapter working, but i need really noddy instructions of how i go about doing this..

Any help appreciated..  ;)

Cheers
M

---

### Post by Seisen on 2007-04-26
This is what you are talking about,


[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

---

### Post by abouttogiveup on 2007-04-26
Thanks for that..   

I have given it a go, but im still not connected.  im not sure where i am going wrong now...
How can i test what is going wrong?  is there a file i should check...

I read that perhaps the key should be xxxx-xxxx-xx is that correct..  or is xxxxxxxxxx still ok
sorry
M

---

### Post by abouttogiveup on 2007-04-26
also..   does it assume WEP or WPA?

---

### Post by abouttogiveup on 2007-04-26
No flashing lights on the dongle...   any advice on this would be appreciated..

its the belkin F5D7040 Version 3001UK

---

### Post by Austin_KW on 2007-04-26
the 7050 v3xxx is the rt73 chipset. The is a native driver see this howto  [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by abouttogiveup on 2007-04-26
Austin...  many thanks, i'm making progress now.

if i do a rausb0 scan it finds the router..  gooodo..

sudo dhclient rausb0 ..  this makes the lights flash (first time thats happened)

but...

says

DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval X

a few times.. then

No DHCPOFFERS received...

any ideas?

Cheers
M

---

### Post by abouttogiveup on 2007-04-26
OK.. not entirely sure what happened as i thought i had typed it correctly before hand.. but..

i removed the WEP security and it connected
added the key back in .. and hey presto. it worked..

Thanks for your help austin.

---

### Post by Austin_KW on 2007-04-26
Glad it helped. But look into WPA encryption. Latest reports have tools to crack wep in 1 minute.

---

