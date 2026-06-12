---
title: "Lexmark Z515"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by sidewalkpilot on 2006-04-21
I have a Lexmark Z515.  How do I get it to work in Ubuntu (breezy badger)?  Thanks! 

/users/newguy

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=sidewalkpilot]I have a Lexmark Z515.  How do I get it to work in Ubuntu (breezy badger)?  Thanks! 

/users/newguy[/QUOTE]
Check [ this tutorial out. ](http://ubuntuforums.org/showthread.php?t=49714&highlight=Lexmark+Printers) Even though it's for Hoary, it will still work and the Z600 driver works with almost every printer. Also try [http://www.linuxprinting.org](http://www.linuxprinting.org) for information about your printer.

Edit: Your printer is confirmed to work with the Z600 driver.

---

### Post by sidewalkpilot on 2006-04-21
The steps were working until I got to the command 'alien.'  

alien -t z600cups-1.0-1.i386.rpm

bash: alien: command not found


Thanks... just let me know how to get around this. ;)

---

### Post by xXx 0wn3d xXx on 2006-04-21
> **sidewalkpilot]The steps were working until I got to the command 'alien.'  

alien -t z600cups-1.0-1.i386.rpm

bash: alien: command not found


Thanks... just let me know how to get around this.  said:**
> 

In terminal put this in:
[QUOTE]
sudo apt-get install alien

Then it should work. :)

---

### Post by sidewalkpilot on 2006-04-21
That did it.  Thanks for your help!

BUT... I ran into another problem.  All steps are going along perfectly except:

Check whether the printer backend works;
Code:
$ cd /usr/lib/cups/backend $ ./z600

I get the following:
shawn@ss-ubuntu:/usr/lib/cups/backend$ ./z600

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Any help would be fab.  Thanks again! :)

shawn

---

### Post by Sef on 2006-04-21
Try this

sudo apt-get install libstdc++.so.5

if that doesn't work then try this

sudo apt-get install libstdc++

---

### Post by sidewalkpilot on 2006-04-21
Uh-oh, neither of those worked.  I'm so close to having this thing installed. :(  Thanks for your help, everybody.  But please help me get past the following:

shawn@ss-ubuntu:/$ sudo apt-get install libstdc++
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc
shawn@ss-ubuntu:/$


shawn@ss-ubuntu:/$ sudo apt-get install libstdc++.so.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc++.so.5
shawn@ss-ubuntu:/$

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=sidewalkpilot]Uh-oh, neither of those worked.  I'm so close to having this thing installed. :(  Thanks for your help, everybody.  But please help me get past the following:

shawn@ss-ubuntu:/$ sudo apt-get install libstdc++
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc
shawn@ss-ubuntu:/$


shawn@ss-ubuntu:/$ sudo apt-get install libstdc++.so.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc++.so.5
shawn@ss-ubuntu:/$[/QUOTE]

Try replacing your sources.list with the one I have attached. Copy and paste. Your sources.list can be found in /etc/apt/sources.list.

---

### Post by sidewalkpilot on 2006-04-21
I replaced the sources.list with the one provided.  I also did all updates.  But I still encounter:

shawn@ss-ubuntu:/$ sudo apt-get install libstdc++
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc
shawn@ss-ubuntu:/$


shawn@ss-ubuntu:/$ sudo apt-get install libstdc++.so.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc++.so.5
shawn@ss-ubuntu:/$

I'm having trouble with that missing package that it's looking for...


any ideas?

---

