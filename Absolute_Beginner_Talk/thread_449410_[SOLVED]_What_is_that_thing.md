---
title: "[SOLVED] What is that thing?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-05-20
hey i saw this Vid on YouTube
[http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)
i'm dying to know what the hell that quick launch bar is called, and how i can install it!

it looks like it would be something really handy to have (and cool to show ppl) - i'd be very grateful if i could find this one out.

i've got Beryl working no problems (i couldn't help myself, i still haven't got my printers working) Beryl is so much fun tho!

---

### Post by overdrank on 2007-05-20
> **Beatbreaker said:**
> hey i saw this Vid on YouTube
[http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)
i'm dying to know what the hell that quick launch bar is called, and how i can install it!

it looks like it would be something really handy to have (and cool to show ppl) - i'd be very grateful if i could find this one out.

i've got Beryl working no problems (i couldn't help myself, i still haven't got my printers working) Beryl is so much fun tho!

I believe it is 
Kiba-dock: [http://www.kiba-dock.org](http://www.kiba-dock.org)
But I could be wrong!;)

---

### Post by Beatbreaker on 2007-05-20
thankx for the reply, your most definately right!

i've got no idea how to install it tho - i've read this and i don't have a clue where to start, if i type that stuff in a terminal i get nothing happening

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)

---

### Post by seshomaru samma on 2007-05-20
you need to provide more info to get help
what do you mean you type 'stuff' in the terminal? 
in the link you sent there is an ubuntu section
the first command you should run is :
```
sudo gedit /etc/apt/sources.list
```
(no need for #)
nothing's happening when you run this command?

---

### Post by taurus on 2007-05-20
> **seshomaru samma said:**
> you need to provide more info to get help
what do you mean you type 'stuff' in the terminal? 
in the link you sent there is an ubuntu section
the first command you should run is :
```
sudo gedit /etc/apt/sources.list
```


Please use gksudo when you run gedit.

```
**gksudo** gedit /etc/apt/sources.list
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by overdrank on 2007-05-20
> **taurus said:**
> Please use gksudo when you run gedit.

```
**gksudo** gedit /etc/apt/sources.list
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Great tip thanks!!!!!!!=D>

---

### Post by Beatbreaker on 2007-05-21
I'm not going to quote anyone here because you're all been very helpful!

sorry i was being a little vague before, i guess i was getting a little short and frustrated with it since nothing i was trying was working. I've got alot to learn here and i think the main thing is being patient with myself.

yes it was the case when i was writing this:

> sudo gedit /etc/apt/sources.list

..nothing was happening, i wasn't sure if i was to expect something. I wasn't even sure if i even had to install something called Sudo because of the little response i was getting.

---

### Post by overdrank on 2007-05-21
> **Beatbreaker said:**
> I'm not going to quote anyone here because you're all been very helpful!

sorry i was being a little vague before, i guess i was getting a little short and frustrated with it since nothing i was trying was working. I've got alot to learn here and i think the main thing is being patient with myself.

yes it was the case when i was writing this:



..nothing was happening, i wasn't sure if i was to expect something. I wasn't even sure if i even had to install something called Sudo because of the little response i was getting.

Hi I understand why you are frustrated. In the link of installing Kiba-dock you can add those link in you software repo's, Then add the key's from terminal and you should be on the go.
This link maybe of some help!
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
:popcorn:

---

### Post by Beatbreaker on 2007-05-27
ok i got it working, i followed the instructions on [http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock) - though i didn't know what i was diong really - I removed the # out of the equasion also.

so now i've got the dock up and working - the physics in it runs very slow unfortuantely, i doubt it's my processor (AMD64 3200+) - i might have to tweak some preferences in it so that it isn't so demanding - it works perfectly without the physics i've tested too.

---

