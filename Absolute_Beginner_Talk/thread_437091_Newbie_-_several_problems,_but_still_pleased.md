---
title: "Newbie - several problems, but still pleased"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by hamishw on 2007-05-08
Hi
I was messing with ubuntu as a live cd and ended up overwriting windows, so am now stuck with Ubuntu, not that I am unhappy about that, it's great.
I have a couple of problems....
1 - workspace on cube has stopped working, not sure why but it has.
2 - can't get video feeds from bbc to work (it want's realplayer or Win media player.
3 - when I turn on the pc it has stopped asking me for login/password.

Please can you help me!!!!
Thanks
Hamish

---

### Post by Obor on 2007-05-08
1. What happens when you go to System - Preferences - Desktop effects / GL Desktop?

2. Look at streaming video section on this page (you might wanna install the rest as well to get other things working) [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

3. System - Admin - Login window - security tab. There should be a automatic login disable

Hope it helps

---

### Post by starcraft.man on 2007-05-08
> **hamishw said:**
> Hi
I was messing with ubuntu as a live cd and ended up overwriting windows, so am now stuck with Ubuntu, not that I am unhappy about that, it's great.
I have a couple of problems....
1 - workspace on cube has stopped working, not sure why but it has.
2 - can't get video feeds from bbc to work (it want's realplayer or Win media player.
3 - when I turn on the pc it has stopped asking me for login/password.

Please can you help me!!!!
Thanks
Hamish

Ok, I will answer in reverse order just because I am canadian and I can :p

3) This is very odd... you actually have to turn it off to get this to happen, it also isn't a good thing if you want to prevent people from using your account. I can't say I'm that sure how it happened, did you modify any specific settings? EDIT: Ya, check the setting Tobor pointed out :)

2) That shouldn't be too difficult to fix...  A) Make sure you of course have real play 10.0.8 installed(In terminal, type "sudo aptitude install realplay). B) Install [this]("https://addons.mozilla.org/en-US/firefox/addon/446") firefox extension. C) When it asks you to configure when you start back up, it will detect Realplayer and ask you what player should play that format, choose real player.

1) There are lots of reasons why the cube can stop working, I don't really personally like the way compiz has been integrated cuz it feels more like a hack and you can't customize from default. Did you check desktop effects so that it didn't turn itself off? If it is on, maybe it just needs to be reinstalled properly... details on installing compiz are available in ubuntuguide, its in my sig :)

---

### Post by hamishw on 2007-05-08
Hi
thanks for your assistance, Login sorted, cube sorted and working on media stuff!
Hamish

---

### Post by cloud1 on 2007-05-09
> **starcraft.man said:**
> Ok, I will answer in reverse order just because I am canadian and I can :p
...
1) There are lots of reasons why the cube can stop working, I don't really personally like the way compiz has been integrated cuz it feels more like a hack and you can't customize from default. Did you check desktop effects so that it didn't turn itself off? If it is on, maybe it just needs to be reinstalled properly... details on installing compiz are available in ubuntuguide, its in my sig :)

Thanks setting hsize to 4 and number_of_desktops to 1 solved the problem. Now my cube is 

working again.

---

