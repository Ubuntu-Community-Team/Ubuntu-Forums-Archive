---
title: "Cairo front-end for Conky!"
date: 2009-10-17
forum: Art &amp; Design
---

### Post by Labello on 2009-10-17
Hello folks!

I would like to show you some of my recent work. I have always been disturbed by conky's limited possibilities when it comes to the presentation of the information that can be collected with conky.

So I started to develop something like a front-end for Conky that uses the Cairo graphics-engine to display the information in a hopefully better and nicer way. It is still in heavy development and unusable for someone not familiar with the code. So the reason why I post this here is, because I wonder whether someone is willing to create some basic mock-ups for some more "widgets" since I am not creative at all. Then I will try to convert them into actual working ones. Let your creativity flow since there aren't almost any restricitions with the cairo engine. So nearly everything is possible as long as my skills allow it.

To show you what I got so far here is a screenshot with all widgets that are avaible at the moment:

[img]https://dl.getdropbox.com/u/416097/sreen_cairo.png[/img]

the actual code for the end-user to get a result like that is the following:
```

draw_curve_clock(10,435,320,200,20,2,85/255,85/255,85/255,1,1,1,1,0.5)
	draw_digit("CPU 1: ", 10, 230, 70, 0, 270, "${cpu cpu1}", 100, 2, 85/255, 85/255,85/255,1,1,1,1,0.5)
	draw_digit("CPU 2: ", 180, 230, 70, 0, 270, "${cpu cpu2}", 100, 2, 85/255, 85/255,85/255,1,1,1,1,0.5)
	draw_circle_stat("CPU 2: ", 180, 25, 70, "${cpu cpu2}", 100, 2,85/255,85/255,85/255,1,1,1,1,0.5)
	draw_circle_stat("CPU 1: ", 10, 25, 70, "${cpu cpu1}", 100, 2, 85/255, 85/255, 85/255, 1, 1, 1, 1, 0.5)
	draw_digit("CPU Temp: ", 10, 645, 70, 0, 270, "${hwmon temp 1}", 85, 2, 85/255, 85/255,85/255,1,1,1,1,0.5)
	draw_h_meter("CPU 2: ", 180, 645, 70, 191, "${cpu cpu2}", 100, 2,85/255,85/255,85/255,1,1,1,1,0.5)
	draw_h_meter("CPU 2: ", 260, 645, 70, 191, "${cpu cpu1}", 100, 2,85/255,85/255,85/255,1,1,1,1,0.5)

```

But there still will be some more improvements concerning ease of use. Of course it will be OpenSource when it comes to a release.

So comments and critics are more than welcome!

---

### Post by Tibuda on 2009-10-17
Have you tried the latest conky with cairo and lua bindings?

See this blog post: [http://blog.conky.be/2009/09/28/lua-cairo-bindings-getting-started](http://blog.conky.be/2009/09/28/lua-cairo-bindings-getting-started)

---

### Post by Labello on 2009-10-18
> **danielrmt said:**
> Have you tried the latest conky with cairo and lua bindings?

See this blog post: [http://blog.conky.be/2009/09/28/lua-cairo-bindings-getting-started](http://blog.conky.be/2009/09/28/lua-cairo-bindings-getting-started)

Yeah that's what I am using! But I am planning to develop a whole set of functions that allow to easily create various effects by using the variables returned by conky!

Therefore I could need some help with some more ideas for effects and widgets.

---

### Post by Tibuda on 2009-10-19
> **Labello said:**
> Yeah that's what I am using! But I am planning to develop a whole set of functions that allow to easily create various effects by using the variables returned by conky!

Therefore I could need some help with some more ideas for effects and widgets.

lol, thats nice. you could call that "conklets".

---

### Post by Labello on 2009-10-19
> **danielrmt said:**
> lol, thats nice. you could call that "conklets".

Yeah I this name came to my mind to. If there will ever be a release, I will consider this one!

Here is another screen showing some gloss-effect that will be available optionally and a very simple clock:

[img]https://dl.getdropbox.com/u/416097/screen_cairo_2.png[/img]

comments and crits always welcome!

---

### Post by SoftwareExplorer on 2009-10-19
Looks Nice. I would tend to not use the glass look, but the flat one, but other people will probably like the glass.
So would you be able to set it up to have a chart (or dial) that takes the number a script gives? Because I have a folding at home script and other people have weather scripts, etc.

---

### Post by Labello on 2009-10-20
> **SoftwareExplorer said:**
> Looks Nice. I would tend to not use the glass look, but the flat one, but other people will probably like the glass.
So would you be able to set it up to have a chart (or dial) that takes the number a script gives? Because I have a folding at home script and other people have weather scripts, etc.

I don't get what you want to know. These widgets can be used together with a normal conky-config and can be placed whereever you like within the conky window.

---

### Post by SoftwareExplorer on 2009-10-20
> **Labello said:**
> I don't get what you want to know. These widgets can be used together with a normal conky-config and can be placed whereever you like within the conky window.
I have stuff like this in my conkyrc and I was basically wondering if it could be put into a dial for instance:
```
${execi 500 cat /opt/foldingathome/1/FAHlog.txt | tr '(' '\n' |tr ')' '\n' | grep -E "(%|percent)"|tail -n 1 | tr  -d 'percent'  | tr  -d '%'} %  ${color2}${execbar echo "scale=2; $(cat /opt/foldingathome/1/FAHlog.txt | tr '(' '\n' |tr ')' '\n' | grep -E "(%|percent)"|tail -n 1 | tr  -d 'percent'  | tr  -d '%')/100" | bc -q}
```

---

### Post by Labello on 2009-10-23
> **SoftwareExplorer said:**
> I have stuff like this in my conkyrc and I was basically wondering if it could be put into a dial for instance:
```
${execi 500 cat /opt/foldingathome/1/FAHlog.txt | tr '(' '\n' |tr ')' '\n' | grep -E "(%|percent)"|tail -n 1 | tr  -d 'percent'  | tr  -d '%'} %  ${color2}${execbar echo "scale=2; $(cat /opt/foldingathome/1/FAHlog.txt | tr '(' '\n' |tr ')' '\n' | grep -E "(%|percent)"|tail -n 1 | tr  -d 'percent'  | tr  -d '%')/100" | bc -q}
```

I still don't get what you want, but ok.

I added another visual effect called shadows. right now you can only set their size but nothing else, but I will certainly include more customization options:

[img]https://dl.getdropbox.com/u/416097/2009-10-22--1256233777_2880x1200_scrot.png[/img]

---

### Post by jeffus_il on 2009-10-23
You seem pretty creative to me, keep going. You know how many people haven't done with Conky what you succeeded in doing?:)

---

### Post by Labello on 2009-10-23
I spent another very productive evening with my project now officially called "Conklets".

Since I am learning Lua and Cairo on the fly while pushing this project, my progress is rather slow and most of my approaches to achieve certain things are not very efficient, but I think I am doing pretty well up to now. I found a way how to "rescue" values of variables from one execution to another which now allows me to draw some nice graphs and more is to follow, since this offers a whole lot more possibilities than ever before.

Moreover I now decided to set two global colours that are used to draw within conky to achieve a maximum of consistency within the conklets

There is a bug in the drop_shadow function that's why shadows are disabled in the following screen. I tried a different wallpaper an colours:

[img]https://dl.getdropbox.com/u/416097/2009-10-24--1256335410_2880x1200_scrot.png[/img]

I still could need some mockups or links that might propose some more ideas for some more conklets. so please feel free to drop anything that could be a help.

thanks for reading!

---

### Post by Rob2687 on 2009-10-23
You seem to be doing alright by yourself. :D

---

### Post by Labello on 2009-10-24
> **Rob2687 said:**
> You seem to be doing alright by yourself. :D

Well alright sound like mediocre which is not my goal to be honest. and as far as I can see the response is not that active and thus I would guess that is due to a lack of interest or neccessity... But maybe I just have got to release something that people got something to get their grip on. maybe then there will be more response and critics.

---

### Post by gabrielaca on 2009-10-26
i don´t think is lack of interest from people around here, my guess is that they want hands on experience, with addons  more finished, and don´t have or know much about design, _wich is your main concern here._

i would like to have it opened in a desk atthe moment of loggin, also show cpus (4 in my case), video card, ram, temps, i know all this can be done, alas not as fashionable as your interface show, so keep developing it.

hope this help, and don´t stop developing this please.


cheers and happy conkying to you ;)

---

### Post by Labello on 2009-11-08
hi everyone!

i made a huge progress with my conklets in developing a proper layout and customizing possibilities. i added a curve-conklet where several curves can be stacked above each other like the graph-conklets. i also added a new conklets that just displays a conky-output with a prefix and a suffix.

screenshot:
[img]https://dl.dropbox.com/u/416097/screen.png[/img]

---

### Post by Der_Baz on 2009-11-16
looks great!!
when are you going to release something? I'm looking forward to it...

---

### Post by Labello on 2009-11-16
> **Der_Baz said:**
> looks great!!
when are you going to release something? I'm looking forward to it...

well you could look at conklets.sourceforge.net to get some code and try it out. but it is rather rudimentary and not expected to work flawlessly. I am still working on a realeaseable and useable version but that will be taking some time.

but thanks for your interest! =)

---

### Post by Labello on 2009-11-18
UPDATE! - New Conklet!
[img]https://dl.dropbox.com/u/416097/2009-11-18--1258580722_2880x1200_scrot.png[/img]

let me introduce to you my twitter-conklet! it displays the recent tweets of the people you are currently following!
I used the following code as a startingpoint:
[http://blog.kadirpekel.com/2009/01/08/how-to-hack-twitter-with-a-few-lines-of-lua-code/comment-page-3/#comment-8928](http://blog.kadirpekel.com/2009/01/08/how-to-hack-twitter-with-a-few-lines-of-lua-code/comment-page-3/#comment-8928)

Next weekend there will be some code cleanup and maybe a new release after finishing some rudimentary documentation to get some people started.

---

### Post by Labello on 2009-11-20
[img]http://conklets.sourceforge.net/img/screen3.jpg[/img]

Now folks... I made the breakthrough... well... almost.

Conklets now can be installed by using a deb-pakage which you can grab here:
[https://sourceforge.net/projects/conklets/files/conklets_0.1.12-1_all.deb/download](https://sourceforge.net/projects/conklets/files/conklets_0.1.12-1_all.deb/download)

and the needed documentation can be found here:
[http://conklets.sourceforge.net/documentation.html](http://conklets.sourceforge.net/documentation.html)

---

### Post by phredbull on 2010-02-20
Wow, really slick looking! Keep up the good work!

---

### Post by PC_load_letter on 2010-02-20
downloaded the deb package, installed it along with 7 dependencies. Typed 'conklet' from a terminal and this is what I got (it kept displaying these lines over & over until I pushed CTRL+Z).

```

Conky: llua_do_call: function conky_init_conklets ex
s/cairo.lua:26: module 'socket' not found:
	no field package.preload['socket']
	no file './socket.lua'
	no file '/usr/local/share/lua/5.1/socket.lua
	no file '/usr/local/share/lua/5.1/socket/ini
	no file '/usr/local/lib/lua/5.1/socket.lua'
	no file '/usr/local/lib/lua/5.1/socket/init.
	no file '/usr/share/lua/5.1/socket.lua'
	no file '/usr/share/lua/5.1/socket/init.lua'
	no file '/usr/lib/conky/libsocket.so'
	no file './socket.so'
	no file '/usr/local/lib/lua/5.1/socket.so'
	no file '/usr/lib/lua/5.1/socket.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'

```

---

### Post by airtonix on 2010-02-21
not my style to be honest.

i prefer the conky setups that are not extroverts... i like them to match the theme and colour scheme of the wallpaper : 

[IMG]https://dl.dropbox.com/u/180039/screenshots/2009-07-15-173127_1920x1080_conky.png[/IMG]

---

