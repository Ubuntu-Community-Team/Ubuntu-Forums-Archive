---
title: "Problem shutting down"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by DrtBikDave on 2007-04-11
When I tell Ubuntu to shut the system down, it doesn't shut the tower off. I assume it is supposed to since that is one of the options. How can I fix this issue?

---

### Post by xopher on 2007-04-11
> **DrtBikDave said:**
> When I tell Ubuntu to shut the system down, it doesn't shut the tower off. I assume it is supposed to since that is one of the options. How can I fix this issue?

Well, yes, it should :)

What happens if you type in: ```
sudo shutdown -h now
``` in the terminal?

---

### Post by IndyBob on 2007-04-11
I was having the same problem and used the following link from the forum and it fixed my problem.  It may or may not work for you.

[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

---

### Post by DrtBikDave on 2007-04-11
Now bear with me please if this sounds a little ignorant but where do I type the commands and is there a cheat sheet for common commands and how to type them. I wasn't very good at typing commands in a windows enviroment either.

---

### Post by Ganda_Melga on 2007-04-11
> **DrtBikDave said:**
> Now bear with me please if this sounds a little ignorant but where do I type the commands and is there a cheat sheet for common commands and how to type them. I wasn't very good at typing commands in a windows enviroment either.


Well, I'm a complete newbie to this Ubuntu things, but i think you should type that in the terminal

In my case (Xubuntu) Applications - System - Terminal

---

### Post by DrtBikDave on 2007-04-11
OK-Thanks, now were getting somewhere.

---

### Post by DrtBikDave on 2007-04-11
Does it matter if it is lower case or upper case? also I assume that the spaces are important.

---

### Post by DoubleQuadword on 2007-04-11
Indeed it matters; and spaces are also important.

---

### Post by bobplano on 2007-04-11
you can just copy and paste the commands (ctrl+c and ctrl+v doesn't work though so you have to right click)

---

### Post by DrtBikDave on 2007-04-11
Sometimes I feel like a bone head, I am in this forum through windows. I didn't think of coming here when I was in UBUNTU even though i do serf the net. I am sorry for being a dip ****, and thanks for your patients.

---

### Post by DrtBikDave on 2007-04-12
Ok, Here is the outcome. When I do what xopher said to do it acted identicle to hitting the red power button and telling it to shut down (it doesn't power off the computer) and The link that i took, I was able to add a line to "sudo gedit /etc/modules" that read "apm power_off=1" and saved it which didn't seem to work either. 
 Do I need to remove that line now? and thanks for the suggestions.

---

### Post by IndyBob on 2007-04-12
Well, being a noob too, I am at a loss.  The link I gave you worked on my computer.  Try searching the forum for any other suggestions/fixes that may be posted.  Since the fix didn't work, I would assume that taking out the line you added might not hurt if someone has a better resolution to your issue.

---

### Post by DrtBikDave on 2007-04-13
I am grateful for any and all suggestions. So thank you.

---

### Post by Gif on 2007-04-13
Hi,

I have had a similar problem and came across the following which helped me!

> sudo nano /boot/grub/menu.lst

find line "[COLOR="DeepSkyBlue"]kernal /boot/vmlinuz-2.6.8.1-3-386 root=dev/hda_ro quiet splash[/COLOR]"

and add "[COLOR="DeepSkyBlue"]acpi=force[/COLOR]" to the end of line and save.

Hope this helps

---

