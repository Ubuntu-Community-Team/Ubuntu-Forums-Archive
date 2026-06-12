---
title: "Help with a script to modify text files"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Mguel on 2006-03-02
Hi, I wanted to create a script to do simple RegExpression text replace of srt subtitle files.


I wanted to use the for example the following command:
```
sed 's/<i>//g;s/<\/i>//g' file.srt > file_new.srt
``` 
What I would like is that the script modifies all the *.srt files of a folder. By "modify" I mean replace the old file with the resulting one (I haven't been able to do that from the terminal using sed).

Regards,
Mguel

PS: Using Kubuntu 5.10, KDE 3.5.1
PSS: On windows I used SubtitleWorkshop which had regexp files for modifying the subtitles easily. I haven't been able to make it run using wine since it seems it depends on DirectX

---

### Post by colo on 2006-03-02
man sed:
```
       -i[SUFFIX], --in-place[=SUFFIX]

              edit files in place (makes backup if extension supplied)
```

This leads us to the following conclusion:
```
$ sed -i "YOUR_SED_COMMANDS_GO_HERE" YOUR FILES GO HERE
```

For example:
```
$ sed -i "s/foo/bar/ig" *txt *asc *utf8
```
would replace all occurences of "[Ff][Oo]{2}" with "bar" in all files ending in {txt,asc,utf8} in the current working directory.

---

### Post by Mguel on 2006-03-02
Thanks a lot, I read the man before, but didn't get it.... so thanks for your answer ;)

---

### Post by Mguel on 2006-03-02
Now I managed to make have it working as an action menu item on konqueror by creating a file (ie: "srtScript.desktop") under:

~/.kde/share/apps/konqueror/servicemenus

> [Desktop Entry]
ServiceTypes=text/srt
Actions=srtScript

[Desktop Action srtScript]
Name=Run srt Script
Exec=sed -i 's:<i>::g;s:<\/i>::g;s:^\.\.\.::g;s:^- \.\.\.:- :g;s:--\r:...:g' *srt 
It works fine with the selected files (can work with more than one file).

If there is an error please correct me.

Cheers,
Mguel

---

