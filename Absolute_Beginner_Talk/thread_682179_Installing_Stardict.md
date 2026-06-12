---
title: "Installing Stardict"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by aslam92 on 2008-01-29
I'm a complete newbie and I don't really know how to install the dictionaries for Stardict. I've just downloaded the dictionary files and I tried extracting it into the folder using the archive manager but it says 
tar: stardict-oald-2.4.2: Cannot mkdir: Permission denied
tar: stardict-oald-2.4.2/oald.idx: Cannot open: No such file or directory
tar: stardict-oald-2.4.2/oald.dict.dz: Cannot open: No such file or directory
tar: stardict-oald-2.4.2/oald.ifo: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
plz help thx

---

### Post by meho_r on 2008-01-29
Into what folder you're trying to extract? It seems that you have no permission to extract in that particular folder. Try this:
1. Copy the dictionary file on your Desktop and extract it there. You'll get a folder, let say its name is "oald" (you should replace this one with original one on every place mentioned below)
2. Open Terminal (Applications > Accessories > Terminal)
3. type in terminal: > **cd Desktop**
4. dictionary files for StarDict are located in /usr/share/stardict/dic (check if this is also true for you). You'll need to copy your "oald" folder there and for that you'll need root/superuser privileges. Do as follows:
5. type in terminal: > **sudo cp -r ./oald /usr/share/stardict/dic/**
6. when requested fill in your password and dictionary should be copied. Don'r forget to replace "oald" with your original dictionary folder name.
7. start StarDict and check Preferences/Manage Dictionaries. It should be there now

---

### Post by nick_h on 2008-01-29
> dictionary files for StarDict are located in /usr/share/stardict/dic (check if this is also true for you). You'll need to copy your "oald" folder there
I think that the 3 files in the archive need to be in /usr/share/stardict/dic and not a sub-directory.

Since there are only 3 files the OP could extract them into their home directory and then copy them to the /usr/share/stardict/dic directory.

To do this in the GUI, nautilus would have to be run as root:
```
gksudo naultilus
```

Alternatively, stardict dictionaries can be placed in ~/.stardic/dic but then they are only available to the user who installed them.

---

### Post by meho_r on 2008-01-31
> **nick_h said:**
> I think that the 3 files in the archive need to be in /usr/share/stardict/dic and not a sub-directory.


I'm really not sure if this is a necessity. All my dictionary files are in their respective folders in /usr/share/stardict/dic/ and StarDict recognized them properly...

---

### Post by nick_h on 2008-01-31
> All my dictionary files are in their respective folders in /usr/share/stardict/dic/ and StarDict recognized them properly
I had a problem with this once and have put the files directly in /usr/share/stardict/dic/, however, it would be neater for them to be in their own directories.  I'll give it another try.

---

