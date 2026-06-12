---
title: "Can you do text to speech in Firefox?"
date: 2006-12-23
forum: Assistive Technology &amp; Accessibility
---

### Post by Sunnz on 2006-12-23
I was wondering it is possible to say, highlight a paragraph in firefox, press a button, and have (Orca) do text to speech to it?

I got this setup in OSX, where I just press Alt-D and it does text to speech to any highlighted words.

---

### Post by kd7swh on 2006-12-28
I don't think Orca has key bindings like that. Gnopernicus may be a good idea. Try it and see if it works for you.

---

### Post by benjaminhawkeslewis on 2006-12-28
Orca works pretty badly with Firefox 2, but should do this fine with Firefox 3 (still in development). For now your best bet would be to use the Fire Vox extension with the FreeTTS speech engine:

[http://www.firevox.clcworld.net/](http://www.firevox.clcworld.net/)

Fire Vox can in theory use Orca as a speech engine, but I found that a somewhat unreliable.

---

### Post by Unreadedpost on 2006-12-29
> **kd7swh said:**
> I don't think Orca has key bindings like that. Gnopernicus may be a good idea. Try it and see if it works for you.
perfect..
T'm reading[ www.unreadedpost.com]("www.unreadedpost.com")

(Quote)

---

### Post by Sunnz on 2007-01-10
> **benjaminhawkeslewis said:**
> Orca works pretty badly with Firefox 2, but should do this fine with Firefox 3 (still in development). For now your best bet would be to use the Fire Vox extension with the FreeTTS speech engine:

[http://www.firevox.clcworld.net/](http://www.firevox.clcworld.net/)

Fire Vox can in theory use Orca as a speech engine, but I found that a somewhat unreliable.
They have a new one called Click Speak I installed it and use it with the Java TTS, pretty cool so far!!! Thanks man!!!

---

### Post by doobit on 2007-01-10
There is Festival. I don't know of anyone who is using it though to give you a review:
[http://www.cstr.ed.ac.uk/projects/festival/](http://www.cstr.ed.ac.uk/projects/festival/)

---

### Post by jackn on 2007-02-16
Sunnz, can you help with the install of Click, Speak?!

I've been struggling with it, but it's come to nothing.
And I'm bothering the write, Charles L. Chen. While he's been very kind about it, maybe you could save him and me some trouble by telling me what to do in Ubunut.

One thing that stumps me, I'm afraid, is that you need admin privileges when installing the Java Runtime. The Jave Runtime is provided in the context menu in the GUI, after I download the CLC4TTS jar. 

But I don't know how to get admin privileges in that context, only in the console.

I think that's why it the installation stops. It tells me:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08 /jre/lib/ext/CLC4TTS_Java.jar (Permission denied).

Help?

Thank,
Jackn

---

### Post by Sunnz on 2007-02-16
Hmmm this is a little confusing.

I guess you have installed the extension, right?

Have you installed Java via apt-get/synaptic?

As far as I recalled, I first run gksu in the terminate, then in the gksu window, I type it "/path/to/java -jar /home/me/CLC4TTS.jar". You'll need to fill in the exact path of your java and the jar file though.

---

### Post by jackn on 2007-02-16
Thank you kindly, Sunnz.

I did finally manage to install Click, Speak and am very happy with it.

Please see [how-to]("http://ubuntuforums.org/showthread.php?t=363915&highlight=click%2C+speak") in these forums.

Jackn

---

### Post by friviere01 on 2009-12-20
Have a look at: [http://ubuntuforums.org/showthread.php?t=363915](http://ubuntuforums.org/showthread.php?t=363915)
**How-To Install Click, Speak, a Web-page Reader (Text-to-Speech) Firefox Extension**

---

### Post by brahmaforces on 2010-03-04
hi all:

i tried to install the software everything went well and it installed. Java is working. I see the 3 icons in the tool bar.  But on pressin g them there is no sound, ie no text to speech after all this.Please help...

---

### Post by JohnPitt on 2010-06-09
I know I'm very late to reply to this thread but I hope it'll help Googlers who are searching for similar answer.  So, have you guys tried Firefox add-on [Text to Voice]("https://addons.mozilla.org/en-US/firefox/addon/91405/") ?  It is very simple, light but yet powerful add-on.  You may download it from AMO website using the link below:

[https://addons.mozilla.org/en-US/firefox/addon/91405/](https://addons.mozilla.org/en-US/firefox/addon/91405/)

---

### Post by biloyp on 2010-06-25
Text to Voice worked perfectly after the install. I have tried and worked on getting many of the others to work but no luck. This one was soooooo easy to install and get to work. Finally!!!! Use Text to Voice add on along with the Readability add on and selecting text is super easy, You need to select text so Text to Voice can read. Wish there was a way to adjust the speed of the reader and not to read a period as a dot, just skip it but hey at least it works. 

Seems like the Text to Voice has some problems if you select too much text for it Cd and it to read. It works but not very practical for reading lots of text at once. I did download and run Vinux from its LiveCD and although the voice is really robotic but it reads your desktop, where your mouse is and webpages. Just wish the voices were better.

---

### Post by surfsteve on 2011-06-20
> **Sunnz said:**
> They have a new one called Click Speak I installed  it and use it with the Java TTS, pretty cool so far!!! Thanks  man!!!

What version of Firefox are you currently running? I tried all day  yesterday to install QuickSpeak on 11.04 and it said it was incompatible  with my 4.0 version of Firefox. 

I downloaded an older version of firefox but I couldn't get it to  install on Ubuntu. Is there some sort of trick or are you stuck with the  firefox that comes with your Ubuntu?

Is there anywhere I can download an older version of Ubuntu that will support ClickSpeak?

I am at a loss of what to do.  I been using Readplease since the year  2000 which only runs on Windows XP.  Why does it seem like operating  systems and browsers are being built so as not to support these types of  programs? Before I discovered Readplease my eyes would tire after  reading 20 pages. Since Readplease I've been able to easily listen to over  200 pages a day for the past 12 years.  It seems barbaric to have to  give that technology up under the guise of progress.

---

### Post by stangw on 2011-06-23
No, i couldn't do that, i think it's cool if anyone could do that

---

### Post by startgame412 on 2011-07-03
Just downloaded and installed FoxVox speech addon. It works but the voice is not that good. Has anyone tired it?

---

