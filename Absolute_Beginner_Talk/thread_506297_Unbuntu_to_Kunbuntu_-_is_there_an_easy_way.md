---
title: "Unbuntu to Kunbuntu - is there an easy way?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by jimbojames on 2007-07-21
Hi All,

I have installed Unbuntu 7.04 on my PC along side XP and all is good with the exception of my ATI X600 card which it's not liking at the moment but the main reason I started to look at Linux was for the Linux Media Centre.  I have just read that I should have installed Kunbuntu and not Unbuntu .... D'oh!!!!  Is there a way that I can swap from Unbuntu to Kunbuntu easily?

Thanks in advance,

James.

---

### Post by qamelian on 2007-07-21
Install the kubuntu-desktop package. This will install all the Kubuntu packages as well. You'll be able to choose Ubuntu or Kubuntu from the session menu at the login screen.

---

### Post by por100pre1 on 2007-07-21
If you have enough space you can install kubuntu in your existing installation:

```
sudo aptitude install kubuntu-desktop
```

You can then select KDE session in the login screen.

---

### Post by jimbojames on 2007-07-21
Excellent - I'm installing as we speak - I'll get back to you with my progress shortly.

Do either of you have any experience with LMCE?

---

### Post by por100pre1 on 2007-07-21
Not me, but I really [looks interesting]("http://linuxmce.com/").

---

### Post by jimbojames on 2007-07-21
just going through the installation now.

It asked me what display manager to use so I selected KDM, was that right?

If so - I am now being asked what type of installation I Want?  I assume it's local?

---

### Post by Old Pink on 2007-07-21
Yes, local sounds right. When you reboot/logout, click sessions and choose KDE/Kubuntu to log in to KDE. :)

---

### Post by Old Pink on 2007-07-21
By the way, it's **Ubuntu** and [B]Kubuntu.

[/B]Not unbuntu and kunbuntu. ;)

---

### Post by jimbojames on 2007-07-21
Oops - sorry - slip of the fingers :)

I have installed now but I only get Kubuntu screens when I log off and log on???  I'm getting very confused.  Is Kubunu stitting on top of Ubuntu?

Should I get an option when I log in to choose one or the other?  If so - I'm not getting that option?

---

### Post by Majorix on 2007-07-21
Ubuntu and Kubuntu work together, but if you install Kubuntu on top of Ubuntu, you will get Kubuntu's boot image at the startup. Its no biggie.

If you want to select one of them to start with, at the screen where you type your password and username there should be a menu saying "Options" at the bottom left. Click that and from there you can choose the desired Desktop Environment. I believe it is located under "Sessions" however I am not sure cause it has been like 6 months since the last time I had two desktop envs.

---

### Post by forestpixie on 2007-07-21
when you login at the bottom left of the screen theres  a options button  - you can change session there - it'll give you the chance to start with either 
Kubuntu or Ubuntu - you cna change default as well

- and I'm constantly moving the cursor to change the spelling  I always do it wrong! :D

---

### Post by por100pre1 on 2007-07-21
At the login screen check "Session Type". 

If you don't like KDM:

```
sudo dpkg-reconfigure kdm
```

and then select GDM for the old login screen :KS

---

### Post by jimbojames on 2007-07-21
Ok - it's all going a bit messy so I have chosen to go back to the start!  I now have only XP on my PC.  My final goal is to get the LMCE up and running, so - I believe that I need Kubuntu to be able to install the LMCE.
Can I just install Kubuntu from fresh?

Sorry for all this run around, I am very very new to Linux and I'm having a hard time wrapping my head round things (been using MS for too long! :( )

---

### Post by bme on 2007-07-21
You should have posted the "mess" you have instead of starting from the beginning.That way you will learn what have gone wrong and the corresponding remedy

---

### Post by por100pre1 on 2007-07-21
> **jimbojames said:**
> Ok - it's all going a bit messy so I have chosen to go back to the start!  I now have only XP on my PC.  My final goal is to get the LMCE up and running, so - I believe that I need Kubuntu to be able to install the LMCE.
Can I just install Kubuntu from fresh?

Yes, you can install Kubuntu with a Kubuntu CD, why not?

> **jimbojames said:**
> 
Sorry for all this run around, I am very very new to Linux and I'm having a hard time wrapping my head round things (been using MS for too long! :( )

It's OK. I know this can feel "messy". I'm a noob learning something new everyday and I know how you feel  :) .

---

### Post by jimbojames on 2007-07-21
I know, I should learn to be patient!!!! :)

---

### Post by jimbojames on 2007-07-21
Seeing as LMCE is my primary goal - I think I will work from there backwards.

---

### Post by por100pre1 on 2007-07-21
> **jimbojames said:**
> Seeing as LMCE is my primary goal - I think I will work from there backwards.

I think you should start trying to learn to use a regular distro like Kubuntu first. LMCE is a beta distro, a very ambitious one, and it can be more troublesome to configure than an average distro.

---

