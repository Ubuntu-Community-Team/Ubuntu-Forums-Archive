---
title: "How do I search for available WLANs?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by Oputres on 2006-06-23
Hi.

How do I search for available WLANs in my neighbourhood? Is there a package I need to download? I know that there are several Wlans available since my WinXP computers can see them.

After my (very short) success of getting my USB Wifi device to work I found these Wlans under ESSID from properties of the Wireless Lan under Network from the Administration menu. But now I only get my own Essid which doesn't work for some reason.

And how do I keep the connection after a reboot? Thus I want Ubuntu to connect to my wireless router from start.

---

### Post by joselin on 2006-06-23
[quote=Oputres]Hi.

How do I search for available WLANs in my neighbourhood? Is there a package I need to download? I know that there are several Wlans available since my WinXP computers can see them.

After my (very short) success of getting my USB Wifi device to work I found these Wlans under ESSID from properties of the Wireless Lan under Network from the Administration menu. But now I only get my own Essid which doesn't work for some reason.

And how do I keep the connection after a reboot? Thus I want Ubuntu to connect to my wireless router from start.[/quote]

I think the best way is using kismet

```

sudo apt-get install kismet

```

---

### Post by TheMono on 2006-06-23
I could be misunderstanding, but Network Manager should cover that fine. Just search for it in synaptic.

---

### Post by Oputres on 2006-06-23
[QUOTE=joselin]I think the best way is using kismet

```

sudo apt-get install kismet

```[/QUOTE]

Hmm, "Could not find the package kismet". I also searched for it in Synaptic but it wasn't there either :( 

Any more suggestions anyone?

---

### Post by hotbrainz on 2006-06-23
Please do:

sudo apt-get update 

This will get all the latest packages and then do

sudo apt-get install kismet

Hope this helps..

---

### Post by joselin on 2006-06-23
[quote=Oputres]Hmm, "Could not find the package kismet". I also searched for it in Synaptic but it wasn't there either :( 

Any more suggestions anyone?[/quote]

Be sure you have universe and multiverse repositories enabled.

Regards

---

### Post by Oputres on 2006-06-23
[QUOTE=joselin]Be sure you have universe and multiverse repositories enabled.

Regards[/QUOTE]

I will try both tips soon but how do I enable these repositories? I remember I did this in Kubuntu but I cant recall where exactly I did what ](*,)

---

### Post by cbudden on 2006-06-23
[QUOTE=Oputres]I will try both tips soon but how do I enable these repositories? I remember I did this in Kubuntu but I cant recall where exactly I did what ](*,)[/QUOTE]

[QUOTE=rado_london]Hi. I am one very proud owner of HP laptop. However the suspend to ram doesnt work. When it tries to wake up the whole system freeze. then I have to restart it the hard way. My question is:
Has anyone of you guys so far found a way to fix this annoying bug?

Thanks[/QUOTE]
 

System-> Admin-> Synaptic.

Then click settings -> repos, and make sure all the entries are ticked.

---

### Post by joselin on 2006-06-23
[quote=cbudden]System-> Admin-> Synaptic.

Then click settings -> repos, and make sure all the entries are ticked.[/quote]

Other way is uncomment all entries that start with deb in file /etc/apt/sources.list

Cheers

---

### Post by Oputres on 2006-07-01
Well this feels pretty awkward to ask but where can I find Kismet after I installed it? It's nowhere in the menus. And by the way, how do I add something to the menus, i.e. the Program-menu?

---

### Post by digby on 2006-07-01
I'm not sure where it would have been put, exactly, but you can find it by running (in a terminal)```
sudo updatedb
locate kismet
```

To add/remove/edit menu entries, go to Applications > Accessories > Alacarte Menu Editor

---

### Post by Oputres on 2006-07-01
Anyone? Please!

---

