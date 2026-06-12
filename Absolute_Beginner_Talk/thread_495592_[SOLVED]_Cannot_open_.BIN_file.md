---
title: "[SOLVED] Cannot open .BIN file"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-07-08
Hello,

Is there a way to open and install .bin files? I downloaded Planeshift (which comes as a .bin) and Ubuntu tells me that the archive is unsupported.

Thanks for your help.

---

### Post by B-777 on 2007-07-08
> **the8thstar said:**
> Hello,

Is there a way to open and install .bin files? I downloaded Planeshift (which comes as a .bin) and Ubuntu tells me that the archive is unsupported.

Thanks for your help.

Thats because a .bin file is not an archive...its a binary file (If I am not mistaken on my file formats).

Being new to Ubuntu and the world of Linux myself, I am not sure of the command you'd use to open it.

Hopefully, someone with more experience than myself will come along and give more information.

---

### Post by louistan3 on 2007-07-08
i believe u run it like a script..

which would be like this

```
sh <nameoffile>.bin
```

but i am not sure.. 

hope this helps :)

---

### Post by the8thstar on 2007-12-15
Bump

---

### Post by llamakc on 2007-12-15
> **louistan3 said:**
> i believe u run it like a script..

which would be like this

```
sh <nameoffile>.bin
```but i am not sure.. 

hope this helps :)

This is correct.

---

### Post by Zackie on 2008-01-21
Yeah i tried the 
sh PlaneShift_CBV0.3.020-x86.bin

just said it could not open it:

sh: Can't open PlaneShift_CBV0.3.020-x86.bin



its on my desktop should it be placed some where else?

---

### Post by Majorix on 2008-01-21
Try doing this:
[php]chmod a+x /path/to/bin/file
#Now if you are in the folder that contains the file in the terminal, do this:
./binfile
#Or else, you have two options
cd /folder/of/the/bin/file; ./binfile
#Or
/path/to/bin/file[/php]
It doesn't matter if you use sh at the start or not, the OS should automatically launch the file via dash, a similar shell to sh.

Hope it helps.

---

### Post by Zackie on 2008-01-21
I just put it from the desktop into my Home/name* dir and the double clicked and it is auto installing.. hum.. odd but what ever thanks!!!

---

### Post by Majorix on 2008-01-21
Glad you got it working :) I would learn the way I explained anyways, as it might come in handy in future.

---

### Post by NicoretteJunkie on 2008-02-08
I've tried every single thing on this page, and still have had no luck installing the exact same file the first poster is trying to install. I tried the chmod, I tried sh <nameoffile>.bin, and still can not seem to install the file.

I've only been using Linux for about a month now, and I'm still completely clueless! Can someone help???

---

### Post by eluzi on 2008-02-08
U should try what Marjorix said:

chmod a+x /path/to/bin/file
#Now if you are in the folder that contains the file in the terminal, do this:
./binfile
#Or else, you have two options
cd /folder/of/the/bin/file; ./binfile
#Or
/path/to/bin/file

This is because a bin is a binary file that, but in order to run it u gotta give executable permission to it. Let me give u a example:

Let's say the file is in your deskop:

In a terminal u should do:

cd /home/user/Desktop
chmod a+x file.bin
./file.bin

That's about it... U can check if the commands where allright doing:

ls -l

The outcome should show that in the permission on the left u have 3 x's and probably the color of the filename would have changed... 

Any further  questions post it :)

---

### Post by craetech on 2008-03-01
Yeap, that worked for me. What I did was:

1. chmod 755 PlaneShift_CBV0.3.020x86.bin
2. ls -l PlaneShift_CBV0.3.020x86.bin (should display -rwxr-xr-x)
3. sudo ./PlaneShift_CBV0.3.020x86.bin (some settings require root access)

GUI installer appears, and done.

P/s: I'm using Kubuntu Fiesty.

---

### Post by /home on 2008-03-01
chmod 755 nameoffile
then ./nameoffile
All you have to do
[CENTER]



[/CENTER]

---

### Post by forrestcupp on 2008-03-01
Or if you like the graphical way, find the file in Nautilus, right click the file and click the Permissions tab.  Then check the box that says 'Allow executing file as a program.'

Then you can just double click the file and it will run.

---

### Post by the8thstar on 2008-04-13
Thank you guys for your good answers. I favor the GUI option, being the simplest of all, but they are all working. :)

---

### Post by Tobi-fp on 2008-06-10
Hey there, if it is on your desktop just do as folowing :
Open a terminal
write "sudo sh" and then drag the file from your desktop into the terminal. 
I just installed google earth on my comp, and i had to write :
$ sudo sh '/home/tobias/Desktop/GoogleEarthLinux.bin'

---

