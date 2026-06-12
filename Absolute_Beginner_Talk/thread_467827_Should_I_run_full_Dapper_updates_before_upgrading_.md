---
title: "Should I run full Dapper updates before upgrading to Edgy?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Enginirical on 2007-06-08
Hi Forum!

Since my first install of Dapper and upgrade to Edgy (which went flawlessly)I have not been able to install without problems cropping up. 

I want to Install Edgy which I have to do by upgrading from Dapper. Oh, by the way I have 64bit Intel machine.

My question is what is the best procedure for doing this? Should upgrading be the first thing I do after an install, or should I run updates first???

While I'm here, does anyone out there know of a good link that teaches you what to do after an install i.e. best practice after an install updating, specific programs I need.(for exampl Automatix2, what is this? Do I need to use this to keep things going all ticketyboo!?)

Cheers 

P.S

I know it's a bit cheeky, but I have an un-answered post here if anyone doesnt mind casting an eye over!
[http://ubuntuforums.org/showthread.php?t=466936](http://ubuntuforums.org/showthread.php?t=466936)
Yeah, I know it's poorly written and there a many many questions, but any pointers on any part will be really helpfull!

---

### Post by viciouslime on 2007-06-08
I should think you're probably best doing the updates first as this is the state dapper will have been in when upgrading to edgy was tested. Although no-doubt there have been subsequent updates since...

Is there no way you can do a fresh install? Always a good idea, especially if you have a separate home partition (again always a good idea). If not I would go with doing the updates, then upgrading and if you hit any issues post back here :)

---

### Post by Enginirical on 2007-06-08
Thanks for such a speedy response! (wow, literaly 20 seconds after posting!)

64bit machine with ATI graphics card wouldn't install Feisty and you can only download Dapper from the ubuntu website and not Edgy. As far as I understand Edgy is more stable than Feisty, and is my best bet to get Beryl working with my graphics card. 

It's wierd it worked the first time, but not the second 2 times!:( 

Thanks for the advice, I'll give it another bash, 4th time lucky!

---

### Post by andydread on 2007-06-08
I always update before upgrading to minimize any unknown bugs.  I would recommend
this with any OS in general.   
As far as getting Feisty installed you can try the the server or alternate install CD
these may work better for you.   I had better luck installing 
Server then
```
sudo apt-get install ubuntu-desktop
```

on some configurations.  
Getting beryl running on Feisty has been a real breeze in most cases 
for me.   There are times I had to wrestle with it.   

The main issue for me had been the missing beryl-xgl package.  
in those cases I simply 

```
sudo apt-get install xserver-xgl
```

then add the beryl repos 
blacklist the beryl in the ubuntu repos so we dont reinstall that one in an update 
and Voila.   Even stubborn ATI cards and legacy NV cards work great.

---

### Post by Enginirical on 2007-06-08
Im hesitant to try the installing the server edition, purely because I'm an absolute novice with only hours of experience!

The alternate CD just didnt work, then I read somewhere I had to use the x86 alternate CD for my 64bit machine with ATI. that didnt work either! 

I'll try the upgrade route once more. 

cheers for you help!:D

---

