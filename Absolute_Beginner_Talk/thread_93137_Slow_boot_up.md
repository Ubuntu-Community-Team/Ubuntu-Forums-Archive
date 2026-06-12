---
title: "Slow boot up"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by aznboi on 2005-11-21
When ubuntu is loading up it always stalls at the configuring network interfaces for like one whole minute unless i have an ethernet cable connected to it. But i use my wifi card but it still takes a while to load.

---

### Post by Kyral on 2005-11-21
This is a known issue. The reason behind it is that the computer is looking for a DHCP signal, and about a minute is about how long it takes before it gives up. It is being worked on in Dapper. I believe there is a fix someplace on the Forums though

---

### Post by aznboi on 2005-11-21
ok thnx ill see if i can find it

---

### Post by Van_Gogh on 2005-11-21
Don't know if it is a real fix, but you can press ctrl-c to cancel the network configuration. If you find a better solution, let me know,I got the same problem.

---

### Post by markr on 2005-11-21
Found this somewhere that will help :

"The default timeout parameter for dhcp is 60 seconds (which I think is way to high) but if you have a fairly responsive network (yo:ur dhcp server responds quickly if you are at all connected) you can lower this to 5 seconds and then you laptop won't hang for 60 seconds when booting away from an internet connection.

Edit /etc/dhcp3/dhclient.conf and uncomment the timeout parameter so that it looks like this
timeout 5;
instead of how it looks by default, something like this
#timeout 60;"

---

### Post by dubz on 2005-11-21
if you're brave enough you can delete the networking link in /etc/rc2.d/(i think its there)

thats will stop the service from starting up.You will then have to start it up manually by going to /etc/init.d/ and running S*networking(i think).i don't know if it's worth it,but thats my 2 cents worth.

thanks.

---

### Post by aznboi on 2005-11-21
[QUOTE=Van_Gogh]Don't know if it is a real fix, but you can press ctrl-c to cancel the network configuration. If you find a better solution, let me know,I got the same problem.[/QUOTE]


Thnx this worked... I foudn some other posts about this so im going to try those solutions out and ill post if it worked or not.

---

### Post by aznboi on 2005-11-21
i found this tried it and it worked. In the terminal type in the following:
```
sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99
```

Rebooted and my laptop booted fine and didnt stall on the "Configuring the network interfaces" and my wireless card still worked perfectly.

---

### Post by Pasto on 2007-05-01
> **aznboi said:**
> i found this tried it and it worked. In the terminal type in the following:
```
sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99
```

Rebooted and my laptop booted fine and didnt stall on the "Configuring the network interfaces" and my wireless card still worked perfectly.

This just worked for me on Feisty

---

### Post by diskotek on 2007-05-01
> **aznboi said:**
> i found this tried it and it worked. In the terminal type in the following:
```
sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99
```

Rebooted and my laptop booted fine and didnt stall on the "Configuring the network interfaces" and my wireless card still worked perfectly.

what does this code changes?

---

### Post by stickx911 on 2007-05-13
worked great for me in feisty as well!
so much better boot time. thank you.

---

### Post by Degeim on 2007-05-27
How can I undo this? My network works nice, but after a reboot it's 90% chance it won't work, and then I'll have to restart my computer several times (up to ten times) before I'm lucky enough to get it up and running.

So; what do I do to fix it again (I'd rather have a slow boot and a network than fast boot and no network ;))

Degeim

---

### Post by ltabora on 2007-06-02
> **diskotek said:**
> what does this code changes?

It just changes the Networking Service startup and Shutdown Sequence Order. Works just great on my HP nc6220!

---

### Post by sandervdv on 2007-06-02
> **Degeim said:**
> How can I undo this? My network works nice, but after a reboot it's 90% chance it won't work, and then I'll have to restart my computer several times (up to ten times) before I'm lucky enough to get it up and running.

So; what do I do to fix it again (I'd rather have a slow boot and a network than fast boot and no network ;))

Degeim

I had the same problem, but i managed to fix it, you need an internet connection!:

in a terminal:
```
sudo apt-get update
sudo apt-get install sysv-rc-conf
```
to download a handy rc.d tool

run the tool in sudo

```
sudo sysv-rc-conf
```

go down to **networking** and mark (with spacebar, or mouse) 0,6,S. Remove the other X-es

Reboot and your (Wifi) network should work again

---

### Post by MasterJS on 2007-11-01
Thanks for the code. It worked pretty well. I've had no problem so far on my Wifi connection and my boot up went from 5 mins to 30 seconds.

---

### Post by Mum_Chamber on 2008-01-06
> **markr said:**
> Found this somewhere that will help :

"The default timeout parameter for dhcp is 60 seconds (which I think is way to high) but if you have a fairly responsive network (yo:ur dhcp server responds quickly if you are at all connected) you can lower this to 5 seconds and then you laptop won't hang for 60 seconds when booting away from an internet connection.

Edit /etc/dhcp3/dhclient.conf and uncomment the timeout parameter so that it looks like this
timeout 5;
instead of how it looks by default, something like this
#timeout 60;"

old, but still helped me ;)

---

