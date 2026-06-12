---
title: "Bob The Builder: The beginners story"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by nijinsky on 2005-12-06
Hi All.

OK call me presumptious, but I think that a thread that shows how to get Ubuntu up and running (from a complete newbies point of view) would be good. I mean from a perspective where someone that has not even seen ubuntu and wanted to try Linux. IE Me.

So here is my story.
I have winXP at home on a fast machine. I have an IBM laptop (nice) that I lug around. I need to keep windows on that for travelling. I have been using it in work and am getting a bit fed up cycling in and out with this on my back.

I bought an AthlonXP2000, 256Mb RAM, 20Gb HD, 64Mb graphics with TV out from ebay. It has win XP on it, but I'm fed up shelling out my own hard earned money to keep machines up and running EG Diskeeper. I don't mind paying for my own machines but not one for work. My work cant supply me with one because I'm a scientist on a grant contract and the funding charity only allow certain things to be bought. 

The roadmap would be 
Burning and installling Ubuntu (with links to helpfull threads)
Getting WIFI up (with hardware recommendations)
Installing apps that get me the basics.


So if you think it is useful... I will add my story here to help newbies.

If this is not allowed or has been covered ad-nauseum then I'll not post it.

END OF DAY 1

DAY2
OK I downloaded the ISO from the ubuntu downloads page and burned it onto a CD.
Put this into the machine and rebooted. The installation process worked until I had to install the kernel. The routine stopped.

So I posted elswhere and got the advice to reburn at a slower rate. I used the "recordNow CD burner SW that sony provide with their DVDR's. In the options there is a dropdown that says
1) burn at maximum speed
2) burn fast
3 burn at slowest speed

I chose option 3. I was in no hurry since my builder was fixing the shower fan. A 20 minute job in "builder time"

1 hour later i left with the new CD. :-)

I inserted the CD and the install worked perfectly. NO partitioning needed, everything worked perfectly. I now have a sys up and running painlessly. :-)

On installation I was asked if I wanrted to configure networking etc and I chose the bottom option. I think it was "configure later". 

The next thing would be to get wireless up and running. I have a Belkin USB F5D7050 stick and Ubuntu does not recognise it. I don't have a wired network to download the drivers etc, so I'll post later on how I got round this.

ATB
Bob

---

### Post by sethmahoney on 2005-12-06
Add your story, by all means!

I think one of the main reasons we don't have something like that is that the problems a person is likely to face vary radically depending on the hardware they're using, so we might not get so far once we get past actually installing Ubuntu.  But the more people who share their experience getting certain pieces of hardware working, the more likely someone in the future will find the info they need, so by all means, tell us what you did to get Ubuntu working the way you wanted it to!

---

### Post by editrix on 2005-12-08
[QUOTE=sethmahoney]Add your story, by all means!

I think one of the main reasons we don't have something like that is that the problems a person is likely to face vary radically depending on the hardware they're using...[/QUOTE]

I never documented all my steps, and I'm still not doing everything I want to in Ubuntu, but the forum's bugging me to post something, so here goes :-)

Actually, I think documentating one's steps is an excellent idea, especially if something goes wrong down the road someplace. I'd recommend a ring binder, so you can either handwrite, or when you find a useful website, print it out.

I'd also recommend prioritizing your needs. Get one problem solved before going on to the next. It's way too easy to get sidetracked, with all the new stuff to learn. One thing I have done is bookmarked every thread that I thought might come in handy when I get to that stage, then I don't have to go searching that problem again.

And the Ubuntu forums are marvellous. I look forward to the day when I can answer questions, instead of asking all the time.

---

### Post by nijinsky on 2005-12-21
OK Update time. Still not managed to get my wifi usb key working. No internet on this machine is a bummer. I ended up having download everything on widows and transfer with a memory key to compile the drivers. I can see the .ko file and it is apparently in the right place, however, nothing is listed in the network.

I thought of moving to linux to save all the hastles with windows, however, I'm having second thoughts. If it is that dificuly to get wifi working (essential for me) then I may have to change my mind. Why cant there be a simple app that installs the drivers from the most popular wifi usb keys or even have them included out the box ibinning the belkin usb (cant remember exactly where I am because I've had to install so much to get a simple driver working) and having a try with a buffalo usb key.

Cheers
Bob

---

### Post by Rinzwind on 2005-12-21
Heya,

Does the command **lsusb** list your device when it's plugged in?
And what's important: did you have the USB wireless in your system when you installed it?
Do you know about **ndiswrapper**?

Oh and have you ever seen this website:
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

> **Easy-Peasy Wireless w/ Ubuntu (Debian) Linux**
In this brief blog entry I will reference the steps it takes to provide a wireless network connection, that is function on both Linux 2.6 and Windows, using a Belkin Wireless G USB Network Adapter. This is basically my first attempt to even use wireless networking yet everything is very clean cut (for the most part).

It's about wifi, belkin, wireless, usb AND ubuntu ;)
Must be ALL you need :D He got it going. So can you!!!! We all have faith :)

---

### Post by nijinsky on 2005-12-21
[QUOTE=Rinzwind]Heya,

Does the command **lsusb** list your device when it's plugged in?
And what's important: did you have the USB wireless in your system when you installed it?
Do you know about **ndiswrapper**?

Oh and have you ever seen this website:
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)



It's about wifi, belkin, wireless, usb AND ubuntu ;)
Must be ALL you need :D He got it going. So can you!!!! We all have faith :)[/QUOTE]


Hi There

Yep I was ranting a bit :-)
I've got a belkin key and a buggalo 54g key. I'll try hte belkin again with this method.

More soon

Bob

---

### Post by nijinsky on 2005-12-21
[QUOTE=Rinzwind]Heya,

Does the command **lsusb** list your device when it's plugged in?
And what's important: did you have the USB wireless in your system when you installed it?
Do you know about **ndiswrapper**?

Oh and have you ever seen this website:
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)



It's about wifi, belkin, wireless, usb AND ubuntu ;)
Must be ALL you need :D He got it going. So can you!!!! We all have faith :)[/QUOTE]


OK Update number 2. I followed this guide. Absolutely great and everythig ran perfectly. Except I didn't get interenet access.

I restarted the machien and it stalled at startup. So I unpluged the usb key and it then started to boot into linux. When I unplugged it said "Failed to initialise the device"

OK So now I'm in Linux and I pluged in the usb key and typed
suso ifup wlan0

I got a lot of text. Too much to type BUT

Line 1
there is already a pid file /var/run

<sound of screethcing vinyl>
Hold on....... I have just been typing and something happened on the screen...
<\sound of screethcing vinyl>


<homer simpson>
WOOOOOOO HOOOOOOOO
<\homer simpson>



It is working I now have internet access.

Now I'm off to try something else. When I installed the buffalo card on my laptop to type as I DIAGNOSE I noticed there was a line rt2500 

Does this use the same driver.

If not, can I simply repeat the scenario with the buffalo drivers?

I have a slight problem now. I cant access any sites outside of our network. But that is another thread and another day.

Cheers
Bob

---

### Post by Rinzwind on 2005-12-21
We solved your wireless in under 1 hour :D

YAY FOR UBUNTU!

:)

And I bet it'll work the same for EVERY wireless usb.

---

### Post by nijinsky on 2005-12-21
[QUOTE=Rinzwind]We solved your wireless in under 1 hour :D

YAY FOR UBUNTU!

:)

And I bet it'll work the same for EVERY wireless usb.[/QUOTE]

Yep Rinzwind... Thanks for the help. The perfect day so far. Off to buy my wife a christmas present (that she will naturally exchange) :-).......

More on the buffalo later.

cheers
bob: sunny Scotland

---

### Post by nijinsky on 2005-12-22
Update 3 

POSTING FROM UBUNTU VIA WIFI IN A WINDOWS WORLD. Excuse the caps I'm sooooo excited. (my wife's translation is "I'm really sad")

Well I could not connect outside of our intranet, however, I had the proxy set as a defined site rather than auto (IE A script).

All working now.

Cheers
Bob:D

---

