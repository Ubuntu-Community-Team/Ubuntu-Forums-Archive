---
title: "Updating GPU and selecting screen"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by BluePlum on 2008-03-16
So basicly i needa no if i can update my GPU and Choose a screen.

[http://ubuntuforums.org/showthread.php?t=720251](http://ubuntuforums.org/showthread.php?t=720251) is the full sotry. Basicly the guy said its not finding my screen so i cant turn my screen upside and it freezes when i do. He says i probly found a bug so if a update my gpu and select a screen cause the defualt is Plug ' n ' play.

---

### Post by BluePlum on 2008-03-16
BUMP going to bed so hopefully we got an answer by morning :P

---

### Post by BluePlum on 2008-03-16
cmon guys this is an easy one someone must no...

---

### Post by BluePlum on 2008-03-17
back from school and not an answer... arg...

---

### Post by BluePlum on 2008-03-17
Heh are all my posts just bumps ? lol need more info? or does every1 hate me ... lol

---

### Post by NightwishFan on 2008-03-17
Hi, again. :)

We do not hate you. I just am no expert. Getting there hopefully. I remember the last thread. From what I see if you can install the restricted drivers it should be smooth sailing from there. Normally installing them or a Compiz issue is the problem, as Compiz is beta. I am back on Gnome for today at least, so I should be able to relate a bit better.

EDIT: I have found my display cannot rotate as well.

---

### Post by BluePlum on 2008-03-17
lol your the only 1 who helps me. Maby if i post in another topic. ISnt rly that begginerish. :P.

---

### Post by NightwishFan on 2008-03-17
I wish I could solve the issue. The only thing I can think of is it is simply not supported. Like I said I will dig around. I am going to be working on KDE4 soon, so I will have a hard time helping after I get that on.

---

### Post by BluePlum on 2008-03-17
Yeah But thats why im asking these 2 questions. Can i update my gpu so it may be. Can i Change my screen from plug ' n ' play because at the end of the other thread ( link first post ) youll see he said it cant find my screen so yer....

---

### Post by NightwishFan on 2008-03-17
You cannot update your gpu. The restricted drivers if enabled are the update. If they are updated and you aren't using vesa, Then the card may not support it. Check the manufacturers page for info.

---

### Post by BluePlum on 2008-03-17
What about screen?

---

### Post by NightwishFan on 2008-03-17
The screen is linked to the gpu. Mine is identified as a Compaq LCD but Windows Vista calls it plug and play. I believe there is no difference. The gpu may not be able to support screen rotation. If it says that It can or cannot on the manufacturer's page we will come closer to understanding whether it can or cannot be fixed.

---

### Post by BluePlum on 2008-03-17
but but it was sopposed to be upside down and flip down :(!!!!!!!!! Im gonna cry lol. Bur realy i dont see why it just cant display on a differnt angle

---

### Post by NightwishFan on 2008-03-17
I would say it is perhaps more complicated than that. My hardware is all fairly common and I have no option at all to flip. It just says, "Normal". As I have said I am no expert. Just research your card. :)

---

### Post by jordanmthomas on 2008-03-17
I still can't believe it doesn't work with compiz disabled.
What does it give you if you type
```
ps -A | grep compiz
```

If anything comes back from that command then you have not disabled compiz and you should turn it off then try again.

---

### Post by BluePlum on 2008-03-17
ill try that in 1 sec but would the GPU not supported cause ubuntu to take like 2 minutes to start up?

---

### Post by jordanmthomas on 2008-03-17
If I remember correctly from your other thread, it looked like xrandr said flipping your screen should work.

Ubuntu taking 2 minutes to start up...that's just how Ubuntu is.  It's not exactly a speed demon.

---

### Post by BluePlum on 2008-03-17
Ok thx and a defiently had clicked for No effects and i cant try that atm cause my number keys died on laptop and my bro stole my keyboard... yer so i can try laterz hehs

---

### Post by jordanmthomas on 2008-03-17
OK, well if you're sure you've turned it off then don't worry about it.

---

### Post by BluePlum on 2008-03-17
Well so i should say goodbye to my dream :(

---

### Post by NightwishFan on 2008-03-17
Only when the manufacturer tells you so. Just google your cards name or find it on ATI page. (ATI right?) I would assume if it tries and you see it flip but with errors its possible but if it just blacks and is upright no. =D

Just look at ati page for card. If they say yes or nothing keep trying if they say no its no.

---

### Post by BluePlum on 2008-03-17
Can you do it for me i dont get ya 100%:confused:

---

### Post by NightwishFan on 2008-03-18
Nope. Find the name of your card and just go to webpage and look at its notes. :)

---

### Post by BluePlum on 2008-03-19
I looked for my gpu but im not to sure what is it.
In terminal says it is....

assasin@Invisible-Assasin:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

and the website is... [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) Basicly it takes 30 secs if u no what ya doing :) but i dont :( cmon nightwishfan you can do it :P

---

### Post by jordanmthomas on 2008-03-19
If you're having a hard time *finding* the right driver, you're going to have a harder time *installing *it.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
This script is very popular among Ubuntu users for installing the latest graphics drivers, and should be easier for you to figure out than doing it yourself (though if you're here to LEARN, do it yourself)

---

### Post by BluePlum on 2008-03-19
U broke my ubuntu. I went install Ati driver automaticly said it wasnt supported with my OS. So i went Manual install the first version then i restarted my system And its all in writing. Its got random letters on screen and i can enter my username and password in some random white writing on the black screen. Cant log in or anything. Its broken! :(

---

### Post by jordanmthomas on 2008-03-19
Well, technically, YOU broke it.  
Anyway, press Ctrl - Alt - F2 then log in and run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
To fix X.  You should be able to answer the default answer to your questions.

After you do this you can either run 
```
sudo /etc/init.d/gdm restart
```
of
```
sudo reboot
```
to get back to gdm

---

### Post by BluePlum on 2008-03-19
meh just reformatted lol

---

### Post by NightwishFan on 2008-03-19
Congrats, you broke it. :)
If you have compiz be happy, and wait for hardy to see if you can rotate. You likely will be able to.

---

### Post by BluePlum on 2008-03-19
wait for hardy? ooooo next ubuntu k :D. And yer im very happy i broke it. bet you cant :P.

---

### Post by NightwishFan on 2008-03-19
Can't is different from didn't. Today I did. =D

Too easy to fix though.

---

### Post by BluePlum on 2008-03-19
heh well i guess its non upside down laptop till next ubuntu :D. But now i need to get it sideways, How do i do that? 


:P thats was a joke heh :P

---

### Post by NightwishFan on 2008-03-19
Don't get hopes up but It might be possible. It supports graphics hardware better as a goal. Does not mean your home free.

---

### Post by jordanmthomas on 2008-03-20
> **BluePlum said:**
> heh well i guess its non upside down laptop till next ubuntu :D. But now i need to get it sideways, How do i do that? 


:P thats was a joke heh :P

Well, for the record, it's also done using xrandr.

---

### Post by NightwishFan on 2008-03-20
You would know more than me. I really do not know much about rotating displays. :)

---

### Post by BluePlum on 2008-03-20
> **NightwishFan said:**
> You would know more than me. I really do not know much about rotating displays. :)

who does? must be a sad life if you are the " rottating display expert " haha.

---

### Post by NightwishFan on 2008-03-20
Hey there needs to be experts in that to! :lolflag:

---

### Post by BluePlum on 2008-03-20
Heh well the guy at ubuntu who made the rotating screens should be fired hah

---

