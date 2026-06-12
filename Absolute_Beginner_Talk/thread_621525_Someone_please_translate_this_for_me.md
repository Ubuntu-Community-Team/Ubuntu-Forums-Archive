---
title: "Someone please translate this for me?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by jonwatts on 2007-11-23
i know this might sound silly, but I'm trying to get my wireless working on 7.10 and can't get past the 1st damn step of the madwifi installation:
"open a shell terminal in the madwifi source directory"
duh! how do i do that?

thank
jon

ps I'm not a total idiot... i've downloaded it and unpacked it, and I know how to open a root terminal, but how do I open a shell terminal in the "madwifi source directory"?

---

### Post by taurus on 2007-11-23
Open a terminal, Applications -> Accessories -> Terminal, and change to where you have saved the madwifi file.  You can change directory with the cd command.

```
cd *directory_name*
```

Do you know exactly where you have unpacked it?

---

### Post by jonwatts on 2007-11-23
on the desktop, so would it be 

cd desktop

?

---

### Post by Sarteck on 2007-11-23
It is as taurus said (assuming you are using regular Ubuntu, and not Kubuntu or other).  However, what instructions are you using to install it?

---

### Post by taurus on 2007-11-23
```
cd ~/Desktop
ls -la 
```

Post the output of the second command.

---

### Post by spiderbatdad on 2007-11-23
i think its the other way around open the directory in a shell terminal.
i think you need to know where the directory is. Then open a terminal and type cd /the/location/of the/directory
and hit enter.
For example if the directory is in Desktop:
```
cd Desktop/
```
enter
then
```
cd nameofdirectory
```

---

### Post by jonwatts on 2007-11-23
um, haha

the squiggly key doesn't seem to work in the terminal...?  
"cd desktop/" doesn't work
I'm using the [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by paradoxni on 2007-11-23
case sensitive.. its Desktop

---

### Post by taurus on 2007-11-23
Linux/Unix is a case sensitive.  It means that desktop IS NOT the same as Desktop.

```
cd ~/**[COLOR="Blue"]D[/COLOR]**esktop
ls -la
```

---

### Post by Sarteck on 2007-11-23
Okay, it seems that they want you to navigate to the directory you unpacked it to.  Just open the terminal, and (assuming you unpacked it to the desktop) type **cd Desktop**.

Now here's the neat part...  If you know the first part of the name, you can just press "TAB" to autocomplete it.  You want to get into the MadWifi directory you unpacked?```
cd mad
```and here, just press the "TAB" key to complete it.  :)  Then press "Enter" of course.

---

### Post by jonwatts on 2007-11-23
ok... thanks for the help!  

so am i now in the madwifi directory, or is there a step after the desktop?

...because none of these codes are doing anything 
(ifconfig ath0 down
ifconfig wifi0 down

cd scripts
./madwifi-unload.bash
./find-madwifi-modules.sh $(uname -r)
cd ..

make)

---

### Post by jonwatts on 2007-11-23
sorry, i wrote that before I saw sartek's response... wow, thanks for all of the patience and help!

---

### Post by Sarteck on 2007-11-23
When you unpacked that stuff, it should have created a directory on your desktop.  "cd" to that directory.

[EDIT] Sorry, wrote that before I saw your response to my response.  And no problem! :)

---

