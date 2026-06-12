---
title: "3d desktop"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-05-24
is 3d desktop enabled in ubuntu ?
if so how to enable it ?

---

### Post by LaRoza on 2007-05-24
Assuming you have the video, RAM, and CPU needed, you would install beryl

sudo aptitude install beryl

I just did this last night and had a lot of fun with Beryl, even though I usually don't care about looks, beryl was like a video game.

---

### Post by Flump5000 on 2007-05-24
yeah first make sure your computer can handle all that eye candy before you install it.

---

### Post by overdrank on 2007-05-24
> **LaRoza said:**
> Assuming you have the video, RAM, and CPU needed, you would install beryl

sudo aptitude install beryl

I just did this last night and had a lot of fun with Beryl, even though I usually don't care about looks, beryl was like a video game.

HI you installed beryl on Dapper?:-k

---

### Post by akkad on 2007-05-24
my system is:
dell inspiron 6400
intel core 2 due 2GHz
2GB DDR2 memory
ATI Radeon Mobility X1400 256MB

is it ok ???

---

### Post by LaRoza on 2007-05-24
If your Video card driver works, you'll have no problem (probably).



> 
HI you installed beryl on Dapper?


No, you can't do that, can you? I installed it on Feisty.

Oh, I see, I am listed as a Dapper user. Well, I am, but also have Feisty and a slew of other operating systems, and could only select one.

---

### Post by akkad on 2007-05-24
actually i dont know what dapper and feisty are :( am totally new to linux
but any way am performing the settings right now and i will give my feed back

---

### Post by akkad on 2007-05-24
ok i executed the command sudo aptitude install beryl
and the terminal window now finished , so whats next ????

---

### Post by Zzl1xndd on 2007-05-24
Also as a Side note to the 7.04 users Compiz is already installed if you go to System < Preferences < desktop effects you should be able to turn it on from there. Although I prefer Beryl myself but this testing with Compiz first will at least let you know if you can handle it.

(PS i might have the the wrong instructions at work and no way to double check ;) )

---

### Post by akkad on 2007-05-24
guyyyyyyyys whats next? beryl installed, i have new entry in the main menu where two icons there
one is "Beryl Manager" and the other is "Beryl settings Manager" , what shall i do now ??

---

### Post by LaRoza on 2007-05-24
Select Beryl Manager, an icon appears in your panel.

Select Beryl manager settings, select all you want, I think you have to enable desktop effects, under System->Preferences.

Have fun.


PS
I assume you already restarted, if you didn't do it.

---

### Post by LaRoza on 2007-05-24
> **akkad said:**
> actually i dont know what dapper and feisty are :( am totally new to linux
but any way am performing the settings right now and i will give my feed back

Ubuntu 6.06 Dapper Drake
Ubuntu 6.10 Edgy Eft
Ubuntu 7.04 Feisty

Dapper is stable, but bland (visually). Edgy, I never used, but it didn't seem all that great, from what I read, and Feisty was just released.

---

### Post by dj1120 on 2007-05-24
Go into Beryl manager and there you can begin to set your preferences. Once you are done you should see a little red icon confirming that Beryl is running. You will have to play around with the settings to get it just right

I am not sure how to make aBeryl run at startup so I put a shortcut on my panel and click on it once I am logged in

---

### Post by akkad on 2007-05-24
it seems my VGA is not supported cuz when select beryl manager the desktop start flickering then it get back to normal mode like nothing happen :(

---

### Post by psmar on 2007-05-24
use the beryl manager to choose the effects and theme manager you would want to use the Emerald theme manager that should have to the beryl package. then in 'Systems/Sessions add beryl-manager" so it will self start

---

### Post by Hobo Joe on 2007-05-24
> **dj1120 said:**
> Go into Beryl manager and there you can begin to set your preferences. Once you are done you should see a little red icon confirming that Beryl is running. You will have to play around with the settings to get it just right

I am not sure how to make aBeryl run at startup so I put a shortcut on my panel and click on it once I am logged in

System>Preferences>Sessions
Then add a new one called Beryl, and set the startup command to be 'beryl-manager'

Ta-da!

---

### Post by vinmar on 2007-05-24
To try it out go to the terminal and run:
beryl-manager
... I think, can't check this at work.

---

### Post by madcow72 on 2007-05-24
Nobody has asked you to check and make sure your video card is working yet, however you'll never get beryl to work if you don't have 3D acceleration going.  Do this:  ```
glxinfo | grep direct
``` in a terminal, and look for output that looks like:  direct rendering: Yes

If it says no, then your video card needs to be installed properly.  In that case, take a look at "envy" written by Alberto Milone [here.]("http://www.albertomilone.com/nvidia_scripts1.html")

---

