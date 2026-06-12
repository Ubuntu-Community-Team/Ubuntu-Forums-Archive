---
title: "Big help please :-0"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Denzle on 2008-03-26
My system keeps crashing :(, i new to ubuntu and i really like it its great, i am a student and vista was far to expensive for me so i seen ubuntu and built my self a tower.

It installed fine and i thought great, i took it round my friends and i updated it and downloaded loads of programmes.

Then i wanted to transfreer all my data from my previous pc and then the problems start,
It wouldn't let me access any of the files on the pen drive, i can see them but cant use them,
it usally happens to my desktop as well,
The brower windows for say my documents, it will crash if i try and access some of my files, on rare occasions it will let me access them.

I wanted to ask wether one of the know all guys will remotly control my p.c and sort the problem out for me.

These are my p.c specs

2667mhz processor
768mb ddr ram
20gb hardrive
dvd and cdrw drives (Master and slave)
asus motherboard, cannot find the make at the moment.

If anyone has answers for me, bering in mind im new and used to xp, i would need the bigginers talk, please can you email me as it would be easyer at <snip>.

(Mod Note:  If you want to email the OP, then click on his name and select the email option.)

Thanks all Steven

---

### Post by ukripper on 2008-03-26
can you plug in your pendrive to your machine and then type  folowing in terminal:

```
lsusb -v 
```

```
blkid
```

```
fdisk -l
```

```
dmesg | grep -i usb
```

and then paste the output here and that will give us substantial amount of details to see where the problem is.

---

### Post by Denzle on 2008-03-28
O.k where can i find the terminal, With my knowledge i think its like the command promt in xp??
Am i right??
Is the terminal in the sytstem tools menu, And if you can could i get a screen shot of the commands in line which will make it easyer for me, thanks,

Denzle

---

### Post by stefangr1 on 2008-03-28
Just press Alt+F2 and then type in xterm

What you could also do is test your memory with memtest86, using the Ubuntu installation cd. Random crashes are often caused by hardware problems, and linux is somewhat more demanding towards hardware then windows.

---

### Post by quill3033 on 2008-03-28
Ok I have Ubuntu 6.06LTS and there you can find the terminal at

in the menu bar                Applications   then Accessories and then Terminal 

Don't really know many commands. I get books out of the library and look when I need to or search here for what I want to do and usually copy the commands that have worked for other people. 

Hope this helps at least with opening the terminal.

---

### Post by Sef on 2008-03-28
You could also do this:

Applications > Accessories > Terminal

---

### Post by stalkingwolf on 2008-03-28
> i took it round my friends and i updated it and downloaded loads of programmes.

The first thing to do is to check and see if you are close to having your HDD full.  20gb is not much after all.

Second you may have to change the permissions on your thumb drive files.  and possibly the drive itself.
If you copied them from XP , right click a file, go down to properties, click properties, if read only is checked , un check it.  If you have copied them to ubuntu you will have to change the permissions to
read and write .

---

### Post by Denzle on 2008-03-29
o.k guys i have been fishing around on ubuntu,

I may have found the problem but i cant correct it, it will not let me

O.k this is what i done,

Places (gutsy gibbon mind.)>computer>then i click on file system(right click) then properties>permissions,

They are all read only and the message i get when i try to change that is> sorry the permissions cannot be changed.
Sorry, couldn't change the permission of filesystem.

Pm my inbox on the forum so i know i have a post back, thanks denzle.

---

### Post by Denzle on 2008-03-29
> **ukripper said:**
> can you plug in your pendrive to your machine and then type  folowing in terminal:

```
lsusb -v 
```

```
blkid
```

```
fdisk -l
```

```
dmesg | grep -i usb
```

and then paste the output here and that will give us substantial amount of details to see where the problem is.

According to my terminal, these codes cannot be found, or i might be that i am typing them wrong, i dont know.

---

### Post by ukripper on 2008-03-30
> **Denzle said:**
> o.k guys i have been fishing around on ubuntu,

I may have found the problem but i cant correct it, it will not let me

O.k this is what i done,

Places (gutsy gibbon mind.)>computer>then i click on file system(right click) then properties>permissions,

They are all read only and the message i get when i try to change that is> sorry the permissions cannot be changed.
Sorry, couldn't change the permission of filesystem.

Pm my inbox on the forum so i know i have a post back, thanks denzle.

go to terminal and and type following to change persmission for usb drive :
```
sudo chown -hR  username /media/usbdisk
```
replace username to your current user and usbdisk to whatever is the name you have mounted usb drive with.

---

### Post by thebigbluecan on 2008-03-30
> **Denzle said:**
> According to my terminal, these codes cannot be found, or i might be that i am typing them wrong, i dont know.

> **ukripper said:**
> 

```
lsusb -v 
```

```
blkid
```

```
fdisk -l
```

```
dmesg | grep -i usb
```


Plug in your USB drive....

Highlight the first box's text... here on the web page right click then select "copy" .... 

Go to your Terminal right click in the window press "paste"   then press the enter button on your keyboard...

Highlight what it says... right click then "copy" and then "paste" on this forum...

Go to the next box on this web page and do the procedure again. and then the next box.. and the next box... until your through with the 4 boxes on this page.

---

### Post by prismpirate on 2008-03-30
Or you could open USB, right click on the file you want to copy, click on the permissions tab, and switch it to your username.

---

### Post by Denzle on 2008-03-30
No thats for my harddrive, my hardrive is saying this :confused:

---

### Post by thebigbluecan on 2008-03-30
This is what it looks like? Your "filesystem permissions"?  
[IMG]http://i210.photobucket.com/albums/bb5/thebigbluecan/Screenshot-1.png[/IMG]

If so the settings are correct... (i'm pretty sure anyway)

---

### Post by Denzle on 2008-03-31
Yes that is what it is saying for my file system, ummm, recently evertime i use the browser to view my files on my pendrive is usally crashes and i have to force quit, sorry now i am getting really confused with it :-%

---

