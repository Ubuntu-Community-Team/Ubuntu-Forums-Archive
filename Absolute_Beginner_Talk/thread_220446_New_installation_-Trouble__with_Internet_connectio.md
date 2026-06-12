---
title: "New installation -Trouble  with Internet connection"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by marcosr on 2006-07-21
[SIZE="3"]Hi, I'm fresh new with Linux. I tried Linux before but never was able to install the system. Now is different, Ubuntu installed in 1/2 hour and everything sounded fine. The only exception is my network connection that runs slow. I'm using the Ubuntu's PC in a Windows Home Network enviroment. I read a suggestion about disconecting one of the Ubuntu features (IP6 or IV6 I think) but it required to save a bad.list file inside the file system . I tried that but I got a message denying the access to save the file there. 
I read another thread telling that you need to reboot the computer in recovery mode and add myself like administrator.
I need some help please. As I said I have no  experience with  Linux so pls help me step by step.
Regards
Marcos:cool:[/SIZE]

---

### Post by Indroth on 2006-07-26
I don't know about the slowness problem, but you can get root privilages by typing 'sudo' before anything that needs it.

for example:
  
```
sudo gedit afile
```

will let you save 'afile' even if it needs root privilages.

another example:

```
sudo cp myfile /etc
```
will let you copy the file 'myfile' to the /etc directory.

---

### Post by adam.tropics on 2006-07-26
To disable [IPV6,]("http://www.ubuntuforums.org/showthread.php?t=87798&highlight=speed") try this guide.

---

### Post by gigaferz on 2006-07-26
well.. what worked for me was to change the media speed on the command line.. by default its 100mbps full duplex..
I think is  worth the try.. i used  mii-tool , and ethtool gives you a status report on your connection...

try setting it up at 10mbps full duplex, then half...

after changing the settings..restart ubuntu (ctrl+ALT+BACK)
AND BRING THE  BROWSER AND TRY FOR A  while.

Im just trying to help..

---

### Post by gigaferz on 2006-07-26
I also tried  disabling ipv6, and many other stuff..but  it was useless..

---

