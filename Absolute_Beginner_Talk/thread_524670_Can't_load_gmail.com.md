---
title: "Can't load gmail.com"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by hannulan on 2007-08-13
I can't load gmail.com in Firefox. I did work yesterday and I can load other webpages, I can ping gmail.com and I can load it using epiphany. What can I have done wrong?

---

### Post by snyling on 2007-08-13
did you make any changes in the settings for your router? Does hotmail.com or microsoft.com load? If they don't it may be a problem with your maximum transmission unit setting.

---

### Post by stchman on 2007-08-13
> **hannulan said:**
> I can't load gmail.com in Firefox. I did work yesterday and I can load other webpages, I can ping gmail.com and I can load it using epiphany. What can I have done wrong?

Is there a possibility that Gmail was down for a bit.  If you are able to load other web pages with no problem then you should nto be excluded from other sites.

---

### Post by nvrpunk on 2007-08-13
Clear cookies and cache, try again.

---

### Post by hannulan on 2007-08-13
I haven't changed anything with the router and gmail.com is not down. I can load it using epiphany, and I can ping gmail.com. 

I have also tried to clear all private data including cookies and cache, but it haven't help me. 

I can load hotmail.com and microsoft.com and other webpages I have tried to visit.

Any other idea?

---

### Post by nvrpunk on 2007-08-13
hmm try google.mail.com?  I am not sure but you possibly blocked something in your firefox setting.  I would love to tell you to just delete a folder.  But it holds plugins.  so um...  sudo apt-get update then sudo apt-get install firefox?  maybe reinstalling it will work.  you should uninstall it first.

---

### Post by nichipet on 2007-08-13
> **hannulan said:**
> I haven't changed anything with the router and gmail.com is not down. I can load it using epiphany, and I can ping gmail.com. 

I have also tried to clear all private data including cookies and cache, but it haven't help me. 

I can load hotmail.com and microsoft.com and other webpages I have tried to visit.

Any other idea?

Try disabling your extensions. If you can connect, enable your extensions one at a time to see which one caused the problem.

---

### Post by nitro_n2o on 2007-08-13
Try this: 
[https://mail.google.com](https://mail.google.com) it should work.. i'm not sure why.. but it should solve your problem

---

### Post by davidjmayo on 2007-08-13
> **nvrpunk said:**
> hmm try google.mail.com?  I am not sure but you possibly blocked something in your firefox setting. .

I thought that too but it should be
mail.google.com (the google.mail.com doesn't resolve)

BTW if you type gmail.com it resolves to mail.google.com to connect to the gmail login page

---

### Post by nvrpunk on 2007-08-13
sorry for the transposition.  Happens :/  but hopefully all this input leads to a solution :)

---

### Post by davidjmayo on 2007-08-13
> **nvrpunk said:**
> sorry for the transposition.  Happens :/  but hopefully all this input leads to a solution :)

don't worry about the transposition. I never tried that before so did it out of curiosity (only wanted to point out to OP that it doesn't resolve)

---

### Post by hannulan on 2007-08-13
Tried to reinstall friefox but nothing happened. Than I recognized some broken packages. Quickly forget their names but I thought they had something to do with latex. Fixed the broken packages and now I can use gmail with firefox again.

---

### Post by huang earnie on 2007-08-14
i've had this problem for a bit.  gmail will only load sporadically.  have reinstalled firefox and all that other jazz.  any recommendations on (latex?!) packages to fix would be most welcome!

---

### Post by hannulan on 2007-08-17
I think i could have something to do with secure homepages and ssl (secure sockets layer). If I try hard to remember which other pages i tried to visit i can recognize some other page that didn't and could have used the ssl protocoll. 

One way to see your broken packages is to run aptitude (just type aptitude in the console) and will tell which of your packages are broken. I don't know how to tell aptitude to reinstall the broken packages (someone else can maybe tell me). If there are just a few packages I reinstall by hand.

---

### Post by ukurko on 2008-07-18
Did this ever get fixed?  I have the exact same issue - I posted a question in the absolute beginners forum on it, but them it seemed to fix itself - now it is back it's intermittent but very annoying - and when it's happening I can't load Gmail using Opera or Firefox.  I haven't changed anything recently other than loading updates.

Ubuntu 8.04, Firefox 3

Annoyingly (because I prefer Ubuntu), if I reboot into vista on this machine I can log in to Gmail no problem using Firefox and IE

---

### Post by Reiger on 2008-07-18
Try enabling JavaScript. AFAIK Firefox disables it by default, you know, security and all that jazz. 

Of course, you could also use Opera instead. ;-)

---

### Post by thane1 on 2008-07-18
Hannulan;
     Have you tried using any other email programs to access your Gmail acct?
I traditionally use one email prog for my main email useage and access my  Gmail acct through this prog for business, etc contacts.  Gmail has always worked flawlessly this way for me using either Kmail or now Thunderbird as my main mail program, which I use to also read my Gmail.  If you're running another mail program besides Gmail, I can give you the settings to access your Gmail from the other mail prog if you'd like.

---

### Post by ukurko on 2008-07-22
> **thane1 said:**
> Hannulan;

     Have you tried using any other email programs to access your Gmail acct?

I traditionally use one email prog for my main email useage and access my  Gmail acct through this prog for business, etc contacts.  Gmail has always worked flawlessly this way for me using either Kmail or now Thunderbird as my main mail program, which I use to also read my Gmail.  If you're running another mail program besides Gmail, I can give you the settings to access your Gmail from the other mail prog if you'd like.

I'm (and I don't think Hannulan was) not talking about using an e-mail program - I'm talking about accessing Gmail in a browser.

> **Reiger said:**
> Try enabling JavaScript. AFAIK Firefox disables it by default, you know, security and all that jazz. 




Of course, you could also use Opera instead. ;-)

Tried that - it's no different.  Epipany will load the list of mail in the inbox page but not any individual messages

---

