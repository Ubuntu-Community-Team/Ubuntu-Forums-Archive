---
title: "Terminal Editing Text File"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Amarasu on 2007-11-22
I want to create a shell script that executes

 "sudo nano /etc/modprobe.d/alsa-base"

Then enters in my password and presses enter to add a line to the end of the file saying

 "option snd-hda-intel model=auto"

How would I do this? 

It would be helpful  because I want to create a library of scripts that I use to get everything in Ubuntu working after I do a fresh install.

---

### Post by Rinzwind on 2007-11-22
sed

> Appending and Inserting Text

Text can be appended to the end of a file by using sed with the "a" option. This is done in the following manner:

$ sed '$a\
> This is where we stop\
> the test' sample_one
one     1
two     1
three   1
one     1
two     1
two     1
three   1
This is where we stop
the test
$

Within the command, the dollar sign ($) signifies that the text is to be appended to the end of the file. The backslashes (\) are necessary to signify that a carriage return is coming. If they are left out, an error will result proclaiming that the command is garbled; anywhere that a carriage return is to be entered, you must use the backslash.

To append the lines into the fourth and fifth positions instead of at the end, the command becomes:

$ sed '3a\
> This is where we stop\
> the test' sample_one
one     1
two     1
three   1
This is where we stop
the test
one     1
two     1
two     1
three   1
$

This appends the text after the third line. As with almost any editor, you can choose to insert rather than append if you so desire. The difference between the two is that append follows the line specified, and insert starts with the line specified. When using insert instead of append, just replace the "a" with an "i," as shown below:

$ sed '3i\
> This is where we stop\
> the test' sample_one
one     1
two     1
This is where we stop
the test
three   1
one     1
two     1
two     1
three   1
$

The new text appears in the middle of the output, and processing resumes normally after the specified operation is carried out.

---

### Post by jordanmthomas on 2007-11-22
```
echo "option snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base
```
You don't want to run nano because it's interactive and won't add to a file without the user inputting it himself.

As for putting in your password by itself, you will only be able to do this if
a)  you just run the script with sudo and put your password in at the beginning (then you can take out the sudo in the script itself as well)
b)  run it as root to start with

Hope this helps.

---

### Post by Rinzwind on 2007-11-22
Example: 
>  more test.txt 
===== BEGIN MILESTONES =====
0x8177510 2007/11/22 08:28:18.1773 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2135 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2136 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2137 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2138 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2139 (USER): debug log dumped due to signal 11
===== END MILESTONES ======


> $ sed '$a\
append this line to this file' test.txt > test2.txt


>  more test2.txt 
===== BEGIN MILESTONES =====
0x8177510 2007/11/22 08:28:18.1773 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2135 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2136 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2137 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2138 (USER): debug log dumped due to signal 11
0x8177510 2007/11/22 08:28:18.2139 (USER): debug log dumped due to signal 11
===== END MILESTONES ======

append this line to this file



---

### Post by Rinzwind on 2007-11-22
> **jordanmthomas said:**
> ```
echo "option snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base
```
You don't want to run nano because it's interactive and won't add to a file without the user inputting it himself.

As for putting in your password by itself, you will only be able to do this if
a)  you just run the script with sudo and put your password in at the beginning (then you can take out the sudo in the script itself as well)
b)  run it as root to start with

Hope this helps.
This works too :) :)

---

