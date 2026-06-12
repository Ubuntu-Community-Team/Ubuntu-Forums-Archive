---
title: "Linux Utter Newbie"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by Bghmsh on 2005-11-05
Ok so I have managed to load and corrupt and remove and detrsoy and re-load I can use a text editor as good as the next man , but need a little help . I have an external drive that I am planning to dedecate to media storage (it has media already on it) Its still in WIn 32 format I would like to unload the media (Done) , would like to format the drive(Dont have permission) and would like to reload the mediaI can do the 1st bit the last bit simple cutnpaste command , but the bit in the middle Well I ask you ? I am running networked up and running / 5 boxes (all AMD) and tghis is my first foray into Linux world - Have MS home / pro / pro -64 This is very stable and will i tghink be easy to use in the end

---

### Post by Kyral on 2005-11-05
Permission....

Well, you can fire up a LiveCD to use GParted (GUI) or invoke fdisk as root with

```
sudo fdisk <device>
```

---

### Post by gord on 2005-11-05
some indication of the 'cut and paste' that your talking about might help ;)
i would suggest that wherever the part where you format your external media is, you prefix it with 'sudo'

ie: if you wanted to remove a file called 'hello.txt' you would normally type
rm hello.txt
well with sudo you would type
sudo rm hello.txt

it'll ask you for a password, just use your user password that you use to log in.

---

### Post by Bghmsh on 2005-11-05
[QUOTE=gord]some indication of the 'cut and paste' that your talking about might help ;)
i would suggest that wherever the part where you format your external media is, you prefix it with 'sudo'

ie: if you wanted to remove a file called 'hello.txt' you would normally type
rm hello.txt
well with sudo you would type
sudo hello.txt

it'll ask you for a password, just use your user password that you use to log in.[/QUOTE]

I am not as far along as you thin kmy original box has two external drives under windows  a 1394 and a usb 2.0 I have stored media on both. I have access to both drives but I I copy a file to my home directory form either drive It becomes protected and undleteable , So my drive will fill up very quickly with 1Gb and up media files In Windows I moved all of the 1394 files to the USB drive Formatted tye drive , so that I can use it under Ubuntu I could reformat under Partion Magic in Windows to make the drive useable , but I neeed to work through Linux as I am damn sick of buying Windows disks. So first I need to be able to read write and delete to the offending drive  so that I can then delete files that are copied form it

---

### Post by gord on 2005-11-05
sounds like your files are owned by root, just type
```
sudo chown <yourusername>. <file>
``` 
at the terminal. if you still can't move them, right click on the files in your file manager, and goto propertys. select the read/write boxes for your groupname and okay it. 

theres a terminal way to do that too, but i can't remeber the flags for that right now.. its pritty late in the day.

---

### Post by Mustard on 2005-11-05
gord, you need to take care with your example commands, both your posts have either a typo or missing command.

---

### Post by gord on 2005-11-05
oop forgot the rm :) allthough for the second post im not quite sure what you meen. if you are talking about the dot, its perfectly fine. at least its what iv used for a long time.

---

