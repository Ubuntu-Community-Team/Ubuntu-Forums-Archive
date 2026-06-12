---
title: "CPU Frequency - basic question about setting it up"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by szymon_g on 2007-03-26
hi....
i'd like to say sorry if there was thread like mine before.

i've got a some questions about manipulating of cpu's frequency: i've got a core 2 duo processor, and i would like to have a following settings :

on the battery: the lowest frequency only (1ghz)
on ac-adapter : usuallly the lowest, but when a using of processor will by bigger than eg 60% and longer than eg.30sec then it should go to the higher frequency (1gzg ->1.33 ->1.67 -> 2ghz)- up to the highest (2ghz), if necessery.

i dont use gnome, so i wuld be happy if this method should work withat gnome (and any window environment, if necessery)...

i've been looking for solution a while, but i haven't found anything interesting (prabably i didn't looking well :-/). any ideas?

i'm not asking for making a work for me, i just ask for any suggestion (if you done it before me you could share your knowledge :-))

i use a ubuntu 6.10


szymon

---

### Post by Kobalt on 2007-03-26
You can follow [these instructions]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features"), this is in command line so common to all desktop environments. But you might find tools in the repos (use Adept to find them) that will do this for you in GUI, such as klaptop for KDE...

---

### Post by szymon_g on 2007-03-26
hi
thank you for response,
but it's not really what i'm looking for: i've checked and used this way: in this way selected governor (in my case- conservative) is alweys on... i'd like to know, how can i setup it in this way, that when i'll unplugged ac-adapter from my laptop (or when i will start it on batteries) the governor will be a 'powersave'... and how can i setup the rules of conservative governer (i.e. : i would like to configure it that when cpu will by loaded 60% or more, after 30 sec it will change cpu's frequency into higher (1gz-> 1.33)? and if still will be more than 60% than make a cpu faster once and once again (1.33 --> 1.67 --> 2ghz)

your sinecerely
szymon g.

---

### Post by Kobalt on 2007-03-26
I'm not a KDE expert, but I think I could manage all of this stuff directly through the power management in the configuration centre...

---

### Post by szymon_g on 2007-03-26
i'm using icewm :-| beside i used to hope that will work in cli as well :-/

---

