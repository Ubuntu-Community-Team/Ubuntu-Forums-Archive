---
title: "Problem installing keyboard drivers."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by sentics on 2007-04-04
I recently tried to install colemak key layout using the following instructions;

Download, untar/gunzip archive 
Under Debian/Ubuntu/Knoppix/Debian derivatives type: install-keymap linux_console/colemak.iso15.kmap to install as the default layout. 
Type: loadkeys linux_console/colemak.iso15.kmap to switch layouts. 
To switch to a ISO8859-15 compatible font type: consolechars -f lat9v-14 
To switch back to QWERTY type: loadkeys us 

However everytime I do this I get command not found or permission denied.   Can somebody explain to me how im supposed to do this as Im having major problems with the terminal and no colemak.  

More info can be found at 
[http://colemak.com/Unix](http://colemak.com/Unix) 
Regarding the drivers for unix.

---

### Post by Kobalt on 2007-04-04
If you get a permission error then you need to type **sudo** before your command in order to give it Super User permissions, here's an example 
```
sudo loadkeys us
```

---

### Post by sentics on 2007-04-04
Thanks so much I shall try this.   Your a lifesaver:)

---

### Post by sentics on 2007-04-04
Okay so I tried the sudo command before the install command and I got the error command not found.

---

### Post by sentics on 2007-04-05
Is there any way around this?

---

### Post by justintime32 on 2007-04-21
Try "sudo apt-get install console-common" first

---

