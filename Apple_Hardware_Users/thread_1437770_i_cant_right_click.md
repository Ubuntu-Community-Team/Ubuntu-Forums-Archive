---
title: "i cant right click"
date: 2010-03-24
forum: Apple Hardware Users
---

### Post by skakid177 on 2010-03-24
i used to have kubuntu on my ibook g4 and my right click was mapped to the eject/f12 button. now after switching to ubuntu my keys are all mapped correctly but now i dont have a right click anymore. suggestions?

---

### Post by linuxopjemac on 2010-03-24
what about F11 ? You can install mouseemu

```
sudo apt-get install mouseemu

```
to have this back

---

### Post by skakid177 on 2010-03-24
where is that. synaptic says i already have it installed but i cant find it on my computer. i just have a mouse preferences which doesnt have what i need

---

### Post by linuxopjemac on 2010-03-25
is mouseemu loaded at startup ?

what does the following give you:

```
ps -ax | grep mouseemu

cat /etc/default/mouseemu
```

---

### Post by skakid177 on 2010-03-25
matt@ubuntu:~$ ps -ax | grep mouseemu
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 1214 ?        S<s    0:00 /usr/sbin/mouseemu
 1215 ?        S<     0:01 /usr/sbin/mouseemu
 2425 pts/0    S+     0:00 grep --color=auto mouseemu
matt@ubuntu:~$ 
matt@ubuntu:~$ cat /etc/default/mouseemu
# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress




im not sure what that all means.

---

### Post by linuxopjemac on 2010-03-26
I think I see the problem...

you have to edit the /etc/default/mouseemu file
```

sudo nano /etc/default/mouseemu
```

you are now in an editor and you see the text. Remove the # in the second part of the file to make it look like this (NOT EVERYWHERE!):

```
# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default.
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 0 87" # F11 with no modifier
#MID_CLICK="-middle 125 272" # Left Apple Key (LEFTMETA) + click
RIGHT_CLICK="-right 0 88" # F12 with no modifier
#RIGHT_CLICK="-right 29 272" # Left Ctrl + click
SCROLL="-scroll 56" # Alt key
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
```

Then CTRL-X and "y" to save
Then restart and you should have right button at F12 and middle click button at F11, hope that is what you wanted...

---

