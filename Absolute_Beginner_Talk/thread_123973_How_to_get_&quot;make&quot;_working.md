---
title: "How to get &quot;make&quot; working?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by sniffass on 2006-01-31
I just got my very first installation of a linux working (kind of) on my laptop, and I'm so happy to have followed a guide in using the console to get the internet working. My next mission is to get the display working 1280x800 which currently shows at 1024x768. I need to use the program 915resolution and I have it here. But first I must execute the command "make" but when I do this the terminal tells me "no command or filename". I'm assuming I need to install this, but how do I do it?

Regards,
Gabe

---

### Post by Adrian on 2006-01-31
[QUOTE=sniffass]I just got my very first installation of a linux working (kind of) on my laptop, and I'm so happy to have followed a guide in using the console to get the internet working. My next mission is to get the display working 1280x800 which currently shows at 1024x768. I need to use the program 915resolution and I have it here. But first I must execute the command "make" but when I do this the terminal tells me "no command or filename". I'm assuming I need to install this, but how do I do it?

Regards,
Gabe[/QUOTE]

Try installing the "build-essential" package.

---

### Post by sniffass on 2006-01-31
Thank you so much. I've been trawling through the internet for about 2 hours trying to find out what I need.
 I've tried using the command and this is what it gives me :(

sniff@ubuntu:/home$ make
make: *** No targets specified and no makefile found.  Stop.
sniff@ubuntu:/home$ make install
make: *** No rule to make target `install'.  Stop.

what must i do? Despite what it says, there is indeed a makefile in the directory, or atleast there is a file called makefile.
Regards,
Gabe

---

### Post by mustang on 2006-01-31
[QUOTE=sniffass]Thank you so much. I've been trawling through the internet for about 2 hours trying to find out what I need.
 I've tried using the command and this is what it gives me :(

sniff@ubuntu:/home$ make
make: *** No targets specified and no makefile found.  Stop.
sniff@ubuntu:/home$ make install
make: *** No rule to make target `install'.  Stop.

what must i do? Despite what it says, there is indeed a makefile in the directory, or atleast there is a file called makefile.
Regards,
Gabe[/QUOTE]

Did you ```
./configure
```

before you tried make and make install. If you did, did it display any errors during the ./configure?

---

### Post by sniffass on 2006-01-31
Hi, thank you, I hadn't tried ./configure (wasn't in the 915 readme). I just tried it now and it says:

sniff@ubuntu:/home$ ./configure
bash: ./configure: No such file or directory

or

sniff@ubuntu:/home$ sudo ./configure
sudo: ./configure: command not found

what am I missing?

Regards,
Gabe

---

### Post by kaamos on 2006-01-31
Are you sure you are in the right directory? When you try make and it fails, what is the output of "ls" ?

---

### Post by sniffass on 2006-01-31
what is "ls"? I said everything that I know. I am certain the directory is correct. I exctracted the files of 915resolution to my home directory, and showed the terminal output in the above post.

Gabe

---

### Post by kaamos on 2006-01-31
the command ls in a terminal shows the files and folders in the current directory.

---

### Post by sniffass on 2006-01-31
I don't understand, this is what I get:

sniff@ubuntu:/home$ ls
sniff

the prompt shows that I'm in /home. And I see home with nautilus and it shows me all the different files. Please, what;s happening?

---

### Post by sniffass on 2006-01-31
Ah I am stupid, i got this part figured now. I ran make, and install etc. Now the only thing I have trouble with is finding boot.local since i need to add some information to it. 
I can't find it in /etc/rc.d or in /etc/init.d
where is this file to be found in ubuntu? Also is there a file searching function in Gnome - so i can just search for any file on my computer?

Thanks for all the help so far,

Gabe

---

