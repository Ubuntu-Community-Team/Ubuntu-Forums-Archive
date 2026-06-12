---
title: "skype"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by epq on 2006-11-20
Hello, I am new to Linux but am enjoying the experiense so far.
I have just downloaded Skype 1.3.
When I open it two windows open:
The first asks me to either sign up or enter my username and password, but it will not connect because my proxy settings arent in.
The second is the usual Skype interface, however it is all greyed out. If I click on 'Tools' the only thing I am allowed to do is to change language. I cannot access the 'Options' in order to enter my proxy settings.
Could someone please tell me how I can configure it?
Thank you

---

### Post by dmizer on 2006-11-20
take a look here: [http://forum.skype.com/index.php?showtopic=57430&hl=proxy](http://forum.skype.com/index.php?showtopic=57430&hl=proxy)

i've never had to deal with proxy's, so i don't know how useable that is.  a side note is that if you have opera installed and configured with proxy settings, skype will pull those settings.

---

### Post by epq on 2006-11-24
Im afraid that wasnt very helpful.
Im on a college network, for some reason they are very particular about the programmes through which one can cconnect to the net. Opera doesnt make the list but skype does.
However, the problem is that im not able to do anything with the version of skype that I downloaded without logging in first. 
Hence I cant configure the proxy in order to login.

Has anybody else had this problem?

Any suggestions?

Does anyone know how I could configure the settings by editing some file and bypassing the inactive skype programme?

Thanks

---

### Post by The Mekon on 2006-11-24
There are several links on Skype Forums but this [one ]("http://forum.skype.com/index.php?showtopic=57430&hl=proxy")gives a couple of "work arounds"

Brian

---

### Post by CoolHand on 2006-11-24
I'll be honest here as I don't use a proxy at home but many applications will grab proxy settings from the environment settings.  I don't know if it will work but it is easy and worth a try.  Open a terminal and type
http_proxy="http://my.proxy.com:myport" ; export http_proxy
Then try running Skype again and see if it gets the setting.  If it works you can always set it in your .bashrc file so you don't have to re-enter it.

---

### Post by dmizer on 2006-12-07
> **epq said:**
> Im afraid that wasnt very helpful.
Im on a college network, for some reason they are very particular about the programmes through which one can cconnect to the net. Opera doesnt make the list but skype does.

what?  how does your college network tell you're using opera rather than firefox or internet explorer?  the web browser you use to view webpages should be of no concern to your network's evil overlords.

---

### Post by Ecthelion on 2006-12-07
I installed skype with [automatix.]("http://www.getautomatix.com/")

Very easy...

... maybe you should give it a try...

---

### Post by Mimsy on 2006-12-07
> **dmizer said:**
> what?  how does your college network tell you're using opera rather than firefox or internet explorer?  the web browser you use to view webpages should be of no concern to your network's evil overlords.

Companies do this all the time. IE is allowed for the internet access required for you to do our job, Firefox and/or Opera are blocked. Beats me why, unless they're of the mentality that "we've already paid for it, we might as well get as much use out of it as we can". Almost every office job I've had, they made me use IE exclusively. Bleh. :neutral: 

/Mimsy

---

### Post by dmizer on 2006-12-08
no ... there's a difference between needing to use internet explorer because the crappy office java script web apps require it, and using it for surfing.

even in your office environment, if you wanted to use firefox to simply pull up webpages, you would be able to.  furthermore, there's no way a college campus can have so much controll over what apps a student decides to use to pull up webpages.

the only way the office can prevent you from using your browser of choice is by preventing you from being able to install them.

---

### Post by Mimsy on 2006-12-08
> **dmizer said:**
> the only way the office can prevent you from using your browser of choice is by preventing you from being able to install them.

Exactly. :)

/Mimsy

---

### Post by dmizer on 2006-12-09
the university cannot prevent the op from installing and using his browser of choice.  especially considering he's using ubuntu to begin with.

so i stand by my original statement.  which is, there's nothing the university can do to prevent the op from using opera.

---

### Post by epq on 2007-05-11
they can prevent me from using opera exclusively though...
they are pretty nasty here in Ireland..
the college forces us to go through an authentication process that lasts a minute and must be performed on either firefox or IE

---

