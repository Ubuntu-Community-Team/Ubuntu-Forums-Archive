---
title: "How to install PowerISO?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by _Pieter_ on 2007-06-15
Hi all!

I have a .daa file that I wish to burn to CD, that's why I need PowerISO. But I have no idea on how to install it... I am not an absolute noob but when reading this thread

[http://ubuntuforums.org/showthread.php?t=435396&highlight=poweriso](http://ubuntuforums.org/showthread.php?t=435396&highlight=poweriso)

I cannot figure it out. So would anyone be so kind to explain in simple language how I can get this puppy working? 

Thanks a lot:)

---

### Post by Tranux on 2007-06-15
Hi,

[http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm)
[http://www.poweriso.com/poweriso-1.1.tar.gz](http://www.poweriso.com/poweriso-1.1.tar.gz)

you can download the program on the site above. It is a binary for the terminal. It means that you do not need to compile the program.
All you have to do is: 
[LIST]Extract the archive e.g with the gui[/LIST]
[LIST]Open the terminal[/LIST]
[LIST]Type: cd ~/Desktop[/LIST]
[LIST]Type: ./poweriso -?[/LIST]

Kind regards, Patrick

---

### Post by _Pieter_ on 2007-06-15
Hey Patrick,

When I type in the terminal ```
./poweriso -?
```, I get the Poweriso help file. So far so good. But when I try to convert my file according to the specified code in the help file

```
poweriso convert /home/pieter/Desktop/Pimsleur Mandarin Chinese 1-3.daa -o /home/pieter/Desktop/Pimsleur Mandarin Chinese 1-3.iso -ot iso
```

I get the following:

```
bash: poweriso: command not found

```

I doublechecked it for typo's but it just won't work :(

Further suggestions are more than welcome.

---

### Post by nosaj on 2007-06-15
you forgot to put the ./ in front of poweriso

---

### Post by elbono on 2008-02-01
Thanks for this post, it's exactly what i needed to convert the file!

---

### Post by Nythain on 2008-02-01
filenames with spaces work different in terminal...
you need to preceed each empty "space" with a \... like
This\ is\ Just\ an\ Example\ of\ What\ I\ Mean.daa
so in your case it would be
```

Pimsleur\ Mandarin\ Chinese\ 1-3.daa

```p.s. make sure you include the ./ before poweriso, like ./poweriso as mentioned above also... my advice was just to help with the next problem you were going to encounter with your current syntax

---

