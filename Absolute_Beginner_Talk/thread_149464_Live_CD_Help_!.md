---
title: "Live CD Help !"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-23
I have a Gateway MX7118 and here are the specs:

2.2 ghz AMD processor
512 of ram
Ati Radeon Xpress 200M graphics card

A little bit after the ubuntu load screen I get "Failed to Start X" I can't do anything now. What should I do ? I have the AMD Live ISO but how can I get it to work ? I really need help on this one :(

---

### Post by bluevoodoo1 on 2006-03-23
Try...

```
sudo dpkg-reconfigure xserver-xorg
```

I did it with the Dapper Live CD a few weeks ago, and it worked just as it would if Dapper were installed. 

(probably don't need to use "sudo" with the Live CD)

---

### Post by xXx 0wn3d xXx on 2006-03-24
I can't get a command prompt. What should I do ???

---

### Post by Sef on 2006-03-24
> I can't get a command prompt. What should I do ???

Applications > Accessories > Terminal

---

### Post by xXx 0wn3d xXx on 2006-03-24
How is that going to help if I have no interface ????? I'm not that stupid.

---

### Post by wsanders on 2006-03-24
Ctrl-alt-F1 should get you there.

---

### Post by xXx 0wn3d xXx on 2006-03-24
ok, let me try that...maybe if this doesn't worl I'll try the dapper live cd: it's not 100 % stable but it's better then windows :)

---

### Post by xXx 0wn3d xXx on 2006-03-24
nope I still can't start x. Should I just give up ? If I can't get this can anyone give me some distros that are simple to use a debian based. Are their any simular to ubuntu. I'm thinking Suse or Fedora Core. Any other ideas. I also need to be able to dual boot it with windows xp.

---

### Post by xXx 0wn3d xXx on 2006-03-24
can someone give me advice ?

---

### Post by xXx 0wn3d xXx on 2006-03-24
please I really need help !

---

### Post by xXx 0wn3d xXx on 2006-03-24
Wow thanks for the help. I've been trying to get help for 3+ days but no one seems to want to help. And I'm really angry right now so I would appreciate any and all help. I'm ready to juist give up because no one wants to help. Then only reason that I am still sticking around is because I had such a good expericence with Ubuntu and I barely had any problems. Once again I am asking the Ubuntu Community for Support. Please, if you can help me.

---

### Post by bluevoodoo1 on 2006-03-24
You said you're using an Ati Radeon Xpress 200M graphics card right? Does the system also have onboard video? I've had a problem with my system recognizing my onboard video but NOT recognizing my video card (which is what my monitor was plugged into). If this is the case, then this might help. 

[http://ubuntuforums.org/showpost.php?p=839044&postcount=4](http://ubuntuforums.org/showpost.php?p=839044&postcount=4)

---

### Post by Magrioteli on 2006-03-24
[QUOTE=MasterChief1234]Wow thanks for the help. I've been trying to get help for 3+ days but no one seems to want to help. And I'm really angry right now so I would appreciate any and all help. I'm ready to juist give up because no one wants to help. Then only reason that I am still sticking around is because I had such a good expericence with Ubuntu and I barely had any problems. Once again I am asking the Ubuntu Community for Support. Please, if you can help me.[/QUOTE]

Sorry, but I have to state this. 
Gee!  People are answering you, aren't they? No one told you to...what ever. It isn't 911 you are calling, it's a forum of people who hang around in here for fun!

Your other thread "[COLOR="Red"]Need Serious Help !!!!!!!![/COLOR]"  was a tribute to Caps Lock! 

Why are you so angry? 

Peace & Out!

---

### Post by xXx 0wn3d xXx on 2006-03-24
[QUOTE=Magrioteli]Sorry, but I have to state this. 
Gee!  People are answering you, aren't they? No one told you to...what ever. It isn't 911 you are calling, it's a forum of people who hang around in here for fun!

Your other thread "[COLOR="Red"]Need Serious Help !!!!!!!![/COLOR]"  was a tribute to Caps Lock! 

Why are you so angry? 

Peace & Out![/QUOTE]
I'm angry b/c I've been trying to get Ubuntu to work for over 3 days and almost all of my threads have been ignored or haven't gotten much attention at all. I know this isn't 911 but what else am I supposed to do ?

---

### Post by RRS on 2006-03-24
Try the 32bit rather then the AMD (64bit) version.

I don't know about the live CD but when I installed the 64 in my AMD machine I never could get X confiquered properly so I tried the 32bit and everything worked "as advertised"

By the way, windows also has problems w/their 64bit OS.

---

### Post by harisund on 2006-03-24
Ok before you start cursing the Ubuntu forums, have you done your part? At the very least, have you searched for "Xpress 200M" within these forums? (Not even in Google.) (and using 32 bit, as the above poster has adviced)

A lot of people have had problems with Xpress 200M (I know, I have one too.) After you do an install, you will have to install the fglrx drivers by doing apt-get install fglrx something something.. search in the forums. There is a howto for installing latest ATI Drivers. I dont know if it works with the live cd, but it will after you install it.

---

