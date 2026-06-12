---
title: "Unbutu on Dell D600 WIFI help"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Bright Hammer on 2006-02-02
Hey I am new to Linux and Unbutu looked like the best  distro for a beginner. I set it up on a Dell D600 laptop and it worked great. How ever I can’t get the wireless to work so I have some questions.

1.	How do I check to see if the driver for the wireless card is installed
2.	How do I get the driver for the card? ( it is a dell 1300 wireless card)
3.	How do I install the driver and configure the card?

I would appreciate any help you can give me with this. Also since I am new, where would be a good place to learn Linux well enough to be an Admin and list it as a skill on my resume.

BH

---

### Post by sailor2001 on 2006-02-02
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by sailor2001 on 2006-02-02
sorry for the delay.......the instructions I got where: if you idetified your wifi, down load the driver and extract from archive....I copied and pasted on the desktop........then:  cd Drive
                            sudo apt-get install ndiswrapper-utils
                            sudo apt-get ndiswrapper -i NET8180.INF
                            sudo ndiswrapper -l
                            dhclient

have no idea where the NET8180.INF comes from........also commands always said no driver found, but was able to go on web anyhow

---

### Post by Bright Hammer on 2006-02-02
Thanks for your help I will try that and let you know how it works.
BH

---

### Post by Bright Hammer on 2006-02-02
Ok here is what I did.

I downloaded the driver which was an exe to the desktop.
I then extracted the file to the desktop in a folder call dell.
I opened up a terminal and changed directory to the dell folder on the desktop
I entered the command sudo apt-get install ndiswrapper-utils
It downloaded and installed some thing
Then I entered the second command sudo apt-get ndiswrapper -i NET8180.INF
I got the following error
E: Invalid operation ndiswrapper –i

Now please take in mind that I am lost when it comes to Linux. Where can I go to learn the basics so that I can have a better idea if I am doing some thing wrong or not. Thanks for all your help by the way.

:confused:

---

### Post by sailor2001 on 2006-02-03
lots of info here.......[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)       I printed it out so always have a handy reference

---

### Post by carlosqueso on 2006-02-03
You just typed too much on the second command.  It should just be ```
ndiswrapper -i NET8180.INF
```

---

### Post by sailor2001 on 2006-02-03
aaaaaaaaaaaarrrrrrrrrrrgh  I'm close to 80 now so the memory isn't that good maybe? sorry

---

