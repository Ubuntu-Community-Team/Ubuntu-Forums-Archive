---
title: "no sound in ubuntu macbook pro"
date: 2010-03-30
forum: Apple Hardware Users
---

### Post by ynnojC on 2010-03-30
I am running on a macbook pro 13" the latest version of ubuntu. I read the article here: [https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound)
Sound is not working, even after i unmute it in alsa mixer. Please help!;)

---

### Post by Neds Moar Salt on 2010-03-31
> **ynnojC said:**
> I am running on a macbook pro 13" the latest version of ubuntu. I read the article here: [https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound)
Sound is not working, even after i unmute it in alsa mixer. Please help!;)

Zap PRAM/NVRAM.  If you can't find linux in the boot menu, use rEFIt to sync your tables.

---

### Post by linuxopjemac on 2010-03-31
which model number ?

[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by ynnojC on 2010-03-31
> **linuxopjemac said:**
> which model number ?

[https://wiki.ubuntu.com/mactelsupportteam/communityhelppages](https://wiki.ubuntu.com/mactelsupportteam/communityhelppages)

(5,5)

---

### Post by ynnojC on 2010-03-31
> **Neds Moar Salt said:**
> Zap PRAM/NVRAM.  If you can't find linux in the boot menu, use rEFIt to sync your tables.

How do i do that?:popcorn:

---

### Post by linuxopjemac on 2010-03-31
I have my doubts that zapping PRAM is a solution to this. You might want to give it a try though. Boot and hold option+command+p+r. Then you here a boing. Then you can release. Your Pram is zapped.

If you want to know about boot codes:
[http://mac.linux.be/content/ten-different-boot-options-leopard](http://mac.linux.be/content/ten-different-boot-options-leopard)

---

### Post by gcndavidmn on 2010-03-31
What kernel version are you using? There have been issues with .20 and MBP sound, which is why I am using .19 at the moment.

---

### Post by ynnojC on 2010-03-31
> **gcndavidmn said:**
> What kernel version are you using? There have been issues with .20 and MBP sound, which is why I am using .19 at the moment.

i am using .20, but the other one, (.14) has to use low graphics mode, and no wifi.
also, zaping didnt work

:shock:

---

### Post by gcndavidmn on 2010-04-01
Give .19 a go. I didn't have to mess around with low graphics mode and sound worked.

---

### Post by ynnojC on 2010-04-01
> **gcndavidmn said:**
> Give .19 a go. I didn't have to mess around with low graphics mode and sound worked.

I dont have .19 . how do i install it?

---

### Post by gcndavidmn on 2010-04-01
> **How to fix**
Install the following packages through synaptic:

linux-image-2.6.31-19-generic
linux-backports-modules-alsa-2.6.31-19-generic
gnome-alsamixer

- Reboot
- Select the 2.6.31-19 kernel option in grub during boot

You'll probably be running in low graphics mode, don't worry. Just click  ok and continue with boot.

Open gnome-alsamixer (Applications >> Sound and Video >>  GNOME ALSA Mixer) un-mute everthing and turn up Front Sp.

Sound should now work.

You'll have to reinstall you're Nvidia driver. And if you want to boot  into the -19 kernel from now on, install the startupmanager package and  run the program then select the -19 kernel from the list.
That is taken from this thread [http://ubuntuforums.org/showthread.php?t=1423422&page=3](http://ubuntuforums.org/showthread.php?t=1423422&page=3)

---

