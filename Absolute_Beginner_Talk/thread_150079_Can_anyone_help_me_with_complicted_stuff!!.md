---
title: "Can anyone help me with complicted stuff??!!"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by clareb on 2006-03-25
Sorry about the title but this is so over my head I don't even know how to describe it!
I've been trying for days to get my Inventel UR045G wireless usb adaptor to work, I managed to get Windows Wireless Drivers in System>Admin but none of the drivers from the modem install CD are working. I've read the wiki, searched the forums, emailed everyone on the planet and I've finally tracked down this site

[http://jbnote.free.fr/prism54usb/index.html](http://jbnote.free.fr/prism54usb/index.html)

If I understand correctly, they've compiled something (that's as technical as I get) that should get my adaptor running (crawling would be good at this point). Trouble is, I get totally lost at the bit about firmware. I know I have a softmac version 2 usb device with chipset GW3887 (not on the sourcefourge list) and I've downloaded the firmware to my desktop but when it says in the instructions:

 copy it to /usr/lib/hotplug/firmware/isl3887usb_bare.

I haven't a clue what to do. If anyone out there can help me I'd really appreciate it. You've no idea how determined I am not to go back to m$, and how much I have actually learned in the last week.
Thanks in advance

---

### Post by John.Michael.Kane on 2006-03-25
You can try Ndiswrapper read here [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by clareb on 2006-03-25
Thanks for getting back to me. I have been through that but none of the drivers I have work. When I install them I'm told 'hardware present - no'. I can't seem to get the drivers I need, but I thought the prism 54 project could help me with that - I just can't follow the instructions on the page. Does anyone know what
 
copy it to /usr/lib/hotplug/firmware/isl3887usb_bare.

means? Please?

---

### Post by clareb on 2006-03-25
Ok, I figured out that  
"/usr/lib/hotplug/firmware/isl3887usb_bare"
is a folder in my file system, I get to
"/usr/lib/hotplug/firmware"
and it's empty and tells me I don't have permission to write to it (which seems a bit cheeky to me ;) )

Anyone have a clue what I should do? Give up and go back to wind**slow[B]s**[/B]?

---

### Post by clareb on 2006-03-25
Ok, I figured out that  
"/usr/lib/hotplug/firmware/isl3887usb_bare"
is a folder in my file system, I get to
"/usr/lib/hotplug/firmware"
and it's empty and tells me I don't have permission to write to it (which seems a bit cheeky to me ;) )

Anyone have a clue what I should do? Give up and go back to wind**slow[B]s**[/B]?

---

### Post by mips on 2006-03-25
sudo might help

---

### Post by clareb on 2006-03-25
Ta, mips. I know sudo is a command but I'm not sure how to use it here, does anyone have any ideas about all this, or know anything about Prism 54?

---

### Post by Paul M on 2006-03-25
sudo command

e.g. 

sudo gedit 

will start gedit as root (after you've been prompted for password).

---

### Post by clareb on 2006-03-25
Sorry, don't  'gedit'. I'm not sure how that helps me copy my file. I don't like to sound stupid, I just can't help it. :mrgreen:

---

### Post by nalmeth on 2006-03-25
I really hesitate to link this to you, but if you're really desperate, you could look into this. Linuxant is a company that apparently makes drivers for linux, at a cost. :rolleyes:
Basically, you sign up, get 30 days free, and pay $20 for a lifetime membership. I think it is a really stupid idea to pay for drivers that you ALREADY HAVE PAID for, but if you're willing this might work for you.

[http://www.linuxant.com/driverloader/?PHPSESSID=ce4b52a44f1268b7ec1192b958ee0e2a]("http://www.linuxant.com/driverloader/?PHPSESSID=ce4b52a44f1268b7ec1192b958ee0e2a")

I really suggest trying to go another way, but hopefully this will give you a last resort above going back to windows. keep pluggin away!

EDIT: If you just need to copy a file, you could do it this way:
(in terminal)
sudo cp /where/the/file/is/now /where/you/need/it/now

'now' being the file itself

---

### Post by clareb on 2006-03-25
Thanks for that. I did try driverloader (the free trial - if I'm paying for anything it'll be a wireless card to replace this flippin' thing). Anyway I went through the whole installation process but when I got to configuration, I had to run a command to set up a password and the terminal just kept telling me permission denied. I emailed their support but so far nada..
Everywhere I go there are dead ends. ](*,)

---

### Post by nalmeth on 2006-03-25
Run the driver loader (or whatever command you're told to) with sudo in front of it.
If you're ever getting "permission denied" sudo is what gives you those priviledges.
I know it is very frustrating, but the all around security you're getting is way more worth it. 
Keep at it
It sucks when you find out you've got unsupported hardware hey? I would end up just buying a new card myself, just to stick it to these companies that refuse to provide non-windows support for their devices. But what do you know when you first buy the thing right? It's just supposed to work dammit!

---

### Post by gr0kzer0 on 2006-03-25
When u get told u dont have permission to do something, u need to put the word 'sudo' in front of the command yr trying to run. The computer will then ask for yr password. U type it in, hit enter, and all being well, it'll run the command

---

### Post by clareb on 2006-03-25
You guys are great for explaining all this stuff to me. If I actually get this thing to work you'll be great x 1,000,000. I'm going back to the linuxant site to see if I have any luck now.

---

### Post by clareb on 2006-03-25
IT'S WORKING, IT'S WORKING IT'S WORKING!!!!!!!!!!!!!!!!!!!!!!!!!:mrgreen: 

I got the driverloader thing up and working, eventually, then I fiddled with the WEP key for half an hour, did some rebooting and hey presto, I'm wireless!!! Mind you, linuxant are going to want some cash off me in a month, aren't they? Nevermind, I'll figure something else out by then...

Thanks to everyone who helped me. :-D

---

### Post by nalmeth on 2006-03-26
Great work clareb 
$20 isn't really unreasonable an amount, but it's still crappy you should have to pay again to get your device working.
I've heard those USB wireless devices are quite good though, so it may be worth it after all!
Feels great when you figure it out though hey?

---

### Post by clareb on 2006-03-26
Felt so good I had to do a very silly dance..:mrgreen: 
I'm not even sure if I could pay the $20 - I'm in the UK and don't use credit cards. I'm going to look into the Prism54 project, see if I can figure that out. 
Thanks again for all your help.

---

