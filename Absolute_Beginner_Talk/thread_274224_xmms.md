---
title: "xmms"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by mee.six on 2006-10-09
I'm sorry, maybe here is lots of such threads... but I haven't found one.
So... my XMMS runs rather strange.. it looks nicely in the places where it uses skins..but standart elements (menus) are 2 times bigger and looks like they don't understand unicode (I'm using russian locale, and menus look like "'$']'")

is there any way to fix it? :( 


Thanks for help:)

---

### Post by aldegaz on 2006-10-09
Have you tried to use amarok instead? I used xmms and now I am totally devoted to amarok.
If you decide to give amarok a try:
```
sudo apt-get install amarok
```

---

### Post by Perfect Storm on 2006-10-09
The reason is that xmms is an old application which uses GTK1 engine. Xmms havn't been developed on for quiet some time (still got some annoying bugs).

If you want the top notch check audacious (which also uses GTK2): [http://audacious-media-player.org/](http://audacious-media-player.org/)

---

### Post by bulldog on 2006-10-09
> **mee.six said:**
> I'm sorry, maybe here is lots of such threads... but I haven't found one.
So... my XMMS runs rather strange.. it looks nicely in the places where it uses skins..but standart elements (menus) are 2 times bigger and looks like they don't understand unicode (I'm using russian locale, and menus look like "'$']'")

is there any way to fix it? :( 


Thanks for help:)

The menu's look a little outdated indeed,but I know no way to fix it.

Have to say I almost never use them though :D

---

### Post by mee.six on 2006-10-09
ok, I'll try another player :) thanks for support

---

### Post by mee.six on 2006-10-09
it's so huge :( it is said that it needs ~140MB to be installed...maybe here are some smaller players? :(


[http://audacious-media-player.org](http://audacious-media-player.org) - doesn't work :(

---

### Post by Perfect Storm on 2006-10-09
The site is down.

---

### Post by IYY on 2006-10-09
If you want something that acts exactly like XMMS, but supports unicode and GTK2 menus, your friend is Beep Media Player.

```
sudo aptitude install beep-media-player
```

---

### Post by skymt on 2006-10-09
> **IYY said:**
> If you want something that acts exactly like XMMS, but supports unicode and GTK2 menus, your friend is Beep Media Player.

```
sudo aptitude install beep-media-player
```

Audacious is a fork of Beep, which is a fork of XMMS. So Audacious is the latest. Or, if you like, there's another fork of Beep, called BMP-X. Take your pick, there are plenty. ;)

---

### Post by smartalecks on 2006-10-09
**INSTALLING AMAROK ON EDGY EFT**

I reccomend amaroK. You will have to add a repopository, and then install from there. Here are instructions (in terminal (Apps > Acces > Terminal)):

```

$  wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg 
$  sudo apt-key add kubuntu-packages-jriddell-key.gpg

```

Then 

```

$  sudo gedit /etc/apt/sources.list

```

Add this to the bottom

```

$  deb http://kubuntu.org/packages/amarok-144 edgy main

```

And do these (in terminal)

```

$  sudo apt-get update
$  sudo apt-get install amarok amarok-xine 

```

Install whatever dependencies it asks for.
If you don't like amaroK (I LOVE it) then there is also Banshee (available in the community maintained repo (disable after use)) and Rhythm Box.

---

### Post by mee.six on 2006-10-10
:) thanks a lot for help :) all try them :) 

(Your community is great! :))

---

### Post by mee.six on 2006-10-10
People, amarok is great :) It said "Unable to play MP3, maybe you use Ubuntu" :))) in fact here is a button "Install MP3 Support" but it does nothing at all :(

can I fix it? :)

---

### Post by smartalecks on 2006-10-10
To add support for MP3's, you can install all the libraries by hand or use Automatix (very easy :) ):

This will install Automatix
```

$  gksudo gedit /etc/apt/sources.list

```

Add this to the bottom

```

deb http://www.getautomatix.com/apt dapper main

```

Then

```

$  wget http://www.getautomatix.com/apt/key.gpg.asc
$  gpg --import key.gpg.asc
$  gpg --export --armor 521A9C7C | sudo apt-key add -

```

Now

```

$  sudo apt-get update
$  sudo apt-get install automatix2

```

Run Automatix now (Applications>Systemtools>Automatix), when it has finished starting up, under the install tab click "Multimedia." Then check the box next to "Multimedia Codecs" and click "Start." I think that this adds MP3 support, if not it might be the "AUD-DVD Codecs." Read the message when it starts up about it first, however. When exiting Automatix, be sure to click "YES" when it asks whether you want to restore your sources.list to the original state.

---

### Post by Perfect Storm on 2006-10-10
Don't use "sudo gedit" but "gksudo gedit" instead. Or "sudo nano".

---

### Post by deadgobby on 2006-10-10
Sound is not working after update. How or what to get this going up agian???
PLease see my post... PLEASE!
Thanks
Gobby

---

### Post by smartalecks on 2006-10-10
> **Artificial Intelligence said:**
> Don't use "sudo gedit" but "gksudo gedit" instead. Or "sudo nano".

Whoops. Error on my part. Edited.

> **deadgobby said:**
> Sound is not working after update. How or what to get this going up agian???
PLease see my post... PLEASE!
Thanks
Gobby

What update? What did you do? What post? Please explain...

---

### Post by mee.six on 2006-10-11
Thanks a lot for help :)

---

