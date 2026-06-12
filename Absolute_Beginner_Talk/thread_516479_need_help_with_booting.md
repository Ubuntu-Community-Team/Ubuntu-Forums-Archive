---
title: "need help with booting"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by df_Fer on 2007-08-03
hi guys i installed Ubuntu ultimate for VMware player  and I'm totally newbie  after that i just jumped up to installing postgresql 8.2 (( thanks to copy and past)  i wrote too many things over there  too many important notes ( at least to me )   after i shut down the pc and tried to turn it on again  i got blank screen the mouse courser keep showing the loading icon  but it stays like this ...... now here's the thing i need  my text files back note that i can login in to root , i pressed ESC to get to setup then chose the last day  to boot from  but i can't see th Desktop and GUI stuff only CL .



k sorry for my English it sucks i know but if you didn't understand anything please let me know

---

### Post by charlier653 on 2007-08-03
look in the foruns on how to restart X,

I've done similar things in the past several days, but can't for the life of me remember how to reconfig X and then restart X

I am assuming you are not on Kubuntu or ??

---

### Post by df_Fer on 2007-08-03
k  sorry  but i didn't understand ^_^ i thought this the ( total newbies place)  you can't imagine how newbie i am ...... i'm in a hurry right now thanx for trying to help and i will be back  to check up what you said more closly

---

### Post by S15_88 on 2007-08-03
sudo dpkg-reconfigure xserver-xorg 

or try 

ctrl + alt + Bacspace

---

### Post by df_Fer on 2007-08-03
thank you  i will try that 




i will come back later to tell you what happened ^_^   



lots of thatnx to all of you guys

---

### Post by df_Fer on 2007-08-03
i couldn't use the CTRL +ALT+backspace cause when i press CTRL + ALT in VMware i get back to windows
so i used  sudo dpkg-reconfigure xserver-xorg  and i went to lots of stuff i don't know what they r hardware stuff 



what abo0ut the server X and restart X thingy   ? should i try that ?

---

