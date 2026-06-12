---
title: "Red light from headphone jack related to poor sound quality?"
date: 2007-03-27
forum: Apple Intel Users
---

### Post by PictureThis on 2007-03-27
Today I noticed a bright red light coming from the headphone jack. It's only visible when running Kubuntu, in OSX the phenomenon does not appear. Therefore I rule out a faulty jack as mentioned [here](http://forums.macrumors.com/archive/index.php/t-232084.html) (I didn't even know the jack was capable of displaying a red light until today)

Still, there's a red light and I suppose it could well be related to a faulty sound setup in Kubuntu. Sound quality is still fairly poor with low volume and a rather distorted signal.

Sound is flawless in OSX. (I really like the MacBook speakers btw)

Anyone with more insight?

---

### Post by cyberdork33 on 2007-03-28
the headphone jack is also capable of optical output. you can turn it off with alsamixer.

I don't use a MacBook (I have an iMac with the same phenomenon). My sound works fine under ubuntu with or without the optical enabled.

---

### Post by kvonb on 2007-03-28
Look closer, it might be Elvis partying with the Aliens in there!!!

Sorry, just couldn't resist :D

---

### Post by PictureThis on 2007-03-28
> **cyberdork33 said:**
> the headphone jack is also capable of optical output. you can turn it off with alsamixer.

I don't use a MacBook (I have an iMac with the same phenomenon). My sound works fine under ubuntu with or without the optical enabled.

Thanks cyberdork33. I switched it off. Press "m" under the IEC958 channel to switch on/off the optical output. I still experience low volume, a crackling left speaker and a slightly distorted sound though.

@kvonb: Elvis has left the building... :lolflag:

---

### Post by oskarloko on 2007-03-28
I noticed it, in my macbook happens the same.

¿¿ You don't like your new red-laser pointer ?? It's soooo cute - just a little expensive !! \\:D/ 


:p :p :p :p :p 

Just kidding...

---

### Post by Chrisj303 on 2007-03-30
Ah, so thats what the red light is - i thought i was going mad when i first noticed it "how long as that been there?" !

chrisj303

---

### Post by rei_t_ex on 2007-04-03
I started to have the same problem today (red light, low volume, distorted sound, crackling in the left speaker) after messing about with the sound settings trying to get Audacity to record my soundcard output.

Before today, sound on my Macbook was working flawlessly.  Thus, it is something strange but rectifiable.  As soon as I figure out what it is I screwed up exactly, I will be sure to post it.

---

### Post by PictureThis on 2007-04-09
> **rei_t_ex said:**
> I started to have the same problem today (red light, low volume, distorted sound, crackling in the left speaker) after messing about with the sound settings trying to get Audacity to record my soundcard output.

Before today, sound on my Macbook was working flawlessly.  Thus, it is something strange but rectifiable.  As soon as I figure out what it is I screwed up exactly, I will be sure to post it.

Two days ago I added the Ubuntu desktop to my Kubuntu-system. Low volume, distorted sound and the crackling left speaker were also present the first time I started Ubuntu. In order to replace the Kubuntu boot splash screen with the Ubuntu one I used the following commands:

```
sudo update-alternatives --config usplash-artwork.so
```

```
sudo dpkg-reconfigure linux-image-`uname -r`
```

Much to my surprise, after executing the last command and rebooting sound is now OK under Ubuntu! Kubuntu unfortunately still has the mentioned issues. I really have no clue why it (only) works under Ubuntu. That last command apparently regenerates the initramfs (which you can further read about [here](http://www.mjmwired.net/kernel/Documentation/filesystems/ramfs-rootfs-initramfs.txt))
and this somehow seems to have corrected a wrong.

---

### Post by PartisanEntity on 2007-04-19
I don't have any sound issues, but I only get the red light coming from the headphone jack when I use Ubuntu. Doesn't happen in Windows.

Anyone what this is for? What's the point of this led in the headphone jack?

---

