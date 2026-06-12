---
title: "What to de never really dealt o"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Terrapin77 on 2006-06-24
I left my laptop at my friends house and I get it back and now it has Ubuntu on it.  I have never really dealt with a linux style os before.  I am going to give it a whirl though.  He explained a little about how to run it.  I just cannot find how to install forstwire and flash player 8.

T77

---

### Post by hippy4life on 2006-06-24
[QUOTE=Terrapin77]I left my laptop at my friends house and I get it back and now it has Ubuntu on it.  I have never really dealt with a linux style os before.  I am going to give it a whirl though.  He explained a little about how to run it.  I just cannot find how to install forstwire and flash player 8.

T77[/QUOTE]


flashplayer 8 is not available for linux although version 7.xx is 

for frostwire see

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

if you're new to linux and ubuntu the ubuntu wiki is your best friend

---

### Post by Fass on 2006-06-24
[http://www.ubuntuforums.org/showthread.php?t=177646&highlight=frostwire](http://www.ubuntuforums.org/showthread.php?t=177646&highlight=frostwire)

You should try automatix. Flashplayer 8 is unavailable for Linux - only 7 has been released by Macromedia/Adobe.

---

### Post by K.Mandla on 2006-06-24
Start here for Java and Flash ...
 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Then try this for Frostwire ...

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

There might be easier ways to install these things; I don't use FrostWire myself so I'll defer to others if there's a better way to install it. :)

---

### Post by hippy4life on 2006-06-24
[QUOTE=Fass][http://www.ubuntuforums.org/showthread.php?t=177646&highlight=frostwire](http://www.ubuntuforums.org/showthread.php?t=177646&highlight=frostwire)

You should try automatix. Flashplayer 8 is unavailable for Linux - only 7 has been released by Macromedia/Adobe.[/QUOTE]


automatix is not recommended as it can seriously damage your system

---

### Post by Terrapin77 on 2006-06-24
Thanks for the replies .... quick ones too!

---

### Post by adam.tropics on 2006-06-25
> automatix is not recommended as it can seriously damage your system

Based on...? I thought this s#$# had been put to bed months ago.

---

### Post by Fass on 2006-06-25
[QUOTE=hippy4life]automatix is not recommended as it can seriously damage your system[/QUOTE]

Since when and based on what?

---

### Post by hippy4life on 2006-06-25
[QUOTE=Fass]Since when and based on what?[/QUOTE]


I've had problems with it before which screwed my system and forced me to do a full re install to correct. if its been fixed then great. but i still feel its best for a noob (myself included) to learn how to do things the proper way first, i see automatix as a last option only.

although i have heard that easyubuntu is much better and simpler if needs be, although i havent tried it myself.

---

### Post by Terrapin77 on 2006-06-25
Well I continue to get an error message.

myusername@computer187:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

---

### Post by adam.tropics on 2006-06-25
> forced me to do a full re install to correct.

...well if you're into doing everything the proper way, then there aint much that could 'force' you to reinstall.Also I think the point of automatix/bumps/easy are that they are the first option, not the last.

---

### Post by Drakkor on 2006-06-25
Get EasyUbuntu

---

### Post by adam.tropics on 2006-06-25
Terrapin77 - you may want to check your repos. You need multiverse for the flashplugin.

---

### Post by adam.tropics on 2006-06-25
[QUOTE=Terrapin77]I left my laptop at my friends house and I get it back and now it has Ubuntu on it. 

T77[/QUOTE]
On a side note, that rocks! I am considering my world domination plan, and reckon if we all went to our nearest local public library and did this, we would be a step closer!!!

---

### Post by hippy4life on 2006-06-25
[QUOTE=adam.tropics]...well if you're into doing everything the proper way, then there aint much that could 'force' you to reinstall.Also I think the point of automatix/bumps/easy are that they are the first option, not the last.[/QUOTE]

try helping this guy out here rather than flooding his thread and flaming me.

i stated my dislike for automatix if you think otherwise try forming an informed responce that this guy can make a decision on for himself. you like automatix for x reasons, i've had problems with it in the past for x reasons. 

end of story, dont take it as a personal attack that someone holds a different opinion from you, and whatever my reasons may be im entitled to them regardless of how much of a linux guru i am or am not.

---

### Post by Terrapin77 on 2006-06-25
Well I think that I am about done with Ubuntu.  I like it other than the fact that I cannot seem to install anything I need in everyday computer use.

---

### Post by hippy4life on 2006-06-25
perhaps what your friend should have done is set you up with a 'dual boot'

that way you could still boot into windows but you would also have the option for booting to ubuntu, you could explore linux in your own time and still retain the windows.

lots of users, myself included started off this way and its a good way to learn without getting too frustrated.

---

### Post by user1397 on 2006-06-25
[quote=Terrapin77]Well I think that I am about done with Ubuntu.  I like it other than the fact that I cannot seem to install anything I need in everyday computer use.[/quote]No wait! Don't give up yet!  Here is what you need to do:
First enable the multiverse repositories, [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html").

Then, to install flash, just open a terminal (applications > accessories > terminal), and type in ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

For frostwire, just go [here.]("https://help.ubuntu.com/community/FrostWire")

---

### Post by Terrapin77 on 2006-06-25
[QUOTE=erik1397]No wait! Don't give up yet!  Here is what you need to do:
First enable the multiverse repositories, [here]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html").

Then, to install flash, just open a terminal (applications > accessories > terminal), and type in ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

For frostwire, just go [here.]("https://help.ubuntu.com/community/FrostWire")[/QUOTE]

Thank you much.

---

