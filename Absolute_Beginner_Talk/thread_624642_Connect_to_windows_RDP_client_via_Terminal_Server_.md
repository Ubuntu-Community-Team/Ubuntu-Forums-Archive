---
title: "Connect to windows RDP client via Terminal Server &amp; access local printer???"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-11-27
we have a windows rdp server at work and i can access it using ubuntu quite nicely and everything runs fine.

however i would like to be able to print documents to my local printer from ubuntu.
i can do it locally via my windows xp machine if i rdp to work so i do have permissions to do so.

is it also possible when i connct to wkr i can copy data to my local hdd as well.this would be handy too. i can do it from my xp machine, but again i can not see options to let me do it in Ubuntu.

using 7.04 & 7.10 (7.04 laptop , 7.10 desktop)

thanks

---

### Post by gigaferz on 2007-11-28
hello, i was working a while ago  using rdc to the main office, 

I noticed when i logged in with xp, i could see all the printers on the network.
 and with ubuntu i didnt see anything at all. I think windows server had to be configured to work with ubuntu. I never asked to the admin , cause they might freak out cause i wasnt using the all mighty xp. and besides the could question why are you using something that doesnt even work, lol,

use the cups configuration page to set your printer so you can share it over the network, [http://www.cups.org/documentation.php/network.html](http://www.cups.org/documentation.php/network.html) now that i remember everytime i tried it it froze, and i was at work, so never really tried fixing it, hopefully it will work for you.

---

