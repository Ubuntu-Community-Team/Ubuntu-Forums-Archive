---
title: "Has Wirless Gotten Any Easier?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by EvansLight on 2007-11-13
I have wanted to move to linux for a long time now, but that presents a problem for me. I can only put it on my laptop, and i only use it for surfing the web. I did switch it one time over to Ubuntu, and loved it, until i tried getting wireless to work. 

I couldn't get my wireless card to work for the life of me. I tried every guide i could find, every solution i came across. By the time i gave up i was really starting to get to love linux. I can't just use wired since my room and the router are quite far apart. 

I would love to switch this back over to linux. I dont have anything important installed or saved on it so i could do it right now if i wanted to, but i want to know if it would be any easier, or if its gotten harder for me to switch over.

Oh and i have a Linksys WPC54G card. I have had it for ages, just never had a reason or money to get another one. When i eventually get a new laptop i probably will be getting a mac so i wont need another wireless card.

I hope there is some new fix or guide or way to get this working as i really want to switch, i miss those few hours playing with linux.

---

### Post by liberalist on 2007-11-13
It is supposed to be easier in Ubuntu 7.10 Gutsy Gibbon. This release namely includes a network manager and sports many improvements. However, I do not know if your wireless card has open source drivers available. If not, it could be quite challenging to install a restricted driver for your Linksys wireless card. Good luck, anyway.

PS: You can always try if your wireless card is supported through a live CD.

---

### Post by robinl on 2007-11-13
Gutsy even got a GUI for you to install Windows drivers using ndiswrapper!

---

### Post by EvansLight on 2007-11-13
Alright well downloading it now. Im alos downloading a few other distros, hoping one of them works well. I also just want to try others, Ubuntu and Knoppix are the only two i have ever used.

---

### Post by crjackson on 2007-11-13
> **EvansLight said:**
> Alright well downloading it now. Im alos downloading a few other distros, hoping one of them works well. I also just want to try others, Ubuntu and Knoppix are the only two i have ever used.

I have three towers in my house that have Linksys wireless cards.  They are all supported out of the box under 7.10.  None of them would work out of the box using 7.04.

I'd say that's much improved...

---

### Post by skymera on 2007-11-13
short answer, no.

its a lot worse than Feisty

---

### Post by crjackson on 2007-11-13
> **skymera said:**
> short answer, no.

its a lot worse than Feisty


And there you have it.  Your mileage may vary.  You try it and let us know...

---

### Post by jaybombalous on 2007-11-13
> **skymera said:**
> short answer, no.

its a lot worse than Feisty



ironic how the person right before u posted its much improved. 


To the thread starter, u can always try it. If it works great, if not great. but one thing I do know, if ubuntu doesn't find it out of box I doubt any other distro's will. Modules are part of the kernel and since ubuntu uses the newest kernel release, or tries too, then its most likely as up to date as u will get with any gnu/linux release.

---

### Post by poudin on 2007-11-13
above a GUI for ndiswrapper was mentioned...can someone elaborate on this package and give the steps to download and install it...would love to check it out.

---

### Post by crjackson on 2007-11-13
> **poudin said:**
> above a GUI for ndiswrapper was mentioned...can someone elaborate on this package and give the steps to download and install it...would love to check it out.

Go to the synaptic package manager and search for ndiswrapper.  There are about 3 packages related and one of them is the GUI.  Read the description and it will tell you.  I used it on one of my laptops (my 4th wireless system) and it worked great the 1st time for me.  Others have reported that they had to use the command sudo depmod -a after using it to make the driver active.

So if you decide you need to use the wrapper, you will install the ndiswrapper, ndiswrapper tools, ndiswrapper GUI for windows drivers....

You need them all if you plan to use the ndiswrapper and load your driver with the GUI...

---

### Post by HermanAB on 2007-11-13
Well, actually WiFi got a lot easier way back at the end of 2005 in Mandriva Linux already, but Ubuntu still has a ways to go.  So, if you wish to install your WiFi adaptor using a wizard that really works, then Ubuntu isn't for you yet, but reading the instructions on the ndiswrapper web site isn't that hard either.

---

### Post by kd7swh on 2007-11-13
My Wireless has worked since Dapper. 

NDISWrapper Does make installing windows drivers a snap though. Also, VPN access has greatly improved over the last two releases. Suse Linux (dare I speak the name of another distro) seems very good at working with wireless hardware in my experience. The package management and GUI  (KDE) both give me a headache though.

Best of Luck :)

---

### Post by EvansLight on 2007-11-14
Well im on my now linux based laptop and online :D only problem? Its not on my wireless card, and not on Ubuntu XD

I decided to also look around at other linux distros. I found that my laptop is more suited for suse (according to this test online) so after trying to install Ubuntu, and my computer not wanting to work with it, i tried suse. 

I had it installed rather fast, and of course my wireless card didnt want to work with it. I then had an awesome idea; we used to use netgear instead of linksys, so i went looking for our old netgear stuff, and low and behold suse found the netgear card right away and after a bit of setup im online and running :D 

Granted after having played with Suse a bit, i do miss Ubuntu, but if my laptop can't even run the live CD enough to get it installed, don't know what im to do. I still got alot to learn about linux though; im just happy to have it installed and online :D

Thanks for everyones help :D

---

### Post by barney385 on 2007-11-14
> **EvansLight said:**
> Well im on my now linux based laptop and online :D only problem? Its not on my wireless card, and not on Ubuntu XD

I decided to also look around at other linux distros. I found that my laptop is more suited for suse **(according to this test online)** so after trying to install Ubuntu, and my computer not wanting to work with it, i tried suse. 

I had it installed rather fast, and of course my wireless card didnt want to work with it. I then had an awesome idea; we used to use netgear instead of linksys, so i went looking for our old netgear stuff, and low and behold suse found the netgear card right away and after a bit of setup im online and running :D 

Granted after having played with Suse a bit, i do miss Ubuntu, but if my laptop can't even run the live CD enough to get it installed, don't know what im to do. I still got alot to learn about linux though; im just happy to have it installed and online :D

Thanks for everyones help :D

Can you provide a link, or a hint, or something?(For the online suitablity test) Sounds interesting and I would like to see it!!:)

Thanks

---

### Post by EvansLight on 2007-11-14
> **barney385 said:**
> Can you provide a link, or a hint, or something?(For the online suitablity test) Sounds interesting and I would like to see it!!:)

Thanks

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

found it just by searching. Asks questions on what you want and what your installing linux on.

---

### Post by barney385 on 2007-11-14
It gave me 4 choices: OpenSuse, Kubuntu, Mandriva, and Ubuntu.

It isn't a hardware related suitability test. It's based on personal preference and linux based knowledge.

How did you come to the conclusion that Suse(OpenSuse?) is better for your particular hardware?

Maybe I'm missing something?

---

### Post by stchman on 2007-11-14
When shopping for laptops or wireless that are Linux compatible get either Atheros or Intel as they seem to have the best compatibilty.

---

### Post by EvansLight on 2007-11-14
> **barney385 said:**
> It gave me 4 choices: OpenSuse, Kubuntu, Mandriva, and Ubuntu.

It isn't a hardware related suitability test. It's based on personal preference and linux based knowledge.

How did you come to the conclusion that Suse(OpenSuse?) is better for your particular hardware?

Maybe I'm missing something?

its not a detailed part of it, but it asks about how old your computer is. While not an exact science, age can mean a lot.

For me it gave me the choice of OpenSuse, Ubuntu, and i think Mandriva. But for Ubuntu, Mandriva, and i think one or two more it had for me, it said my computer might not be able to handle it.

I remember the first time i installed ubuntu on this computer, after finally getting online (invading my sisters room with an ethernet cable) and updating ubuntu, it was moving slower then xp. Ive already got suse configured to my needs, updated anything i wanted too/needed to update, and am working on adding all my programs, and so far so good :D

Granted i miss Ubuntu, and i really wanted to use the newest version of it. i might try running the install again in a few weeks, for now i have this working and will stick with it at least long enough to learn more about linux.

---

