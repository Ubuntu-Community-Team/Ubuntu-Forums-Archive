---
title: "[SOLVED] Help setting up internet.."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Pioneer5000 on 2007-10-18
Ive had trouble setting up the internet on Ubuntu with my laptop and i thought the latest release 7.10 might solve my problems and help me out in automatically detecting my wireless internet connection but its not doing it and i have not clue how to set it up. Ive only tried this while doing the ubuntu live thing cause i dont want to install it until im sure that i can get internet working.

Ive used linux before i only stopped using it once i got my laptop a couple of months ago becuse i havnt been able to get the internet up and running for it. The Laptop is Dell Inspiron 1501 with a Dell Wireless 1390 802.11g 54Mbps Wireless Mini Card.

Can any body help me out here or point my in the right direction. Thanks. :)

---

### Post by WakkiTabakki on 2007-10-18
Try
1. Have you got one of those "disable the wireless card"-buttons on your laptop? (Not poking fun at you, really! Was phone-supporting my uncle the other week with Vista. After about 45min we realized that was the problem, the card was simply switched off and Vista didn't even hint about it...). 

2. Have you checked what the restricted driver manager says? It may be simply to enable the wireless restricted driver

If none of above. Have you got a network icon next to the clock? Left-click on it, does it say anything about wireless?

/N

---

### Post by mikeyphi on 2007-10-18
You might get some good suggestions from the Ubuntu Dell Support forum.

---

### Post by WakkiTabakki on 2007-10-18
This one may be helpful (not sure if it still applies to Gutsy, though).

[https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

Good luck...
/N

---

### Post by dward526 on 2007-10-18
I had problems connecting to the internet with my laptop via an atheros card.  I eventually solved it by using 'ndiswrapper' and using the xp driver.  You might want to look into that or to MadWiFi.

---

### Post by Pioneer5000 on 2007-10-19
> **WakkiTabakki said:**
> This one may be helpful (not sure if it still applies to Gutsy, though).

[https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

Good luck...
/N

Thanks for this but it doesnt work well not for me.

I get up to this part..

$sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf

and then i get this error:   sudo: ndiswrapper: command not found


I dont have internet running on this laptop at all i had to d/l the other files from another computer. Can someone help me out ive tried all of the above nothing seems to be working...

---

### Post by Pioneer5000 on 2007-10-19
Just a reminder that i am using Ubuntu 7.10

---

### Post by WakkiTabakki on 2007-10-19
Hmmm... ok, try:
```
sudo apt-get install ndisgtk
sudo ndisgtk
```
And then use the application to install the driver...

/N

---

### Post by Pioneer5000 on 2007-10-19
^ Oh man this is rubbish i did what you  said above seems to be workin and then i relase that the wifi is now off it was on before when i was doing the stuff earlier but now its off and i cant get it back on cause ubuntu doesnt seem to recongized the speical dell key you push with f2 to turn the wifi on and off. Any ideas?

---

### Post by Pioneer5000 on 2007-10-19
I've got it working.

Here's what happened, while following instructions at first i noticed that my wifi light was on but then later on i dont know which command i typed in while trying to set it up i did but some how i turned it off and coulndt get it back on.

After connecting my laptop to the net using a wired ethernet connection i tried the steps given to me above with no luck but then i decided to go back to just doing the basic restricted drivers thing with a internet connection and then it worked it updated something and then i clicked on the connections icon in the top right of the screen and changed from wired connection to wireless and it was working. :)

Also i had to undo the blacklist bcm43xx.

Thank you to everyone who helped me out and gave me advice on this and hopefully this thread will help someone else, Thanks again.

---

