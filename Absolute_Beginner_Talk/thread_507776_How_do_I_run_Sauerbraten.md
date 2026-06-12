---
title: "How do I run Sauerbraten?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-23
I don't understand how to get this game running. I downloaded it and extracted the files to a new folder in my Home Folder as suggested. I then double clicked the sauerbraten_unix file as suggested and selected run in terminal, but I just see a quick flash and then nothing. 
Any help would be appreciated.

---

### Post by SPQQKY on 2007-07-23
Anyone?

---

### Post by Majorix on 2007-07-23
Can you run it from the terminal manually please?

It is most likely creating errors and then quitting, and you can't see those errors.

Like I said you have to run sauerbraten from the terminal to see if that would help. cd to its directory and finally type in ./sauerbraten_unix .

Paste the errors here and see if anyone went through the same process and can help.

Good luck.

---

### Post by SPQQKY on 2007-07-23
> **Majorix said:**
> Can you run it from the terminal manually please?

It is most likely creating errors and then quitting, and you can't see those errors.

Like I said you have to run sauerbraten from the terminal to see if that would help. cd to its directory and finally type in ./sauerbraten_unix .

Paste the errors here and see if anyone went through the same process and can help.

Good luck.

So how do I do that? Look at my bean count......LOL. You're talking to a n00b here.

---

### Post by Majorix on 2007-07-23
Ok I will take it a bit slower :)

First tell me where the Sauerbraten folder is located. Only then can I tell you how to go to that folder in terminal.

---

### Post by SPQQKY on 2007-07-23
It's in my Home Folder/Sauerbraten folder.

Edit: Bah, fah kit.

---

### Post by Majorix on 2007-07-23
Then do this:
- Go to terminal (Apps > Accessories > Terminal).
- Type in 
```
cd Sauerbraten
```
- The above is how you change directories. Change the directory until you are in the folder that contains "sauerbraten_unix" file.
- Then when you are there, type in
```
./sauerbraten_unix
```

Hope it helps. If not post back with any problems you got.

---

### Post by SPQQKY on 2007-07-23
> **Majorix said:**
> Then do this:
- Go to terminal (Apps > Accessories > Terminal).
- Type in 
```
cd Sauerbraten
```
- The above is how you change directories. Change the directory until you are in the folder that contains "sauerbraten_unix" file.
- Then when you are there, type in
```
./sauerbraten_unix
```

Hope it helps. If not post back with any problems you got.

```
cd Sauerbraten
```
No such filer or directory......

....and thanks goes out to Cube for their "beginners guide". Here are their instructions.....

For *nix users - usage as usual for you.  LOFL. That is so helpful.

---

### Post by Orochi on 2007-07-23
In terminal type 'ls' to get a list of files and directories in your home folder. Keep in mind that everything is case sensitive, so 'Sauerbraten' is different that 'sauerbraten'.

---

### Post by SPQQKY on 2007-07-23
it's there, lower case

---

### Post by Orochi on 2007-07-23
So if it's lowercase, type 'cd sauerbraten' instead of 'cd Sauerbraten' to change to the correct directory.

---

### Post by SPQQKY on 2007-07-23
I've already done that. It still says no such file or directory

Edit: LOL. Got it running. This happened to me before with something else (can't remember) where I seemed to have to type the same thing in terminal a few times before it would run. At first it said I was missing a package, so I installed it using synaptic and it's going. Not that exciting of a game (reminds me of Doom), but it was just another obstacle I refused to believe I couldn't hurdle. Thanks for all your help, guys. Cheers.

---

### Post by Technophobia on 2007-07-23
Stop wasting time go here download the two files and have fun.

[http://www.getdeb.net/search.php?keywords=Sauerbraten](http://www.getdeb.net/search.php?keywords=Sauerbraten)

Install order- 

 sauerbraten-data.deb

and then

 sauerbraten.deb


Edit- knowing how to do a Linux install is nice, but when you have a .deb you use it. If you didn't know a .deb is the Debian/Ubuntu equivalent to a .msi or microsoft installer. The best thing IMO about .deb is that you can see everything that is being installed and then some.

---

