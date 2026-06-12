---
title: "I'm afraid of Linux ...."
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Cbotron on 2007-07-15
I'm afraid of using Linux.Because every time I need to add some programs or some stuff,I always need to use the terminal.I want to know :

1-I'm using a Del XPS m1710 laptop.Is there an easier way to install the video driver on Ubuntu?I got a nvidia geforce go 7950 512 video ram

2-Are gaming performance better on Ubuntu compared to Windows XP and Windows Vista?

3-I am using wifi,how do I configure it?Because on Vista,it configures automaticly.

---

### Post by macogw on 2007-07-15
Why do you need to use the terminal?  Go to Add/Remove in the Applications menu or Synaptic under System > Admin.

Did you try going System > Admin > Restricted Driver Manager?

If the games work on Linux, it should run better because Ubuntu will run it faster due to using less of your resources than XP does.

What wifi card is it?

---

### Post by Cbotron on 2007-07-15
Connexion réseau PRO/Sans fil 3945ABG Intel(R)

---

### Post by DoctorMO on 2007-07-15
"I'm afraid of Linux... I'm afraid I can't help it! Dootat, doodat"

sorry where were we?

---

### Post by Cbotron on 2007-07-15
> **DoctorMO said:**
> "I'm afraid of Linux... I'm afraid I can't help it! Dootat, doodat"

sorry where were we?

........I was hoping a more mature responce from the Linux comunity but anyway ...

---

### Post by brim4brim on 2007-07-15
Intel provide drivers for at least some of their cards (I can't say all becuase I don't know if they do), my card was automatically configured.  All I had to do was select which network I wanted to connect to in the Network Manager.

Winehq.org has a list of games that it can run in Linux.  Also some games run natively like id softwares (some of them anyway) and you'll find Linux games that you like too.

---

### Post by KiwiNZ on 2007-07-15
> **Cbotron said:**
> ........I was hoping a more mature responce from the Linux comunity but anyway ...
 
I agree 
 
DoctorMO sometimes it is just better to say nothing.

---

### Post by Cbotron on 2007-07-15
The only game I plan to get is UT3 coming this november.

---

### Post by macogw on 2007-07-15
> **Cbotron said:**
> Connexion réseau PRO/Sans fil 3945ABG Intel(R)

I have that card.  It should work by default.  Check that it's enabled in the Restricted Driver Manager.  The NetworkManager applet in the top right of the panel lets you pick which network you want to connect to.

---

### Post by Cbotron on 2007-07-15
Thanks!! :)

the only question I have in mind is that is Unreal tourmament 3 gonna be better playing it on Windows Xp or Ubuntu.

---

### Post by Stew2 on 2007-07-15
I think DoctorMo was trying to be humourus, not sarcastic or mean...

---

### Post by agurk on 2007-07-15
I have the Intel Pro Wireless 3945 abg in my laptop and it works great with Ubuntu Feisty, NetworkManager picks it up and it's easy to configure without using the terminal. Actually, I didn't have to configure it at all, I just picked the desired network from the NetworkManager list and that was it.
It needs the linux-restricted-modules package, which is available on the alternate CD or from the restricted repository (because of its non-free binary firmware).

---

### Post by ice60 on 2007-07-15
the terminal is great once you start using it.

probably a bit OT, but i was thinking of my greatest fear when i saw this thread. i think there are things more frightening then linux lol

---

### Post by zero244 on 2007-07-15
One of the easiest ways to install your video drivers is first install Automatix2.........then open it click on drivers and install them.
With video drivers its best to do some reading you may have to do some configuring with your xorg.conf file.
Especially if you want to use beryl.

---

### Post by C.S.Cameron on 2007-07-15
Zero is right, after many attempts over the years to use Linux only to be frustrated by Nvidia drivers, Automatix got them working for my 8800gts. Read the instructions first. Don't forget to backup your xorg.conf.
Cork

---

### Post by xpod on 2007-07-15
> Re: I'm afraid of Linux ....

So was i to start out....i was so scared i refused to go anywhere near that precious XP drive of mine back then.
How things change:)

The only thing i have to be scared of now apparently is the wife but she`s promised that as long as theres noooo more "Linuxes" then i`ve nothing to afraid of:)

---

### Post by Skidpad on 2007-07-15
> **C.S.Cameron said:**
> Zero is right, after many attempts over the years to use Linux only to be frustrated by Nvidia drivers, Automatix got them working for my 8800gts. Read the instructions first. Don't forget to backup your xorg.conf.
Cork
Or, you could try [nVidia Driver Installation Guide]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html") or [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), which is an automated GUI to install the correct driver automatically.

---

### Post by Istonian on 2007-07-15
About the UT3 question, I belive it will run better under Ubuntu. Good choice for a game because UT3 runs natively on linux.

---

### Post by steve8track on 2007-07-15
A great game you should try if you like first person shooters is Nexuiz.  I tried it in both Windows XP and Ubuntu and it runs great on both.

The problem with testing performance of games on different operating systems is  it is difficult to be fair.  For example, my Windows XP computer has a far better graphics card, so obviously Nexuiz performed better on it.  Also, different games do different things that could be faster or slower depending on what the operating system is doing, and how it is configured.  All said, my impression is that games run just as well on Ubuntu as on Windows XP, if the game runs on Ubuntu natively, and not through WINE or a virtual machine.  I don't know about WINE's performance, since the only game I have run on WINE is Warcraft 2, which is so small in system requirements, it could run fine on most computers, run natively or not (though on a virtual machine it does slow down and distort the sound for me).  Also, it can depend on WINE's settings.

Sorry I can't say anything about Unreal Tournament 3.

Where is this Restricted Driver Management?  It doesn't appear in my System->Administration-> menu.

Thanks.

---

### Post by Cbotron on 2007-07-15
For UT3,people on this board think XP is better.Is it true?

[http://forums.epicgames.com/showthread.php?t=573884](http://forums.epicgames.com/showthread.php?t=573884)

---

### Post by Istonian on 2007-07-15
Meh... opinons. Some ppl have different ones. Try for yourself.

---

### Post by agurk on 2007-07-15
I don't believe all those people have tried Linux, though I suspect they are right when it comes to Vista being the worst of the three, as bad 3D performance is something I have experienced myself with Vista. Why don't you try it and let us know your verdict on the matter.

---

### Post by Stew2 on 2007-07-15
I've played Unreal and Unreal tournament 2 on both Windows and Ubuntu on my dual booting gaming rig and i couldnt tell any diffrence between the two operating systems in how the games ran. Ran great on both :D. Doom 3 however (even with the native linux port) had lower fps on ubuntu than windows but I might not have had my ati drivers set up 100%.

---

