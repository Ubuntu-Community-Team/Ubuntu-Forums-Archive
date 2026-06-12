---
title: "Ubuntu Font"
date: 2006-09-08
forum: Art &amp; Design
---

### Post by the_french_canadian on 2006-09-08
I just found out how to get the official Ubuntu font so that it is accessable to all programs running under you're Ubuntu operating system (including The Gimp)! This could have many uses for ubuntu associated art and could add a touch of style to any picture. It is also extremely easy to install!
[I]
Go to the 'System' option in you're toolbar, the to 'Administation' and finally 'Synaptic Package Manager'. You should now be asked for you're password which you should input.

Once in the package manager, press 'search' and input "ttf-ubntu-title" then press 'search'

There should be only one package which is called 'ttf-ubuntu-title'. Right click this package and select 'Mark for Installation"

Finally press 'Apply' in the package manager which should sucessfully install your new ubuntu font![/I]

---

### Post by HanZo on 2006-09-08
yep! but as you mention it... having always worked with a font management software I was pretty disappointed by the lack of such an app in ubuntu/linux... then I found out I just have to copy fonts from wherever I keep them to the .font folder in my home dir to "activate" them system wide...

---

### Post by the_french_canadian on 2006-09-08
I know what you mean! Ubuntu has a knack of not making this obvious, but once you're used to it, its quite easy!!!

I really think the ubuntu font is great though, and can be used for almost EVERYTHING!! :D :D

---

### Post by christooss on 2006-09-20
Thank you for this tip. I wanted to use this for a long time funaly I will work on logo of my project.

---

### Post by Kayne on 2006-09-21
> **the_french_canadian said:**
> I just found out how to get the official Ubuntu font so that it is accessable to all programs running under you're Ubuntu operating system (including The Gimp)! This could have many uses for ubuntu associated art and could add a touch of style to any picture. It is also extremely easy to install!
[I]
Go to the 'System' option in you're toolbar, the to 'Administation' and finally 'Synaptic Package Manager'. You should now be asked for you're password which you should input.

Once in the package manager, press 'search' and input "ttf-ubntu-title" then press 'search'

There should be only one package which is called 'ttf-ubuntu-title'. Right click this package and select 'Mark for Installation"

Finally press 'Apply' in the package manager which should sucessfully install your new ubuntu font![/I]
Or
```
sudo apt-get install ttf-ubuntu-title
```;)

---

### Post by the_french_canadian on 2006-09-21
Personally, i always favour the GUI method of installing packages rather than going through the Terminal, but it all depends on user preferance! As you correctly said, it can be installed via the Terminal with the command ```
sudo apt-get install ttf-ubuntu-title
```

---

### Post by Quoll on 2006-09-21
Thanks the_french_canadian!, now installed and working fine. The only thing I'd add is that you need to have the LTS Backports Repository enabled - ttf-ubntu-title isn't available on the default repositories.

---

### Post by commodore on 2006-09-24
Lol I have always thought that copying the font is very easy. I found it out first thorugh some how-to. I don't copy them to .fonts but to /usr/share/fonts (IIRC). I think the Ubuntu font should come installed with Ubuntu (if GIMP's there why not).

---

