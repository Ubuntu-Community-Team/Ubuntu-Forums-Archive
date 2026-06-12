---
title: "setup ?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by deadmnky on 2008-01-18
i have just built a desktop with an Asus m2a-vm hdmi motherboard and an amd 64x2 cpu i have installed a version of ubuntu 7.10 on the desktop but no internet connection it registers the cable internet when it is plugged in it receives packages a little at a time though.
my isp is comcast cable company 
i think i am using a lan net work connection
i have yet to set up any drivers from the mother board support cd due to i do not know how to go about it. i am thinking that may help i am not sure have never built a computer before and i dont know any one who has setup a desktop or laptop for that matter on linux from the get go so i have no one to help make sure it set up right. any suggestions on where to start looking and some reference material would be nice.

---

### Post by Dynaflow on 2008-01-18
Could you please be more specific on your hardware, what version of Ubuntu you're using (Ubuntu/Kubuntu/UbuntuStudio/etc.), if you're not getting any Internet connectivity at all or just a trickle, etc.?

---

### Post by deadmnky on 2008-01-18
ok i am just getting a trickle of internet activity. amd athalon dual core 6400+ black book edition. the mother board is an asus M2A-vm hdmi with 690g chipset socket am2. ati radeon x1250 integrated graphics card i have 2 gig ram. i have ubuntu 7.10 installed on a 300 gig hard drive. what more do you need to know i am new to computers and am not always sure what to type for info what do you need how do i find it if i dont know already.

---

### Post by IAmAnEvilTaco on 2008-01-18
internet connectivity first and foremost, do you have any windows pcs or apples in your house you can use as a frame of reference, to see if it's the linux and not your network?

in your taskbar, go to system, administration, network tools. select ping, then in the box enter 192.168.1.1 (assuming you didn't mess with your router's ip and it's all default) and tell us what kind of speeds you get. look for average ms and post that number.

If you've got a pc with windows, open a dos prompt and enter "ping 192.161.1.1" without quotation marks and compare the numbers. if they're near the same, it's the network. 

is wireless configured on your router? if so, for now turn it off and see if your speeds improve. if so, someone's probably leeching off of your wireless and killing your connection speeds.

this is a pretty broad question, getting the drivers to work. My biggest suggestion, personally, is to read as many of the help files as possible. familiarize yourself with the operating system a bit and deal with one problem at a time. internet speed is probably your most important issue, after that you can fine tune and make the rest of it work.

---

### Post by Dynaflow on 2008-01-18
In regards to that particular motherboard, this might interest you: [http://www.phoronix.com/forums/showthread.php?t=4301&page=2]("http://www.phoronix.com/forums/showthread.php?t=4301&page=2")

---

### Post by IAmAnEvilTaco on 2008-01-18
open the package manager and search for an mp3 decoder, and an mpg decoder, and install them. you'll thank me later.

---

### Post by deadmnky on 2008-01-18
thank you guys i will check and get back to you an those numbers i tried to ping some thing else with it and no dhcp was found. no wireless routers just putting the internet cord from one to the other for now. i am actually trying to set the desk top as my main computer and was trying to set it up to become more familiar with things as i am new to all of it. stopped using them when i left school and started back up. hate the conglomerate fascism of windows. i can match the pings with ubuntu studio i have on my laptop

---

### Post by deadmnky on 2008-01-18
> **IAmAnEvilTaco said:**
> open the package manager and search for an mp3 decoder, and an mpg decoder, and install them. you'll thank me later.

can i get them with out an internet connection running on the desk top.? i belive i have down loaded them on the laptop already

---

### Post by deadmnky on 2008-01-18
round trip time stats are what you are looking for correct?
the average time for both my laptop and my desktop are 0.00ms i dont know if that is right but they both said that on 5 request. with 5 packets transmitted and 0 received and 0% successful packages

and for an mp3 decoder i have libflac8 installed i could not find a mpg decoder as an available up date with no internet on the desktop

---

### Post by IAmAnEvilTaco on 2008-01-18
[http://packages.debian.org/gstreamer0.10-fluendo-mp3](http://packages.debian.org/gstreamer0.10-fluendo-mp3)


there's the mp3 decoder. copy it over to your desktop and open it, and it should just run and work.

mpg decoders seem to be a bit harder to find in debian packages. I'll do what I can. search for mpg debian package with google. vlc is good if you can find a debian package, but I can't find one that's just plug and play right now and I'm trying to find low-maintenance for you. you won't be able to run movies without it, but at least you'll have music.

---

### Post by IAmAnEvilTaco on 2008-01-18
hmmm..... 0% and 0 successful.


go to toast.net and take a speed test with picture and text and see what it tells you. post the results. looks like ping is broken right now.

[http://performance.toast.net/](http://performance.toast.net/)

shuttle and text is what you want, for this purpose. it'll give a benchmark. try it with both computers and post both results.

---

### Post by IAmAnEvilTaco on 2008-01-18
I've got to sleep, but I subscribed to this thread. I'll poke back in after I get off of work tomorrow, and hopefully have a few solutions for you.

good luck in the meantime. :)

---

### Post by deadmnky on 2008-01-18
i have vlc on my laptop how would i copy the files for my desk top i have a flash drive would that be enouhg space?
well thank you for the help so far.
the other thing i noticed in the terminal window on the laptop has my name@ host name 
the desktop goes my name@myname
could that effect it at all

i got the mp3 download but have yet to find the mpg down load. i will be able to get it all after i figure out the internet problem on the desktop

performance test via website was 754,929 bytes in 2.568 seconds from open hosting uk source on the laptop did not try it on the desktop since i can not use mozilla.
i forgot to mention any live cd i put in does not allow me to use mozilla either.

i found the google ping umber on four pings the avg time for the laptop was 77.7ms
the desktop transmitted the 4 pings but no time or response

---

### Post by deadmnky on 2008-01-18
this is my ifconfig message:


eth0      Link encap:Ethernet  HWaddr 00:1B:FC:1F:8F:84  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6720 (6.5 KB)  TX bytes:1368 (1.3 KB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by deadmnky on 2008-01-19
i dont really know what i did but it is working now thank you for all those who helped me get as far as i did.

---

