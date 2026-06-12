---
title: "Wine folder"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by 941989 on 2007-05-30
Ok, I know I will sound like a total idiot, but I am switching from XP so bear with please.

Where can I find the folder that contains C:// and my wine apps. in the terminal it says it is located /home/XXXXX/.wine/drive_c: yet when I search for that folder, i come up emptyhanded.

---

### Post by chamberlain2006 on 2007-05-30
Have you installed wine?  You need to go to System>Administration>Synaptic Package Manager and install the wine package.

---

### Post by taurus on 2007-05-30
The XXXXX in "/home/XXXXX/.wine/drive_c" should be the name of your login name or 

```
ls -la ~/.wine/drive_c
```

---

### Post by Nekiruhs on 2007-05-30
The period before wine means that its hidden just go to you home directory and press ctrl-h and you'll see a fold called .wine.

To make a link to the folder on your desktop (Very handy)
```
ln -s ~/.wine/drive_c/ ~/Desktop/
```

---

### Post by zvacet on 2007-05-30
**home directory>view>show hidden files**

---

### Post by ryanVickers on 2007-05-30
1. Make sure wine is installed.

2. Then go to your home directory

3. View > Show hidden files

4a. then go into .wine

OR

4b. type /home/yourusernamehere/.wine/drive_c

---

### Post by 941989 on 2007-05-30
Thank you tons for the ctrl + h stuff, Now I can use steam, and as thus will not ever be going back to windows.:D

---

### Post by daimaru on 2007-05-30
> **941989 said:**
> Thank you tons for the ctrl + h stuff, Now I can use steam, and as thus will not ever be going back to windows.:D

wow what games are u using on steam cause i really cant believe that for example counter strike source is playable through wine ...

---

### Post by 941989 on 2007-05-30
I am pretty sure that you are able to play HL2+CSS on wine. There should be some vids of it. I also got unreal working, so I am a happy camper right now.

---

