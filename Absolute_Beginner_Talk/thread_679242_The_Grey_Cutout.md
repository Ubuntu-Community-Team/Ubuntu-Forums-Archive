---
title: "The Grey Cutout"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Spoken on 2008-01-26
Well, here let me just give you an example.  If i have youtube opened listening to music while im surfing another webpage, sometimes when i click on another vid or type in something in the youtube search and hit enter, it will freeze, then my entire screen looses color and is black grey and white.  I have to close the window then it comes with "force quit" or cancel.  Why does it freeze up and go grey?


Ubuntu version 7.10, i have compiz fusion enabled when this happens, i dont know if it happens when i dont have compiz enabled. any ideas?

---

### Post by AndyCooll on 2008-01-26
It is Compiz Fusion that causes the greying out. Essentially it's indicating your processor is maxed out. Clearly some webpages require plenty of RAM. If you left things a bit longer you'd eventually find that your screen hasn't actually frozen, it's still working it's way through the processes.

You can turn Compiz off by going to System > Preferences > Aoppearance > Visual Effects.

:cool:

---

### Post by red_Marvin on 2008-01-26
The symptoms match the ones I get when the flash player freezes and then blocks the browser too.
If you want to kill the frozen player without killing firefox you can open a terminal and type:
(I printed the output from my terminal, yours will vary but the emphasized number is what you are interested in, the text in bold is what you type in)

```
leo@nomad2:~$ **ps -ef | grep flash**
leo      [COLOR="Red"]21352[/COLOR] 21132 10 01:34 ?        00:00:05 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-nonfree/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/21132-1
leo      21390 21311  0 01:35 pts/0    00:00:00 grep flash
leo@nomad2:~$ **kill [COLOR="Red"]21352[/COLOR]**
leo@nomad2:~$ 
```

What it does
*ps -ef* lists all running processes along with some information such as the pid  (process ID -a unique identification number)
The output from this command is "piped" to *grep* which searches the incoming data and prints the rows matching our specification, in this case rows containing the word flash
We then run the command *kill* with the pid of the flash process as a parameter so it terminates the process and everyone is happy.

---

