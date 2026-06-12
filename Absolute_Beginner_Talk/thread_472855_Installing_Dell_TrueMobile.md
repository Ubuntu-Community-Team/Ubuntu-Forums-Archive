---
title: "Installing Dell TrueMobile"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by limelightos on 2007-06-13
I am having trouble getting my [COLOR="Red"][COLOR="Red"]Dell TrueMobile 1400[/COLOR][/COLOR] wireless card to work in Feisty. I have installed ndiswrapper and bcmwl5.sys and when I do ```
sudo ndiswrapper -l
``` is says bcmwl5 installed hardware present. As I am a complete noob could somebody help me.

I have switched to Ubuntu as my m$xp pro takes quarter of an hour to start up. ouch

---

### Post by rondackcpu on 2007-06-13
Welcome to Ubuntu,

Do you have the whole "recipe" for getting Ndiswrapper running? After 
'ndiswrapper -l' shows that the software and hardware are in place, you need to, at the terminal, type:

"sudo depmod -a"   (without the quotes, of course)

"sudo modprobe ndiswrapper"  Your card should come alive at this time.

"sudo ndiswrapper -m"  puts an alias somewhere, then edit '/etc/modules' file

"sudo gedit /etc/modules"  and add the line 'ndiswrapper'  (without the quotes)

save the edited file, and you should be done.  

Let us know if this didn't fix it.

CRS

---

### Post by limelightos on 2007-06-13
thanks for the help i will try it now

---

### Post by limelightos on 2007-06-13
nope didn't work

followed the instructions and restarted but the network manager could not pick up any signal

---

### Post by limelightos on 2007-06-13
please help me as i would love to switch to ubuntu permanently but no internet is the only thing stopping me

---

### Post by limelightos on 2007-06-13
please could you help me

please?

---

### Post by rondackcpu on 2007-06-13
Sorry it didn't work.  I don't know why.  You might check a thread under "Networking and Wireless" named "bcm4306 ndiswrapper installation guide".  The author claims success

Use the search function to help you find the thread.

CRS

---

