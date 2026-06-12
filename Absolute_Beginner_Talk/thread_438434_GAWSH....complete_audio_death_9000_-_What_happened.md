---
title: "GAWSH....complete audio death 9000 - What happened??"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by rubix64 on 2007-05-09
O.K. I know this is going to be one of those things that ends ups being so simple that I spend a day meditating on the meaning of humble and promise not to be such a git in the future byt at this point I am stumped so sacrificing my pride on the alter that has become my feisty desktop I ask....

WHY HAS MY SOUND DISSAPPEARED??

I had working sound via my nvidia geforce 7900 (restricted drivers enabled) from the minute I installed and at somepoint in the last day or so I lost sound. all sound. even the soothing little african jingle at boot :(

Ive tried near everything I could think of and am stumped.

the system>pref>sound under soundplayback with autodetect selected doesent even make a peep.

while I love serenity I WANT MY SOUIND back...sorry didnt realize I was raising my voice.

Thanks in advance ubuntu ninjas

rbx

---

### Post by mills on 2007-05-09
have you gone through [this troubleshooting guide?]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

ps, you love serenity but live in bangkok, hmm strange :lolflag:

---

### Post by Shazaam on 2007-05-09
Did you check your cables? :)

---

### Post by rubix64 on 2007-05-09
Whew...got it.

Thanks for the super audio ts link mills. It did the trick. I needed to remove the alsa pkg "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils" and then reinstall "sudo apt-get install linux-sound-base alsa-base alsa-utils".

checked my alsa sound settings with alsamixer and voila!

Khap kun khap guys I appreciate it.

ps. re:BKK - serenity is wherever you seek it but having ko samet 3 hrs away doenst hurt.

cheers
rbx

---

