---
title: "I feel like a fool asking that but..."
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by jofre on 2006-02-14
I feel like a fool asking that, but it really annoys me. I know that the easiest way to install thunderbird is to go to synaptic, but i just wanted to do it Windows way, go to their website donwload and install. Well, I manage the donwload part, but how do you install it:confused: ? 

I am trying to learn to do things from the shell as much as I can, because I am running in a slow machine. My next step will be to learn how to compile myself the software but if I am not able even to install software... I am still far away.

Thanks a million, Jofre.

---

### Post by Klaidas on 2006-02-14
If it's a .deb file, type:
```
dpkg -i filename.deb
```

Here's a cool guide that will help you lear installing/compiling: [http://www.linux.org/lessons/interm/c191.html](http://www.linux.org/lessons/interm/c191.html)

---

### Post by george_apan on 2006-02-14
Assuming you downloaded the correct file (it should be something like thunderbird-1.5.tar.gz) you just open a console window and type:
```
tar -xvzf thunderbird-1.5.tar.gz
```
That's it. If you were on your home directory (~) there should be a thunderbird directory under it now (~/thunderbird or something like that). You can then cd into it and run the execution script (something like thunderbird.sh or maybe run-thunderbird.sh)

But synaptic isn't just easier. It is the recommended way of adding application to your ubuntu, since all the updates will be done automatically too.

---

### Post by cstudent on 2006-02-14
Thunderbird is a tarball if downloaded from Mozilla. It doesn't need to be compiled to run. It only needs to be unpacked to some directory and then run the thunderbird executable file. You can install the deb from the repositories, but it won't be version 1.5.

To install it from the repositories:

```


sudo apt-get install mozilla-thunderbird


```

To install the downloaded tarball from Mozilla:

```


sudo tar -xzvf thunderbird-1.5.tar.gz -C /opt


```

/opt is the directory I would use, but you can put it in any you'd like.

You then would run thunderbird using the command line with something like:

```


/opt/mozilla-thunderbird/thunderbird


```

The actually path and directory names might be different, you will use the path needed to where the thunderbird executable file is.

---

### Post by Lord Illidan on 2006-02-14
[quote=jofre]I feel like a fool asking that, but it really annoys me. I know that the easiest way to install thunderbird is to go to synaptic, but i just wanted to do it Windows way, go to their website donwload and install. Well, I manage the donwload part, but how do you install it:confused: ? 

I am trying to learn to do things from the shell as much as I can, because I am running in a slow machine. My next step will be to learn how to compile myself the software but if I am not able even to install software... I am still far away.

Thanks a million, Jofre.[/quote]

Thunderbird isn't installed per se. All you have to do is extract it, then run the execution script from where it is.

Good for you learning how to use the shell.
Don't forget the man pages.. for example type ```
man tar
``` in a terminal to view a very useful help page on tar.

---

### Post by jofre on 2006-02-14
Guau!!! Just impressibe! :p (For the so fast answers!)

Thanks a million, 
but... 

when I tried to run the .sh script I get that:

jofre@edoras:~/Desktop/thunderbird$ sudo ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

I guess that's Linux world, nothing work at the first go:cry:

---

### Post by kaamos on 2006-02-14
[quote=jofre]jofre@edoras:~/Desktop/thunderbird$ sudo ./run-mozilla.sh[/quote]
should probably be
```
jofre@edoras:~/Desktop/thunderbird$ ./thunderbird
```

---

### Post by george_apan on 2006-02-14
[QUOTE=jofre]Guau!!! Just impressibe! :p (For the so fast answers!)

Thanks a million, 
but... 

when I tried to run the .sh script I get that:

jofre@edoras:~/Desktop/thunderbird$ sudo ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

I guess that's Linux world, nothing work at the first go:cry:[/QUOTE]
Try running the executable directly without the script. Probably:
~/Desktop/thunderbird/mozilla-thunderbird
for you. And you don't need sudo for that.

---

### Post by jofre on 2006-02-14
I am confused.

If I have understand well things, the tar -xzvf thunderbird-1.5.tar.gz is just an extraction command, so no installation has been made at this point. 

When I ran the suggested command by Kaamos, thunderbird just pop out like it was already installed! 

What have I miss here? There is something that i have understood very wrongly here...

But, thanks for everything.
Jofre.

---

### Post by george_apan on 2006-02-14
The extraction is the installation. You can put the directory that was created by the extraction anywhere and run thunderbird from there.

---

### Post by jofre on 2006-02-14
Thanks lads, I have learn something new today:p 

Well, highly probably I will be around asking more annoying questions ;) 

Thanks again, Jofre.

---

### Post by anirban.sam on 2006-02-14
the files will be extracted within a new directory named thunderbird on your specified path. just type the path and presst+tab or thunderbird. You can simply run the executable - just like windows

---

### Post by Lord Illidan on 2006-02-14
[quote=jofre]Guau!!! Just impressibe! :p (For the so fast answers!)

Thanks a million, 
but... 

when I tried to run the .sh script I get that:

jofre@edoras:~/Desktop/thunderbird$ sudo ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

I guess that's Linux world, nothing work at the first go:cry:[/quote]

Since everything is working, you have disproved your last statement then!

---

### Post by bessie on 2006-02-24
This link helped me! 

[http://www.ubuntux.org/firefox-1-5-locally-on-my-ubuntu-5-10](http://www.ubuntux.org/firefox-1-5-locally-on-my-ubuntu-5-10)

It seems the **ln** command might be the missing command you were looking for.

I would suggests to sharp up on your skill using google, everything you want to know is out there, you just have to find it. :) 

Good luck

---

