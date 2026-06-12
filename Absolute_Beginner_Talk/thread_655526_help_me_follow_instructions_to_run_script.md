---
title: "help me follow instructions to run script"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by rutilajw on 2008-01-01
So, I downloaded [http://ubuntuforums.org/attachment.p...1&d=1155502600](http://ubuntuforums.org/attachment.p...1&d=1155502600) this for m4a to mp3.  Inside there is a readme with instructions for installation.  They are:

# Download packages: 
# 1 - sudo apt-get install mplayer-386 faad lame libfaad2-0 id3v2
# 2 - Extract all files to a temporary folder and cd to that directory
# 3 - Move the bash & python script to the bin folder:
#     sudo mv aac2mp3.txt /usr/local/bin/aac2mp3
#     sudo mv py_aac_2_mp3 /usr/local/bin/py_aac_2_mp3
# 4 - Make these files executable:
#     sudo chmod +x /usr/local/bin/aac2mp3
#     sudo chmod +x /usr/local/bin/py_aac_2_mp3

i dont understand what the second step means.  Extract what files to a temporary folder?  The programs from step 1?  Because if that's so, I can't figure out what it's talking about.  When you sudo apt-get install, it's very nice and easy and doesn't give you any files so I don't know what to extract.

---

### Post by Dr Small on 2008-01-01
Step number two, means Right click on the archive and extract it. Then in the terminal, cd to the new extracted directory:
```
cd *directory_name*
```

---

### Post by rutilajw on 2008-01-01
Alright, I figured it out.  I didn't realize it was just talking about cd'ing to the directory of the folder you just downloaded.  That is all :)

---

