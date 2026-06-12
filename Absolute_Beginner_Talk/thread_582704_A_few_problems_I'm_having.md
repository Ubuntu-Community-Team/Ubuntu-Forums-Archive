---
title: "A few problems I'm having"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Herbonator on 2007-10-20
Firstly, I apologize for registering and asking questions with my first post.

I have just installed 7.10 on my Intel Dual Core HP Pavilion dv2000 and I'm having a couple problems.

**Mic not working**
I have installed skype and my mic is not working. I went to system\preferences\sounds to test it and it gave the following error:

> Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'


**Headphone volume control is not working**
The volume control on my laptop is working for the speakers but not the headphones.

**Webcam**
The in built webcam isnt working as far as I can tell. I cant find anyway to test this.

**Small USB drive is undetected**
My 160gb I.O Data HDPG drive is not being detected. It was partitioned when i got to it have a small partition that displays as a CD drive with all of the vendor software on it. I couldnt get rid of it on windows either. Ubuntu is finding the faux-cd part of the drive fine.  I have the main part of the drive formatted to NTSF and it is empty. Ubuntu cant find it.

**Wacom not detected**
Wacom Bamboo detected but not working.



The funny thing is that the HDD was fine on the Live CD but stopped working when i installed linux (i am dual booting if that makes a difference).

Thanks a lot for any help you can give me.

---

### Post by sayuki288 on 2007-10-20
sounds to me that you just had a bad installation :)
or ubuntu just don't like HP :lolflag:

---

### Post by Herbonator on 2007-10-20
> **sayuki288 said:**
> sounds to me that you just had a bad installation :)
or ubuntu just don't like HP :lolflag:

So you think I should try re-installing ubuntu?

---

### Post by Herbonator on 2007-10-21
Anyone? I've really had a search but I cant find any solutions to my problems.

---

### Post by MatthewPlanchard on 2007-10-21
For the speakers:
From [http://ubuntuforums.org/showthread.php?t=574175&highlight=speaker+volume]("http://ubuntuforums.org/showthread.php?t=574175&highlight=speaker+volume")

> 
try this on a terminal:

```
sudo gedit /etc/modprobe.d/alsa-base
```

At the end of the file add this line:

```
options snd-hda-intel model=3stack
```

Save the file and restart. Sound should work normally now .

For the mic:
[http://ubuntuforums.org/showthread.php?t=312237&highlight=speaker+volume]("http://ubuntuforums.org/showthread.php?t=312237&highlight=speaker+volume")

Here's a general 7.10 HP Laptop Install Help Guide:
[http://ubuntuforums.org/showthread.php?t=569789&highlight=webcam]("http://ubuntuforums.org/showthread.php?t=569789&highlight=webcam")

Let us know if any of that works.

---

### Post by Herbonator on 2007-10-21
Excellent speakers are now working fine. The volume control on my laptop is working with my speakers now but not with my headphones.

I'm still working on the other links you sent me.

---

### Post by BaffledMollusc on 2007-10-21
> **Herbonator said:**
> Excellent speakers are now working fine. The volume control on my laptop is working with my speakers now but not with my headphones.

I'm still working on the other links you sent me.

For the Wacom bamboo problem, have you looked at this thread: [http://ubuntuforums.org/showthread.php?t=488013](http://ubuntuforums.org/showthread.php?t=488013)

... specifically the post by jun_shindo on page 3. That's for Ubuntu 7.04, but may still be helpful.

---

