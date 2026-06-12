---
title: "Need help with boot choices"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by halcyoncmdr on 2006-08-09
OK, I have installed Ubuntu 6.06 and I absolutely love it, however I have run into a couple of problems.

1. Is there any way to change the default boot order in GRUB? When I run things in Windows that automatically restart the computer, they can't finish because it boots into linux, which then takes more time because I have to restart and go back to Windows to finish them.

2. Are dual-monitors supported in Ubuntu dapper? My second monitor constantly gets a "Signal out of band" message, and I can't seem to find the setting anywhere to get the second monitor up and running.

3. Don't understand the terminal :( But that just will take time.

I am running a Opteron 165 on an ASUS A8N-E mobo, and a nVidia GeForce 7600GT.

---

### Post by hopstah on 2006-08-09
1.  in your /boot/grub/menu.lst file, scroll to the bottom and find which entry you want to be the default.  each new entry starts with the word 'title' and the numbering begins with 0.  then go back up to the top, and replace the 0 after the word 'default' with the number corresponding to the entry that you want to be the default boot.

2.  i'll let someone else handle that.

3.  yes, time is what it will take.  time and reading and trial and error.

---

### Post by GuitarHero on 2006-08-09
do
sudo gedit /boot/grub/menu.lst
And change the order of the listed boot options by number, they are under the commented stuff.

For dual monitors theres a howto somewhere on the forums, search for it.

And I know the feeling of fearing the terminal.  You get used to it, and eventually will like it.

---

### Post by hopstah on 2006-08-09
> **GuitarHero said:**
> ... and eventually will like it.

:werd:

---

### Post by halcyoncmdr on 2006-08-09
Grr, I can do almost anything in windows, but linux brings me to my knees :(

I found and edited the file, but I can only open it as a read-only, so it is a moot point. Trying to change the file permissions from the properties menu doesn't help. How can I open it in a form that I can edit and then save?

---

### Post by hopstah on 2006-08-09
sorry, i forgot to mention that.  whenever you need to access a file that the system has protected from the normal user, you need to enter what is called 'super user' mode.  you can do this a couple of ways.

at a terminal type ```
sudo gedit (path to file)
``` which for you right now would be /boot/grub/menu.lst

also, you could hit alt+f2 and type in ```
gksudo gedit (path to file)
```

gksudo just gives you a graphical password prompt, and sudo gives you a password prompt in the terminal.

you can also use either of those commands to open up a file browser so you can graphically browse for files and right click to change properties and stuff like that.```
sudo nautilus
```

that should help you out.

edit: and don't get frustrated.  most ubuntu users experienced what you are experiencing right now, and are willing to help.  once you un-learn your windows habits, linux will seem to make much more sense.  trust me on that one.

---

### Post by halcyoncmdr on 2006-08-09
Thanks, I wasn't going to give up, I'm not one to give up easily, but I just don't understand the terminal. The Windows bug has me, I must have a GUI.

I love all of the security in Ubuntu, makes it much more secure than Windws, and it isn't as obtrusive as Vista's, OMG don't even get me started on that.

edit: I got the dual monitors working now too, thanks guys! :)

---

### Post by skale on 2006-08-10
The site in my sig has a good command-line tuorial, under the arrow:
 |
 V

---

