---
title: "oops!"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Xxbrandnew10xX on 2008-03-23
Ok  well i have had the ubuntu live cd sitting around for some time now and i decided i was finally going to dual boot my laptop and i went to install and it erased my windows xp completely.  Anyways i have decided to not get mad because i dont really use anything windows specific just maybe an instant messenger.  so my problem i accidently erased windows xp so now i have no choice but to get ubuntu to work and so far so good. Install went well but i have two immediate problems and the rest i think i can figure out through forums and just by using it.  first problem is the biggie, on my hp dv6000 notebook i cannot get my wireless to work it recognizes my network but when i type in the passphrase key it wont connect.  I see there is a lot of topics on setting it up but im really confused and cant figure it out.  
and my second problem which isnt a huge deal is when i log in the font is like 40 so i cant see my username when i type it.  any help would be greatly appreciated i really need wireless help.  Thanks in advance

Im a little stressed about my OS messup but im actually pretty excited about ubuntu and getting it to work smoothly.  also i have seen a cool window where the main screen is a 3d cube and you can spin it to a clean page i think its called beryl does anyone know how i can get that to just because its cool thanks again

---

### Post by orangemoose on 2008-03-23
Yeh, I've done that too!

Ok, wireless should be easy.  Double click on the computer icons in the upper right of the screen.  It should give you a list of available wireless networks.  Select the one you want and you will get a new window asking for the security info -- if the network is secured.

If it WPA just type in the key and select TKIP if it is a shared key and you will see an animation on the menu bar.

The 3d desktop is now called Compiz --Beryl project merged back-- but before you can get it   running you have to make sure your graphics card drivers are installed.

If you have nvidia go to System -> Preferences -> Appearance -> Visual Effects.  Select the third option Extra.  You will be prompted to upgrade the graphics driver.

Then a restart.  Then go back and select Visual Effects again and Extra.
Google Compiz for all the keyboard shortcut to get the thing spinning.

Hope that helps.

---

### Post by spiderbatdad on 2008-03-23
I believe this model is one that takes a little tinkering to get working properly. For starters try going to the restricted drivers manager and selecting the broadcom and nvidia drivers. System>>Administration>>Restricted Drivers Manager
Once you get your graphics and wireless straightened out. You can install compizconfig-settings-manager from Synaptic Package Manager to configure compiz-fusion...The Cube.

You might also consider Hardy Beta, as long as you're just getting started. The final release is due in april.

---

### Post by Xxbrandnew10xX on 2008-03-23
i have tried entering the passphrase for my router it searches and searches and then asks me to fill it out again it wont connect any ideas

---

### Post by AvalonSpirit on 2008-03-23
Try enabling restricted drivers, 

system --> Administration --> Restricted Drivers Manager

see if that gets it to work, it might be that there are no open drivers for your network card.

Thats how i got my wireless to work.

---

### Post by Xxbrandnew10xX on 2008-03-23
im sorry im totally new at this but i have went to restricted drivers and it says my intel PRO/Wireless 3945 driver is enabled and it still wont connect to my security enabled router 
thanks for all those who have helped im sure ill getting it working soon

---

### Post by nothingspecial on 2008-03-23
Don`t know if this will help but .... when I first installed on my laptop I had a similar problem. Have you selected the correct encryption? 
 When it asks you for your key it shows a dropdown menu displaying WAP. Well mine is a WEP which you have to select before the key will work.  
 Sorry if that wasn`t well explained but I hope you know what I mean.

---

### Post by Xxbrandnew10xX on 2008-03-23
Yea that makes sense i have been toying with it entering my passphrase in all the options wpa wep etc... and still no luck.  
I just realized though i cant even manage my network anymore... when i deleted XP i deleted the setup wizard and now the linksys cd wont auto run it comes up in files and i dont know how to get it to install on my computer so i can manage my network.  I was thinking if i could change it I would be able to take the security setting off but i cant get it to even run the cd... I need help

---

### Post by Dennis on 2008-03-23
Most routers can be administered from a browser using something like [http://192.168.1.1](http://192.168.1.1)

If it's any consolation my HP laptop has the same Intel Wireless gubbins and works fine.

---

### Post by nothingspecial on 2008-03-23
If you`ve wiped windows the set up cd will not work. I`ve only ever used windows for a couple of days when I bought a laptop before installing Ubuntu. I`m afraid I`ve no other suggestions (new to computers, never mind Ubuntu) but there will be an answer. Just keep searching. Sorry I can`t help

---

### Post by Xxbrandnew10xX on 2008-03-23
Thank you all... I now have wireless i appreciate all your help  Happy Easter!

---

