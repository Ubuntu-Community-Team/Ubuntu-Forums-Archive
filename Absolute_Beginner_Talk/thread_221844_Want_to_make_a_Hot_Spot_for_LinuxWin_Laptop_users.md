---
title: "Want to make a Hot Spot for Linux/Win Laptop users"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by fonggiding on 2006-07-24
Due to my unbounding newbieness I will try to ask this as simple as possible.
   I own a desktop with Dapper/Xp and will be moving. At my new place I will have internet but would like to use wireless internet and have a network for sharing files(samba?) between wireless Linux/XP laptops(firends family etc.).
   What do I need? How do I set this up? Many ISP's here only allow one IP(bunch of facist Japanese) will that be a problem? Can I still use my Desktop(which would be broadcasting the internet) normally while others access the internet? Are there any other factors that I haven't considered?
   If there is a pre existing link(which I couldn't find) then please re-direct me there.
   Thank you in advanced.:KS

---

### Post by it.henrik on 2006-07-24
Ok what you want is something called a NAT. It works like this: On one side of the NAT-box you have an entire network and on the other side of the NAT-box you have internet. Your NAT-box gets one IP adress from your ISP and then every computer in your network behind the NAT-box talks to the rest of internet through the NAT-box.

Read more here [http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

There are cheap router-NAT-wifi-access points combos from ex D-Link and Netgear, ask in a store in the country where you live and they can help you more. 

BTW your desktop does not broadcast the internet ;) I guess what you mean is that other computers are connected to internet through you computer. With a device like the one I described above you do not need to have all the other computers on your network connect to internet through your computer. Instead all other computers on your local network connects through the router/NAT-box.

Good luck with the facist japanese ;) (I am just kidding here .. I have very nice japanese friends of my own and I love visiting Japan ;) )

---

### Post by fonggiding on 2006-07-24
WOW! Thanks!
So I need to aquire a router-NAT-wifi-access point-box and I'll be up and running ? Then how would I set up a network where I could share files and such?

All praise to the awsome Ubuntu community, and to it.henrik:KS 

Oh and P.S. I was in my local Bookstore(local=Tokyo) and I saw a Linux magazine and the cover was Dapper! Go Ubuntu!

---

### Post by it.henrik on 2006-07-24
One example of what you may want might be this. 

[http://www.dlink.com/products/?sec=1&pid=385](http://www.dlink.com/products/?sec=1&pid=385)

Since you ppl in Japan usually are leaps and bounds ahead the rest of us when it comes to technology I guess you can find some cooler stuff in some local store. 

The most common way of sharing files between computers on your local network would be using SAMBA. SAMBA is the "linux version" of windows networking.

There are some very easy ways of sharing files with SAMBA and there are some more secure ways of sharing files with samba :)

One easy way in ubuntu is SYSTEM -> ADMINISTRATION -> SHARED FOLDERS and then add the folders you want to share.

A more comprehensive way would be like this

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

or like this

[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

You wont be the first one to get stuck sharing files with SAMBA so there will be TONS of information about it in the forums :)

---

### Post by it.henrik on 2006-07-24
> **fonggiding said:**
> WOW! Thanks!
All praise to the awsome Ubuntu community, and to it.henrik:KS 


Thnx a lot :) The main reason why I am stuck with Ubuntu is the great attitude in community. It was thnx to the ubuntuforums I finaly managed to get rid of windows and now I am trying to give something back to everyone else that ask for help.

---

### Post by fonggiding on 2006-07-24
Well thanks again. I'll study up so I can be knowledgeable enough to give back and more!

---

