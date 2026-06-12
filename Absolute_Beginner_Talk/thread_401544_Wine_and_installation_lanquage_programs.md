---
title: "Wine and installation lanquage programs"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-04
[COLOR="DarkRed"]Hello, I am trying to install several language programs, I have downloaded Wine from automatix.  I opened up my CD program hit the exe. and thr properties to Wine opened.  I chose 95 the first time then XP the second.  I did open the terminal and typed wincecfg, but just have a blinking cursor.  I am not sure how to get the program up and running can someone help me please?

Thank you 
Sherri[/COLOR]

---

### Post by cypherzero on 2007-04-04
type 'wine <appname>' where appname is the exe you wish to run.

---

### Post by delilahjed44 on 2007-04-04
[COLOR="DarkRed"]Hey thanks for replying.  I was able to install the program files but I am getting[COLOR="DarkRed"]cannot find *.wav file and I was trying to look at an e-mail that required a wmv filr for totem, so I could see a dvd play.  I dont know if its two of the same thing. Where can I get this file? the program opened up and began to play, but then needed that wav file.  Ok Thanks, geezzzzzz I actually have several to install but what I learn here I will try.  I downloaded the wine from a file here and unloaded it, followed the path and it worked.

Sherri[/COLOR][/COLOR]

---

### Post by delilahjed44 on 2007-04-04
[COLOR="DarkRed"]Hello, I am finding that the program needs *wav pcx and avi files to run.  I saw on the net about file conversions in which I am clueless.  I am wondering though if I convert these files if it will affect other movies I have.  I dont even know if I need to do that.  I dont know what to look for in my properties for the files, I know wav is oudn, and I have sound now, but dont know what my probram file requires outside of what is said above.

Sherri[/COLOR]

---

### Post by david_kt on 2007-04-04
It might be your installation is not successfull, i.e. it unable to extract your video file. So, it not the player problem, but file problem. Could your repeat the installtion in terminal, and observe any error encounter.

Another ease way is to repeat installation in windows, and after copy the entire program folder, for example:

C:/Program Files/Your_Program_Folder

and move it to your linux:

Open nautilus, press CTRL+H, click .wine folder, click drive_c,click Program Files, and paste your folder there. After that, try to run your program again and see what happen.

DK

---

### Post by delilahjed44 on 2007-04-05
> **david_kt said:**
> It might be your installation is not successfull, i.e. it unable to extract your video file. So, it not the player problem, but file problem. Could your repeat the installtion in terminal, and observe any error encounter.

Another ease way is to repeat installation in windows, and after copy the entire program folder, for example:

C:/Program Files/Your_Program_Folder

and move it to your linux:

Open nautilus, press CTRL+H, click .wine folder, click drive_c,click Program Files, and paste your folder there. After that, try to run your program again and see what happen.

DK

[COLOR="DarkRed"]Hi David, thank you for your help.  I tried to open wine with Control + H , it would not open. First I copied the folder I needed from my CD.
then went to Aplications where wine is, and went through file manager, found wine, opened it, went to paste and there was no option to do that.  I had right clik and no options for paste.  I am running full system Ubuntu no XP Windows at all.  I did see in the file manager an existing program file stating C, opened it and nothing came up but 3 files that did not contain my CD I am trying to load or I may have been able to copy and paste from there.  I am not familiar with Nautilus, but I did try to open CTRL + H but it did not open.  So I am still at zero trying to get this fixed.  I have 3 programs to put in, I beleive once one is in the others should relatively comply some where along the same lines.

Sherri

Sherri[/COLOR]

---

### Post by delilahjed44 on 2007-04-05
[COLOR="DarkRed"]Hi David, I am wondering something now, how do I find the exact name of the program, since what is labled on CD is not working in terminal, I typed it several ways, running it together and with dividers, I originally use the exe file which is typed this way> AutoRun.exe, I have checked the properties of the Program and found TMMS_GERMAN_CD1 < tried this also with no luck in the termian, what the heck??? great now I cant even find the name of the program, do you know how I can get this, of course I will need this first I suppose.  Thanks.[/COLOR]

Sherri

---

### Post by delilahjed44 on 2007-04-05
[COLOR="DarkRed"]Sorry for so many post, I was able to get this program running, dont know how, it would not open earlier, it did open and had some serious lock-ups, not I am getting sound one program but not the other, its all on the same particular disk in which my choices for using the program, I do have other disk that apply to it.  But the sound is on some of this and not all, what should I do? at least it is working that is a plus! just no sound on every part and it is needed of course.

Sherri[/COLOR]

---

### Post by david_kt on 2007-04-05
> **delilahjed44 said:**
> [COLOR="DarkRed"]Hi David, I am wondering something now, how do I find the exact name of the program, since what is labled on CD is not working in terminal, I typed it several ways, running it together and with dividers, I originally use the exe file which is typed this way> AutoRun.exe, I have checked the properties of the Program and found TMMS_GERMAN_CD1 < tried this also with no luck in the termian, what the heck??? great now I cant even find the name of the program, do you know how I can get this, of course I will need this first I suppose.  Thanks.[/COLOR]

Sherri

I am not sure about it as well. First of all, make sure wine is installed properly. When you open terminal and type 

```
winecfg
```

Did it run something? If it is as you said, just a cursor blinking, then your wine is not properly installed.

DK

---

### Post by delilahjed44 on 2007-04-05
> **david_kt said:**
> I am not sure about it as well. First of all, make sure wine is installed properly. When you open terminal and type 

```
winecfg
```

Did it run something? If it is as you said, just a cursor blinking, then your wine is not properly installed.

DK
[COLOR="DarkRed"]Hey, well the program has started up and I was able to use fome of its functions including sound, but I still get error sign for the files I listed.  It freezes up when I try to close out.  It only has sound from page to page, some pages in the program have sound and others do not.  Since it is a lanquage program I need all the sound working.  I do have the wind installed, it is in my applications menu inder its name wine.  I open the program usually by the AutoRun.exe file and open it from there.  I dont know what to do with the sound problem?

Sherri[/COLOR]

---

### Post by david_kt on 2007-04-05
> **delilahjed44 said:**
> [COLOR="DarkRed"]  I dont know what to do with the sound problem?

Sherri[/COLOR]

Try to run winecfg on terminal, and click on sound tab. Try different options on that sound tab.

DK

---

