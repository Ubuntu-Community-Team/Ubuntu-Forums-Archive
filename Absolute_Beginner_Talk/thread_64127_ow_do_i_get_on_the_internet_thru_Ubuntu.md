---
title: "ow do i get on the internet thru Ubuntu?"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by sooperspook on 2005-09-10
Just like the title says. I am comletely new to Ubuntu an dLinux in general so right now im lost. I use a D-link adsl modem which , as far as i can tell, is working fine.I start firefox, type in a address and.... nothing. I get told that the address cant be found.

is there something i should hav edone beforehand? what did i miss?

any help will be appreciated. thanks

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=sooperspook]Just like the title says. I am comletely new to Ubuntu an dLinux in general so right now im lost. I use a D-link adsl modem which , as far as i can tell, is working fine.I start firefox, type in a address and.... nothing. I get told that the address cant be found.

is there something i should hav edone beforehand? what did i miss?

any help will be appreciated. thanks[/QUOTE]
The following will let us know if you have a general connectivity problem.  Open a terminal and type the following commands:
```

$ ifconfig -a
$ route

``` 
and post the output back here.  The first command will show how your network cards are setup.  The second will show your routing information.

Also, in the terminal try:
```

$ ping 216.109.117.108

``` 
If that seems to work, you may just need to configure your DNS settings.

Is your PC directly connected to the modem, or are you connected to a router or hub?

---

### Post by heimo on 2005-09-10
Is this ADSL modem USB or do you connect to it using ethernet network card? 

You can check your network configuration in System->Administration->Networking.

You could also open terminal and check that DNS is working correctly:
 ```
dig ubuntu.com
``` 
If it's working correctly you will get several lines and one is like this:
 > ubuntu.com.             1800    IN      A       82.211.81.130 

Now you can try to ping this address, try:
 ```
ping 82.211.81.130
``` 
You should see lines like this:
 > 64 bytes from 82.211.81.130: icmp_seq=2 ttl=51 time=563 ms 
(break with CTRL+C)

Please post your findings and more information so we can get better understanding of your situation. (I won't be able to post today, but others will.)

---

### Post by sooperspook on 2005-09-10
wow! That was a fast response. in fact, several of them!  :) 

Great to see us new fellas have such a helpful community to turn to. 

I'll try your suggestions soon and i 'll let you know what happens.

Thanks again!

---

### Post by sooperspook on 2005-09-18
Well dont i feel a right twit? The modem wasnt configured! D'oh!  ](*,) Heh. I'll let everyone know how it goes after...

---

### Post by sooperspook on 2005-09-18
Well i have a new problem now. How do i configure the modem? I think a package is missing. 
I have a dual boot pc and in windows it says its:
 ISDN channel D-link DSL-200 USB ADSL modem  
on 64k digital line

where can i find instructions on how to configure it?

---

### Post by heimo on 2005-09-18
So it's this device?
[http://www.dlink.com.au/products/broadband/dsl200/](http://www.dlink.com.au/products/broadband/dsl200/)

Sorry, but I have no experience on USB ADSL modems, I avoid these devices - I prefer using network devices that connect to computer using ethernet.

Do you see your ADSL modem under System->Administration->Networking? Check properties.

---

### Post by sooperspook on 2005-09-19
yup! thats the one. Anyone know of a good easy to read resource i can use?

---

### Post by heimo on 2005-09-19
For most tasks, [http://wiki.ubuntu.com](http://wiki.ubuntu.com) is great place to start. However I didn't find page for configuring USB ADSL modem. There are probably lots of information on these forums. Do you see that device under System->Administration->Networking?

---

### Post by happychap on 2005-09-21
Hi,

I'm a noob too - have just installed Ubuntu and now finding my way around.

Go to:
[http://users.tpg.com.au/johnd/dsl200.html](http://users.tpg.com.au/johnd/dsl200.html)
and read up what has been done here. It may help. I have not used it yet - only finished the basic install today - but it is quite detailed.

---

### Post by az on 2005-09-21
You shoudl not have to compile anything:

Can you download this elsewhere and transfer it to you box?


[http://packages.ubuntu.com/hoary/net/eciadsl](http://packages.ubuntu.com/hoary/net/eciadsl)


sudo dpkg -i eciadsl*.deb
sudo apt-get -f install

I do not know how much this package does.  I suspect you need to install it, run the eciadsl-config-tk program and then make a pppoe connection by running pppoeconf...


sudo eciadsl-config-tk

sudo pppoeconf

---

