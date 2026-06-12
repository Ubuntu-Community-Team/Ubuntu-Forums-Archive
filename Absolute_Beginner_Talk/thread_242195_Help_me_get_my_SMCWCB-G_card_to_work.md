---
title: "Help me get my SMCWCB-G card to work"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by mertz on 2006-08-23
I've installed Dapper Drake, I plugin my SMCWCB-G wifi card ... the system recognizes the unit but I can't get it to connect to WLAN.

I run a 128 bit WEP encryption - and the computer in question is an older IBM ThinkPad T23.

Unfortunately I am a total Ubuntu/Linux newbie. I've spent the last three weeks searching the net for some way to get this bloody thing to work ... and I'm about to throw the towel into the ring. 

Help me, please!

---

### Post by benfindlay on 2006-08-23
Hi there!

First of all I'd check on your router to make sure it isn't set up to only allow trusted MAC addresses. If your card is recognised and configured ok as you say, then there is no reason why it won't work

There is a good chance however that the device isn't actually working properly. I'd recommend installing ndiswrapper and NetworkManager from the Synaptic Package Manager. Ndiswrapper allows you to use windows drivers with your card. I remember it being an absolute pain to get WPA working, so you'll most likely be limited to WEP, but since you are using this over WPA encryption, it shouldnt be a problem. NetworkManager is a nifty little utility for manageing your network connections. Both it and the ndiswrapper configurations have GUI configs available.

Hope this helps!

---

### Post by mertz on 2006-08-23
My home network isn't configured to require specific MAC adresses.

I'll try that the second I get home. Are there any decent guides on how to use ndiswrapper and NetworkManager out there?

---

### Post by benfindlay on 2006-08-23
To be honest I'm not entirely sure. I've only used ndiswrapper under SuSE Linux 10, and to be honest the install pretty much pre-configured everything i needed, since my pcmcia wireless card uses a very generic chipset (PRISM).

Since you can do a lot of stuff via the very self explanatory GUI config (instead of terminal) in both ndiswrapper and NetworkManager under Ubuntu this makes it a LOT easier than working through terminal! Some info on network manager can be found at [http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/") and info on ndiswrapper can be found at [http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")

---

### Post by mertz on 2006-08-23
You are way cool, benfindlay.

So here's to me crossing my fingers for the sweet wireless  ubuntu bliss.

---

### Post by mertz on 2006-08-24
Hmmm ... I can't seem to get Ndiswrapper installed. When I try to run the command 'make install' Ubuntu comes up telling me 'No such command' ...

Is there anything I'm doing wrong?

---

### Post by benfindlay on 2006-08-24
I take it you downloaded the binaries and are doing it manually?

So I take it you've done the following:

tar -xfvz [ndiswrapper version].tar.gz
cd [ndiswrapper version]
./configure
make
make install 


Seriously though, I'd just use Synaptic Package Manager, because it will just install it automatically (ok, its kinda cheating, but it gets the job done! :wink: )

---

### Post by mertz on 2006-08-24
Actually, I have _no_ idea what I'm doing! This is my first real dive into Linux. :p Sofar it's been fantastic (a part from the wifi thing).

Anyway... I don't know what I did ... but it's working. Although I have to run the modprobe command every time I boot the computer!

*sigh* I'm such a newbie!

- mertz

---

### Post by FuriousLettuce on 2006-08-24
To get it to load on boot, try doing the following:

```
sudo nano /etc/modprobe.conf
```

and adding the line

```
alias wlan0 ndiswrapper
```

then press ctrl+x and choose save.

This should work IIRC [i'm not at my computer]

---

### Post by mertz on 2006-08-25
And here I again point out my utter newbieness. I think that my WiFi card is mapped to "ath0" instead of "wlan0" ... so in the code you entered above I just exchange the one for the other?

---

### Post by benfindlay on 2006-08-25
Indeed you do! If you go into "Network" under Administration in the System tab, you can see for definite what your wifi is mapped to. Just use whatever value it says in there.

---

### Post by FuriousLettuce on 2006-08-25
Yes. Also, in the terminal, you can just do 

```
sudo iwconfig
```

that will bring up a list of any wireless enabled interfaces.

---

