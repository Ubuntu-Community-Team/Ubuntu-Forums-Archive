---
title: "Can't install .bin files"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by cyberbuff on 2006-12-11
Dear friends, 
I am new to linux. I cant install any file with .bin extension. sh /where/the/file/is/XXXX.bin gives me: ```

unexpected syntax "("

```
Someone please tell me how to intsll them

---

### Post by nickburns on 2006-12-11
Is it all .bin files...

What bin file exactly?

what are the permissions on the file?  Do a ls -l to see the permissions

---

### Post by po0f on 2006-12-11
cyberbuff,

Bash is not set as the default shell interpreter on Edgy, Dash is.  You can change it with this command:
```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```

---

### Post by cyberbuff on 2006-12-12
It is RealPlayer10.bin file. I downloaded it from real's website. I'll try with ```
 $ sudo dpkg-reconfigure dash
```
(I am typing from XP)

---

### Post by cyberbuff on 2006-12-12
i tried with the code but it still shows ```
unexpected syntax
```
What to do?

---

### Post by igknighted on 2006-12-12
did you read the installation in instructions from the realplayer site?

```
Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window. 

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player. 

- Enjoy your RealPlayer10 for Linux!
```

---

### Post by cyberbuff on 2006-12-12
oh, i installed it. Thanks for the information. seems like I overlooked it. But I dont know where to start it from. I mean how to fire up RPlayer.

---

