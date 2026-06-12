---
title: "Off Switch."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by wavemaker on 2008-01-01
Gooday all, first post on the forum. I have been using KUBUNTU and actually arrived at UBUNTU by mistake. However whilst I'm here I would like to know where the off switch is. The little green bloke top right doesn't give me the option to turn the computer off. Any help appreciated. Regards from the land down under, James.
PS. Happy new year.

---

### Post by doorknob60 on 2008-01-01
Welcome to the forums, wavemaker! We give support for all *buntus so you're fine posting here. To shut down the computer in Kubuntu, click the K menu in the bottom left and click Log Out (Or something like that) and then click shut down.

---

### Post by rivalarrival on 2008-01-01
I have a similar problem on one machine - the GUI power button would allow me to logout, suspend, and a couple other options, but no restart or power off.

I suspect it is a problem with permission settings, but I haven't bothered to track it down. since I always have a terminal window open and the machine in question is a production server and always on, I just type "sudo reboot" on the rare occasions when Ubuntu needs to be reset.

Still, if anyone can point me in the right direction, I'd appreciate it!

---

### Post by AvengingAngel718 on 2008-01-01
ok it sounds to me like when you click the log out icon it doesnt give you the shut down option, is that right? if thats the case, go into your options and open up the Login Window manager. Under the Local tab, make sure the box is checked next to "show actions menu". I've had that problem before and this fixed it for me.

---

### Post by natehall on 2008-01-01
sudo halt will also shut your machine down. Alt. Ctrl f1 if you need a terminal to do that in.

---

### Post by rivalarrival on 2008-01-01
I think that's gonna do it, Thanks!

---

### Post by hyper_ch on 2008-01-01
or
```

sudo poweroff

```

---

### Post by wavemaker on 2008-01-02
Thanks for the replys. AA1718 you got it in 1. Can you point me to the options you mentioned, I can't seem to find them.

---

### Post by wavemaker on 2008-01-03
Gooday again, I located the log in manager but there was no "local" option nor any of adding an off switch. I hope you can point this out for me. TiA. Regards, James.

---

### Post by AvengingAngel718 on 2008-01-17
wow, i guess i should have subscribed to this thread and i wpuld have been able to reply sooner lol

if you're still having this problem, the options i mentioned are under System (in the upper right corner of the screen) > Administration > Login Window

after you open that up, there should be a series of tabs at the top of the window. click on "local" (second one over) and you should see vaious login themes you can use. underneath where you can switch those, there is a box for the option "show actions menu". Make sure it's checked.

it worked for me when i had this problem a few months ago.

let me know how it turns out, and i'm sorry it took so long to reply. i'm now subscribed so i'll know whats going on :)

---

