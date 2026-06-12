---
title: "very close to smashing computer"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by robinc on 2006-08-21
proftpd decided to create some users on it's own after i loaded in a .conf from the internet, I guess that's the downfall of being forced to run something as ROOT.

anyway now I can't *&%^ing delete the users, if i delete them using the users and groups panel...next time I open it...they're back :) :) :) :) :) :)  YAY!

I'm literally about to smash my own face with a brick.

please help me :(

---

### Post by Kilz on 2006-08-21
> **robinc said:**
> proftpd decided to create some users on it's own after i loaded in a .conf from the internet, I guess that's the downfall of being forced to run something as ROOT.

anyway now I can't *&%^ing delete the users, if i delete them using the users and groups panel...next time I open it...they're back :) :) :) :) :) :)  YAY!

I'm literally about to smash my own face with a brick.

please help me :(

Have you tried removing the .conf file? That or reading the conf file and seeing if the users are in it and can be edited out?

---

### Post by steve.horsley on 2006-08-21
Don't do that. It'll hurt.

I presume that proftpd is creating the users by itself. Try killing the profpd process and then deleting the users to prove the point. Then prove that the users are only recreated as proftpd starts up.

Assuning you can prove this, I don't know what to suggest. Undo the proftp config you downloaded? It depends on how much you need proftp I suppose - I'm not familiar with it.

If the users are still recreated when proftp is not running then I would start to worry about what's gotten into my PC. Maybe even to the point of re-formatting and reinstalling. I would certainly try and track down the rogue process.

You could try deleting the groups and users by hand if you doubt that the GUI editor is failing to delete them. You can at least view the files concerned to get at the underlying truth. The files are /etc/passwd and /etc/group, for users and groups respectively. Be careful editing these. You can delete any user or group by deleting the matching line, and you can of course delete vital users and groups leaving your machine useless.

---

### Post by robinc on 2006-08-21
ahh I've had a diet coke and a jacket potato and I'm calm now...thank you for your responses.

even when proftpd is not running the users come back again, I think i'm just going to wipe the machine and run windows xp and filezilla on there, less headaches...but slower performance, thanks everyone.

---

### Post by xpod on 2006-08-21
Well if your going to GIVE UP that easy.....????????????????????
Wheres your determination man??????????????

---

### Post by robinc on 2006-08-21
I have been trying for a few days and I'm a grown man on the verge of TEARS!!!!

---

### Post by xpod on 2006-08-21
Nothing wrong with a few tears......ASK my missus...she`s for ever bubbling over something.

Listen you obviously know something about computers so you must already KNOW that they can be a right pain in the backside regardless of what OS you use OR even move to.I dont know jack s**t about these things and only switched a pc on for the first time.. since my mom bought me a commodore 64 20odd years ago...a few months ago.

I dont mean to rile you even more than what you obviously already are BUT...
IT`s only a computer ...so are you going to let some minor little setback put you completely off WHEN ..with a wee bit more patience you could be using the   
best new toy you`ve EVER had???????????????????????

---

### Post by robinc on 2006-08-21
very true.

everything else installed and worked perfectly

Apache
MySQL
PHP       -> PhpMyAdmin

just the DAMN ftp server, I will keep trying.

---

### Post by xpod on 2006-08-21
Well.there you go then.So it`s not all as bad as you first alluded to is it.
And you would`nt have "smashed your computer" up would you????.......You`d have just crawled  back to your xp sys with your head in hands.

AND we dont want that do we....Im sure with a little patience and mabey even giving some of the pro`s a bit of detail about where your breaking down they should be able to help you more than i ever could.

Better still im actually quite sure IF you put your mind to it you`ll even suss it out youself..............THEN how good will you feel with yourself eh

PS......smile:confused: :-k :D

---

### Post by kebes on 2006-08-21
My suggestion would be to get rid of that mysterious configuration. Uninstall proftp completely:
```
sudo aptitude remove proftp --purge-unused
```
Then go and delete that config file that you've been using. 

I would hope the problem no longer appears. If it does, then I would guess it's actually not proftp making the new users... it's some other process. If the problem is fixed, then reinstall proftp:
```

sudo aptitude install proftp
```
And use the default config. You can manually reconfigure proftp to do what you want (whatever that config file you downloaded was supposed to do).


If the problem still exists when proftp is fully uninstalled, then you've got to search for a different source to your problems. Do the new users reappear instantly, only when you reboot, or what? You can use the command "top" to watch what processes are running... might give you a clue as to what is creating the users.

---

### Post by xpod on 2006-08-21
Sorry if i was a bit condecending mate....JUST trying to make you all the more determined.Dont want you to be giving in without a fight.

---

### Post by Scorpuk on 2006-08-21
Can you show us your proftpd.conf file?

If all else fails and you end up reinstalling then you could follow this HOWTO guide. 

[link]("http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd")

I used "B - The secure way" and eventually got it working by adding in passive port option and adding those ports to my routers forwarding range. You can see my proftpd.conf file on page 22 i think. I have removed one item to keep my url hidden.


Anywho hope you get it working as its deff worth it. :-)


John.

---

### Post by harisund on 2006-08-21
A couple of things. 

One thing you could always do is start a fresh. Completely remove proftpd from your system. Use 'aptitude purge proftpd' as root (or with sudo) and remove your old config file. 

By the way, might I ask what is the name of this new user that keeps getting created and that keeps bugging you? 

To ensure that he doesnt' exist list out the contents of /etc/passwd and look for the new user's name. If it is not in there, it is not in your system. If it is there, use 'userdel -r user_name' to cleanly wipe out the user from your system

Then use your system for a while to ensure that the new user doesn't get created again, and satisfy yourself of that. 

Now install proftpd. One thing you can't help is the fact that the proftpd installs a system user called 'ftp' which is used for anonymous ftp access and stuff. If this is the user you are complaining about I doubt if there's anything that can be done about it 

Can you list the .conf file you downloaded from the internet here perhaps?

---

