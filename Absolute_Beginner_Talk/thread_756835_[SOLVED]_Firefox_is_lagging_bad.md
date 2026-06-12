---
title: "[SOLVED] Firefox is lagging bad"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-04-16
So I am having an issue with Firefox.  It has become Slowfox overnight.  It has always been fast on the Verizon FIOS network, but this morning it is sooooo bad.   As I am typing this post it is still loading up!   There is a Vista machine in the house (Grrrr) and it is fine with the connection and it is running as fast as ever, so I know it is just me.  Kind of hard to brag about how good Ubuntu is over Vista when I can barely load a page and my sister can speed though the net.


HELP!

---

### Post by Inxsible on 2008-04-16
Try this```
killall firefox
``` Then start up firefox again

---

### Post by raoufathar on 2008-04-16
i am new in ubuntu forum. i want to post a topic/ thread. how do i do that....
can u tell me that. i am sorry to disturb this thread

---

### Post by OZFive on 2008-04-16
This is from a cold startup this morning so there are ot any Firefox processes going on other than what was started this morning.

Also I tried that in the terminal and it does nothing (I am kind of linux noob)

---

### Post by Inxsible on 2008-04-16
> **raoufathar said:**
> i am new in ubuntu forum. i want to post a topic/ thread. how do i do that....
can u tell me that. i am sorry to disturb this threadOn the main page under Absolute Beginners, look for a link called Make New Post

---

### Post by Inxsible on 2008-04-16
> **OZFive said:**
> This is from a cold startup this morning so there are ot any Firefox processes going on other than what was started this morning.

Also I tried that in the terminal and it does nothing (I am kind of linux noob)Do you have any other browsers installed?

Do the other browsers give you the same result ?

---

### Post by northern lights on 2008-04-16
Is it a network or a browser issue?

If you don't know which, have you...
...tried another browser?
...pinged some random domain/URL?
...checked out whether apt-get or aptitude are as slow?

---

### Post by philinux on 2008-04-16
Close firefox and then in a terminal use

firefox -safe-mode

See if that cures the problem. If so it's one of your addons.

---

### Post by diplomat.x on 2008-04-16
Try this, delete the ./mozilla folder from the /home/USERNAME directory. (ctrl+h to show hidden files).
Restart firefox, it would be all new and clean.

PS: all ur bookmarks, options, history will be deleted.

---

### Post by northern lights on 2008-04-16
> **diplomat.x said:**
> Try this, delete the ./mozilla folder from the /home/USERNAME directory. (ctrl+h to show hidden files).


ehm, this is beyond the shadow of a doubt the better option:

> **philinux said:**
> Close firefox and then in a terminal use

firefox -safe-mode

---

### Post by Tom--d on 2008-04-16
> **diplomat.x said:**
> Try this, delete the ./mozilla folder from the /home/USERNAME directory. (ctrl+h to show hidden files).
Restart firefox, it would be all new and clean.

PS: all ur bookmarks, options, history will be deleted.


Dont delete it. Just re name it to something like Firefox and then if that cures it. Then it might be an add on doing it. And once its sorted, you can just rename it .mozilla and all your bookmarks and everything will be there again.

Clear your cache and history as well. See if that helps.

---

### Post by OZFive on 2008-04-16
Thank you to all for the advice.  

I am happy to report that the issue has been resolved and that Firefox is innocent of all charges and I want to make a public apology to the worthy browser and offer my hand in friendhsip so that we might once again surf together in harmony with all the internet.

I do however blame my nephew and his tendency to get into a particular closet that the WiFi transmitter is located in and knocking it down and covering it up with a bunch of clothes and junk!  

Thanks again all!

---

### Post by northern lights on 2008-04-16
> **OZFive said:**
> I do however blame my nephew and his tendency to get into a particular closet that the WiFi transmitter is located in and knocking it down and covering it up with a bunch of clothes and junk!
My niece did the same thing few years back - too funny.

---

