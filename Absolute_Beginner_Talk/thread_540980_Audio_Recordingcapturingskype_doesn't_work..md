---
title: "Audio Recording/capturing/skype doesn't work."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-02
Hi, I have a problem with my audio recording in Ubuntu. The thing is that I have had the same problem on my laptop and my desktop computer. Right now I'm focusing on the desktop.

The problem is that I can't record anything or speak to anyone using skype.

If i boot up into windows everything works fine. My audio soundcard is onboard a MD-5000 M-ATX motherboard - a RealTek ALC650 and the chipset is SiS 648 and SiS963.

Does anyone know what might be wrong, also VirtualBox recognize that there is a problem with my soundcard, so I guess it might be a driver problem and not a settings problem.

Any help appreciated.

---

### Post by terabyte1 on 2007-09-02
Check to see if you have the "Restricted Repositories" if you don't have these, you need to load these to get the corect Codecs so that your Audio Files/Skype can run. Although not Ubuntu or supported by them, there is a program called "Automatix" which is a little program that will load your repositiories and the 'Restricted Ones' under Codecs, should you require them. To get Automatix type in on the address line of your browser: "www.getautomatix.com" and this should solve your problem *should this be the problem*.

I hope this helps and I hope I haven't trodden on too many toes mentioning Automatix :) !

terabyte1

---

### Post by kasperbs on 2007-09-04
HI, thanks for your reply. I tried what you mentioned but it didnt work. I should maybe mention that none of my recording software works, it's not only skype.

As i said i think it might be a driver problem, because even Virtualbox recognizes that there is something strange with my soundcard.

---

### Post by ramjet_1953 on 2007-09-04
Open your volume control mixer by right clicking on the [COLOR="Blue"]speaker icon in the top taskbar.[/COLOR]

Click on [COLOR="Blue"]Open Volume Control[/COLOR].

When the window opens, click on [COLOR="Blue"]Edit>Preferences[/COLOR]

When the new window opens, [COLOR="Blue"]put a tick in every box[/COLOR] (to be sure)

Click [COLOR="Blue"]Close.[/COLOR]

Sometimes it's a good idea here to close the Volume Control Window and re-open it again at this point.

OK, now you have re-opened the window, make sure that the [COLOR="Blue"]sliders are all at maximum[/COLOR], initially. You can alter this later to suit.

Now, click on the [COLOR="Blue"]Recording Tab[/COLOR] and make sure that the [COLOR="Blue"]Capture Sliders are at maximum.[/COLOR]

Next, click on the [COLOR="Blue"]Switches Tab[/COLOR] and make sure that there is a [COLOR="Blue"]tick in Microphone Capture.[/COLOR]

[COLOR="Blue"]Close the mixer[/COLOR] and re-try a test call to Skype. Hopefully, all will be well.

Regards,
Roger :cool:

---

### Post by vikrant82 on 2007-09-04
I have another issue here.

Whenever i use Microphone, I hear a constant hummmm[hiss??] [sometimes disturbing...].

I can get rid of this sound by minimizing "Capture Slider" in recording tab. However doing so, also decreases my microfone sound, the other party is getting.

---

