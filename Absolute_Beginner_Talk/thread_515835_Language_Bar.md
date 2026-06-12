---
title: "Language Bar"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by shakujou on 2007-08-02
For school and other activities, I need to be able to type Japanese and soon Chinese for reports, assignments, and email.  When I was using Windows, I was just set up the language bar on my task bar, so that I could switch between English and Japanese.  

So, now, I have no clue how to set something similar to this up.  I heard you set up SCRIM, but can't figure it out myself.

---

### Post by Vanish00 on 2007-08-02
Sorry I can't help you but I am interested in this too!

---

### Post by andyho on 2007-08-02
go to synaptic package manager and type in scim! :) Add whatever language packs you need. I have Japanese and Korean installed, works pretty much like the language bar in windows does and offers different input types.

---

### Post by atomkarinca on 2007-08-02
right click one of the panels (sorry i forgot to mention you should click on "add to panel" after this), down in the list under utilies there's keyboard indicator, add that. then right-click that icon and select keyboard preferences, add whichever language you like. then you can switch back forth by right-clicking the icon and selecting the language from groups.

(for example now i'm changing it to greek :) &#968;&#959;&#959;&#955; &#951;&#945;)

(i just discovered you can change the language simply clicking on the language sign)

---

### Post by Vanish00 on 2007-08-02
Everything you said was right on about SCIM.  I got worried cause I didn't how to use it then I hit refresh here. :)  Now I got the keyboard indicator up top, just having problems getting the charaters to show now...hmmm

---

### Post by shakujou on 2007-08-02
So, I tried the first method (provided by andyho), and that didn't work (and there was no Japanese package listed).  

Then I try the second method (provided by atomkarinca), the panel appeared, I went to keyboard preferences, and then I added Japanese.  Now, when I try to type in Japanese, it wont work and I still get all english characters (and they stay english characters).

---

### Post by atomkarinca on 2007-08-02
alright, i see what you mean, japanese and chinese don't work on my machine, either. now i'm trying something but i think it will take a while so you can check it, too.

system > administration > language support

and select chinese and japanese, does it work now?

---

### Post by shakujou on 2007-08-02
Okay, I have absolutely no clue what I did.. but I went to language support, selected those two languages, they installed, then asked to restart my computer.

This is a the tricky part, when I boot my system back up, it asks for my login and password in a graphical set up (usually it asks for this in a similar fast to the terminal), and when I login, all my settings are erased.  I look in my root folder, and all the files I put in there (pictures and music that were backed up from my switch to Linux) were gone.  All my settings for gaim and Firefox were gone as well...

---

### Post by Vanish00 on 2007-08-02
Under the language support I installed Japanese but I wasn't prompted to restart computer.  Sorry to hear you lost all your files, shakujou.   I'm still trying to get characters though.

---

### Post by atomkarinca on 2007-08-02
i did the same thing as above and everything's back up. are you sure the files are gone? have you look into you home folder?

after the install you should see an icon on the notification area. when you are writing hit ctrl+space bar and a settings panel appears. you can select chinese and japanese from that panel.

---

### Post by shakujou on 2007-08-02
It's really no big deal that I lost those files, since all they were were files that are backed up anyway.  

The language packs are installed, but still can't type in Japanese.

---

### Post by atomkarinca on 2007-08-02
okay let's go step by step:

- open a text editor (eg. applications > accessories > text editor)
- hit "ctrl + space bar"
- a small panel should appear (it probably says "english")
- click it and select the language
- to turn it off just hit ctrl + space bar again.

---

### Post by shakujou on 2007-08-02
> **atomkarinca said:**
> i did the same thing as above and everything's back up. are you sure the files are gone? have you look into you home folder?

after the install you should see an icon on the notification area. when you are writing hit ctrl+space bar and a settings panel appears. you can select chinese and japanese from that panel.

I've looked through the home folder, since that's where I kept everything to begin with, nothing like a clean desktop.  

[quote=atomkarinca]okay let's go step by step:

- open a text editor (eg. applications > accessories > text editor)
- hit "ctrl + space bar"
- a small panel should appear (it probably says "english")
- click it and select the language
- to turn it off just hit ctrl + space bar again.[/quote]

ctrl+space bar doesn't bring up anything for me, sadly.

---

### Post by Vanish00 on 2007-08-02
I don't see any icon after i installed the japanese support, but what or where is the notification area?  Besides that I went to the text editor but when I press ctrl+space bar I dont get any panel/menu.

---

### Post by atomkarinca on 2007-08-02
hit alt + f2 or open up a terminal and type
```
scim
```
and try the above again.

---

### Post by shakujou on 2007-08-02
Still nothing.

---

### Post by atomkarinca on 2007-08-02
well, mine is working like a charm.

when you type scim in the terminal what is the output?

---

### Post by shakujou on 2007-08-02
It flashes the terminal by me (thats when I select run by terminal), and then starts up the program.  I see it running in the task bar, and I've gone through "SCIM Setup," and all the settings are where I'd like them.  I just don't know how to switch to Japanese.  When I select Japanese on the Keyboard Inidicator you told me to add earlier, it still types in English.

---

### Post by Vanish00 on 2007-08-02
Okay, I think i'm getting close because when I go into SCIM I see mentions of hiragana/katakna mode under IMEngine.  Now under that I choose Anthy and pick the Key bindings tab.  atomkarinca, can you find which feature for you has Control+Spacebar Key bound?

---

### Post by atomkarinca on 2007-08-02
alright, i guess now you got the scim setup icon on your taskbar, am i right? so if you hit ctrl + backspace now something should pop up. you should select japanese from that list, not from the first one i told.

---

### Post by atomkarinca on 2007-08-02
> **Vanish00 said:**
> Okay, I think i'm getting close because when I go into SCIM I see mentions of hiragana/katakna mode under IMEngine.  Now under that I choose Anthy and pick the Key bindings tab.  atomkarinca, can you find which feature for you has Control+Spacebar Key bound?

you see the scim setup icon on your taskbar? right-click it. select "SCIM Setup". under frontend > global setup trigger > hotkey you should see some keyboard shortcuts. if not, then hit the "..." button on the right and configure a keyboard shortcut.

that should be about it.

---

### Post by Vanish00 on 2007-08-02
> **atomkarinca said:**
> you see the scim setup icon on your taskbar? right-click it. select "SCIM Setup". under frontend > global setup trigger > hotkey you should see some keyboard shortcuts. if not, then hit the "..." button on the right and configure a keyboard shortcut.

that should be about it.

I see the "..." button but I have 6 choices.  Under the Trigger, it does have Control+space but that is the only one with that configure.  Btw, i've tried control+space and still no panel nothing.  Yes, your right I do have the SCIM on the taskbar now.

---

### Post by atomkarinca on 2007-08-02
i think that's all i got, i guess. in that trigger section is ctrl+backspace the first one? if it's not make it the first one. if this doesn't work i'm gonna give up and play some &#12377;&#12393;&#12367;&#12288;:P

---

### Post by Vanish00 on 2007-08-02
Not exactly sure where I find this other panel for SCIM, because the one I was talking about was a little icon next to the time.  Now I see a SCIM panel with the words English/European but I can't  change to Japanese. (I think this is what you've been talking about now)

---

### Post by atomkarinca on 2007-08-02
> **Vanish00 said:**
> Not exactly sure where I find this other panel for SCIM, because the one I was talking about was a little icon next to the time.  Now I see a SCIM panel with the words English/European but I can't  change to Japanese. (I think this is what you've been talking about now)

exactly! :D now when you open that panel, click on english/european and a list should come up. select japanese from that list and you're done.

---

### Post by Vanish00 on 2007-08-02
> **atomkarinca said:**
> i think that's all i got, i guess. in that trigger section is ctrl+backspace the first one? if it's not make it the first one. if this doesn't work i'm gonna give up and play some &#12377;&#12393;&#12367;&#12288;:P

&#12354;&#12426;&#12364;&#12392;&#12358; &#12372;&#12374;&#12356;&#12414;&#12377; :KS

---

### Post by atomkarinca on 2007-08-02
> **Vanish00 said:**
> &#12354;&#12426;&#12364;&#12392;&#12358; &#12372;&#12374;&#12356;&#12414;&#12377; :KS

i'm sorry but i took a beginner lesson years ago and i forgot. but i'm glad you got it working :D

---

### Post by atomkarinca on 2007-08-02
> **shakujou said:**
> It flashes the terminal by me (thats when I select run by terminal), and then starts up the program.  I see it running in the task bar, and I've gone through "SCIM Setup," and all the settings are where I'd like them.  I just don't know how to switch to Japanese.  When I select Japanese on the Keyboard Inidicator you told me to add earlier, it still types in English.

shakujou: if i couldn't help, i found a howto for you, maybe that could help:

[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

---

### Post by Vanish00 on 2007-08-02
I was just saying thank you! ;)

If anybody else is following this, I ended up finding I had to right-click the actual document then 
Input Methods->SCIM Input Method.  Once i did do that everything fell into place.

---

### Post by shakujou on 2007-08-02
&#12391;&#12365;&#12427;&#12424;&#12397;
I haven't gotten the hot keys to work yet, but at least I can type Japaense again.

---

### Post by atomkarinca on 2007-08-02
> **Vanish00 said:**
> I was just saying thank you! ;)

&#12393;&#12356;&#12383;&#12375;&#12414;&#12375;&#12390;&#12288;(i guess it was something like this :))

---

### Post by n.aggel on 2007-08-02
I am from greece...and that tip was the best...now i can read greek in ubuntu!!!

---

### Post by atomkarinca on 2007-08-02
> **n.aggel said:**
> I am from greece...and that tip was the best...now i can read greek in ubuntu!!!

&#928;&#913;&#929;&#913;&#922;&#913;&#923;&#927; (is that right? :))

---

### Post by n.aggel on 2007-08-02
> **atomkarinca said:**
> &#928;&#913;&#929;&#913;&#922;&#913;&#923;&#927; (is that right? :) )
LOL....almost correct, you missed one letter!
{i can write this after using your tip :P }

&#928;&#913;&#929;&#913;&#922;&#913;&#923;&#937;

so once again thank you Or as we say it here in greece &#917;&#933;&#935;&#913;&#929;&#921;&#931;&#932;&#937; !!!

---

### Post by OsakaWilson on 2007-10-01
If you get SCIM running, be sure to test it in something other than Firefox. I have been using SCIM on my system for a year now, but have never been able to use it in Firefox. It works for everything else though. If I want to input Japanese into Firefox, I have to put it into the notepad, then cut and paste it. A major pain in the ***. Never have found a fix despite hours of searching and tweaking. Just a heads up.

---

