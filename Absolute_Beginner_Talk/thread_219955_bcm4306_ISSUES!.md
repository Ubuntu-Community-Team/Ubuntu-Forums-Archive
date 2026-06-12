---
title: "bcm4306 ISSUES!"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by ubun00b on 2006-07-20
Hello everyone...  As the name suggests i am the absolute n00b on Ubuntu or anything linux.  What i'm having a problem with has to do with wireless.  I've follwed the directions on this link [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174) and the card is recognized in network manager but will not connect.  I've stripped off all my security settings and still nothing.  To make matters worse, i dont even know how to get the thing to show me it's mac address!  The card is a broadcom 4306 running on an HP zx5000 series laptop.  Any suggestions would be very helpful.  Thanks!

---

### Post by mbrang00 on 2006-07-20
Your not alone my friend, I too have a 4306 in my dell inspirion 9100.....Like yours it is reconized, just not working. I have not disabled all of the wep setting on my router yet, because i know my wife will give me heck if she goes without internet
....


as i said, you are not alone....

Someone please help us.

Is there a tool that will let us see the SSID broadcast?

Noonbies R us

Im going to try this link:
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=network+manager](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=network+manager)


Ill let you know what happens

---

### Post by ubun00b on 2006-07-20
I tried using the ndiswrapper method and that just completely fooked up my wireless.  When i initially installed 6.06 the card was recognized but i'd have to activate it manually each time i started up which served no purpose anyways since when after i started up it wouldnt connect to anything.  

To summarize, ndiswrapper hurt more than helped.  But i could have easily dorked up the instructions and created my own disaster.  Matter of fact, i just reloaded 6.06 last night since i couldn't figure out what i needed to undo to fix it.  

I've been reading a few posts and digging.  Try using this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

it hasn't worked for me so far, but maybe it'll bring you better luck.

also, when i ran

gedit /etc/network/interfaces

i noticed it was still holding my essid and the wep key i'd entered earlier.  I'm going to copy/paste it to a text file and delete it out of there to see if it will iwlist scan and pick up my AP.

---

### Post by ubun00b on 2006-07-20
Ok, so i deleted the essid and the wep key out of /etc/network/interfaces file and saved it.  Now when i run iwlist scan, it picks up my AP essid "appears" to connect for a minute then drops off.  I'm now trying to decipher this step:

VERY IMPORTANT: MOST PEOPLE NEED TO USE THE FOLLOWING COMMAND TO GET CONNECTED

 sudo iwconfig ethX rate 11M 

You can add this to you /etc/network/interfaces file to get connected at startup. Like so:

iface eth1 inet dhcp
     pre-up iwconfig eth1 rate 11M

Alternatively just add "rate 11M" to /etc/network/interfaces like this example of an 802.11b WEP network:

iface eth1 inet dhcp
wireless-rate 11M
wireless-essid My network
wireless-key 1234-5678-9abc-def0-1234-5678-9a

You might also need to add this to associate your wifi card automatically:

pre-up ifconfig eth1 up


I'll keep you posted on if i get a positive result.  BTW, i put the wrong version of my card in the original post, its actually a broadcom 4303, but i don't think it really makes a difference.

---

### Post by sread on 2006-07-20
Hi, I just went through the same process you are a few days ago. What worked for me (I have a 4306) was to install the firmware as the guide you're following says, and then stop at the point "VERY IMPORTANT..." 

I then installed network-manager (a nice program for laptops).

Then, following advice in another thread, I edited my /etc/network/interfaces file and commented out (#) every line except

auto lo
iface lo inet loopback

and voila! Network-manager took care of the rest. 
Hope this helps.
-Stuart

---

### Post by ubun00b on 2006-07-20
so far i can follow your directions up until the part where you mention editing the interfaces file.  I know how to edit it, i just am not sure as to what i need to edit.  Can you post a copy of yours in here?  Thanks!

---

### Post by mbrang00 on 2006-07-21
Im going to work on this some more when i get home from work today...I had to s step away from it last night, i was getting a little two twitchy, not to mention when my keybord on the desktop stopped working, i got a little PO'ed.



Id like to find this "Network Manager" that you are talking about. Im just so new to this i dont know where to find it or how to install it once i do find it. Is that where Yum comes in?
All the new terminology is what is makes switching to linux hard. I think it will be ok once i get my hands dirty.

Any help is welcomed and greatly appreciated.

On a side note: I started playing around with Fedora and did a little reading, everyone pointed to Ubuntu saying it was a somewhat a better platform to learn on. I agree so far. At least Ubuntu reconized the card.

:)

Mike

---

### Post by ubun00b on 2006-07-21
I agree, i'm cutting my teeth on linux using ubuntu.  For the network manager, you can get it via command prompt:

sudo apt-get network-manager-gnome

I think that should get it for you.  But if you installed the latest version of Dapper Drake, it should have come bundled on the install disc.  At least i think mine did.  If you want to check it's under administration -> networking.  Unless this isn't network manager...

---

### Post by sread on 2006-07-21
unbun00b:
Here's part of mine:

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
```
etc.

Notice how # is in front of all the other lines, that means that the line will be ignored.

mbrang00:
the NetworkManger is under Add/Remove Programs, under the category Internet. It's *not* the same as the System/Administration/Networking panel. That panel will be disabled by NetworkManager.

Note about network manager, it only connects on login (as far as I've been able to see so far), so if you need internet access to your box on boot, this won't work for you. (If anyone knows better, please feel free to correct/PM me :D)

-Stuart

---

### Post by mbrang00 on 2006-07-21
I mananaged to goof stuff up yesterday so i did a re-load of the OS.....Im not giving up though. I found the apps for the network manager, i didnt realize there was stuff to download there....installing now


Im going to do my best to tackle this thing tonight

---

### Post by mssever on 2006-07-21
I too have an HP laptop with the same card, and beat my head against the wall trying to get it working. For me, ndiswrapper didn't help at all. I posted step-by-step what I did to get my card working [here]("http://ubuntuforums.org/showpost.php?p=1251630&postcount=2"). Hope this helps.

---

### Post by mbrang00 on 2006-07-21
I am sitting here in my living room, with absolutly no cords hooked up to my computer besides the cord for my mouse...


Needless to say I got it working, It is only connecting at 11Mbs But its working. Im not going to complain. I followed the how to posted at the beginning of this thread and got it to work.

Its all a big blur to me still, I dont really know what happend, but it did. If your still haveing trouble, I would do a fresh install and do it all over agian. It takes less than an hour including all of the updates. I have installed ubuntu 5 times in the last 4 days.... I hope im good for a while. I dont want to go through this agian.


Keep us posted on your progress, we are routing for you:eek:

---

### Post by ubun00b on 2006-07-22
still no luck with getting this thing working, but i still have options.  Sooner or later its gotta work right?

---

### Post by ubun00b on 2006-07-22
well, as a status update, i can get it to recognize the Wireless Nework in Network-Manager, but it won't connect.

---

