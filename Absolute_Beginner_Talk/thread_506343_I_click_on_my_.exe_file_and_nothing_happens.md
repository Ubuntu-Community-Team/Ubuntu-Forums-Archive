---
title: "I click on my .exe file and nothing happens"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by ichez on 2007-07-21
I downloaded gridwars 2 for linux and after I extracted it I got an .exe file in a folder. I double click on my .exe file and nothing happens. I'm kind of new to this, but ive set all my permissions for that file to read and write for every one.

---

### Post by por100pre1 on 2007-07-21
Try this first:

```
wine routetoexecutable
```

---

### Post by Majorix on 2007-07-21
I don't think you have wine installed at all.
```
sudo aptitude install wine
```

Then do as told above.

---

### Post by por100pre1 on 2007-07-21
> **Majorix said:**
> I don't think you have wine installed at all.
```
sudo aptitude install wine
```

Then do as told above.

I agree with Majorix. Usually when right-clicking an .exe file the execute with Wine option appears.

---

### Post by NESFreak on 2007-07-21
since you say it's a linux version, first try looking for a file gridwars.bin or gridwars.x86 or something like that. right click on it and select the bottom option. go to the rights tab and select execute. close the window and try running the file u just gave the right to run. If you cant find a file like that then search the forums or the wiki on how to compile applications.

---

### Post by ichez on 2007-07-21
I got the game from here [http://gridwars.marune.de/](http://gridwars.marune.de/)
wine tells me it's a bad .exe file or something like that

---

### Post by Campingman on 2007-07-21
Did you end up with gridwars_lin.zip?  
If so open with archive manager and extract to where you require. 
In the extracted folder there is a file called gridwars, this is the executable just click on it and it will launch the game.
You can then open preferences>menu  and add a link to the executable and put the launcher on your menu

---

### Post by FleetAdmiral74 on 2007-07-21
You can also right click the exe, and open it with the custom command "wine" (without quotes) if you don't like the command prompt a whole lot

---

### Post by Campingman on 2007-07-21
> **ichez said:**
> I got the game from here [http://gridwars.marune.de/](http://gridwars.marune.de/)
wine tells me it's a bad .exe file or something like that

If you downloaded the correct file, the "lin" selection, you do not need wine, follow the steps above and it will work fine.

---

### Post by ichez on 2007-07-21
yes i've got the correct file from the website, im running Kubuntu and I extracted the archive to my desktop, I double-click on gridwars.exe and then nothing appears. Im not quite sure why it would do that.

---

### Post by Campingman on 2007-07-21
> **ichez said:**
> yes i've got the correct file from the website, im running Kubuntu and I extracted the archive to my desktop, I double-click on gridwars.exe and then nothing appears. Im not quite sure why it would do that.
Very odd, when I extract it I just get gridwars with no extension and the following files:
gfx(folder), music (folder), sounds (folder), bass.dll, config.txt,.  Double clicking or right click and open runs the game.  I am in Ubuntu though so maybe that is the issue

---

### Post by FleetAdmiral74 on 2007-07-21
Maybe give us a link to the page where you are downloading, and we can sort it out. 

And its not executing the exe because that is not an extension used in Linux natively.

---

### Post by Campingman on 2007-07-21
> **ichez said:**
> I got the game from here [http://gridwars.marune.de/](http://gridwars.marune.de/)
wine tells me it's a bad .exe file or something like that

He gave the download link earlier, it works fine for me with no wine.

---

### Post by Depressed Man on 2007-08-01
Is it outputting an errors.txt in the directory you placed it? For example mine says "Can not set graphics mode: Windowed - 1024x768"

---

### Post by Sspankyy on 2007-08-01
Hmmm....  Just for fun, I downloaded it and tried to load it...

   When I double clicked on the file, it kinda "half rebooted" my computer...  Not from the bios, but it seemed to reload most of Ubuntu... The first thing it said was "Starting Portmap Daemon".

            Any Ideas?

Scott

---

