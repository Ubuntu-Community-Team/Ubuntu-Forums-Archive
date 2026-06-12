---
title: "cannot see network manager"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by poobalanc on 2008-03-23
:confused:

good day!

i have install ubuntu 7.10 ( gutsy) in my amd64 bit notebook. in process of learning. i have been using this for past one month. 

suddenly, i couldnt see network manager, ( it was working fine) im not sure how it disappear. i have check with add/remove and the manager is installed. but i couldnt find the path of the software. and how to enable it back to my task manager. 

or do we have alternatif way to choose/listdown wireless access point?

please help. thank you.

---

### Post by smartboyathome on 2008-03-23
Try doing alt+f2 then running nm-applet, if the applet doesn't show up then try running it from a terminal and see if that gives you any errors. :)

---

### Post by moephan on 2008-03-23
If it's installed, you should be able to bring it up from terminal:
```

sudo network-admin 

```

Not sure why it would disappear from your menu though

HTH

Cheers, Rick

---

### Post by poobalanc on 2008-03-23
I Have installd compiz fusion recently..is it related?

---

### Post by smartboyathome on 2008-03-23
> **poobalanc said:**
> I Have installd compiz fusion recently..is it related?

That shouldn't be affecting it, try my and moephan's suggestions and see if either of them help.

---

### Post by pHreaksYcle on 2008-03-23
This may be a bug worth looking at or I might be stretching it a bit buuuut...

In my adventures today I was spinning the compiz cube continuously in frustration and suddenly network manager just closed out of the blue. So, I can confirm that the two might be related...maybe.

---

### Post by poobalanc on 2008-03-23
smart..

i could run the network manager, but i couldnt list down all the access point available and connect it. 

do u have any idea, how to list down the ap? and conect it?
once i connected i will able to download..any other wifi manager..

thanks.

---

### Post by poobalanc on 2008-03-24
some body please help me. i couldnt get the network manager. avahi. 
im have trying this sicne morning. do u all have idea..how to list down the ssid's? and connect it? im using public wifi.

thanks.

---

### Post by leroyc on 2008-03-24
Why don't you just install wicd?

It will solve all problems at once.

Check this solution for complete explanation how to set it up:

[Ubuntu Wireless Fix]("http://top-web-solutions.com/ubuntu-wireless-application")

---

### Post by lswest on 2008-03-24
and if you need to connect to the internet, use the terminal.

```
sudo iwconfig [name of card] essid [name of network] key [hex key if there is one]
sudo dhclient [name of card]
```

---

### Post by poobalanc on 2008-03-25
> **lswest said:**
> and if you need to connect to the internet, use the terminal.

```
sudo iwconfig [name of card] essid [name of network] key [hex key if there is one]
sudo dhclient [name of card]
```


thanks. with the method above. i manage to go online. and download wcid. 

thanks all. 

cheers.

---

