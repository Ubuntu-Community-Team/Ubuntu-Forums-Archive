---
title: "help installing themes"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by matious on 2007-06-11
I've been trying to test out themes in Ubuntu, downloaded a couple from gnome-look. i figured they would come in the correct format for themes.

i save them to my desktop, go to themes, click install theme, then pick the folder i downloaded, but anything inside of the folder it says is not the correct file type.

i know this is probably an extremely simple question, but anyone mind me telling me what I'm doing wrong?

i didn't find a tutorial on gnome-look, and the "download anything" tutorial was unsuccessful in answering my problem.

thanks in advance.

---

### Post by ^Pho[T]on on 2007-06-11
system -> preferences -> themes

click install, open the .tar.gz file for the theme.
it expects a tar.gz file as a theme.
DO NOT extract the files.
enjoy your new theme ;)

---

### Post by steveneddy on 2007-06-11
Just drag the .tar.gz file to the theme window and it installs itself

---

### Post by Inxsible on 2007-06-11
I downloaded some 7 themes, and only 2 got installed :(

It keeps saying "The file format is invalid" for the rest.

---

### Post by carloslosgrande on 2007-06-11
The first time I tried to get more themes nothing worked! I did it all wrong!
then i found a thread about this very subject and did this;
Downloaded a bunch of themes to a folder I made (Didn't extract)
then opened system>preferences>theme and just dragged each one across, answering the menu boxes as required.
As Steveneddy and ^phoTon said, it just installs by itself.
I don't recall having the problem of Inxsible, I must of just been lucky.

---

### Post by rfurman24 on 2007-06-12
I think some of the themes on gnome-look have to be extracted and then installed to the system rather than in theme manager. I just throw them away when I find one.

---

### Post by Inxsible on 2007-06-12
> **rfurman24 said:**
> I think some of the themes on gnome-look have to be extracted and then installed to the system rather than in theme manager. I just throw them away when I find one.
Do you know of a way to install them after extracting them ?

---

### Post by matious on 2007-06-12
:)

thanks guys, i guess the only thing i was doing wrong was extracting them.

---

### Post by terabite on 2007-06-13
> **Inxsible said:**
> Do you know of a way to install them after extracting them ?

To install the theme engine extract it to somewhere convenient and in that directory run:
```
./configure --prefix=/usr -enable-animation
```
obv...  the command line parameters vary...


then
```
 make 
```

Then as a root user 
```
make install
```


Then install the themes by extracting them to your ~/.themes.


This works in most cases of 'theme installation'.

---

