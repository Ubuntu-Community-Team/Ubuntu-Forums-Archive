---
title: "How to draw a button connected to an arrow using the Gimp"
date: 2008-12-15
forum: Art &amp; Design
---

### Post by Jonas thomas on 2008-12-15
Hi all,
I usually hang out more in the programming section, but my hair is getting all frazzled trying to figure out this Gimp.
It seem's that there are many roads to a solution, none of which I've been on before.

Here's what I'm trying to do... I've been basically working through a tutorial on wxwidgets and taking screen shots of some of the more salient points and keeping notes on what I got out of the tutorial. I want to be able plop an bullet on the form, add a note withing the bullet, and draw an arrow from the bullet to the point of interest. 

So far, I managed to take a screen shot of a form, crop to size, and Bucket fill the background the rest of the back ground to my favorite color cyan...  Anyway...

Since I haven't played with the Gimp that much, I don't know the lingo well enough to ask the question of a browser.

I was hoping to stay with stuff down loadable within synaptic...
Is there an easy way of doing this so I can stay focused on my main goal of learning wxwidgets???

I found some stuff [here]("http://www.orrery.us/node/35") and was going to give the wingding / rotation method a whirl.  I thought I had the font I needed (ttf-opensymbol) which is supposedly the Open office equivalent of wingdings but it's not showing up in the font list.

I've spent all morning on this and have had no tangible results...
Is there an easy Linux way of doing this??

:confused:
JT

---

### Post by DieB on 2008-12-15
I'm sorry I didn't completly understand what is what u want but did u take a look on the tutorials here?

[http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)

---

### Post by -yay- on 2008-12-15
uhhh.. so you want an arrow? Why not just draw one? or you could download arrow brushes for gimp and then just insert the arrows with just one click using the paintbrush tool.

here are some arrow brushes:
[http://www.gimphelp.org/color_arrow_brushes.shtml](http://www.gimphelp.org/color_arrow_brushes.shtml)

---

### Post by Jonas thomas on 2008-12-16
> **DieB said:**
> I'm sorry I didn't completly understand what is what u want but did u take a look on the tutorials here?

[http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)

I did take a look at the tutorial's... What a beautiful forest to get lost in ;)
I guess perhaps a picture is worth a thousand words....
[IMG]http://www.metalshaperman.com/wp-content/uploads/2008/12/gtc_sample.png[/IMG]

My apologizes on the poor quality here... My impression is that the gimp is more gear toward image manipulation then what I'm trying to do here.
Is there perhaps a different (open source) package anyone can recommend like Powerpoint... Oopps a light bulb just when on.... I have open office on my machine which has the powerpoint clone..

---

### Post by Jonas thomas on 2008-12-16
> **DieB said:**
> I'm sorry I didn't completly understand what is what u want but did u take a look on the tutorials here?

[http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)

I did take a look at the tutorial's... What a beautiful forest to get lost in ;)
I guess perhaps a picture is worth a thousand words....
[IMG]http://www.metalshaperman.com/wp-content/uploads/2008/12/gtc_sample.png[/IMG]

My apologizes on the poor quality here... My impression is that the gimp is more gear toward image manipulation then what I'm trying to do here.
Is there perhaps a different (open source) package anyone can recommend like Powerpoint... Oopps a light bulb just went on.... I have open office on my machine which has the powerpoint clone..

---

### Post by unutbu on 2008-12-16
You could also use the dia package:

---

### Post by lyceum on 2008-12-16
If you want straight arrow, hold "shift" while you draw with a pen tool or the like. If you want bullets then use a pen shape that looks like a circle.

---

### Post by Jonas thomas on 2008-12-16
> **unutbu said:**
> You could also use the dia package:
Thank you for that suggestion.
I believe I found the home for dia @ [http://live.gnome.org/Dia]("http://live.gnome.org/Dia")
Just out of curiosity.  I don't think this is in Synaptic? Is that correct?

---

### Post by Jonas thomas on 2008-12-16
> **lyceum said:**
> If you want straight arrow, hold "shift" while you draw with a pen tool or the like. If you want bullets then use a pen shape that looks like a circle.

I had tried that and I wasn't able to get an arrow. (It's not a big deal since I have some options here)... Is it possible that you have addon or something thats doing that for you?

---

### Post by unutbu on 2008-12-17
The dia package is in the official repositories:
```
sudo apt-get install dia 
```
The only thing I don't like about it is that the arrows seem to be non-antialiased. There might be a way to fix that; I haven't used dia very much.

---

### Post by Jonas thomas on 2008-12-17
> **unutbu said:**
> The dia package is in the official repositories:
```
sudo apt-get install dia 
```
The only thing I don't like about it is that the arrows seem to be non-antialiased. There might be a way to fix that; I haven't used dia very much.
Opps... Me bad... I went to the synaptic gui and typed Dia and for some reason I thought it wasn't there. (I guess the letters "dia" get used alot. Didn't see the tree because of the forest)
I downloaded dia-gnome (not sure what the difference is).
Thanks....

So in conclusion, who it be safe to say that while the Gimp is very good at many things it's not the ideal tool for what I'm trying to do?

Alternatives more suited to the task is Open-office presentation or dia.
Anything else anyone can suggest? Gimpwise or otherwise??

---

### Post by digitalis_vulgaris on 2008-12-17
Inkscape is an answer on all your problems ;-). I use Dia at first but now I'm using Inkscape for drawing diagrams. It even has connect tool!

---

### Post by Jonas thomas on 2008-12-17
> **digitalis_vulgaris said:**
> Inkscape is an answer on all your problems ;-). I use Dia at first but now I'm using Inkscape for drawing diagrams. It even has connect tool!

Solutions just coming out of the woodwork here...:) I was just looking at Inkscape website.  Very interesting.... If I understand this correctly, Inkscape uses Gtk with some thoughts about converting to wxwidgets in the future..

Since my main interest is in learning wxWidgets anyway, it would be cool for me to use a tool which uses that library. ...  I runing out of lunch time.  I need to look at this when I get home from work... Can anyone offhand suggest a package??

---

### Post by unutbu on 2008-12-17
I have a hard time remembering all the cli commands for searching for packages. So I collected them in this script.
I think it could help you to discover on your own what is in the official repos.

Save this script in ~/bin/apt_search.
[PHP]
#!/usr/bin/env python

import sys
from subprocess import Popen,PIPE
def do_cmds(cmds):
    for cmd in cmds:
        print '%s\n? ([Y]/n/q) '%cmd,
        resp=raw_input()
        resp=resp.upper()
        if resp.startswith('Y') or resp=='':
            proc=Popen(cmd, shell=True, stdout=PIPE, )
            print proc.communicate()[0]
        elif resp.startswith('Q'):
            sys.exit()
        print

args=' '.join(sys.argv[1:])
cmds=[
    "apt-cache search %s"%args,
    "dpkg -S %s"%args,
    "dpkg --get-selections *%s*"%args,
    "dpkg -l | grep %s"%args,
    "dpkg-query --list *%s*"%args,
    "dpkg-query --search *%s*"%args,
    "apt-file search %s"%args,
    ]            
do_cmds(cmds)  
[/PHP]
Make it executable.```

chmod +x apt_search
```

Run it like this:
```

apt_search inkscape
```

You can search by keyword, or (partial) package name.
If you are wondering what package provides a certain file, you
can also type
```

apt_search /path/to/file
```
and the script will tell you which package (if any) provides that file.

The last command, apt-file, requires that you install the apt-file package. It allows you to find which package provides a file, even if the package is not installed on your system.

---

### Post by Jonas thomas on 2008-12-19
Are trying to get my brain to explode?  My poor old brain is all ready filled up with this wxWidget/C++ stuff and now you roll in a little Python... ;)  What the heck... We're snowed in today midwest anyway... 
Btw..
I loaded up your script and it bombed on the the os.system command.
> jonas@Ubuntu4:~$ apt_search inkscape
apt-cache search inkscape
? ([Y]/n/q)  Y
Traceback (most recent call last):
  File "/bin/apt_search", line 24, in <module>
    do_cmds(cmds)  
  File "/bin/apt_search", line 9, in do_cmds
    os.system(cmd)
NameError: global name 'os' is not defined
jonas@Ubuntu4:~$ 
I'm current running Ubuntu 8.04 with default Python 2.5.
This function might be deprecated..[http://www.python.org/doc/2.4/lib/node235.html]("http://www.python.org/doc/2.4/lib/node235.html")

My five years school just got cancelled.  So much for the quite time playing with Ubuntu...\\:D/\\:D/   (She picked out the smiley face.... More later.....)
Btw... I like your script concept... (Only thing is you know what all the command mean already... I'm think about redoing it slightly to list out what this stuff does first and then have a select option to select it.

---

### Post by unutbu on 2008-12-19
I've edited the script to use subprocess... Thanks for pointing that out.

---

### Post by Jonas thomas on 2008-12-20
> **digitalis_vulgaris said:**
> Inkscape is an answer on all your problems ;-). I use Dia at first but now I'm using Inkscape for drawing diagrams. It even has connect tool!

I gave Inkscape a whirl.. It looks like it has some interesting features but I'm getting some downright bizarre behaviors with mouse clicks.

It seems like everything works with the keyboard but the mouse is behaving very badly... (For some reason what I just wrote struck me as funny).

Anyway..
I think whats happening is the windowstate (sorry about the vb-speak) is changing on a clickevent which moves the object that was just clicked so it changes the focus.  This is most strange..
Is anyone else getting this??
[EDIT]
I found the program to be usable in fullscreen mode (F11)

---

### Post by Jonas thomas on 2008-12-21
> **digitalis_vulgaris said:**
> Inkscape is an answer on all your problems ;-). I use Dia at first but now I'm using Inkscape for drawing diagrams. It even has connect tool!

Thank you for pointing out inkscape... 
I'm starting to have some for with it as you can see.:popcorn:

[IMG]http://www.metalshaperman.com/wp-content/uploads/2008/12/drawing.png[/IMG]

---

