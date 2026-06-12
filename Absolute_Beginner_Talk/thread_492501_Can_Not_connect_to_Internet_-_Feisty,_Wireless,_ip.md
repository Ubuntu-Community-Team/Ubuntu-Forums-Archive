---
title: "Can Not connect to Internet - Feisty, Wireless, ipconfig what?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by letmein on 2007-07-04
Hello, 
Firstly, i have no idea what im doing...at least lets assume that when you give your suggestions;

I 'had' a strong internet connection until i tried to set up port forwarding on my linksys router, i have 2 computers, desktop and laptop.  After 'setting up' the port forwarding (and unsetting it up), im unable to connect my laptop (wireless or wired) to the internet.  The desktop is live and accessing the internet no problem...but my laptop seems to have gone nuts.

ifconfig shows and eth1 and an eth1:avah....what the heck is avah?
My ip address for eth1 avah, is shown as: 169.254.255.255..."you'll never get online with that address says the internet tech support guy"..."we dont support linux" he adds, when i asked how do i reset it or release & renew it.  Its DHCP anyways, so not sure why im getting an address that can't connect...anyway, hoping someone out there knows what the issue is, or at least can point me (in english) on how to get more information or post some hints...or inform me how to get additional information that you might need to get me connected again

---

### Post by ubuntu.daemon on 2007-07-04
hrm i dont know why your laptop would have gone bonkers bc of ipforwarding  but try taking it off and see if you get internet again.  As for the avah daemon, it basically creates an ip for you so your pc boots up faster as far as i understand, then when you connect to another network wired or wireless you get an actual ip.  you sure what you set up what ip fowarding?  not block addresses?? =P  Try posting this in the wireless forums as well and see if you get an answer, ill try looking elsewheer to see if i can find your booboo lol

:popcorn:

---

### Post by letmein on 2007-07-04
I think i found the 'boo boo', while i was in the router configuration i changed DHCP to Static IP.  Then I had my laptop set up for DHCP, while the router was still in Static IP...oh boy, the crazy things we do :-)

Anyway, that pretty much solves my connectivity issue, but im still in the dark on the port forwarding...ill just research it to death and then give it a try in a week, thx for you time, hope my idiotic-ness helps someone else.

---

### Post by ubuntu.daemon on 2007-07-04
lol the port fowarding is pretty easy, i have a linksys myself, select the port i would usually do say like 5326 - 5326 for azuerus then foward it to your computers ip, but thing is your computer might not always get that same ip, so you might wanna set a static ip for you mac address, anyways when you figure out what you wanna do you just open those ports on your pc/laptop via firestarter

---

