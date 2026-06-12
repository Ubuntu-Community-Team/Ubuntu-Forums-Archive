---
title: "Problems installing flow with wine."
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-09-25
I downloaded this game called Flow, and I put the file that came in the zip package on the desktop and its called flow classic.exe, I went to terminal and put in 
```
wine flow official.exe
``` and it said
```
wine: could not load L"c:\\windows\\system32\\flow.exe": Module not found
```
What did I do wrong?

---

### Post by Narcoleptic_Insomniac on 2006-09-25
bump

---

### Post by Narcoleptic_Insomniac on 2006-09-25
bump again... I hope someone helps me soon.

---

### Post by Narcoleptic_Insomniac on 2006-09-25
bump

---

### Post by catlett on 2006-09-25
You need to put the classic.exe file in wine' folder, inside the program file folder to be exact.
First launch nautilus by going to Places<Home folder. When it opens press the control key and the h key at the same time (Ctrl-h). This shows your hidden folders. That is where wine is or more exactly where .wine is (a period in front of a folders name makes it hidden)
Open up wine and then open up drive C and finally open up Program Files. As you can see, this is the folder setup for windows, Windows is usually installed on the C drive and all programs are installed to the Program Files folder.
Now drag and drop your classic.exe file from the desktop into your Program Folder. Now the file will be in wine's path. Either double click the file or enter the command in the terminal.
If you have an issue post. I only run a couple of apps through wine and that is how I did it. It may not be the 100% correct procedure but it works for me, my apps launch. Again post if you have an error and hopefully we can figure it out but I think it will work.

---

### Post by Narcoleptic_Insomniac on 2006-09-25
> **Narcoleptic_Insomniac said:**
> I downloaded this game called Flow, and I put the file that came in the zip package on the desktop and its called flow classic.exe, I went to terminal and put in 
```
wine flow official.exe
``` and it said
```
wine: could not load L"c:\\windows\\system32\\flow.exe": Module not found
```
What did I do wrong?

Still didnt work, it gave me the same thing as before. Module not found. When I double clicked the file it said "Couldn't display '/home/matt/.wine/drive_c/Program Files/flow classic.exe'"

---

### Post by Narcoleptic_Insomniac on 2006-09-26
bump

---

### Post by crokett on 2006-09-26
> **Narcoleptic_Insomniac said:**
> Still didnt work, it gave me the same thing as before. Module not found. When I double clicked the file it said "Couldn't display '/home/matt/.wine/drive_c/Program Files/flow classic.exe'"

I don't know much about wine but sounds to me like it is looking for the file and can't find it in 

'/home/matt/.wine/drive_c/Program Files/flow classic.exe'
try this:

```
 mv classic.exe /home/matt/.wine/drive_c/Program Files/flow classic.exe
```

the space in 'flow classic' may or may not be a problem.

---

### Post by ignorance on 2006-09-26
i think the space in flow classic gives a problem.
I runed my programs by putting the folders into the wine folder, than going to that folder and run the program by using wine "progam name + extension".
In your case do: wine flow classic.exe

---

### Post by Narcoleptic_Insomniac on 2006-09-26
I tried both your guys things and still nothing worked.

---

### Post by JNowka on 2006-09-26
Goto the terminal.
if the package is on your desktop type
"cd ~/Desktop"

if the package is in your .wine folder type
"cd ~/.wine/drive_c/Program\ Files/"

once there type
wine flow\ classic

This should start up either the game or the installer depending on what it is.  And make sure you use the correct slashes.  It makes all the differance.

---

### Post by Narcoleptic_Insomniac on 2006-09-26
> **JNowka said:**
> Goto the terminal.
if the package is on your desktop type
"cd ~/Desktop"

if the package is in your .wine folder type
"cd ~/.wine/drive_c/Program\ Files/"

once there type
wine flow\ classic

This should start up either the game or the installer depending on what it is.  And make sure you use the correct slashes.  It makes all the differance.

Still didnt work, I got this
```
matt@ubuntu:~$ cd ~/.wine/drive_c/Program\ Files/
matt@ubuntu:~/.wine/drive_c/Program Files$
matt@ubuntu:~/.wine/drive_c/Program Files$ wine flow\ classic
wine: could not load L"c:\\windows\\system32\\flow classic.exe": Module not found

```

What am I doing wrong?

---

### Post by JNowka on 2006-09-27
Will you please give me a link to download for the game you are trying to install, I can try to see if I can get it to work

---

