---
title: "Apache in ubuntu ?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by MaaSTaaR on 2006-01-15
Hello ...

i am install Apache and PHP4 in my system , but i have problem , when i go to [http://localhost](http://localhost) it's not work , what is the sloution

---

### Post by npmeyer on 2006-01-15
I assume you are following the instructions  in the Ubuntu Starter Guide at [http://help.ubuntu.com/starterguide/C/faqguide-all.html#installapachehttpserver]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installapachehttpserver").

What happens when you go to [http://localhost/]("http://localhost/")?

---

### Post by MaaSTaaR on 2006-01-15
hi 

i am install it but ubuntu didn't show World Wide Web menu  , when i go to localhost after long time it's show this for my 

The connection has timed out

      

      
      
      

      
        
        

          

The server at localhost is taking too long to respond.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

---

### Post by npmeyer on 2006-01-15
When you say you couldn't find the "World Wide Web" menu, did you first open Synaptic (under System > Administration > Synaptic Package Manager)?  There should be a category called "World Wide Web" in the left panel.

If it's not there, be sure you followed the link in the starter guide (see the link in my earlier post) that said "Read How do I add Universe and Multiverse" (it's Step 1 in the instructions).  You might need to do that before the "World Wide Web" category shows up at all.

---

### Post by MaaSTaaR on 2006-01-15
hello ...

i am found World Wide Web category in Package Manager , but i didn't found it in applications list .

---

### Post by npmeyer on 2006-01-15
Once you select the World Wide Web category in the Package Manager, you should look back over in the right panel and see apache2.  If it's not there, try following the instructions to add the Universe and Multiverse repositories to Synaptic.  Here's a shortcut:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by MaaSTaaR on 2006-01-15
Hello ...

ok , i am found World Wide Web category in the Package Manager and apache2 is installed in my system , but the problem when i go to [http://localhost](http://localhost) it's don't work ?

---

### Post by npmeyer on 2006-01-15
Okay,

Try going to System > Administration > Services.  Check toward the bottom of the list to see if "Web server (apache2)" is on that list.  Is it checked?  If not, check it and try again.

If it is checked, or if checking it does not fix the problem, try going to [http://127.0.0.1]("http://127.0.0.1") instead of [http://localhost]("http://localhost").  Let me know if that works, and we'll take it from there.

---

### Post by MaaSTaaR on 2006-01-15
Hello ...

i am found Apache2 in service list and it's checked .

when i go to [http://127.0.0.1/](http://127.0.0.1/) the same problem show for me

---

### Post by hen3rz on 2006-01-15
Try un checking the service then re checking it.

The problem you are having is very strange. When i install apache2 all i did was:

```
sudo apt-get update
sudo apt-get install apache2
```

---

### Post by MaaSTaaR on 2006-01-15
hmmmmm , it's show for me new problem when i go to localhost , it's Firefox can't establish a connection to the server at localhost.

i don't know if i should make any setting before start ?

---

### Post by npmeyer on 2006-01-15
This is indeed a strange problem.  Have you installed a firewall (firestarter, shorewall, or something else) by any chance?  I can't imagine it would block access to your own server, but it might.

Also, try running the command

```
sudo ifconfig lo
```

and post the output here.

Thanks.

---

### Post by MaaSTaaR on 2006-01-15
Hello ...

i haven't installed a firewall , and the output of command :

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by MaaSTaaR on 2006-01-15
Hello ...

it's work fine now after open Network Setting , but the new problem i can't browse PHP files , FireFox try to download it for me ?

---

### Post by npmeyer on 2006-01-16
Yeah, it seems your loopback network interface wasn't running, which makes it impossible to reach any servers running on your own computer.

How did you install PHP?  Until you've installed PHP and configured Apache (which happens automatically when you install it with Synaptic but not when you download it from php.net) Firefox doesn't realize it's a page and will try to download it.

---

### Post by MaaSTaaR on 2006-01-16
hi ..

i am do like this 
"
sudo apt-get install php4
sudo /etc/init.d/apache2 restart
"

it's from [http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver) 

to install it

---

### Post by MaaSTaaR on 2006-01-16
up

---

### Post by hen3rz on 2006-01-17
Hi,

I would recommend installing it through synaptic as its much easier and is recommended in the Ubuntu Starter Guide 5.10. The guide at ubuntuguide.org is old and is for 5.04. Below is the link to the synaptic tutorial:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installphpapache]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installphpapache")

---

