---
title: "Ubuntu Nature Splash"
date: 2005-09-15
forum: Art &amp; Design
---

### Post by Perfect Storm on 2005-09-15
[http://ubuntuforums.org/gallery/showimage.php?i=860&original=1&c=](http://ubuntuforums.org/gallery/showimage.php?i=860&original=1&c=)


I'm at the moment cleaning it and making it more smooth so a new version of it is on its way.
Also I'm planning a GTK and Icon theme which suit it.

Ideas, suggestions or anything are welcome :)


.:=The AI Dude=:.

---

### Post by Lord Illidan on 2005-09-15
*mouth drops*.

I like it. I like it a lot. It is a wallpaper or a splash as in boot splash?

---

### Post by Perfect Storm on 2005-09-15
It's a splash that comes after you typing username and password. But I'm gonna make a complete set which contains boot splash, splash, wallpaper, icons and gtk theme (and metacity) and perhaps cursor.



.:=The AI Dude=:.

---

### Post by Perfect Storm on 2005-09-18
I'm remaking some of bvcs gtk themes into a Nature theme...Still in early stage and lot of things can change and will be change untill I'm saticefied ;)
I havn't modified the Meta theme yet.

[IMG]http://thilockdominus.freehomepage.com/images/MyThemes/PreGTK.jpg[/IMG] 


[IMG]http://thilockdominus.freehomepage.com/images/MyThemes/preGTK2.jpg[/IMG] 


[IMG]http://thilockdominus.freehomepage.com/images/MyThemes/Screenshot-Save.jpg[/IMG]


.:=The AI Dude=:.

---

### Post by benplaut on 2005-09-18
[QUOTE=Artificial Intelligence]I'm remaking some of bvcs gtk themes into a Nature theme...Still in early stage and lot of things can change and will be change untill I'm saticefied ;)
I havn't modified the Meta theme yet.
[/QUOTE]

gimme gimme! 

this might break me off my adiction to whiteplate (the gtk theme, that is)  :shock:

---

### Post by bvc on 2005-09-18
umm...whiteplate is industrial...should be an easy break :-P ...except for the speed you'll lose.

---

### Post by karuptdata on 2005-09-18
You have got to release that theme that looks nice good job....ill be waiting on the release.... \\:D/

---

### Post by idn on 2005-09-19
Yeah looks good, well done

---

### Post by benplaut on 2005-09-19
[QUOTE=bvc]umm...whiteplate is industrial...should be an easy break :-P ...except for the speed you'll lose.[/QUOTE]

no, whiteplate is waaay better than industrial  :)

---

### Post by bvc on 2005-09-19
[QUOTE=benplaut]no, whiteplate is waaay better than industrial  :)[/QUOTE]again [whiteplate is industrial](http://gnome-look.org/content/pre1/16301-1.png)

AI, let us know the progress of the theme!

---

### Post by Perfect Storm on 2005-09-19
Okay will do. 

Just a question: is it possible to give an item both Prelight and insensitive?
```

{
     function			= BOX
     state				= INSENSITIVE
     state                              = PRELIGHT
     file				= "button-insensitive.png"
     border			= { 8, 8, 4, 4 }
     stretch			= TRUE
    }

```

---

### Post by bvc on 2005-09-20
[QUOTE=Artificial Intelligence]Okay will do. 

Just a question: is it possible to give an item both Prelight and insensitive?[/QUOTE]

you can give 1 image diff states like below but not in the same call like you have it above.....gtk will use the first state it finds.
```

{
     function			= BOX
     state				= INSENSITIVE
     file				= "button-insensitive.png"
     border			= { 8, 8, 4, 4 }
     stretch			= TRUE
    }
{
     function			= BOX
     state                              = PRELIGHT
     file				= "button-insensitive.png"
     border			= { 8, 8, 4, 4 }
     stretch			= TRUE
    }

```

---

### Post by Perfect Storm on 2005-09-23
Sorry I've to inform that I get a bit delayed, a foolish mistake I erease my work :/....don't worry I can build it again, but it's a bit step back  ](*,) 

One thing I learn is to multiply backup  :roll:

---

### Post by krusbjorn on 2005-09-23
[QUOTE=Artificial Intelligence]Sorry I've to inform that I get a bit delayed, a foolish mistake I erease my work :/....don't worry I can build it again, but it's a bit step back  ](*,) 

One thing I learn is to multiply backup  :roll:[/QUOTE]

ouch! it looked really good. hope it will be even better, now that you have to redo it ;)

---

### Post by Perfect Storm on 2005-09-23
Good news! I found most of my work shattered around my home directory, so only a little set back ^^

---

### Post by benplaut on 2005-09-23
[QUOTE=bvc]again [whiteplate is industrial](http://gnome-look.org/content/pre1/16301-1.png)

AI, let us know the progress of the theme![/QUOTE]

actually it is a bit darker around the edges, and has different contro buttons, but they're very close

---

### Post by Perfect Storm on 2005-09-25
I need some opinions! To much green? Is it to much with the ubuntu logo which is melted into the background? To bright to Dark?

[IMG]http://thilockdominus.freehomepage.com/images/MyThemes/Screenshot-Keyboard%20Preferences.jpg[/IMG]

---

### Post by heart_reaver on 2005-10-23
Its :razz:   to good, just release it man. My desktop is striping to ware it ;)

---

### Post by shade11 on 2005-10-26
My god it is soooooo cool.

---

### Post by qalimas on 2005-10-27
I'll be waiting on all this to be released as a final :D  My desktop will definately sport it!

---

### Post by jabagawee on 2008-02-04
any updates? bump~

---

### Post by Perfect Storm on 2008-02-05
No it's abandoned after a hardware failure which I couldn't recover it sadly.

---

