---
title: "What did I do to my system....?????"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by bubbadawg on 2006-02-20
Hello ---

While attempting to resolve my WiFi card issues, apparently I unknowningly deleted or changed something that I should not have :confused: . When logging in, I now get the message:

> 
Could not look up internet address for DellLinux. This will prevent Gnome from operating correectly. 
It may be possible to crrect the porblem by adding DellLinux to the file /etc/hosts


I tried to edit the hosts file and get this error:
> 
uanble to lokup DellLinux via gethostbyname()


This probably goes hand in hand, but when I click on the configure button in the connection properties, nothing happens.

If anyone can be so kind as to help me to resolve this issue, I promise to immediately shutdown the system for the night..... :( 

Thanks for any and all replies.

---

### Post by jrib on 2006-02-20
[LIST]
[*]boot in recovery mode by selecting it in the grub menu (press ESC if you don't see the grub menu when you boot
[*]look at what is in /etc/hostname, let's assume it says "DellLinux"
```
# cat /etc/hostname
```
[*]make the first line of /etc/hosts look like this: ```
127.0.0.1 localhost.localdomain localhost DellLinux
```
To edit the file you can use this command (press ctrl+o to save and ctrl+x to exit):
```
# nano /etc/hosts
```
[/LIST]

---

### Post by bubbadawg on 2006-02-20
[QUOTE=_jason][LIST]
[*]boot in recovery mode by selecting it in the grub menu (press ESC if you don't see the grub menu when you boot.......
[/LIST][/QUOTE]

Thanks very much for the prompt and kind assistance. That worked! I wondered what the recovery mode was....now I guess I know.

Any chance that you can help me resolve my [other issue]("http://www.ubuntuforums.org/showthread.php?t=133869")?


Thanks again.

---

### Post by funkyboss on 2007-05-07
Thanks for this thread! I messed up my network settings the same way and got it back up thanks to this... :)

---

