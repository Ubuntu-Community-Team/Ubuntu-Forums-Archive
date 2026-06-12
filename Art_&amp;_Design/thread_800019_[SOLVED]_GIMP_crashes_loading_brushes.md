---
title: "[SOLVED] GIMP crashes loading brushes"
date: 2008-05-19
forum: Art &amp; Design
---

### Post by Tsukino Kyuuketsuki on 2008-05-19
I've been having a problem with GIMP, I had all my .abr brushes in the /usr/share/gimp/brushes (that's the right folder... right?) but whenever I tried to open GIMP it crashed. So I assumed it was the .abr files fault, even though I read that this version supports .abr brushes.

Anyways, I converted all my brushes into .gbr, tried to open GIMP and gets stuck trying to load them. Actually, the whole Ubuntu gets stuck and I have to restart the computer, and that never happened to me using Ubuntu! I don't have a clue what the problem is.

If someone knows what's going on with my GIMP, any help is appreciated. Thank you!

---

### Post by Half-Left on 2008-05-19
No, your brushes should go in /home/username/.gimp-2.4/brushes


Run in the terminal ```
gimp --verbose
``` if this still happens

If you can't do anything just do Ctrl, Alt, Backspace to exit your window manager.

---

### Post by Tsukino Kyuuketsuki on 2008-05-19
This is what I get...

```

INIT: gimp_load_config
Parsing '/home/xxxxx/.gimp-2.4/unitrc'
Parsing '/etc/gimp/2.0/gimprc'
Parsing '/home/xxxxx/.gimp-2.4/gimprc'
gimp_composite: use=yes, verbose=no
Processor instruction sets: +mmx +sse -sse2 -3dnow -altivec -vis
Adding theme 'Default' (/usr/share/gimp/2.0/themes/Default)
Adding theme 'Small' (/usr/share/gimp/2.0/themes/Small)
Writing '/home/xxxxxy/.gimp-2.4/themerc'
Trying splash '/home/xxxxx/.gimp-2.4/gimp-splash.png' ... failed
Trying splash '/usr/share/gimp/2.0/images/gimp-splash.png' ... OK
INIT: gimp_initialize
INIT: gimp_real_initialize
INIT: gui_initialize_after_callback
INIT: gimp_restore
Parsing '/home/xxxxx/.gimp-2.4/parasiterc'
Loading 'brush factory' data
```

And gets stuck trying to load them... T_T

---

### Post by unutbu on 2008-05-19
Does the problem persist if you move the .abr / .gbr files to a temporary directory not read by gimp? 

If gimp works when you move the brush files, then you can add the brush files back one by one to discover exactly which file is the problem.

If gimp does not work even after you move the brush files, then I would check/move the patterns files  because 
"Loading 'pattern factory' data" is the next line after "Loading 'brush factory' data".

---

### Post by Half-Left on 2008-05-19
Delete your ~/.gimp-2.4 directory and put your brushes in ~/gimp-2.4/brushes

You will lose your config, dont put them in /usr/share/gimp/brushes because they are readonly.

---

### Post by Tsukino Kyuuketsuki on 2008-05-19
> **unutbu said:**
> Does the problem persist if you move the .abr / .gbr files to a temporary directory not read by gimp? 

If gimp works when you move the brush files, then you can add the brush files back one by one to discover exactly which file is the problem.

I did move them before and GIMP works just fine, I'm pretty sure the problem are the brushes. I would move them one by one like you suggested but just thinking about moving 3677 files one by one gives me a headache. T_T



> Delete your ~/.gimp-2.4 directory and put your brushes in ~/gimp-2.4/brushes

You will lose your config, dont put them in /usr/share/gimp/brushes because they are readonly.


I did, keeps crashing. T_T


Ok... I'm just wondering... could be that I have way too many brushes? If that's the problem, then I need to find an alternative to GIMP, I used to load them all in PS without a problem. So I never really thought having more than 3000 brushes could be a problem on GIMP.



Update: Ok, I reduced my brushes folder to just 300 files... keeps crashing... so I assumed having a lot of brushes isn't the problem.

---

### Post by Half-Left on 2008-05-19
You better use gimp brushes from here then [http://gimp-tutorials.net/taxonomy/term/21](http://gimp-tutorials.net/taxonomy/term/21)

---

### Post by Tsukino Kyuuketsuki on 2008-05-19
So that means I can't use the brushes I always used?

---

### Post by unutbu on 2008-05-19
Can you post one of your brushes?

---

### Post by Tsukino Kyuuketsuki on 2008-05-19
> **Half-Left said:**
> You better use gimp brushes from here then [http://gimp-tutorials.net/taxonomy/term/21](http://gimp-tutorials.net/taxonomy/term/21)

Ok, I moved all my brushes to another folder, and used some of the brushes on that website. I have 292 files in the brushes folder, and when I try to load  GIMP keeps crashing. So it's not having more than 3000 brushes... ain't my own brushes either... I mean, something must be really wrong with the GIMP, I just can't figure it out what's my problem.

I reinstalled GIMP, a friend told me "when everything fails, reinstall" lol so I did... just in case... but didn't fix it either.

---

### Post by Half-Left on 2008-05-20
Can you create another user account and try it in there?

---

### Post by Tsukino Kyuuketsuki on 2008-05-20
> **Half-Left said:**
> Can you create another user account and try it in there?

I did what you said. It got stuck trying to load just 207 brushes. 
I was going to organize all my brushes in different folders and open each folder as I need to use different kind of brushes, (apparently gets stuck if I have more than 100 files in the same directory) but I realized that if I change the brushes folder I have to close the GIMP to see the new path. And closing the application every time I need to use a different brush isn't practical to me. I just wish I could find the problem.  :frown:

---

### Post by Half-Left on 2008-05-20
Well it's obviously a brush thats coursing the issue, may even be one or just a few of yours.

You dont have to restart GIMP everytime you add brushes, just hit refresh brushes in the brushes palette.

---

### Post by Tsukino Kyuuketsuki on 2008-05-20
> **Half-Left said:**
> Well it's obviously a brush thats coursing the issue, may even be one or just a few of yours.

You dont have to restart GIMP everytime you add brushes, just hit refresh brushes in the brushes palette.


It crashed even when I wasn't using my brushes (I used the ones on the link you posted).

I didn't mean adding brushes but organizing all of them in different folders and change the brushes path every time I need to use a different kind of brush, but I do have to restart the application or the new path isn't showed.

---

### Post by Half-Left on 2008-05-20
Have you actually tried putting all the brushes in one directory, as in all the .abr files, no other directories, ~/.gimp-2.4/brushes

---

### Post by Tsukino Kyuuketsuki on 2008-05-20
> **Half-Left said:**
> Have you actually tried putting all the brushes in one directory, as in all the .abr files, no other directories, ~/.gimp-2.4/brushes

That's what I did the first time, had all the 3677 (or something) brushes in the /usr/share/gimp/brushes, then I moved all of them to the /home/xxxx/~.gimp-2.4/brushes like you suggested. It kept crashing.
I'm not even using .abr files because I thought that was the problem in the first place. I'm using just .gbr files.

---

### Post by Half-Left on 2008-05-20
Try purging your package manager of cache and fully remove gimp then have it download GIMP from the net, remove ~/.gimp-2.4 directory first.

sudo apt-get clean

sudo apt-get purge gimp-data

---

### Post by Tsukino Kyuuketsuki on 2008-05-20
> **Half-Left said:**
> Try purging your package manager of cache and fully remove gimp then have it download GIMP from the net, remove ~/.gimp-2.4 directory first.

sudo apt-get clean

sudo apt-get purge gimp-data



OK, I did that and tried to reinstall from the terminal and not from the package manager this time. I found a lot of issues and stuff missing. (Can't remember all but I remember something about the python headers, lol)

So I reinstalled GIMP following this tutorial [http://www.gimpusers.com/tutorials/compile-gimp23-with-ubuntu.html]("http://www.gimpusers.com/tutorials/compile-gimp23-with-ubuntu.html")
It took more than 1 hour to install... but now it works, well, it takes a while to load the 3677 brushes (less than PS though) but it doesn't get stuck and I can see all the brushes and use them.

Well, that will teach me to install my stuff from the terminal and not from the package manager #-o

Thanks for all your help and your patience! :biggrin:

---

