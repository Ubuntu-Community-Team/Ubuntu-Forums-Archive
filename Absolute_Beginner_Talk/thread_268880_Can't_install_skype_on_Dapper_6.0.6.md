---
title: "Can't install skype on Dapper 6.0.6"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by muskyminxx on 2006-09-30
I originally installed Skype using Automatix.  The first time I tried to use it, nothing happened (the pointer had the little bouncing Skype icon, but after about 45 seconds it would disappear and nothing would happen).  I tried  it several times, rebooted, updated packages in Adept - nothing.  So I uninstalled it, but can't seem to reinstall it.  I run Automatix and it tells me that it's installed, but it doesn't appear on my program list, and typing Skype into the terminal only gets me
bash: skype: command not found
So I tried installing it with Adept, but it won't even let me request install.  Every time I click on the request install button, it doesn't even queue up as a requested change.  
Any ideas on what I might do to fix this?

---

### Post by AllenGG on 2006-09-30
Could you provide some information:
32 bit, 64 bit ?  processor ?  alsa or ESD ? etc more details please.

---

### Post by baylorbear on 2006-09-30
It did the same thing to me so I asked for help directly from Skype -- their tech support told me that Skype is unstable on the latest Ubuntu release and some folks have reported that it won't run on their systems while others report it works fine.  They said they're working on a stable release that should be available soon...

---

### Post by AllenGG on 2006-09-30
Strange !  works fine for me on an AMD64 system and an X86 system, both with Dapper 6.06. How does your sound system work ?

---

### Post by muskyminxx on 2006-10-02
I have a 32 bit processor and am using alsa for sound.  Maybe I just have to wait until skype comes out with a more stable version :(

---

### Post by eric.stone on 2006-10-06
AllenGG,
How'd you do you insstall on your AMD64 with Dapper?  I've got the same system.  Detailed instructions would be helpful.
Thanks much,

---

### Post by 5-HT on 2006-10-07
> **muskyminxx said:**
> 
Any ideas on what I might do to fix this?

Have you tried installing the .deb from Skype's website?

---

### Post by Dinerty on 2006-10-07
Try:

```
sudo gedit /etc/apt/sources.list
```

then add:

## skype (official)
## only uncomment it if you need it
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

save and exit. Then do

```
sudo apt-get update
```

then

```
sudo apt-get install skype
```

---

