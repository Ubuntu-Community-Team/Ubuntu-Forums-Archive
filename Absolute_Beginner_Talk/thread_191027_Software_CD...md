---
title: "Software CD.."
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Impsy on 2006-06-07
Hi i recently installed Xubuntu on my internet-less computer and I am looking for a cd that is full of software with a nice mp3 player with ipod support and stuff like that. I know how to use the Synaptic Manager and how to ADD A cdrom, please help me out!

Thanks!

---

### Post by aysiu on 2006-06-07
[It's in the works](http://www.ubuntuforums.org/showthread.php?t=183933).

---

### Post by Impsy on 2006-06-07
I actually found and read that thread already, thought it might be dead so my hopes went really really low. Do you think it will be out soon.

---

### Post by morequarky on 2006-06-07
On another computer you could run apt-get -d (download only) and copy the packages you download onto a CD.  :)

Why does your computer have no internet?

---

### Post by Impsy on 2006-06-07
dont know, its just an older computer i put in my room. I'm buying a wireless router and one of those wireless cards and putting it in, the guy at the store said i could get internet on it then :p Hopefully it detects it or something because then im screwed, i cant even get any games working on Xubuntu or any sound. w0w ;p

---

### Post by rcarring on 2006-06-07
Do you have cable modem access or dsl access to a dsl modem where you live, as ethernet may be a cheaper solution with a nice 4 port router connected to your modem

---

### Post by Impsy on 2006-06-07
well we have a DSL thing in the basement and my computer is upstairs.

---

### Post by rcarring on 2006-06-07
If the DSL thing is wireless then the store guy is correct.

---

### Post by Impsy on 2006-06-07
well umm i was gonna buy the wireless card and the wireless modem/router thing.

---

### Post by morequarky on 2006-06-07
It is a desktop computer?
There is no "phone looking jack" on it?
How many floors?

Signal might not be the wonderful through the floor.

Use ethernet cat 5 cable to get the wireless router in a location that gets you the best signal.  Wireless Technology has channels. 1 to 11 I think, anyway change the channel in your router and see if you get a better signal.  If you can get the router on the same floor it will help.  If you have the dough you can but a "wireless hub" or router to REPEAT the signal downstairs to upstairs.  aka linking the router/hub together.

Remember a wireless router spreads out its signal in all directions...if you get an antanna attachment you can FOCUS the waves in ONE direction which might help you if you have issues.

If you have a desktop, get a wireless PCI card might be the best.  USB may not be supported very well.

---

### Post by Impsy on 2006-06-07
They are two desktop computers, two floor home which is my basement and normal level. I have two internet box thingies here which are : a small one that says "SMC Ez Switch 10/100  105SDT" and a bigger one that has westell on the front and theres an ethernet cord (theres a bunch of other wires as well :p), what do these two boxes do.

---

### Post by morequarky on 2006-06-07
I am going to say that that the [COLOR="Red"]westell[/COLOR] is your ethernet/cable modem.  That converts phone company internet language into standard ethernet language.  

The other box is a [COLOR="Red"]ethernet switch[/COLOR].  It allows more computers to use one internet connection.  The switch accepts the Internet Protocol Address(IP) from the modem.  Then assigns random addresses to the computers attached to it.  The switch is also called a "router" because it directs or routes internet traffic.

You might be able to edit your switch settings by going to 192.168.1.1 in a browser of a computer attached to the switch.  

Your house is a small LAN(Local Area Network).

Does that make sense?

---

### Post by Impsy on 2006-06-07
ok so what will i need to buy then?

---

### Post by morequarky on 2006-06-07
Either of the following:

1. A long cat 5 [COLOR="SeaGreen"]wire[/COLOR] to run from the switch to your computer upstairs attached to a ethernet card in your computer.

2. A wireless "[COLOR="SeaGreen"]switch[/COLOR]" [COLOR="Red"]replaces[/COLOR] the switch you have, which then connects wirelessly to the computer upstairs.

3. A wireless [COLOR="SeaGreen"]hub[/COLOR] attaches to your current switch by wire.  The hub would then attach to your computer upstairs wirelessly.  A hub by definition extends a network.  So here the hub would extend your network to computers with wireless cards/ability.

I suggest number 2.

You could combine two and three by
Switch A you currently have
Switch B has wireless ability
Hub C has wireless ability.

Do this IF and ONLY IF the signal strength between upstairs computer and Switch B downstairs is not good and you have enough cash.

Switch B replaces switch A.  Hub C would be upstairs in a location where it gets the best signal from switch B.  Switch B would then communicate wirelessly with Hub c.  Hub C would then communicate with Upstairs computer with a better signal strength being that it doesn't have to send a signal through the floor.

Typically option 2 is the best.  Option 3 may be cheaper, but you can't use a hub without a switch.

Linksys has great equipment.  I use a Linksys WRT54GC.  I have a desktop, two laptops, and a PDA all online.

---

