---
title: "Apache2 removal/re-install issues"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by chrismacp on 2006-03-27
Hello, I have only started using ubuntu (and linux for that matter) and am a little stuck installing apache2.

I originally installed apache2 using apt-get but was getting confused where to edit stuff in the apache config files as I'm used to the Windoze version. 

So...I then removed the apache 2 installation using apt-get remove etc. 

I then (this is where I think I went wrong) thought the removal had failed as the /etc/apache2 folder still existed, and I deleted it using the delete key and emptied the waste basket.

Now when I try to install apache2 again using apt-get the /etc/apache2 folder doesn't get remade and when I try to start apache it says:

'apache2: could not open document config file /etc/apache2/apache2.conf
                                                                         [fail]'

Can anybody suggest what to do next?

---

### Post by chrismacp on 2006-03-27
I managed to solve the problem. I'm not sure why I had to do all this though.

I used Synaptic to uninstall apache2

I then used : apt-get remove apache2 

and then did : apt-get clean apache 2 a couple of times


That seemed to do the trick and it then installed and started properly.


I'm probably just doing things wrong, but starting to get to grips with linux and I like it a lot. Now if I can just get eclipse to install plugins correctly......

---

