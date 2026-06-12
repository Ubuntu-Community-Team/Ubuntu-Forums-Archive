---
title: "Greetings, new to Ubuntu."
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by GreenLungz on 2007-07-18
Hello fellow Ubuntu users, I am a complete, well for a lack of better word, n00b on this here Ubuntu but I gotta say from the few hours I've had with it so far I am really impressed. The reason for my switch is a little strange, I've always liked the idea behind linux just never really went into it to much, until a month ago when my pride and joy laptop started going on the fritz. Just about 4 days ago it seemed to hit catastrophic failure and windows just shut down on me. So rather then fix another damned computer I decided to just switch over to another OS. I'm living at a friends who has a new MacBook and seeing that run gave me the incentive to just leave Windows behind me. My laptop is a 2.16 ghz centrino duo, 2 gigs of ram, ATI mobility x1600, etc etc and is loving Ubuntu right now. 

Alright well now onto the questions, alright when I said I am a complete novice I wasn't kidding, I have about 3 hours of Linux/Ubuntu under the belt right now. I have already installed Automatix and installed plenty of cool things, my main goal right now is to get tahoma fonts installed, steam installed, and CS:Source running well. Any threads out there that have this issue already addressed in a walkthrough? I've found things on the web, but my complete lack of knowledge for LInux has me confused, I have tahoma.tff and tahomabd.tff downloaded and everything and I even know that I have to move them to a directory in WINE but I have not a clue how to do any of this! 

Help appreciated :redface:

---

### Post by Hobo Joe on 2007-07-18
I'll help as best as I can.

```

sudo aptitude install wine

sudo aptitude install msttcorefonts

wget http://www.steampowered.com/download/SteamInstall.exe

cd Desktop

wine SteamInstall.exe


```

let me know of any problems you have! :)

---

### Post by felicity on 2007-07-18
Welcome to Ubuntu! 

You should be able to make a folder in your home directory called .fonts 
then you can add the Tahoma fonts to that folder and they should be available on rebooting. 

You may have to do that if you want Tahoma as I don't believe they are included in the msttcorefonts package.

---

### Post by GreenLungz on 2007-07-18
See this is where I start feeling more and more dumb :( hah, where do I type in that code, terminal?

Wine is installed, and I dont want any of the other mattcorefonts, just Tahoma and Tahomabd to get Steam running properly.

---

### Post by Ralob on 2007-07-18
yup, type (or copy/paste) into the terminal :guitar:

---

### Post by Hobo Joe on 2007-07-18
Don't feel dumb, everyone has to start at the bottom. :)

Yeah, you copy that into the terminal, one line at a time, of course.

I'd recommend getting the whole font pack though, not only will it be easier, but it'll sort out several problems that you could have in the future.

---

### Post by GreenLungz on 2007-07-18
> **felicity said:**
> Welcome to Ubuntu! 

You should be able to make a folder in your home directory called .fonts 
then you can add the Tahoma fonts to that folder and they should be available on rebooting. 

You may have to do that if you want Tahoma as I don't believe they are included in the msttcorefonts package.

Worked like a charm. Thanks!

Wow, I can already tell why people like Ubuntu, this forum responded quick, talk about "customer" service. :)

---

### Post by GreenLungz on 2007-07-18
> HTTP request sent, awaiting response... 200 OK
Length: 725,262 (708K) [application/x-msdos-program]

100%[====================================>] 725,262      250.62K/s             

12:55:40 (249.89 KB/s) - `SteamInstall.exe' saved [725262/725262]

greenlungz@greenlungz-laptop:~$ cd Desktop
greenlungz@greenlungz-laptop:~/Desktop$ wine SteamInstall.exe
wine: could not load L"c:\\windows\\system32\\SteamInstall.exe": Module not found
greenlungz@greenlungz-laptop:~/Desktop$ 


:confused:

---

### Post by Hobo Joe on 2007-07-18
Glad to be of service. :)

Just as a a warning, most Steam games will work, BUT you may, and probabaly will have, a performance decrease over Windows, its native OS.

EDIT:

Just saw your post, did the file download to the desktop?

---

### Post by GreenLungz on 2007-07-18
Nope, where could it have gone...

Err nevermind, found it in the /home directory. So now, what do I put into Terminal?

---

### Post by Hobo Joe on 2007-07-18
You may just be able to double-click to open it, try that. 

If that doesn't work, just move it to the desktop and use the previous instructions.

---

### Post by GreenLungz on 2007-07-18
> **Hobo Joe said:**
> You may just be able to double-click to open it, try that. 

If that doesn't work, just move it to the desktop and use the previous instructions.

Yep, worked. :guitar:


Thanks a lot guys, this was way more help than expected, especially that quickly.

---

### Post by Hobo Joe on 2007-07-18
Welcome to the Ubuntu family. :D

You'll like it here.

---

