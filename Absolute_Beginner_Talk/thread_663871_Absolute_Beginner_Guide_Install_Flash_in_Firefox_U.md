---
title: "Absolute Beginner Guide: Install Flash in Firefox Ubuntu 64 (Firefox32)"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by ninboy on 2008-01-10
I'm pretty sure a LOT of people out there, who doesn't know too much about Ubuntu and Linux, are suffering and returning to Windows/MacOSX because in Firefox Youtube doesn't works on Ubuntu AMD64 (aka. Ubuntu for 64 bits processors)! OMG! :(:(:(

Me, being a Ubuntu beginner too, used to have a LOT of troubles trying to see Flash and Java contents in the web...

A lot of scripts for install these plugins are written per day, so, having so much material I decidied to write my own shell script.

**FOR BEGINNERS:**
If you want Java and Flash in your 64bits Ubuntu, you must install Firefox 32bits. The default is Firefox 64bits. This takes some installation knowledge, and usually (the first time) a LOT of time... I made a simple script to install it...

**Steps:**
1) First download the script you need (firefox32-eng.sh for English install, firefox32-spa.sh for Spanish) to you home folder.
2) Press Alt+F2 and write: *gnome-terminal* and click *Run*
3) Write in the shell:* sh firefox32-eng.sh* or *sh firefox32-spa.sh* (depends of wich file you downloaded)
4) Put your admin password as many times as needed...
5) Done!

**FOR THE EXPERTS**
I'm planning of distributing this in a bunch of Ubuntu 64bits PC, how can I make this more efficient?

-----------------------------------------------------------------------------
Estoy seguro que MUCHAS personas, que no conocen mucho acerca de Ubuntu y Linux, están sufriendo y regresando a Windows/MacOSX porque en Firefox Youtube no funciona en las distribuciones de Ubuntu 64 bits (Ubunut AMD64). :(:(:(

Yo, siendo un aprendiz también, solia tener MUCHOS problemas tratando de tener Flash y Java instalado en Firefox...

Muchos scripts para instalar estos plugins son escritos por dia, entonces teniendo tantomaterial a la mano decidí escribir mi propio script.
[B]
PARA APRENDICES[/B]
Si quiere tener Java y Flash en tu Ubuntu de 64bits, debes instalar Firefox para 32bits. Se instala por defecto la version de 64bits, si no sabes cual tienes lo mas probable es que sea esta. Para esto se requiere algo de conocimiento de instalación, y normalmente toma mucho tiempo la primera vez. Aqui tienen un script para hacerlo en pocos pasos :)

**Pasos:**
1) Primero baja el script que necesites (firefox32-eng.sh para instalar en inglés firefox32-spa.sh para español) a tu carpeta home.
2) Teclea Alt+F2 y escribe: *gnome-terminal* y haz click *Run*
3) Escribe en el shell:* sh firefox32-eng.sh* o *sh firefox32-spa.sh* (depende de cual hayas bajado)
4) Coloca tu clave de administracion cuantas veces sea necesaria...
5) Listo!

**FOR THE EXPERTS**
Estoy planeando distribuir este script en algunas maquinas con Ubuntu AMD64, ¿Cómo pordía hacerlo mas eficiente?

---

### Post by nikoPSK on 2008-01-10
I believe this belongs in tuts and tips. :p

---

### Post by Semong on 2008-01-14
> **nikoPSK said:**
> I believe this belongs in tuts and tips. :p

I second that. I used this to put flash on my little brothers computer with great results. Thanks :)

---

### Post by nikoPSK on 2008-01-14
> **Semong said:**
> I second that. I used this to put flash on my little brothers computer with great results. Thanks :)
 
Guide helped my friend get it on his tower. :KS

---

### Post by ninboy on 2008-01-14
Yeah, I think too this belongs to Tuts, but I want this to help the newcomers in Ubuntu... This is probably the first forums they see...

I like to hear the script helps some people!

I'm planning on making some scripts, i have to thinks which ones, jejeje.

---

### Post by nikoPSK on 2008-01-14
> **ninboy said:**
> Yeah, I think too this belongs to Tuts, but I want this to help the newcomers in Ubuntu... This is probably the first forums they see...

I like to hear the script helps some people!

I'm planning on making some scripts, i have to thinks which ones, jejeje.

No offense, but it will probably get moved, as this is a section for questions.

nikoPSK

---

### Post by ninboy on 2008-01-14
> **[LEFT][COLOR=red][FONT=serif]**_nikoPSK_**[/FONT][/COLOR][/LEFT] said:**
> No offense, but it will probably get moved, as this is a section for questions.

[LEFT][COLOR=red][FONT=serif]**_nikoPSK_**[/FONT][/COLOR][/LEFT]
I've already report it to be moved to the tuts forum... And no offense taken, just [LEFT][COLOR=red][FONT=serif]**_newbie's_**[/FONT][/COLOR][/LEFT] mistakes, [LEFT][COLOR=red][FONT=serif]**_jejeje_**[/FONT][/COLOR][/LEFT].

---

### Post by nikoPSK on 2008-01-14
> **ninboy said:**
> I've already report it to be moved to the tuts forum... And no offense taken, just [LEFT][COLOR=red][FONT=serif]**_newbie's_**[/FONT][/COLOR][/LEFT]
 mistakes, [LEFT][COLOR=red][FONT=serif]**_jejeje_**[/FONT][/COLOR][/LEFT]
.

That's fine, I had troubles finding where to place threads in my time too. :)

nikoPSK

---

### Post by MavrikX4 on 2008-01-14
Sorry, this may be a lame question, but how does one download the firefox32 script?  I can't seem to figure out how to get past step 1.

---

### Post by nikoPSK on 2008-01-14
> **MavrikX4 said:**
> Sorry, this may be a lame question, but how does one download the firefox32 script?  I can't seem to figure out how to get past step 1.

it's at the bottom of the post, in attached files. :)

---

### Post by ninboy on 2008-01-14
At the bottom of the post... here...
[IMG]http://i6.photobucket.com/albums/y220/ninboyexe/Screenshot-1.png[/IMG]

---

### Post by nikoPSK on 2008-01-14
Thanks for the screeny for clarification. :D

---

### Post by TRANQU111TY on 2008-01-17
Thanks a lot for the script but when I open Applications -> Internet -> Firefox Web Browser 32bits, my cursor thinks for 5 seconds and then nothing happens?

I am running Gutsy 64bits. Thanks.

---

### Post by nikoPSK on 2008-01-17
what does this return:

drag the link to your desktop or something, right click it, goto properties, launcher tab then copy and paste the command into terminal and give us the output. :)

---

### Post by ninboy on 2008-01-17
The command is firefox32. You can write that in the terminal and give us the output...

I was wondering... Maybe you're trying to open Firefox 32 while having the 64bits firefox open... Am I right? You can't open the both versions at the same time, you can open just one version at the time!

I'm at the U right now, when I get home I read better this post... :-)

---

### Post by oldos2er on 2008-01-17
Just FYI, there already is a script to install Flash on 64-bit Ubuntu. [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by nikoPSK on 2008-01-17
> **ninboy said:**
> The command is firefox32. You can write that in the terminal and give us the output...

I was wondering... Maybe you're trying to open Firefox 32 while having the 64bits firefox open... Am I right? You can't open the both versions at the same time, you can open just one version at the time!

I'm at the U right now, when I get home I read better this post... :-)

thanks, didn't use it, didn't know. :)

---

### Post by TRANQU111TY on 2008-01-27
> **nikoPSK said:**
> what does this return:

drag the link to your desktop or something, right click it, goto properties, launcher tab then copy and paste the command into terminal and give us the output. :)

Sorry I didn't see your reply sooner. I've already switched to 32Bit Ubuntu because my wireless absolutely hates 64Bit :)

---

