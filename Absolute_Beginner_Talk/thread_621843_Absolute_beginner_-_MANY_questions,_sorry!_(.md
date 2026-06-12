---
title: "Absolute beginner - MANY questions, sorry! :("
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Murxidon on 2007-11-24
Sorry for my complete lack of knowledge with all things Ubuntu. But I'm getting bored of Windows (again) and I want to re-install the latest version of Ubuntu instead  of revising for my Maths exam on Monday.

I have many a question which I hope you kind people could answer for me :)
   
**Networking**

I  have two Windows XP machines currently, both with NICs. The older PC uses an ethernet cable to connect into the back of my PC, so it can share the internet connection and files. The printer itself is on the older PC and I can connect to it also from this one. How could I go about replicating this on Ubuntu? Has it been made easier with the new version?

**User accounts**

When I last used Ubuntu, I found it impossible to achieve a seemingly simple task. I had two accounts, an Administrator (Me) and a Guest account. I wanted my account to be password protected, but not the Guest account. I also wanted the logon screen to show when I booted up. I asked here a while back and found no answers unfortunately. Is it possible with this version?


I think that's it actually for now.. Heh.. The most important thing I would like to do is be able to share the internet connection, printer and files with my second PC.

Thanks for any advice :)

---

### Post by Sarteck on 2007-11-24
**Networking**
Man, that really bites...  I had to do the same thing with my girlfriend's computer about three years ago, when I was on dial-up.  I wasn't on Ubuntu then, though--the only way I could find to do it was by her using my computer as a proxy.  >.<



**User accounts**
It's theoretically entirely possible to do this, and has been for quite some time.  :)
In reality, though, everytime I've tried to do it, I've had a lot of trouble, and only got it working once. XD  I'm not an idiot, mind you, but it just seems that Ubuntu never likes to STAY the way I put it.  It's all like, "look Sarteck, I'm a freakin' computer, I know how to take care of myself."

You might find it easier than me, though--I encourage you to give it a try, at least.  You could make a small partition for Ubuntu at first, and if you find that you liek it, you can just do away with Windows entirely.  :)  (Personally, I keep Windows just as a backup, just in case, but I VERY rarely want to or have to use it.  I then keep a larger NTFS partition that both my Ubuntu and my Windows can access as my main storage.)

---

### Post by KhaaL on 2007-11-24
The login thing you're asking for is possible. I don't think it's possible (or recommended for that matter) that you roam around your system as a superuser... but anyway, A login screen with a guest account that has no password is possible!

---

### Post by Murxidon on 2007-11-24
> **Sarteck said:**
>  You could make a small partition for Ubuntu at first, and if you find that you liek it, you can just do away with Windows entirely.  :)  (Personally, I keep Windows just as a backup, just in case, but I VERY rarely want to or have to use it.  I then keep a larger NTFS partition that both my Ubuntu and my Windows can access as my main storage.)

Thank you both for your advice!

Is this really possible? that would be great. I can dual-boot both of them, but could I actually remove Windows completely and give the rest of the space to the Ubuntu installation?

---

### Post by Sarteck on 2007-11-24
> **Murxidon said:**
> Thank you both for your advice!

Is this really possible? that would be great. I can dual-boot both of them, but could I actually remove Windows completely and give the rest of the space to the Ubuntu installation?
Yes, it's very possible.  In fact, I did it with my last computer.  :)  On this (my new) computer, I kept Windows on because my mother needed Shockwave for one of her online classes, and now I just keep it on in case I have to fall back on it for one reason or another.  I would recommend that you do the same--keep both Ubuntu AND Windows on there, so you can switch if needs be.

On this computer, I have a 500GB drive.  I dedicated 20GB to Windows Vista, 45GB to Ubuntu, and the remaining 435GB to a 2GB Swap space and an NTFS partition so that I can access it from both Ubuntu and Windows with no problems.  (Also, if I ever severely screw up one or both of my OSes, at least the main partition retains all files.  :D)

If you really want to, though, you CAN just entirely do away with Windows.  I don't recommend it until you've got Ubuntu running just how you want it, though.

---

### Post by tibellus on 2007-11-24
> I can dual-boot both of them, but could I actually remove Windows completely and give the rest of the space to the Ubuntu installation?

You want to do that after you've installed Ubuntu?

---

### Post by Murxidon on 2007-11-24
> **tibellus said:**
> You want to do that after you've installed Ubuntu?

Yes, if it's possible.

Thanks

---

### Post by roaldz on 2007-11-24
Well.. those are not many questions, they´re questions that cause many answers. One thing is very important if you want to use Ubuntu (or linux in general): A system administrator like you always has 2 accounts: his own account, which is equal to any other normal user account, and a root account. This root account is only used for administration purposes.
If you already know this: don´t be offended, it can do no harm to hear it again. This is one of the most important reasons why ubuntu is virus-free. If you´d go wandering around in root, you´ll have your ubuntu installation just as f*ckt up like windows will be. The guest account can be done, that´s no problem.

Printing: I would first test if your printer is supported by ubuntu - just pop in a live cd and find out:) If it´s supported, then you can install ubuntu on all pc´s. Sharing them is much easier these days:)

Good luck & greets,

Roald

---

### Post by tibellus on 2007-11-24
Ok. To "recover" the space used by windows you can install a partition manager, like Gparted (which I recommend), and edit the partitions as you like with it.

To install it, type this in a terminal:

```
sudo aptitude install gparted
```

Afterwards, you can run it by typing in a terminal

> sudo gparted

If you don't use the sudo command, the application won't start, because it needs administrative privileges.

---

### Post by Murxidon on 2007-11-24
Thanks everyone. But I've just hit my first hurdle.

I've downloaded and burned the image, it's the Live CD. I booted into it and everything was fine until it finished loading... The screen went off.

My monitor is quite ancient, and it can't handle increased resolutions and refresh rates. Have these settings changed for the Live CD since earlier versions?

---

### Post by philinux on 2007-11-24
Reboot the live cd and click the option to check the cd - make sure it burned ok first.

---

### Post by giusepperossi on 2007-11-24
how can i do the good partition to install the ubuntu ???

---

### Post by KhaaL on 2007-11-24
this is a good resource: [http://psychocats.net/ubuntu/partitioning]("http://psychocats.net/ubuntu/partitioning")

---

