---
title: "Spotlight equivalent in Ubuntu ?"
date: 2011-12-05
forum: Apple Hardware Users
---

### Post by blackbird34 on 2011-12-05
Hi
had a mac till recently, liked the SPOTLIGHT feature that not only searched (VERY VERY well) for files anywhere and everywhere (much better that gnome search or synapse) but also, BEST OF ALL, seaarched for words inside the files (Open/libreOffice documents especially).

Is there anything with that KILLER feature in Ubuntu repos somewhere? Was very very useful. It  :guitar:'ed  ;)

(even, does the Unity dash do it? I haven't noticed so... )

Thanks all

PS main system : Natty w/Gnome Classic :)

EDIT: PPS: 100th bean !!! :)

---

### Post by crazy bird on 2011-12-05
Can you provide us with a link so we can see better what kind of program it is?

---

### Post by CoffeeRain on 2011-12-05
Spotlight is an AWESOME feature that lets you search through your files. It can look at the content of the documents and do math equations etc.

---

### Post by Lars Noodén on 2011-12-05
I'm not so familiar with Spotlight, but it sounds like something that [Strigi](http://strigi.sourceforge.net/), [Tracker](http://projects.gnome.org/tracker/), [Recoll](http://www.recoll.org/), and [Pinot](http://pinot.berlios.de/) can do.

Also, I am not sure what Nepomuk does and if it is relevant.

---

### Post by yugnip on 2011-12-05
Hi. Gnome Do and Kupfer, both available in the repos, are about the closest I have found. They are kinda like Quicksilver in that they actually have more functionality ala plugins than does Spotlight. And yet they still aren't quite as good either. 

I know zeitgeist is working on this functionality as well... But it doesn't seem to be there yet.

---

### Post by blackbird34 on 2011-12-05
Recoll and Pinot look fairly close... Never be as elegant as Spotlight, but i'm apt-getting them to have a look.

i'll report back if they work nicely. For anyone interested, Synapse is very elegant, fast and good at looking for files, but doesn't search inside them.

EDIT: Recoll looks fairly powerful, currently indexing with 100% CPU:D. Pinot i dunno what to make of it, but basic. Tracker's comments in Software Center weren't encouraging, and Strigi's website is offline...

Link for spotlight : [https://en.wikipedia.org/wiki/Spotlight_%28software%29](https://en.wikipedia.org/wiki/Spotlight_%28software%29)

---

### Post by lael on 2011-12-05
I used to use Beagle, which worked pretty well.  Haven't bothered with it in a year or so since I've started using the command line more.

---

### Post by blackbird34 on 2011-12-06
@Lael Beagle doesn't seem good at the moment. Comments in the Software Center complain about a lot of bugs in recent iterations. 

Recoll is quite powerful, it displays results in a similar format to Google search results, i like it a lot. But it's a full blown window, not a little search box in the corner of the screen ike spotlight. I'd recommend it :D, with four stars:KS:KS:KS:KS

---

### Post by LewisTM on 2011-12-06
Recoll is my favorite, seems to have taken the lead in usability, reliability and accuracy. 
Bind a keystroke to the provided /usr/share/recoll/filters/hotrecoll.py to instantly bring it up.
Run 'recollindex -m' as a startup item for automatic indexing.
Beats Google Desktop Search in every respect :D

I find it best to exclude the hidden home subdirectories ~/.* &#8212; except ~/.thunderbird if you want to index your mail. So the latter has to be explicitly added as a top directory.

Cheers!

EDIT: recollindex may use up quite a bit of processing power, especially at login. To decrease it's impact on system performance, use command
'nice -n 10 recollindex -m' instead
That will decrease the task's priority and make it more transparent

---

### Post by BDNiner on 2011-12-06
This is a great post. I will try Recoll out. Spotlight is one of the best desktop search applications around.

---

