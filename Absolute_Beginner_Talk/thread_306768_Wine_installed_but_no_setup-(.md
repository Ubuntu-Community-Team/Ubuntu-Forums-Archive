---
title: "Wine installed but no setup:-("
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by dogwi11hunt on 2006-11-25
Okay I've installed Wine, but when i try to run "wine setup" it wont run. It says it cant find the wine setup file but shouldn't it be somewhere if i installed wine. help would be sper appreciated. I have ran the Winecfg.

---

### Post by tocleora on 2006-11-25
"wine setup" would be what you'd type if you were trying to run setup.exe.  The only one I know of is winecfg.  I was able to get starcraft working without anything other than winecfg.  What exactly are you trying to do?

---

### Post by dogwi11hunt on 2006-11-25
im trying to run steam and i can run it but you cant see words and you have to put tahoma.ttf file in the "hidden" wine files but with out wine setting up it cant make the files.

---

### Post by bodhi.zazen on 2006-11-25
To set up wine type winecfg in a terminal.

To use your fonts, copy the font to ~/.wine/c/fonts or wherever in your wine "fake c drive" you have your fonts installed.

---

### Post by dogwi11hunt on 2006-11-25
i did winecfg a bunch of times and then try and run wine setup and it still says it cant find file "wine wetup"

---

### Post by bodhi.zazen on 2006-11-25
That is because there is no such thing as "wine setup".

If you are trying to install something you need to run:

wine /full/path/to/setup.exe
If the path has spaces, like Program Files, use double quotes:

```
wine "/full/path/to/setup.exe"
```

---

### Post by dogwi11hunt on 2006-11-25
aparently if you type wine setup in the terminal it sets up the fake c drive files and i need the fake c drive files to install tahoma font in them so when i run steam with wine you can read the tahoma font.

---

### Post by bodhi.zazen on 2006-11-25
As has been mentioned, to set up wine type winecfg in a terminal.

The fake c drive is in your home folder, but hidden.

to see it, in a terminal type:```
 ls -al ~ | grep .wine
```

Now try this:

```
cd ~/.wine
ls
```

the "c" is your fake c drive.

now ```
cd ~/.wine/c/
ls
```

---

### Post by steve.horsley on 2006-11-25
Maybe I've got the wrong end of the stick, but if you're trying to run a windows installer program, shouldn't it be **wine setup.exe** rather than **wine setup**?

---

### Post by dogwi11hunt on 2006-11-25
i dont know im suuper new to linux. i tried wine setup.exe though and it didn't do anything

---

### Post by dogwi11hunt on 2006-11-25
by some amazing act of god i can read the words on the steam installation windows, but when i get to the second step it freezes

---

### Post by tocleora on 2006-11-25
You don't have to setup or configure to add a font, you just need to add it to the right folder.  Do this:

1. Run winecfg (yes, winecfg).
2. Click on the "drives" tab.
3. You should have an option for "C:" here.  What this does is it tells you what linux location it maps (or assigns) the drive letter "C" to.  In my situation, My C: drive is mapped to /home/tocleora/.wine/drive_c/. 
4. Navigate to that folder.  So for me I would type "cd /home/tocleora/.wine/drive_c/" without quotes.
5. From here it should look just like your C drive, for example, I have a "program files" folder, and a "windows" folder, just like in my actual c drive in windows.  so from here I "cd windows" without quotes to get into the windows folder (which is actually located [for me] at /home/tocleora/.wine/drive_c/windows/).
6. in the windows folder I have a fonts folder, just like in windows.  Copy the file into this fonts folder and you should be good to go.  So if I had a font in my home directory for example, I could type: "cp /home/tocleora/fontname.tff /home/tocleora/.wine/drive_c/windows/fonts" without quotes.

Does that make more sense?

Regarding "wine setup"... The way wine works is, if you have a windows application you want to run, you would type in "wine [application executable]"  so if I wanted to start notepad.exe, I would type in "wine notepad.exe".  This is what we are trying to explain to you, when you type in "wine setup" it's looking for a windows file named setup.exe to run, and that's why it's giving you the error.  The setup you are looking for is called "winecfg", and that's the *only* one that relates to wine setup and/or configuration.  Now when you put in a CD, you can navigate to that CD and type "wine setup" to run the application's setup, but that's the only time you'll use it.  

Hope that helps you get a little closer, good luck. :)

---

