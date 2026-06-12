---
title: "gedit and gPhpedit"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2007-06-01
I've been reading the threads about these, and would like to try them for designing a web page.  In the past I have written the html in a word processor and not used any program.  These seem like the best next step up from that.  

Some things I've not been able to find.

1)  Where do I download or find gedit and get started with it?

2)  Does gPhpedit do all the same things - do you use one or the other or both?

Thanks much for comments.  :)

---

### Post by v8YKxgHe on 2007-06-01
I normally use gPHPEdit for when coding PHP/HTML - it's really a great editor and very lightweight. 

You can install it by going to System->Admin->Synaptic and searching for gPHPEdit, or in terminal if you prefer, type:

```
sudo apt-get install gphpedit
```

To get to Gedit, go to Applications->Accessories->Text Editor.

---

### Post by GoneWithTheWind on 2007-06-01
Thanks much.  :)

I've installed gphpedit.  Is it possible to add it to the panel at the top?

---

### Post by v8YKxgHe on 2007-06-01
There sure is, go to Application->Programming and right-click on gPHPEdit and select - Add to panel =)

---

### Post by GoneWithTheWind on 2007-06-01
Excellent - thank you!  :D

---

### Post by GoneWithTheWind on 2007-06-01
Gedit looks fantastic.  I love the color coding.

Is there somewhere I can paste the code to see what the web page would look like?

Also is there a way to check the code to make sure it's all matching - and does gedit already have all the plugins or do I need to add them?

Thanks.

---

### Post by bobplano on 2007-06-01
> **John Rupp said:**
> Gedit looks fantastic.  I love the color coding.

Is there somewhere I can paste the code to see what the web page would look like?

Also is there a way to check the code to make sure it's all matching - and does gedit already have all the plugins or do I need to add them?

Thanks.

for just plain HTML you can just open the file in your browser. for anything like PHP you need to set up a webserver like apache and then you need to put the files in the root directory for the webserver

---

### Post by GoneWithTheWind on 2007-06-01
> **bobplano said:**
> for just plain HTML you can just open the file in your browser. for anything like PHP you need to set up a webserver like apache and then you need to put the files in the root directory for the webserver

That is very cool, thanks.

Is there any way to check the code for completeness in gedit?

---

### Post by v8YKxgHe on 2007-06-02
How do you mean, completeness? No Editor will be able to tell you if your project is completed or not =D, or do you mean if it's valid?

---

### Post by GoneWithTheWind on 2007-06-02
> **AlexC_ said:**
> How do you mean, completeness? No Editor will be able to tell you if your project is completed or not =D, or do you mean if it's valid?

Yes, to check if it's valid.  :)

---

### Post by v8YKxgHe on 2007-06-02
I normally use [http://validator.w3.org/](http://validator.w3.org/) to check for valid HTML, and if you want true valid PHP code - then set your error_reporting to E_ALL | E_STRICT if on PHP5, or E_ALL on php4

---

### Post by GoneWithTheWind on 2007-06-02
> **AlexC_ said:**
> I normally use [http://validator.w3.org/](http://validator.w3.org/) to check for valid HTML, and if you want true valid PHP code - then set your error_reporting to E_ALL | E_STRICT if on PHP5, or E_ALL on php4

Direct input worked well and - surprise - all valid the first time.  :o

Thanks again.  :)

---

