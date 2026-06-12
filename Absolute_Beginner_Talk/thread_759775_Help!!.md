---
title: "Help!!"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by bad73mav on 2008-04-19
ok i jus installed ubuntu 7.10 im coming from windows so i have no clue on how to fix.. heres ther issue like i said fresh install whewn u first load it has balloon for updates and another one for graphics driver well it said something about allowing 3d acceleration i dled it  rebooted and now  when i get to login screen it flashes white so can i reset the graphics driver in recovery mode but i dont know what to type to fix it .. any help is appreciated

---

### Post by quirks on 2008-04-19
I could imagine, that the program makes a backup of your Xorg.conf file, before applying the changes. Can you tell me what the output of this command is:
> ls -l /etc/X11

---

### Post by Martin Witte on 2008-04-19
You can run the command 'sudo lshw' to list your hardware (sudo runs a command as root user, that's why it asks for your password), look in the output for display controller, that should give you  an idea what driver you need. Next step is eventually downloading and installing the driver from synaptic, if you have the driver you can set it up with command 'sudo dpkg-reconfigure xserver-xorg'.

---

### Post by forrestcupp on 2008-04-19
Boot to recovery mode and type
```
dpkg-reconfigure xserver-xorg
```This will take you through a setup to reconfigure X.  When it asks for your video card, choose Vesa.  This will guarantee that you will be able to get back to your desktop.  You won't have 3D support, though.

Now, when you get back to your desktop, you will be able to set it up with workable drivers.  If you have an nvidia or ATI video card, you may have more success using [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to automatically download and install the latest drivers.

---

### Post by prshah on 2008-04-19
> **bad73mav said:**
>  when i get to login screen it flashes white so can i reset the graphics driver in recovery mode but i dont know what to type to fix it .. any help is appreciated

When you get the white screen, switch to a command line screen by pressing Ctrl+Alt+F1, then login as usual. Then give the command ```
metacity --replace
``` and switch back to Ctrl+Alt+F7. Has your screen reappeared? If not, press Ctrl+Alt+BkSpace, and it should reappear. 

If it still does not come back, post here.

---

### Post by bad73mav on 2008-04-20
thanks for all the answers.. ill member that stuff if it happens again.. i redid the whole thing but this time i set up partitions ..so im still learning  so far i like better than windows..and  i even figured out how to download music and  put them on my mp3 player alot of forum reading ....

---

### Post by Saint Angeles on 2008-04-20
> **prshah said:**
> When you get the white screen, switch to a command line screen by pressing Ctrl+Alt+F1, then login as usual. Then give the command ```
metacity --replace
``` and switch back to Ctrl+Alt+F7. Has your screen reappeared? If not, press Ctrl+Alt+BkSpace, and it should reappear. 

If it still does not come back, post here.
its alt+f2 then "metacity --replace"

do that while the screen is white. it happens to me on a fresh install when i havent configured my Xorg.conf yet

---

### Post by prshah on 2008-04-20
> **Saint Angeles said:**
> its alt+f2 then "metacity --replace"
do that while the screen is white. it happens to me on a fresh install when i havent configured my Xorg.conf yet

When Compiz is not properly setup, you get a "white-out" screen where you cant see anything. Rather than do a command in-the-blind, it better and safer if he see what he's doing, hence the suggestion to switch to a virtual terminal.

---

### Post by Saint Angeles on 2008-04-20
> **prshah said:**
> When Compiz is not properly setup, you get a "white-out" screen where you cant see anything. Rather than do a command in-the-blind, it better and safer if he see what he's doing, hence the suggestion to switch to a virtual terminal.
true... but it doesnt hurt your computer to "do it blind" that way it immediately shuts off compiz and you are back at a desktop again. the computer works fine when the white screen is on... its just the screen thats messed up.

---

### Post by bad73mav on 2008-04-20
ok i cant find a  post with this problem so ill post it first off lennox is alot better but im coming to find out its alot more irratating but herea issue i cant seem to resolve ok, in windows to load music files to mp3 player u drag from yer saved folder to the player  well i try same thing in lennox and it gives me i/o error. ok can i not do that or is there another way im not aware of to do it or do i need a plug in or something still fresh install the only thing i did was get g streamer plug ins so totem would work other than that done nothing else... sorry for so many problems but im irratated and trying to learn how to fix these issues

---

### Post by Saint Angeles on 2008-04-20
in a terminal, type:
```
sudo apt-get install ubuntu-restricted-extras
```

and its Linux, not lennox

---

### Post by bad73mav on 2008-04-20
well it worked.. irratation gone :) and its funny cause i couldnt put comedy tracks on my player on windows but i can on here.. how great is that and no more stupid tracking cookies..the only reason i was hesitant on switching to linux was im a gamer and im not sure if u can game on linux yet.. but now that it is set up it is sooo much better.. u have any sites that r good to learn about the sudo commands so next time i have issue ill hopefully be able to solve it.. and thanx for all the help

---

### Post by bad73mav on 2008-04-20
ok hmm everything is working great..this new issue is coming up that when i rungnutella to get music i have im's going that i wont be able to get to home folder ill click on it nothing it freezes  i can still use firefox but icons on the desktop i click on those and it says error too many apps going i shut them down same thing i dont get it... i try sudo apt-get update and theres some but how do i install ???

---

### Post by nicedude on 2008-04-21
Just use the update manager, by going to top toolbar menu named System->Administration->Update Manager its GUI interface so you will figure out the rest.

Also try clicking "Synaptic Package Manager" on the same system admin menu, its a searchable list of all the things you can install from the ubuntu repositories. Its nice if you don't know what is available just search around in there.

---

