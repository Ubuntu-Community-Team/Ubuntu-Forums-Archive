---
title: "Just Installed and..."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Rileymd on 2007-11-29
I need some help! How do I go about copying files into my usr folder? I want to copy some fonts into there but it's saying I don't have permission or some bullocks...Ok so that's my first question my 2nd one is how come my sound is not working for my aMSN? It works for everything else but for some reason it'snot working for aMSN and it's pretty annoying..Anyways thanks to anyone who can help me out!

---

### Post by icechen1 on 2007-11-29
for question 1 you have to be the superuser to modify files in all folder except your home folder.
In a terminal do this to modify things in /usr:
```
sudo nautilus
```
BE CAREFUL DO NOT USE THIS UNLESS YOU HAVE TO,because if you mess the files ubuntu may have problems.

---

### Post by powder on 2007-11-29
You can try using these directions to install new fonts.  Sorry, I don't use aMSN.

1.  ```
mkdir ~/.fonts
```
2.  Copy the fonts to the .fonts folder in your home directory
3.  ```
fc-cache -f -v ~/.fonts
```

---

### Post by quandary on 2007-11-29
For sound, go to console and type:
echo "MSN_EXECUTABLE_NAME 0 0 direct" > /proc/asound/card0/pcm0p/oss

replace MSN_EXECUTABLE_NAME with the actual executable filename of your msn-application.
Perhaps that helps, perhaps not...

---

### Post by fineas on 2007-11-29
For sounds, try also this:
Go to account>preferances>others tab. In sound server replace "play $sound" with "aplay $sound" and save (may also need to exit aMSN and relogin)

---

