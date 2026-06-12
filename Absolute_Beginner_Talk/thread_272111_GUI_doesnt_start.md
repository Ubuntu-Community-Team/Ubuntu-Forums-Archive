---
title: "GUI doesnt start"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by y3ahright on 2006-10-05
I dual booted with windows and now when ever i try and load ubuntu the gui doesnt start.  It gave me a blue screen saying something was wrong and try and fix it with diagnostics.  I tryed startx but nothing works.. please HELP!!!

---

### Post by y3ahright on 2006-10-05
IT states.
Failed to start X server.
It is likely that it is not setup correctly.  Would you like to view the Xserver to diagnose the problem
<YES>         <NO>

---

### Post by bodhi.zazen on 2006-10-05
Answer no.

You will drop to a CLI.

Log in.

Then:```
sudo dpkg -reconfigure -phigh xserver-xorg
sudo gdm
```

---

### Post by y3ahright on 2006-10-05
it says conficting actions dpkg: --control and remove--

---

### Post by y3ahright on 2006-10-05
it shows a lot of help topics but i dont know what they mean lol...

---

### Post by ewl1217 on 2006-10-05
It should read like this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo gdm
```
There should be no space in the dpkg-reconfigure command.

---

### Post by y3ahright on 2006-10-05
THANK YOU SO SO MUCH there is just one weird thing... when i typed sudo gdm it sayed ABORTING!! already running. so i did startx but its in 640x480... it wont lemmie change any way to change in the terminal???
thx

---

### Post by Lord Illidan on 2006-10-05
You should have did ```
sudo gdm restart
```

---

### Post by bodhi.zazen on 2006-10-05
> **y3ahright said:**
> THANK YOU SO SO MUCH there is just one weird thing... when i typed sudo gdm it sayed ABORTING!! already running. so i did startx but its in 640x480... it wont lemmie change any way to change in the terminal???
thx

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm stop (second time for good measure)
sudo gdm
```

---

### Post by ewl1217 on 2006-10-05
Did you choose the correct resolutions and graphics driver during that command? Try it again using this command:
```
sudo dpkg-reconfigure xserver-xorg && sudo /etc/init.d/gdm restart
```

**EDIT:** What bodhi.zazen reccomended will do almost the same thing as mine (my command will reconfigure xorg again). Just try mine if his idea doesn't work.

---

### Post by y3ahright on 2006-10-05
> **bodhi.zazen said:**
> ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm stop (second time for good measure)
sudo gdm
```

says its command not found.
same with ewl1217.. this is so weird..

---

### Post by ewl1217 on 2006-10-05
Could you post the output of the following command?
```
ls /etc/init.d | grep dm
```
I just edited that so it wont give such lengthy output.

---

### Post by y3ahright on 2006-10-05
no such file or directory... great this is a problem LOL my luck

---

### Post by y3ahright on 2006-10-05
even after the edit no such file or directory do i have to remake it or something???

---

### Post by ewl1217 on 2006-10-05
Just try this:
```
sudo gdm restart
```
If that doesn't work:
```
sudo apt-get install --reinstall gdm
```

---

### Post by y3ahright on 2006-10-05
GDM already running ABORTING!!!
and i am using an installed version.. not a live cd

---

### Post by ewl1217 on 2006-10-05
Yeah, I just realized that. It's always confusing going back and forth betwen a bunch of threads...

---

### Post by y3ahright on 2006-10-05
its cool lol.. i just like the fact that ur helpin me...

---

### Post by y3ahright on 2006-10-05
lol when i did the reintall gdm thing. and nothing rly happend cept it was like uhhh should i reinstall yes or no... i really want to know why 640x480 is the highest resolution i have (and lowest.. its the only choice)

---

### Post by y3ahright on 2006-10-05
ls /etc/init.d | grep dm 
when i type that in it says 
"no such file or directory" im thinkin that  might be a big problem??

---

### Post by bodhi.zazen on 2006-10-05
Starting to look that way.

Output of ls /etc/init.d

---

### Post by az on 2006-10-05
> **y3ahright said:**
> THANK YOU SO SO MUCH there is just one weird thing... when i typed sudo gdm it sayed ABORTING!! already running. so i did startx but its in 640x480... it wont lemmie change any way to change in the terminal???
thx

boot into recovery mode and run

dpkg-reconfigure xserver-xorg

and that will ask you a bunch of questions (you don't get asked questions with the -phigh option).  Lower your color depth to 16 bit.  This will work for you if you are using an older video card and it has not a lot of ram.

Did you change cards after installing Ubuntu?  Ubuntu only detects your video card at install time.  Which is why you need to do it again if you change your hardware.

EDIT:  Run
init 2
to get out of recovery mode...

---

### Post by y3ahright on 2006-10-05
ok i have a compaq presario and its the intel somthineranother video card.  the only option i have in my change screen resolution is 640x480 and nothing else.  I updated the vcard in windows yesturday... and my windows went to 640x480 with like low 8 bit but i was able to change that y cant i change linux????:confused:

---

### Post by bodhi.zazen on 2006-10-06
> **y3ahright said:**
> ok i have a compaq presario and its the intel somthineranother video card.  the only option i have in my change screen resolution is 640x480 and nothing else.  I updated the vcard in windows yesturday... and my windows went to 640x480 with like low 8 bit but i was able to change that y cant i change linux????:confused:

Try this link:

[[color=blue]bodhi's resolution solution[/color]](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)

---

### Post by y3ahright on 2006-10-06
lol thx for all ur help guyz... when i updated the divers on windows it changed the CMOS setting for my integreated card to 1 MB so all i did was changed it to 8MB insted.. THX again

---

