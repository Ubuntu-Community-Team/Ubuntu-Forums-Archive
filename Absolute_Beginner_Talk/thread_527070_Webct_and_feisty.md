---
title: "Webct and feisty"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by de_battre on 2007-08-16
Hi folks, i am having this problem that i can't solve and i have seen threads where other people have the same problem and no resolutions have been offered. I have recently switched to ubuntu and have everything running pretty much without a hitch. My one problem is i can't load my university's webct page in firefox (2.0.0.5). As i said i have checked around for possible solutions and have found nothing. What is strange is i am pretty sure it was working ok in the first couple of days after i installed feisty, so i don't know what has gone wrong since.  

Oh and i have also tried to load the page in konqueror with no luck. 

Cheers, Thanks in advance for any help!

---

### Post by Happy_Man on 2007-08-16
Then try every browser! Get Opera, get Galeon, get Lynx, even. See what works.

---

### Post by quinnten83 on 2007-08-16
Or if you could be a bit more specific about what does not work about it?

---

### Post by de_battre on 2007-08-16
So you think it's a browser thing rather than a linux thing? Actually on my windows partition i have to open webct in safari rather than firefox now you say it...

thanks

---

### Post by jw5801 on 2007-08-16
It's most likely a Java issue! I'm at Monash uni and we use WebCT and it always gets cranky at me 'cause I don't have a browser it expects (I think it wants IE... which just ain't gonna happen :p) and because I have a different version of Java (Blackdown as opposed to Sun), but it all works fine.

Do you have a Java runtime environment? There isn't one with the default Ubuntu install (due to some of the source code being closed) but you can install it if you have the universe and multiverse repositories enabled. Try: ```
sudo apt-get install sun-java6-bin
``` I'm reasonably sure that's the package you need, if not just search for sun java and you'll find the right one!

EDIT: After reading your post above (posted while I was still writing!) do you mean that WebCT tells you you're using an unsupported browser? Or does something actually fail to load? I've never had any trouble running it using Firefox, in both Windows and Linux (once I got the Java thing fixed anyway), in spite of Firefox being an 'unsupported' browser. Although given the number of Firefox users I have no idea why this is the case!

---

### Post by thefoolisme on 2007-08-16
You could try installing the IE tab in Firefox.  

[https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419)

It allows IE sites to open in Firefox.  That might fix your problem.  I haven't used WebCT in Ubuntu, but I have been using WebTycho (similar thing).  I find that it works well with the IE tab installed.  

There are also ways to install IE with Wine, and if you do a search, you will come up with posts like this one:  
[http://ubuntuforums.org/showthread.php?t=466342&highlight=internet+explorer+plugin](http://ubuntuforums.org/showthread.php?t=466342&highlight=internet+explorer+plugin)

I would try using the plug-in first.  :-)  It may just solve your problems.

---

### Post by de_battre on 2007-08-16
> **quinnten83 said:**
> Or if you could be a bit more specific about what does not work about it?

Well, after the login the page just hangs. It keeps saying it is loading but never actually loads. And actually some of the time i can't even get to the login page for the same reason. It is the same problem in firefox, konqueror and now galeon. I think i may have also tried epiphany as well. 

Thanks

---

### Post by jw5801 on 2007-08-16
> **thefoolisme said:**
> You could try installing the IE tab in Firefox.  

[https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419)

It allows IE sites to open in Firefox.
Hey nifty... I didn't know about that but I'll keep it in mind!

EDIT:
[quote=IE Tab Site] Works with:

    * Firefox Firefox: 1.5 &#8211; 3.0a5

Install Now (Windows)
IE Tab is not available for Linux.[/quote]
:(

---

### Post by de_battre on 2007-08-16
> **thefoolisme said:**
> You could try installing the IE tab in Firefox.  

[https://addons.mozilla.org/en-US/firefox/addon/1419](https://addons.mozilla.org/en-US/firefox/addon/1419)

It allows IE sites to open in Firefox.  That might fix your problem.  I haven't used WebCT in Ubuntu, but I have been using WebTycho (similar thing).  I find that it works well with the IE tab installed.  

There are also ways to install IE with Wine, and if you do a search, you will come up with posts like this one:  
[http://ubuntuforums.org/showthread.php?t=466342&highlight=internet+explorer+plugin](http://ubuntuforums.org/showthread.php?t=466342&highlight=internet+explorer+plugin)

I would try using the plug-in first.  :-)  It may just solve your problems.

Thanks, i just followed the plug-in link and it said that it is not available for linux!

---

### Post by de_battre on 2007-08-16
> **jw5801 said:**
> It's most likely a Java issue! I'm at Monash uni and we use WebCT and it always gets cranky at me 'cause I don't have a browser it expects (I think it wants IE... which just ain't gonna happen :p) and because I have a different version of Java (Blackdown as opposed to Sun), but it all works fine.

Do you have a Java runtime environment? There isn't one with the default Ubuntu install (due to some of the source code being closed) but you can install it if you have the universe and multiverse repositories enabled. Try: ```
sudo apt-get install sun-java6-bin
``` I'm reasonably sure that's the package you need, if not just search for sun java and you'll find the right one!

EDIT: After reading your post above (posted while I was still writing!) do you mean that WebCT tells you you're using an unsupported browser? Or does something actually fail to load? I've never had any trouble running it using Firefox, in both Windows and Linux (once I got the Java thing fixed anyway), in spite of Firefox being an 'unsupported' browser. Although given the number of Firefox users I have no idea why this is the case!

Hi, i actually thought this was the issue when first came up against it so i installed java. The pages still would not render properly, though and continued to say i needed a java plug in. I might try removing and installing again???

---

### Post by jw5801 on 2007-08-16
You could try that. Are you running 32-bit or 64-bit and which version of java did you install.
Also make sure you install the browser plugin... I forgot about that bit :$
I'm not sure what the sun plugin package is called: I run 64-bit and there isn't one, but if you're on 64-bit then I can tell you exactly what to install. A search in synaptic ought to tell you about 32-bit though.

---

### Post by de_battre on 2007-08-16
64 bit or 32 bit? I am not sure...i am a pretty unsophisticated user. How can i find out?

Ummm i just used the command you suggested in the terminal and installed it. Is there any more i need to do for it to work?

Cheers

---

### Post by de_battre on 2007-08-16
> **jw5801 said:**
> You could try that. Are you running 32-bit or 64-bit and which version of java did you install.
Also make sure you install the browser plugin... I forgot about that bit :$
I'm not sure what the sun plugin package is called: I run 64-bit and there isn't one, but if you're on 64-bit then I can tell you exactly what to install. A search in synaptic ought to tell you about 32-bit though.
 

The new java install worked! it is working fine now, i don't understand why it didn't work with the previous installation.

Anyway, it looks like problem solved! Thank you so much. If i'm ever at monash i owe you a coke...

---

### Post by jw5801 on 2007-08-16
Hehe, if you don't know then it's probably 32-bit. There is a 64-bit distribution of Ubuntu for use with 64-bit processors (although a 64-bit processor can still run a 32-bit OS). 32-bit is the norm but there's pro's and con's for each (there's also hundreds of threads discussing these, so lets not turn this into one).
You'll need to find a firefox plugin that will allow firefox to use the Java app you just installed. A quick search tells me it's: ```
sudo apt-get instal sun-java6-plugin
```
This is all assuming that the WebCT problem is java related of course... If it's not then we'll have to try and sus out what the error might be!

EDIT: Posted above! :p Yay coke!

---

### Post by de_battre on 2007-08-18
Hi, this is embarrassing... false alarm. I still have the same problem. It has worked a few times since re-installing java but it is mostly up to the same old tricks. I have tried heaps of browsers now (except opera, i couldn't get that to work) and they all fail to load my webct page. I also tried to load the page in firefox on my windows partition and it worked fine there. This must be a linux thing...

---

### Post by de_battre on 2007-08-18
bump

---

### Post by jw5801 on 2007-08-18
Hmm... What exactly happens when you try to load the page? Does it load all but parts of it? Or does it completely crash firefox? Or does it just not load anything and leave you with a white page?
You could try opening the error console (tools > error console) in firefox and then loading the page to see if it gives you anything useful there.

---

### Post by de_battre on 2007-08-18
> **jw5801 said:**
> Hmm... What exactly happens when you try to load the page? Does it load all but parts of it? Or does it completely crash firefox? Or does it just not load anything and leave you with a white page?
You could try opening the error console (tools > error console) in firefox and then loading the page to see if it gives you anything useful there.


I just get a white page ...nothing loads at all. Much of the time, even the login page fails to load.

---

### Post by jw5801 on 2007-08-19
What does the error console have to say?

---

