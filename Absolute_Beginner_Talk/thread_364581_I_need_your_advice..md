---
title: "I need your advice."
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by paker on 2007-02-18
Situation:

1) This is about my friend's computer. His need is word processor (he is writing a book now) and e-mail. He has $10 Juno dialup.

2) I installed Ubuntu 6.10 32 bit on his machine. It works well. But the modem part I cannot test because I dont' have dialup.

Questions:

1) Do you anticipate difficulty with Juno dialup? Or dialup in general?
2) Can he convert a OpenOrg document to $.DOC format later, if his publisher wants *.DOC format?
3) Can OpenOrg read *.DOC?

Thanks.

---

### Post by teaker1s on 2007-02-18
I've had problems with an intel modem that wasn't supported any more in linux. in my country we have pay as you go dial up-with no contract. do you have similar in your country to test modem

---

### Post by k1001001 on 2007-02-18
I don't know about the modem, but OpenOffice 2.0 integrates perfectly with Microsoft Office as far as I know. At least basic word processing will. I don't know about any complicated things like tables or macros or anything.

---

### Post by paker on 2007-02-18
Thanks for the info on OpenOrg-Microsoft compatibility. His need is basic editing, no macros.

The modem card has Intel chip. I guess it can be a problem. Thanks.

---

### Post by laidback on 2007-02-18
Question 2 and 3

Yes you can convert both ways but you might loose some of the formatting.

Make sure you have Miscrosoft's Truetype fonts installed:-

msttcorefonts  
     in synaptic package manager

I've found this helps with compatability. It's not perfect in my experience, but can be quite/very good. Number of pages and page layout go off when my wife sends me things from work. She uses Word, I of course use OOowriter. We haven't finished our tests yet but have had trouble with tables. We could only edit part of it from within Writer. But this may be due to my/our systems, more test are needed.

I'd be interested to know how you get on.

On question 1 my advice is to use a router/modem via ethernet.

---

### Post by teaker1s on 2007-02-18
Maybe, while I can't remember the model I remember that intel didn't support the dapper kernel. I got as far as dialing out and conecting and  being disconnected. I would check the intel model support first.

---

### Post by K.Mandla on 2007-02-18
> **paker said:**
> 1) Do you anticipate difficulty with Juno dialup? Or dialup in general?
Do you know what kind of modem it is? If I recall correctly, there are some modems which are troublesome, but others that work fine. I think it depends on the model.

---

### Post by Skidpad on 2007-02-18
> **paker said:**
> Situation:

1) This is about my friend's computer. His need is word processor (he is writing a book now) and e-mail. He has $10 Juno dialup.

2) I installed Ubuntu 6.10 32 bit on his machine. It works well. But the modem part I cannot test because I dont' have dialup.

Questions:

1) Do you anticipate difficulty with Juno dialup? Or dialup in general?
2) Can he convert a OpenOrg document to $.DOC format later, if his publisher wants *.DOC format?
3) Can OpenOrg read *.DOC?

Thanks.

I can only help with Q2 & Q3...
You have a couple of options with OOo (2.1 here) regarding compatibility with MS Office when creating and saving documents in OOo.  

If you want to create a document in OOo and send it to an MS user who must **view or modify** it, select "Save As" and then change the file type to "Microsoft Word 97/2000/XP  *.doc".  If you don't do this, your MS user will see nothing but jibberish when opening your OOo document.  (ask me how I know  :D).

If you create a document in OOo and your MS user only needs to **view** the document, OOo has a wonderful option in the File menu called "Export as PDF".  This will automatically create a .pdf version of your document for high cross-platform compatibility.

---

### Post by laidback on 2007-02-19
I've just done my first test with OOo to pdf, fantastic; also .doc to OOo to pdf and then across the net to be printed with a pdf reader. Result, printed pdf version same as OOo. Only slight formatting differences to the original .doc version, which may of course be caused by the way I have my pages defined.

Thanks skidpad for pointing that facility out.
:)

---

### Post by paker on 2007-02-19
Thanks for explaining the available document formats.

---

### Post by Skidpad on 2007-02-19
> **laidback said:**
> I've just done my first test with OOo to pdf, fantastic; also .doc to OOo to pdf and then across the net to be printed with a pdf reader. Result, printed pdf version same as OOo. Only slight formatting differences to the original .doc version, which may of course be caused by the way I have my pages defined.

Thanks skidpad for pointing that facility out.
:)
Your welcome!  Glad to help.

---

