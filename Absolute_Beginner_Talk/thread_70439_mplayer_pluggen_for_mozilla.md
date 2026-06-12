---
title: "mplayer pluggen for mozilla"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-09-29
it does not work same thing with the main mplayer app.
any ideas?

---

### Post by nitricacid on 2005-09-29
Please note this setup is for a PC running intell processor and not AMD.

Open the Synaptic package manager and click the search button
Search for MPLAYER.

Install the following:
Libpostproc0
mencoder-586
mozilla-mplayer
mplayer-586
mplayer-686
mplayer-fonts
xmms-xmmplayer

Efter everything is installed open a terminal and type:
Sudo apt-get update

After that has finished type:
sudo apt-get upgrade
---

I just installed mplayer on my computer and everything works wonderfull.

Hope this helps

---

### Post by aysiu on 2005-09-29
How did you install it?

---

### Post by nitricacid on 2005-09-29
[QUOTE=aysiu]How did you install it?[/QUOTE]

In the synaptic all you have to do is check the boxes next to what you want to install (the boxes should show green, meaning they are ready to be installed).
Then just click apply

---

### Post by jasonpeinko on 2005-09-29
ok im testing it now

---

### Post by jasonpeinko on 2005-09-29
now it still gets stuck but the app works 
just the mozilla gets stuck

---

### Post by jasonpeinko on 2005-09-29
it is tyring to play an audio file. Dont know if that has anything to do with it

---

### Post by nitricacid on 2005-09-29
Are you trying to play the audio file from the site itself or did you download it and then try to play it?

Try to update.
if that doesn't work try restarting the computer and then playing the file again

---

### Post by jasonpeinko on 2005-09-29
from the site i will try downloading 
and i dont want to restart right now im working on a school paper

---

### Post by jasonpeinko on 2005-09-29
nvm cant download

---

### Post by nitricacid on 2005-09-29
I just found it much easier to install and update using Synaptic then to go through the hassel of trying to install the actual file.

---

### Post by jasonpeinko on 2005-09-29
how do i update?

---

### Post by nitricacid on 2005-09-29
Did you install mplayer from synaptic?
If so could you give me a list of what you installed?

---

### Post by nitricacid on 2005-09-29
[QUOTE=jasonpeinko]how do i update?[/QUOTE]

open a terminal and type
sudo apt-get update

after that is done type:
sudo apt-get upgrade

---

### Post by jasonpeinko on 2005-09-29
ok i updated and i have everything installed from a few posts back

---

### Post by nitricacid on 2005-09-29
everyting ok now or is it still having problems?

---

### Post by jasonpeinko on 2005-09-29
still have the problem but i think it is that it is trying to run a real player file

---

### Post by nitricacid on 2005-09-29
oh.... i don't think mplayer supports .ra files yet.
Try some other files from the net and see if they work.

---

### Post by Qrk on 2005-09-29
You may want to type 

killall esd

into a terminal. I've had similar problems as you and this cleared some them up, particually with realplayer.

---

### Post by nitricacid on 2005-09-29
[QUOTE=Qrk]You may want to type 
killall esd
into a terminal. I've had similar problems as you and this cleared some them up, particually with realplayer.[/QUOTE]

thank you for that enlightend suggestion. :D

Also I have been informed from a friend that Kafiene should play realplayer files or you could just download the actual REALPLAYER from their site but i would check the synaptic manager for 'realplayer'.

---

### Post by Sheytan on 2005-10-01
Mplayer works perfectly for me but when i try to play a movie in firefox the buffering just stops at 99% :(

---

### Post by bob k on 2005-10-02
Thats a known problem, goto the mplayer plugin site and update to the latest plugin.

---

