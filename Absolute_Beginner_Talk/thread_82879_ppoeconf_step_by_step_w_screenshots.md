---
title: "ppoeconf step by step w/ screenshots?"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-10-27
Hi,
I am preparing to install ubuntu on my mom's comp, but I need a step-by-step guide (with screenshots?) to use ppoeconf correctly + I need to know what info it will need (and what is the meaning of that info it asks...) before I scratch off windows. 
I would appreciate any help.
PS. google didn't help...
thanks.

---

### Post by nsa_767 on 2005-10-27
Hi there,

pppoeconf isn't that complex, so I doubt whether you'll need screenshots. As for settings, I can't remember exactly what you need, but I do remember it wasn't anything more than what windows needed (or more what I was able to retrieve from my Windows system)... 

Just check your windows pppoe settings, write everything down and you should be OK.

pppoeconf is surprisingly simple, several dialogs will appear explaining exactly what is expected of you... Just run it and you'll see... Also, if you do find your missing some info, you can always cancel it and start it up again when have the info.

Hope that helps.
Oh, not sure if it'll work (but it should), try and run it off of the liveCD first. That way you can experiment.....

---

### Post by Kapre on 2005-10-27
[QUOTE=towsonu2003]Hi,
I am preparing to install ubuntu on my mom's comp, but I need a step-by-step guide (with screenshots?) to use ppoeconf correctly + I need to know what info it will need (and what is the meaning of that info it asks...) before I scratch off windows. 
I would appreciate any help.
PS. google didn't help...
thanks.[/QUOTE]

I haven't found any screenshot too for setting up pppoeconf but I know that you'll need the user name that the ISP gave you and the password that your using on windows (to connect to the internet).

I'm in the office now and is not using Ubuntu...but as I've setup my pc to use pppoeconf it will just be like this....

Using Breezy
Goto Applications---->select Terminal----->on the Terminal Window type "sudo pppoeconf"------>a dos type window will open----->read on------username given by ISP will be asked ----key it in------>Password will be asked----->key it in------>It will set it up and give info as to clampsomething---->Show you all the details----->will asked if you want to start the connection (select Yes)----->that's it..

As long as you've given all the info, you can check your connection by typing in the terminal "plog" or "ifconfig".

K

---

### Post by towsonu2003 on 2005-10-27
[QUOTE=Kapre]I haven't found any screenshot too for setting up pppoeconf but I know that you'll need the user name that the ISP gave you and the password that your using on windows (to connect to the internet).

I'm in the office now and is not using Ubuntu...but as I've setup my pc to use pppoeconf it will just be like this....

Using Breezy
Goto Applications---->select Terminal----->on the Terminal Window type "sudo pppoeconf"------>a dos type window will open----->read on------username given by ISP will be asked ----key it in------>Password will be asked----->key it in------>It will set it up and give info as to clampsomething---->Show you all the details----->will asked if you want to start the connection (select Yes)----->that's it..

As long as you've given all the info, you can check your connection by typing in the terminal "plog" or "ifconfig".

K[/QUOTE]

thanks so much both of you. for some reason, it didn't come to me to run configurations in the live cd...

hmmm,  I know no one really uses windows here anymore but, would "ipconfig" in a command promt give me the info I need? (am I risking to be kicked by asking too many newbie questions?)

again, thanks so much...

---

### Post by herrpoon on 2005-10-27
I believe its "ifconfig" you're looking for :)

---

### Post by towsonu2003 on 2005-10-27
[QUOTE=herrpoon]I believe its "ifconfig" you're looking for :)[/QUOTE]

oh, sorry for the misuderstanding. I meant ipconfig in windows xp :) thanks though :cool:

---

