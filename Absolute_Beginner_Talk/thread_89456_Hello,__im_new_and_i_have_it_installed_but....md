---
title: "Hello,  im new and i have it installed but..."
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by Pwn* on 2005-11-12
Hello!!!

I just got ubuntu working :D from a dual boot with xp pro and ubuntu horray

but now i am a n00b again... i dont know how or what to do but right now im primarly concerened about getting my grafix card drivers installed so could i please have sme help with that?

i am running an NVIDIA Geforce FX 5200 128 Mb  and i need help installing drivers i am a total noob sorry and the read me is confuzing... i am a pro at mac and windows though time for linux 

my msn address is [email]maxstunts@gmail.com[/email] that is also my email

:cool:

---

### Post by tseliot on 2005-11-12
Use my guide. You can find it in my signature.

---

### Post by bluefrog on 2005-11-12
if you have the chance get ubuntu breezy (latest) not hoary, then use nvidia-glx package that you will find in the cdrom using synaptic package manager. for problems pop in irc.freenode.net #ubuntu

james

---

### Post by Pwn* on 2005-11-12
> if you have the chance get ubuntu breezy (latest) not hoary LOL i have breezy badger, i said horay because i was happy and i missspelled it ... its horray LOL 

and idont know what the nvidia-glx package is

---

### Post by ThirdWorld on 2005-11-12
update to breezy, its way better, more hardware support...

edit: LOL ok i didnt read your last thread

---

### Post by salva on 2005-11-12
[QUOTE=Pwn*]and idont know what the nvidia-glx package is[/QUOTE]

Go to System>Administration (as i recall), where you will find your Synaptic package manager. Once inside it selecet find from the menu, or press Ctrl+f and do a search for nvidia-glx. Once you found it dbl-click and apply.

If you are feeling like getting to grips with command line package management (its very simple) open up a terminal and type (or copy/paste)

```
sudo apt-get -i nvidia-glx
```

this should prompt you for your password and then do an install. Very simple :)

After a reboot you should be up and working.....

Enjoy ;)

---

### Post by davidgypsy on 2005-11-12
[quote=salva]Go to System>Administration (as i recall), where you will find your Synaptic package manager. Once inside it selecet find from the menu, or press Ctrl+f and do a search for nvidia-glx. Once you found it dbl-click and apply.

If you are feeling like getting to grips with command line package management (its very simple) open up a terminal and type (or copy/paste)

```
sudo apt-get -i nvidia-glx
``` 
this should prompt you for your password and then do an install. Very simple :)

After a reboot you should be up and working.....

Enjoy ;)[/quote] 
You also need to do this in a Terminal:

sudo nvidia-glx-config enable

...otherwise it still doesn't work. :)

---

### Post by invalid on 2005-11-12
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
Then restart X (ctl-alt-backspace)

Cheers,
Cb

---

### Post by davidgypsy on 2005-11-12
[quote=invalid]```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
``` Then restart X (ctl-alt-backspace)

Cheers,
Cb[/quote]

SNAP! ;)

---

### Post by tseliot on 2005-11-12
That's what I call method 1 in my guide [http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")

---

### Post by Pwn* on 2005-11-12
WOW thanks guys!!! fastest most amount of help ive gotten this fast erver!!!


*BEST FOURMS EVER AWARD*

add me on msn if ya want : [email]maxstunts@gmail.com[/email]

---

### Post by davidgypsy on 2005-11-12
[quote=Pwn*]WOW thanks guys!!! fastest most amount of help ive gotten this fast erver!!!


*BEST FOURMS EVER AWARD*

add me on msn if ya want : [EMAIL="maxstunts@gmail.com"]maxstunts@gmail.com[/EMAIL][/quote]

Ubuntu Forums aims to please... what is msn? ;)

---

### Post by Pwn* on 2005-11-12
holey shit you are the first person who ever asked whats msn lol

msn is microsoft service network??? i think thats it but im reffering to msn messenger uhh you can talk on msn with gaim (comes with ubuntu)

or my aim: bmxicanmax

also how do i get my sound card drivers installed???
im useing intagrated sound card 

heres my mobo [http://usa.aopen.com/products/mb/s661FXm-7US.htm](http://usa.aopen.com/products/mb/s661FXm-7US.htm)

---

### Post by tseliot on 2005-11-12
[QUOTE=Pwn*]holey shit you are the first person who ever asked whats msn lol

msn is microsoft service network??? i think thats it but im reffering to msn messenger uhh you can talk on msn with gaim (comes with ubuntu)

or my aim: bmxicanmax

also how do i get my sound card drivers installed???
im useing intagrated sound card 

heres my mobo [http://usa.aopen.com/products/mb/s661FXm-7US.htm](http://usa.aopen.com/products/mb/s661FXm-7US.htm)[/QUOTE]

1) Does this mean you can't hear any sound from your pc?
2) get to the menus System/Preferences/Sound and see the name of your sound card (and post it)
3) get to Applications/Sound and video/Volume Control and make sure that Master and PCM's volume is not muted or too low

---

### Post by Pwn* on 2005-11-12
i gave you the mobo link and it says the sound card, i CAN hear  but in Nexuiz (3d game) the sounds are "gettoh" and it lags ???? the grafix look realy bad yet its lagging when i can play half life 2 with near full grafix WTF??? also how/where do i get wine  to run exe's

---

### Post by tseliot on 2005-11-12
[QUOTE=Pwn*]i gave you the mobo link and it says the sound card, i CAN hear  but in Nexuiz (3d game) the sounds are "gettoh" and it lags ???? the grafix look realy bad yet its lagging when i can play half life 2 with near full grafix WTF???[/QUOTE]

The soundcard is ok then. However I don't use Linux for playing and I don't know how to help you.

[QUOTE=Pwn*]also how/where do i get wine  to run exe's[/QUOTE]
Install Wine in Synaptic.
Then right click on the .exe file and select "Open with Wine" [COLOR="Red"]OR[/COLOR] (if this option doesn't exist) select "Open with Other Application" and then select Wine

---

### Post by tseliot on 2005-11-12
If you have problems with games you should post in the following section: [http://ubuntuforums.org/forumdisplay.php?f=93]("http://ubuntuforums.org/forumdisplay.php?f=93")

---

### Post by Pwn* on 2005-11-12
> Install Wine in Synaptic.
Then right click on the .exe file and select "Open with Wine" OR (if this option doesn't exist) select "Open with Other Application" and then select Wine
uhh with synaptic do you mean synaptic package manager??? if so i downloaded wine from there and when i right click it doesent put it in the list????  what do i dooo

---

### Post by pochonox on 2005-11-12
thx i need this informaiton jejejejej

---

### Post by tseliot on 2005-11-13
[QUOTE=Pwn*]uhh with synaptic do you mean synaptic package manager??? if so i downloaded wine from there and when i right click it doesent put it in the list????  what do i dooo[/QUOTE]
If you right click on the file select "Open with" then "Open with Other Application" and you will see a list of applications.

Isn't Wine listed?

---

### Post by davidgypsy on 2005-11-13
[quote=Pwn*]holey shit you are the first person who ever asked whats msn lol

msn is microsoft service network??? i think thats it but im reffering to msn messenger uhh you can talk on msn with gaim [/quote]

I have heard of Gaim, I use it daily, but what is microsoft? ;)

---

### Post by Major Matt Mason on 2005-11-13
I'm having similar problems getting the right resolution to display, which I am guessing is something to do with me not having the correct graphics drivers installed. I can only display 640x480.

The problem is, I don't know what the graphics card in my Toshiba Tecra 8000 is. Is there a way that I can a) install generic drivers or b) get a wider choice of resolutions to display in System/Preferences/Screen Resolution?

Thanks folks

---

### Post by salva on 2005-11-13
a quick search of the forums reveals this
[http://www.ubuntuforums.org/showthread.php?t=86586]("http://www.ubuntuforums.org/showthread.php?t=86586")
There should be some info for your situation there
;)

---

