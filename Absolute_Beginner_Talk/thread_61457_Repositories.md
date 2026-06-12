---
title: "Repositories"
date: 2005-08-31
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-31
One can either go and follow the ubuntuguide for adding extra repositories, via command line and  that uncommenting business. Except i never find my section corresponds to either section 3 or 4 exactly. And so i always find that there is an element of luck and guess involved as far as uncommenting and adding to the file.

On the other hand one can simply go to Synaptic Manager/ Settings/ Repositories and do it at the click of a button. 

Why then, does the ubuntuguide not prescribe the  via the Synaptic route  method? Any ideas? is one method better than the other? Does one end up with more packages one way or the other?

I appreciate your counsel on this,


cordially,

sophtpaw

---

### Post by DJ_Max on 2005-08-31
It's easier to explain how to copy and paste, rather then open, click this option, open that dialog, and enter each URL in that.

Plus copy and paste is a lot simpler.

Synaptic is just an interface for APT, so it simply adds the lines to /etc/apt/sources.list. No difference.

---

### Post by jasmuz on 2005-08-31
I consider that uncommenting and adding extra repositories via command line, is far quicker than opening the Synaptic interface. You end up with the same result either way, but using the terminal  is far more fun and practical.

---

### Post by sophtpaw on 2005-08-31
[QUOTE=jasmuz]I consider that uncommenting and adding extra repositories via command line, is far quicker than opening the Synaptic interface. You end up with the same result either way, but using the terminal  is far more fun and practical.[/QUOTE]


Thank you for the feedback. Good to know that both achieve the same end. However, i do find clicking on Synaptic/ Repositories/ Settings as quick as one two three. 

I don't mind following clear instructions in command line, and i love the ubuntuguide but that particular one i find hard to follow. I find it very hard as said to match my source files with section 3 or 4 and finding what is to be uncommented. so, i'm quite surprised to hear you guys saying it is more practical and quicker,

thx again,

--
sophtpaw

---

### Post by weasel fierce on 2005-09-01
I think its more a case of habit really. I find synaptic easier in general too, unless Im looking for something really specific

---

### Post by xmastree on 2005-09-01
[QUOTE=sophtpaw]I find it very hard as said to match my source files with section 3 or 4 and finding what is to be uncommented. [/QUOTE]I found that, as I'm in a different country, all the repos were different. I just copied and pasted the whole thing from the guide.

As for what to uncomment, everything that looks like a url with a comment (#) in front of it. Remove the #

easy.

---

### Post by xmastree on 2005-09-01
[QUOTE=weasel fierce]I think its more a case of habit really. I find synaptic easier in general too, unless Im looking for something really specific[/QUOTE]I often use synaptic just to see what's out there. Select a section and browse the offerings.

---

### Post by Lord Illidan on 2005-09-01
Yeah, and sometimes apt-get doesn't work, so I use synaptic...

---

### Post by poofyhairguy on 2005-09-01
[QUOTE=sophtpaw]
Why then, does the ubuntuguide not prescribe the  via the Synaptic route  method? 
[/QUOTE]

Besides the answers given, the reason synaptic is not used as the route there or anywhere in the guide is because the margin of error with copying and pasting is lower (I know there is an initial fear, but you don't have to know what you are copying for it to work). Also the guide is a volunteer project that uses a lot of bandwidth as it is, and to do a synaptic guide correctly would require screenshots that would cripple the site.

After Breezy if some kind soul wants to host it, I would make a GUI Ubuntu Guide myself.

---

### Post by Hobbsee on 2005-09-01
[QUOTE=xmastree]I found that, as I'm in a different country, all the repos were different. I just copied and pasted the whole thing from the guide.

As for what to uncomment, everything that looks like a url with a comment (#) in front of it. Remove the #

easy.[/QUOTE]

Then you just got rid of all your local mirrors for the file, which ends up taking longer for each file to download, as it has to go half way around the globe first - that's the point of mirrors, to stop that happening.

The ubuntuguide repository text that you are supposed to replace doesnt seem to match up to what the original sources lists say, in either ubuntu or kubuntu (as i've tried both).  However, check the edited sample - it shows where the lines are supposed to be placed.

---

### Post by sophtpaw on 2005-09-01
Poofyhariguy,

You say, "...the margin of error with copying and pasting is lower (I know there is an initial fear, but you don't have to know what you are copying for it to work). Also the guide is a volunteer project that uses a lot of bandwidth as it is, and to do a synaptic guide correctly would require screenshots that would cripple the site."

I don't understand where the margin of error using Synaptic could be?

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)  
makes it pretty simple.

" I would make a GUI Ubuntu Guide myself"

I think alot of people would appreciate that!  

I would!   O:) 


--
sophtpaw

---

### Post by Wolki on 2005-09-01
[QUOTE=sophtpaw]
I don't understand where the margin of error using Synaptic could be?

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)  
makes it pretty simple.[/QUOTE]

Just take a look at how long that wiki entry is, plus pictures and everything. Simple, but long. While that has its good parts (they can actually explain a little) its not really a concise, short guide anymore, right? :)

---

### Post by aysiu on 2005-09-01
[QUOTE=poofyhairguy]
After Breezy if some kind soul wants to host it, I would make a GUI Ubuntu Guide myself.[/QUOTE] Likewise. I love making screenshot tutorials to help out people, but when I look at the bandwidth demand on my website, almost all of it is for .jpg or .png.

Maybe what we should do is create a .pdf GUI tutorial and ask for volunteers to host it on mirror sites for download...

---

### Post by xmastree on 2005-09-02
[QUOTE=Hobbsee]Then you just got rid of all your local mirrors for the file, which ends up taking longer for each file to download, as it has to go half way around the globe first - that's the point of mirrors, to stop that happening.[/QUOTE]Maybe, but maybe not...
I read on another forum, Philippine based but hosted in the USA, that the backbone in here isn't complete, and most traffic goes via the US anyway. So I may have cut the distance in half.

---

