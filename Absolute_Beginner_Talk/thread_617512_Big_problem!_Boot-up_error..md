---
title: "Big problem! Boot-up error."
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by MONODA on 2007-11-19
Hi I am still kinda new to ubuntu, I started using it about a month ago, and have encountered many weird problems. First of all whenever I boot up, I get a screen saying, failed to load mem resource. But my computer boots normally. What do you think this means?? Any help would be appreciated. thanx

---

### Post by Inxsible on 2007-11-19
> **MONODA said:**
> Hi I am still kinda new to ubuntu, I started using it about a month ago, and have encountered many weird problems. First of all whenever I boot up, I get a screen saying, failed to load mem resource. But my computer boots normally. What do you think this means?? Any help would be appreciated. thanxThat has been a problem for HP laptops. Even mine does it. There is nothing to worry about. Like you said, everything works normally.

I have seen that since Feisty on my HP laptop. Before that I used a Thinkpad, so Breezy, Dapper and Edgy didnt have that issue. But it could well be because of the manufacturer of the laptop rather than Ubuntu.

Is that the only problem (NOT) that you have?

I thought you said you had many weird problems.

---

### Post by cmnorton on 2007-11-19
> **MONODA said:**
> Hi I am still kinda new to ubuntu, I started using it about a month ago, and have encountered many weird problems. First of all whenever I boot up, I get a screen saying, failed to load mem resource. But my computer boots normally. What do you think this means?? Any help would be appreciated. thanx

Is your Ubuntu system a laptop? I get the same message on an Acer Travel Mate 630, and boot fine with this message.

---

### Post by Inxsible on 2007-11-19
> **cmnorton said:**
> Is your Ubuntu system a laptop? I get the same message on an Acer Travel Mate 630, and boot fine with this message.Aha !!

So it's not only HP laptops !

But then again, all these supposed manufacturers get their hardware from the same 4-6 actual manufacturers. HP, Dell, Acer and others more or less simply put their logos on the machines and re-package and sell them.

---

### Post by cmnorton on 2007-11-19
> **Inxsible said:**
> Aha !!

So it's not only HP laptops !

But then again, all these supposed manufacturers get their hardware from the same 4-6 actual manufacturers. HP, Dell, Acer and others more or less simply put their logos on the machines and re-package and sell them.

At 250 MB RAM, this Acer used to Blue Screen or hang all the time running XP. It ran with Ubuntu just fine, although slowly with some slow applications like Evolution, at 256 MB RAM.

---

### Post by MONODA on 2007-11-19
well thats not my only problem.. Like from before whenever I logged on I had to changed the resolution which would be reset everytime i rebooted. and when the top panel gets super unorganized when I log in sometimes. Oh btw whats up with those key combonations. I mean like when I press ctrl+alt+F10 Everything exits and all i can see is a black screen... and alt+F3 gives me a black screen with a terminal. I just wanna know how to return to Ubuntu after these are clicked and if there are anymore. thanx

---

### Post by frodon on 2007-11-19
For your control + alt issue it is a known bug which have a painless workaround, see this thread (especially post 7):
[http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)

To make the fix permanent just add the 2 modules in your /etc/modules file.

---

### Post by jaybombalous on 2007-11-19
U have a proprietary laptop, what do u expect?

---

### Post by linuxlizard on 2007-11-19
I've got that same problem with the top panel becoming disorganized at seemingly random boots. Always irritates me...

---

### Post by LowSky on 2007-11-19
> **linuxlizard said:**
> I've got that same problem with the top panel becoming disorganized at seemingly random boots. Always irritates me...

make sure the icons are all locked, righ click on them and lock them. if they are not locked then the might bounce around the bar a little bit

---

### Post by MONODA on 2007-11-19
Hey I have a very big problem! I tried using netboot or whatever its called to install ubuntu on my 7 year old pc cuz it doesnt have a cd drive. But the thing is that in the middle of th installation, there was a power cut and whenver I turn on the laptop it says, "failed to load operating system". So basically im reall screwed unless I can somehow install ubuntu on it from a floppy or something. thanx for ur help guys

---

### Post by ayenack on 2007-11-19
Have a look at this it'll explains how you can do this.

[UbuntuGeek]("http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html")

Good luck.

---

### Post by MONODA on 2007-11-19
thanx for ur response but it wont work cuz i cant boot from my hard disk cuz theres no os there. I need to boot from an external source and install ubuntu from there. btw i dont have an external cd drive but i have fast internet.

---

### Post by ayenack on 2007-11-19
There's a link on the site for [Active@ Partiton Recovery]("http://www.partition-recovery.com/index-overture.htm?ovmtc=content&ovadid=1788047522") software. It's the link that says partition software. To my knowledge this can be used on a floppy to partition your drive ready for network install of Ubuntu. I take it you have two PC's?

---

### Post by aqchat300 on 2007-11-19
if power went out do what i did.... i reinstalled just run through with your network install again i mean power outs will just make u reinstall =\ now.... to my xp pc for bf2-2142-halo-blahblaahblah,,, oh no forgot gottah fix the grub booter i removed with my ubcd :P bye. :KS

---

### Post by linuxlizard on 2007-11-19
Everything on mine is carefully locked - it scrambles everything about once a week anyway.

---

### Post by MONODA on 2007-11-19
well the icons are locked when it happens but its easy to fix them. Also this weird thing happens sometimes with my menu bar in all applications where the close max and min buttons disapear, they reapear at mouse over and everything works fine but its just weird. Also why can tu put the recycl bin on ur desktop???

---

### Post by Inxsible on 2007-11-19
> **MONODA said:**
> well the icons are locked when it happens but its easy to fix them. Also this weird thing happens sometimes with my menu bar in all applications where the close max and min buttons disapear, they reapear at mouse over and everything works fine but its just weird. Also why can tu put the recycl bin on ur desktop???you can put the Trash icon on the desktop.

1) Press Alt + F2
2) Type in gconf-editor and hit enter.
3) Navigate to apps>>nautilus>>desktop
4) Enable the "trash_icon_visible" check box

about your window border greying out, that's because of Compiz not ubuntu. if you do not want to use compiz, you can use metacity and you wont see that. I agree its annoying, but that's what it is....just annoying, doesnt do any harm.

Alternatively, you can use emerald as your window decorator and that problem should go away.

---

### Post by MONODA on 2007-11-20
UUUGHHH another thing went wrong! my screen just flashes randomly for like half a second. it gets really anoying!! anyone else having this probelm??

---

### Post by Inxsible on 2007-11-20
> **MONODA said:**
> UUUGHHH another thing went wrong! my screen just flashes randomly for like half a second. it gets really anoying!! anyone else having this probelm??Its a problem for quite a few people.

Check this [thread]("http://ubuntuforums.org/showthread.php?t=579565&highlight=screen+flickering") out

---

### Post by MONODA on 2007-11-20
oh thanx solved that problem. but a few minutes ago i tried to log off but all that happened is that the screen went black for a long time so i forced a shutdown. Also how can i find out the password for my root? thanx alot

---

### Post by Inxsible on 2007-11-20
> **MONODA said:**
> oh thanx solved that problem. but a few minutes ago i tried to log off but all that happened is that the screen went black for a long time so i forced a shutdown. Also how can i find out the password for my root? thanx alot
you should have given it enough time to shutdown. I can't really say what happened there unless you tell me what changes you made before shutting down, if any.

What do you mean find out the root password? Its the same as the password for the FIRST user that you created during installation. You can change the password, if you like by logging into recovery mode and typing ```
pwd
``` at the prompt.

---

### Post by MONODA on 2007-11-20
I was asking because whenver I try to log in as root in a virtual terminal or at the login screen, it says that my username and password combo is incorrect. and yes I did enable root login.

---

