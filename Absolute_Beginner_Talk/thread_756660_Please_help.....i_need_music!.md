---
title: "Please help.....i need music!"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-16
Can someone just help me get any audio program to work. Rhythm box wont open my mp3's. Ive tried to install both Amarok and Banshee and both of them give me error messages in both the terminal and the synaptic package manager. I just need anything right now. Really desperate to get my music working.

AeThEr777

---

### Post by kaptengu on 2008-04-16
vlc plays most formats I guess.

---

### Post by AeThEr777 on 2008-04-16
i need a program that organized my music though like itunes. Please can someone just give me a step by step troubleshooting guide.

---

### Post by erginemr on 2008-04-16
For your mp3 problem, please refer to:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and install **ubuntu-restricted-extras** from either Menu -> Admin -> Synaptic or from the terminal with:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by kaptengu on 2008-04-16
```
sudo apt-get install listen
```

---

### Post by ad_267 on 2008-04-16
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

It seems like so many people can't figure this one out. I had to google it when I first used Ubuntu as this was one of the first things I tried to do. It needs to be more obvious like how you get a message about being able to install a restricted driver for a video card. When someone opens rhythmbox for the first time they should get a message saying they need to install these to play mp3

---

### Post by kesman on 2008-04-16
For a **good** organizing and playlist handling, I'd suggest Gmusicbrowser, you can easily install it by adding this line in /etc/apt/sources.list 
deb [http://squentin.free.fr/gmusicbrowser](http://squentin.free.fr/gmusicbrowser) ./ 
and then running:
```

sudo apt-get update
sudo apt-get install gmusicbrowser

```

---

### Post by erginemr on 2008-04-16
> **ad_267 said:**
> It seems like so many people can't figure this one out. I had to google it when I first used Ubuntu as this was one of the first things I tried to do. It needs to be more obvious like how you get a message about being able to install a restricted driver for a video card. When someone opens rhythmbox for the first time they should get a message saying they need to install these to play mp3

You are right. But it is actually prompted when you first try to open an MP3 file, but with Totem as far as I can remember, not with Rhythmbox...

Maybe, when the user installs the system and launches Firefox first, the welcome page of Firefox could be arranged in such a way that it would point to an Ubuntu Welcome page explaining why these extras are not installed by default, and with clear directions on howto install restricted drivers, java, DVD playback support, etc.

---

### Post by hyper_ch on 2008-04-16
> **ad_267 said:**
> It seems like so many people can't figure this one out. I had to google it when I first used Ubuntu as this was one of the first things I tried to do.

One doesn't need to know a solution for every problem by heart... it is sufficent to know how to find the answer when needed...

---

